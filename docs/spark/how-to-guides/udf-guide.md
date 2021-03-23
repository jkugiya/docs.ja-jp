---
title: .NET for Apache Spark でユーザー定義関数 (UDF) を作成する
description: .NET for Apache Spark アプリケーションでユーザー定義関数 (UDF) を実装する方法を学習します。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 13898bdbd9522730c8f0cd19bd13d4e6f3a6a10e
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874070"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a>.NET for Apache Spark でユーザー定義関数 (UDF) を作成する

この記事では、.NET for Apache Spark でユーザー定義関数 (UDF) を使用する方法を学習します。 [UDF](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) は、システムの組み込み機能を拡張するためにカスタム関数を使用できるようにする Spark の機能です。 UDF では、テーブル内の 1 行から値を変換し、UDF で定義されているロジックに基づいて、行ごとに 1 つの対応する出力値を生成します。

## <a name="define-udfs"></a>UDF を定義する

次の UDF の定義を確認します。

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

UDF では、[Dataframe](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24) の [Column](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) の形式で入力として `string` を受け取り、入力の前に `hello` が追加された `string` を返します。

次の DataFrame `df` には、名前の一覧が含まれています。

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

次は、上記の定義された `udf` を DataFrame `df` に適用してみましょう。

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

以下の DataFrame `udfResult` は、UDF の結果です。

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

UDF を実装する方法について理解を深めるために、GitHub の [UDF ヘルパー関数](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616)と[例](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49)を参照してください。

## <a name="udf-serialization"></a>UDF のシリアル化

UDF は worker で実行する必要がある関数であるため、シリアル化し、ドライバーからのペイロードの一部として worker に送信する必要があります。 現在のデリゲートでインスタンス メソッドを呼び出すクラス インスタンスである、その[ターゲット](xref:System.Delegate.Target%2A)だけでなく、メソッドへの参照である、[デリゲート](../../csharp/programming-guide/delegates/index.md)もシリアル化する必要があります。 この [GitHub のコード例](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149)を確認し、UDF のシリアル化がどのように行われるかについて理解を深めてください。

.NET for Apache Spark では、デリゲートのシリアル化がサポートされていない .NET Core が使用されます。 代わりに、リフレクションを使用して、デリゲートが定義されているターゲットをシリアル化します。 共通のスコープで複数のデリゲートが定義されている場合、シリアル化に対するリフレクションのターゲットとなる共有クロージャがあります。

### <a name="serialization-example"></a>シリアル化の例

次のコード スニペットでは、結果としてそれぞれの文字列を返す 2 つの関数デリゲートで参照されている 2 つの文字列変数を定義します。

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

上記の C# コードでは、コンパイラから次の C# 逆アセンブリ (クレジット ソース: [sharplab.io](https://sharplab.io)) コードが生成されます。

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

`func` と `func2` の両方で同じクロージャ `<>c__DisplayClass0_0` が共有されます。これは、デリゲート `func` および `func2` をシリアル化するときにシリアル化されるターゲットです。 `Func<string, string> a` で `s1` のみが参照される場合でも、バイトが worker に送信されるときに `s2` もシリアル化されます。

これにより、実行時に何らかの予期しない動作が発生する可能性があります ([ブロードキャスト変数](broadcast-guide.md)を使用する場合など)。そのため、関数で使用される変数の可視性をその関数のスコープに制限することをお勧めします。

次のコード スニペットは、必要なシリアル化動作を実装するために推奨される方法です。

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

上記の C# コードでは、コンパイラから次の C# 逆アセンブリ (クレジット ソース: [sharplab.io](https://sharplab.io)) コードが生成されます。

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

`func` と `func2` でクロージャが共有されなくなり、それぞれに独自の個別のクロージャ `<>c__DisplayClass0_0` と `<>c__DisplayClass0_1` があることに注目してください。 シリアル化のターゲットとして使用される場合、デリゲートのためにシリアル化されるのは、参照される変数のみとなります。 共通のスコープで複数の UDF を実装する場合は、この動作に注意することが重要です。

## <a name="some-spark-udf-caveats"></a>Spark UDF に関するいくつかの注意事項

* UDF の null 値では、例外がスローされる場合があります。 これを処理するのは開発者の責任です。
* UDF では、Spark の組み込み関数によって提供される最適化が利用されないため、可能な限り組み込み関数を使用することをお勧めします。

## <a name="faqs"></a>FAQ

**引数または戻り値の型として `ArrayType`、`MapType`、`ArrayList`、または `HashTable` を使用して UDF を呼び出そうとすると、エラー `System.NotImplementedException: The method or operation is not implemented.` または `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` が表示されるのは、なぜですか。**  
`ArrayType` と `MapType` のサポートは [v1.0](https://github.com/dotnet/spark/releases/tag/v1.0.0) まで提供されていません。そのため、このエラーが発生するのは、それ以前のバージョンの Apache Spark で .NET を使用していて、これらの型を UDF の引数として、または戻り値の型として渡そうとした場合です。
`ArrayList` および `HashTable` の型は非ジェネリック コレクションであるため、UDF の戻り値の型としてサポートすることはできません。したがって、その要素の型定義を Spark に指定することはできません。

## <a name="next-steps"></a>次の手順

* [.NET for Apache Spark の概要](../tutorials/get-started.md)
* [Windows で .NET for Apache Spark アプリケーションをデバッグする](debug.md)
