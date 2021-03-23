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
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a><span data-ttu-id="31551-103">.NET for Apache Spark でユーザー定義関数 (UDF) を作成する</span><span class="sxs-lookup"><span data-stu-id="31551-103">Create user-defined functions (UDF) in .NET for Apache Spark</span></span>

<span data-ttu-id="31551-104">この記事では、.NET for Apache Spark でユーザー定義関数 (UDF) を使用する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="31551-104">In this article, you learn how to use user-defined functions (UDF) in .NET for Apache Spark.</span></span> <span data-ttu-id="31551-105">[UDF](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) は、システムの組み込み機能を拡張するためにカスタム関数を使用できるようにする Spark の機能です。</span><span class="sxs-lookup"><span data-stu-id="31551-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) are a Spark feature that allow you to use custom functions to extend the system's built-in functionality.</span></span> <span data-ttu-id="31551-106">UDF では、テーブル内の 1 行から値を変換し、UDF で定義されているロジックに基づいて、行ごとに 1 つの対応する出力値を生成します。</span><span class="sxs-lookup"><span data-stu-id="31551-106">UDFs transform values from a single row within a table to produce a single corresponding output value per row based on the logic defined in the UDF.</span></span>

## <a name="define-udfs"></a><span data-ttu-id="31551-107">UDF を定義する</span><span class="sxs-lookup"><span data-stu-id="31551-107">Define UDFs</span></span>

<span data-ttu-id="31551-108">次の UDF の定義を確認します。</span><span class="sxs-lookup"><span data-stu-id="31551-108">Review the following UDF definition:</span></span>

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

<span data-ttu-id="31551-109">UDF では、[Dataframe](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24) の [Column](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) の形式で入力として `string` を受け取り、入力の前に `hello` が追加された `string` を返します。</span><span class="sxs-lookup"><span data-stu-id="31551-109">The UDF takes a `string` as an input in the form of a [Column](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) of a [Dataframe](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) and returns a `string` with `hello` appended in front of the input.</span></span>

<span data-ttu-id="31551-110">次の DataFrame `df` には、名前の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="31551-110">The following DataFrame `df` contains a list of names:</span></span>

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

<span data-ttu-id="31551-111">次は、上記の定義された `udf` を DataFrame `df` に適用してみましょう。</span><span class="sxs-lookup"><span data-stu-id="31551-111">Now let's apply the above defined `udf` to the DataFrame `df`:</span></span>

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

<span data-ttu-id="31551-112">以下の DataFrame `udfResult` は、UDF の結果です。</span><span class="sxs-lookup"><span data-stu-id="31551-112">The following DataFrame `udfResult` is the result of the UDF:</span></span>

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

<span data-ttu-id="31551-113">UDF を実装する方法について理解を深めるために、GitHub の [UDF ヘルパー関数](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616)と[例](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31551-113">To better understand how to implement UDFs, review the [UDF helper functions](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) and [examples](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) on GitHub.</span></span>

## <a name="udf-serialization"></a><span data-ttu-id="31551-114">UDF のシリアル化</span><span class="sxs-lookup"><span data-stu-id="31551-114">UDF serialization</span></span>

<span data-ttu-id="31551-115">UDF は worker で実行する必要がある関数であるため、シリアル化し、ドライバーからのペイロードの一部として worker に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31551-115">Because UDFs are functions that need to be executed on workers, they have to be serialized and sent to the workers as part of the payload from the driver.</span></span> <span data-ttu-id="31551-116">現在のデリゲートでインスタンス メソッドを呼び出すクラス インスタンスである、その[ターゲット](xref:System.Delegate.Target%2A)だけでなく、メソッドへの参照である、[デリゲート](../../csharp/programming-guide/delegates/index.md)もシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="31551-116">The [delegate](../../csharp/programming-guide/delegates/index.md), which is a reference to the method, needs to be serialized as well as its [target](xref:System.Delegate.Target%2A), which is the class instance on which the current delegate invokes the instance method.</span></span> <span data-ttu-id="31551-117">この [GitHub のコード例](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149)を確認し、UDF のシリアル化がどのように行われるかについて理解を深めてください。</span><span class="sxs-lookup"><span data-stu-id="31551-117">Review this [code example in GitHub](https://github.com/dotnet/spark/blob/main/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) to get a better understanding of how UDF serialization is being done.</span></span>

<span data-ttu-id="31551-118">.NET for Apache Spark では、デリゲートのシリアル化がサポートされていない .NET Core が使用されます。</span><span class="sxs-lookup"><span data-stu-id="31551-118">.NET for Apache Spark uses .NET Core, which doesn't support serializing delegates.</span></span> <span data-ttu-id="31551-119">代わりに、リフレクションを使用して、デリゲートが定義されているターゲットをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="31551-119">Instead, reflection is used to serialize the target where the delegate is defined.</span></span> <span data-ttu-id="31551-120">共通のスコープで複数のデリゲートが定義されている場合、シリアル化に対するリフレクションのターゲットとなる共有クロージャがあります。</span><span class="sxs-lookup"><span data-stu-id="31551-120">When multiple delegates are defined in a common scope, they have a shared closure that becomes the target of reflection for serialization.</span></span>

### <a name="serialization-example"></a><span data-ttu-id="31551-121">シリアル化の例</span><span class="sxs-lookup"><span data-stu-id="31551-121">Serialization example</span></span>

<span data-ttu-id="31551-122">次のコード スニペットでは、結果としてそれぞれの文字列を返す 2 つの関数デリゲートで参照されている 2 つの文字列変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="31551-122">The following code snippet defines two string variables that are being referenced in two function delegates that return the respective strings as a result:</span></span>

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

<span data-ttu-id="31551-123">上記の C# コードでは、コンパイラから次の C# 逆アセンブリ (クレジット ソース: [sharplab.io](https://sharplab.io)) コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="31551-123">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="31551-124">`func` と `func2` の両方で同じクロージャ `<>c__DisplayClass0_0` が共有されます。これは、デリゲート `func` および `func2` をシリアル化するときにシリアル化されるターゲットです。</span><span class="sxs-lookup"><span data-stu-id="31551-124">Both `func` and `func2` share the same closure `<>c__DisplayClass0_0`, which is the target that is serialized when serializing the delegates `func` and `func2`.</span></span> <span data-ttu-id="31551-125">`Func<string, string> a` で `s1` のみが参照される場合でも、バイトが worker に送信されるときに `s2` もシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="31551-125">Even though `Func<string, string> a` is only referencing `s1`, `s2` is also serialized when the bytes are sent to the workers.</span></span>

<span data-ttu-id="31551-126">これにより、実行時に何らかの予期しない動作が発生する可能性があります ([ブロードキャスト変数](broadcast-guide.md)を使用する場合など)。そのため、関数で使用される変数の可視性をその関数のスコープに制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="31551-126">This can lead to some unexpected behaviors at runtime (like in the case of using [broadcast variables](broadcast-guide.md)), which is why we recommend that you restrict the visibility of the variables used in a function to that function's scope.</span></span>

<span data-ttu-id="31551-127">次のコード スニペットは、必要なシリアル化動作を実装するために推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="31551-127">The following code snippet is the recommended way to implement the desired serialization behavior:</span></span>

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

<span data-ttu-id="31551-128">上記の C# コードでは、コンパイラから次の C# 逆アセンブリ (クレジット ソース: [sharplab.io](https://sharplab.io)) コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="31551-128">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

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

<span data-ttu-id="31551-129">`func` と `func2` でクロージャが共有されなくなり、それぞれに独自の個別のクロージャ `<>c__DisplayClass0_0` と `<>c__DisplayClass0_1` があることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="31551-129">Notice that `func` and `func2` no longer share a closure, and they have their own separate closures `<>c__DisplayClass0_0` and `<>c__DisplayClass0_1` respectively.</span></span> <span data-ttu-id="31551-130">シリアル化のターゲットとして使用される場合、デリゲートのためにシリアル化されるのは、参照される変数のみとなります。</span><span class="sxs-lookup"><span data-stu-id="31551-130">When used as the target for serialization, nothing other than the referenced variables will get serialized for the delegate.</span></span> <span data-ttu-id="31551-131">共通のスコープで複数の UDF を実装する場合は、この動作に注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="31551-131">This behavior is important to keep in mind while implementing multiple UDFs in a common scope.</span></span>

## <a name="some-spark-udf-caveats"></a><span data-ttu-id="31551-132">Spark UDF に関するいくつかの注意事項</span><span class="sxs-lookup"><span data-stu-id="31551-132">Some Spark UDF caveats</span></span>

* <span data-ttu-id="31551-133">UDF の null 値では、例外がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="31551-133">Null values in UDFs can throw exceptions.</span></span> <span data-ttu-id="31551-134">これを処理するのは開発者の責任です。</span><span class="sxs-lookup"><span data-stu-id="31551-134">It's the responsibility of the developer to handle them.</span></span>
* <span data-ttu-id="31551-135">UDF では、Spark の組み込み関数によって提供される最適化が利用されないため、可能な限り組み込み関数を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="31551-135">UDFs don't leverage the optimizations provided by Spark's built-in functions, so it's recommended to use built-in functions where possible.</span></span>

## <a name="faqs"></a><span data-ttu-id="31551-136">FAQ</span><span class="sxs-lookup"><span data-stu-id="31551-136">FAQs</span></span>

<span data-ttu-id="31551-137">**引数または戻り値の型として `ArrayType`、`MapType`、`ArrayList`、または `HashTable` を使用して UDF を呼び出そうとすると、エラー `System.NotImplementedException: The method or operation is not implemented.` または `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` が表示されるのは、なぜですか。**</span><span class="sxs-lookup"><span data-stu-id="31551-137">**Why do I get the error `System.NotImplementedException: The method or operation is not implemented.` or `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` when trying to call a UDF with `ArrayType`, `MapType`, `ArrayList`, or `HashTable` as argument or return type?**</span></span>  
<span data-ttu-id="31551-138">`ArrayType` と `MapType` のサポートは [v1.0](https://github.com/dotnet/spark/releases/tag/v1.0.0) まで提供されていません。そのため、このエラーが発生するのは、それ以前のバージョンの Apache Spark で .NET を使用していて、これらの型を UDF の引数として、または戻り値の型として渡そうとした場合です。</span><span class="sxs-lookup"><span data-stu-id="31551-138">Support for `ArrayType` and `MapType` is not provided until [v1.0](https://github.com/dotnet/spark/releases/tag/v1.0.0), and so you would get this error if using a .NET for Apache Spark version prior to that, and trying to pass these types either as arguments to the UDF or as a return type.</span></span>
<span data-ttu-id="31551-139">`ArrayList` および `HashTable` の型は非ジェネリック コレクションであるため、UDF の戻り値の型としてサポートすることはできません。したがって、その要素の型定義を Spark に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="31551-139">`ArrayList` and `HashTable` types cannot be supported as return types of a UDF as they are non-generic collections and hence their element type definitions cannot be provided to Spark.</span></span>

## <a name="next-steps"></a><span data-ttu-id="31551-140">次の手順</span><span class="sxs-lookup"><span data-stu-id="31551-140">Next steps</span></span>

* [<span data-ttu-id="31551-141">.NET for Apache Spark の概要</span><span class="sxs-lookup"><span data-stu-id="31551-141">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="31551-142">Windows で .NET for Apache Spark アプリケーションをデバッグする</span><span class="sxs-lookup"><span data-stu-id="31551-142">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
