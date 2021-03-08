---
title: ローカル関数 - C# プログラミング ガイド
description: C# のローカル関数は、別のメンバーの入れ子になっているプライベート メソッドであり、その親メンバーから呼び出すことができます。
ms.date: 10/16/2020
helpviewer_keywords:
- local functions [C#]
ms.openlocfilehash: 1c0cd1b8122f9069e5d6385d698f0ff8278912dd
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103245"
---
# <a name="local-functions-c-programming-guide"></a>ローカル関数 (C# プログラミング ガイド)

C# 7.0 以降、C# では *ローカル関数* がサポートされています。 ローカル関数は、別のメンバーの入れ子になっているタイプのプライベート メソッドです。 親メンバーからのみ呼び出すことができます。 ローカル関数は次の要素で宣言し、呼び出すことができます。

- メソッド (特に反復子メソッドと非同期メソッド)
- コンストラクター
- プロパティ アクセサー
- イベント アクセサー
- 匿名メソッド
- ラムダ式
- ファイナライザー
- その他のローカル関数

ただし、ローカル関数は、式形式のメンバーの内部では宣言できません。

> [!NOTE]
> 場合によっては、ラムダ式を使用して、ローカル関数でもサポートされている機能を実装できます。 比較については、「[ローカル関数とラムダ式の比較](#local-functions-vs-lambda-expressions)」を参照してください。

ローカル関数を使用すると、コードの意図が明確になります。 コードを見た人は、メソッドが親メソッドによってのみ呼び出し可能であることがわかります。 また、チーム プロジェクトの場合は、別の開発者がクラスや構造体の別の場所から誤ってメソッドを直接呼び出すことができなくなります。

## <a name="local-function-syntax"></a>ローカル関数の構文

ローカル関数は、親メンバーの内側に、入れ子になったメソッドとして定義されます。 その定義の構文は次のとおりです。

```csharp
<modifiers> <return-type> <method-name> <parameter-list>
```

ローカル関数と共に次の修飾子を使用できます。

- [`async`](../../language-reference/keywords/async.md)
- [`unsafe`](../../language-reference/keywords/unsafe.md)
- [`static`](../../language-reference/keywords/static.md) (C# 8.0 以降)。 静的なローカル関数では、ローカル変数やインスタンスの状態をキャプチャすることはできません。
- [`extern`](../../language-reference/keywords/extern.md) (C# 9.0 以降)。 外部ローカル関数は `static` である必要があります。

メソッドのパラメーターを含め、親メンバー内で定義されているすべてのローカル変数は、非静的ローカル関数からアクセス可能です。

メソッド定義とは異なり、ローカル関数の定義にメンバー アクセス修飾子を含めることはできません。 すべてのローカル関数はプライベートであるため、`private` キーワードなどのアクセス修飾子が含まれていると、コンパイラ エラー CS0106 "修飾子 'private' がこの項目に対して有効ではありません" が生成されます。

次の例は、`GetText` というメソッドに対してプライベートな `AppendPathSeparator` というローカル関数を定義しています。

:::code language="csharp" source="snippets/local-functions/Program.cs" id="Basic" :::

C# 9.0 以降、次の例に示すように、ローカル関数およびそのパラメーターと型パラメーターに属性を適用できます。

:::code language="csharp" source="snippets/local-functions/Program.cs" id="WithAttributes" :::

上の例では、[特殊な属性](../../language-reference/attributes/nullable-analysis.md)を使用して、Null 許容コンテキストでの静的分析に関してコンパイラをサポートしています。

## <a name="local-functions-and-exceptions"></a>ローカル関数と例外

ローカル関数の便利な機能の 1 つは、例外を直ちに検出できることです。 メソッド反復子の場合、例外は返されたシーケンスを列挙する時点でしか検出されず、反復子を取得した時点では検出されません。 非同期メソッドの場合、非同期メソッドでスローされた例外は、タスクの戻りを待機中に検出されます。

次の例は、指定した範囲にある奇数を列挙する `OddSequence` メソッドを定義しています。 100 より大きい数値を `OddSequence` 列挙子メソッドに渡しているため、メソッドは <xref:System.ArgumentOutOfRangeException> をスローします。 この例の出力が示すように、例外は列挙子を取得したときではなく、数値を反復処理した時点でのみ検出されます。

:::code language="csharp" source="snippets/local-functions/IteratorWithoutLocal.cs" :::

反復子ロジックをローカル関数に追加した場合、次の例に示すように、列挙子を取得すると引数の検証例外がスローされます。

:::code language="csharp" source="snippets/local-functions/IteratorWithLocal.cs" :::

## <a name="local-functions-vs-lambda-expressions"></a>ローカル関数とラムダ式の比較

一見したところ、ローカル関数と[ラムダ式](../../language-reference/operators/lambda-expressions.md)は、非常に似ています。 多くの場合、ラムダ式とローカル関数の使用のどちらを選択するかは、スタイルと個人的な好みの問題です。 ただし、どちらか一方を使用できる場合、認識しておくべき実質的な違いがあります。

階乗アルゴリズムのローカル関数とラムダ式の実装の違いについて見てみましょう。 ローカル関数を使用するバージョンを次に示します。

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLocal" :::

このバージョンでは、ラムダ式が使用されます。

:::code language="csharp" source="snippets/local-functions/Program.cs" id="FactorialWithLambda" :::

### <a name="naming"></a>名前を付ける

ローカル関数には、メソッドと同様に明示的に名前が付けられます。 ラムダ式は匿名メソッドであり、`delegate` 型の変数 (通常は `Action` 型または `Func` 型) に割り当てる必要があります。 ローカル関数を宣言する場合、プロセスは通常のメソッドを記述するのと似ています。戻り値の型と関数シグネチャを宣言します。

### <a name="function-signatures-and-lambda-expression-types"></a>関数シグネチャとラムダ式の型

ラムダ式は、引数と戻り値の型を決定するために割り当てられている `Action`/`Func` 変数の型に依存します。 ローカル関数では、構文は通常のメソッドの記述とよく似ているため、引数の型と戻り値の型は既に関数宣言の一部になっています。

### <a name="definite-assignment"></a>確実な代入

ラムダ式は、実行時に宣言されて割り当てられるオブジェクトです。 ラムダ式を使用するには、その式を確実に代入する必要があります。代入先の `Action`/`Func` 変数と、代入するラムダ式を宣言する必要があります。 `LambdaFactorial` では、ラムダ式 `nthFactorial` を定義する前に、宣言と初期化を行う必要があることにご注意ください。 その手順を踏まないと、`nthFactorial` の割り当て前に参照することによるコンパイル時エラーが発生します。

ローカル関数は、コンパイル時に定義されます。 これらは変数に割り当てられないため、**スコープ内の** どのコードの場所からでも参照できます。最初の `LocalFunctionFactorial` の例では、`return` ステートメントの上または下でローカル関数を宣言して、コンパイラ エラーが発生しないようにすることができます。

これらの違いは、再帰的なアルゴリズムの作成はローカル関数を使用する方が簡単であることを意味します。 自身を呼び出すローカル関数を宣言して定義することができます。 ラムダ式は宣言して、既定値を割り当てないと、同じラムダ式を参照する本体に再割り当てできません。

### <a name="implementation-as-a-delegate"></a>デリゲートとしての実装

ラムダ式は、宣言時にデリゲートに変換されます。 ローカル関数は、従来のメソッド "*または*" デリゲートと同様に記述できるので、より柔軟性があります。 ローカル関数は、デリゲートとして "***使用される***" 場合にのみ、デリゲートに変換されます。

ローカル関数を宣言し、メソッドのように呼び出して参照のみを行う場合は、デリゲートに変換されません。

### <a name="variable-capture"></a>変数のキャプチャ

[確実な代入](../../../../_csharplang/spec/variables.md#definite-assignment)のルールは、ローカル関数またはラムダ式でキャプチャされる変数にも影響を与えます。 コンパイラによって静的分析を実行できます。これにより、ローカル関数で外側のスコープ内のキャプチャされた変数を確実に割り当てることができます。 次の例について考えます。

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

コンパイラは、呼び出し時に `LocalFunction` が `y` を確実に割り当てるかどうかを確認できます。 `return` ステートメントの前に `LocalFunction` が呼び出されるため、`y` は `return` ステートメントで確実に割り当てられます。

ローカル関数によって外側のスコープ内の変数をキャプチャする場合、ローカル関数はデリゲート型として実装されることにご注意ください。

### <a name="heap-allocations"></a>ヒープの割り当て

ローカル関数では、その使用に応じて、ラムダ式では常に必要なヒープの割り当てを回避できます。 ローカル関数がデリゲートに変換されておらず、ローカル関数でキャプチャされたいずれの変数も、デリゲートに変換された他のラムダやローカル関数でキャプチャされていない場合は、コンパイラによってヒープの割り当てを回避できます。

次の非同期の例について考えます。

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLambda" :::

このラムダ式のクロージャに含まれるのは、`address`、`index`、および `name` 変数です。 ローカル関数の場合、クロージャを実装するオブジェクトが `struct` になる場合があります。 その構造体型はローカル関数に参照によって渡されます。 この実装の違いにより、割り当てが少なくなります。

ラムダ式に必要なインスタンス化では、余分なメモリの割り当てが必要となり、タイム クリティカルなコード パスに影響を与えるパフォーマンス因子となる可能性があります。 ローカル関数では、このオーバーヘッドは発生しません。 上記の例では、ローカル関数のバージョンは、ラムダ式のバージョンよりも割り当てが 2 つ少なくなっています。

ローカル関数がデリゲートに変換されず、それによってキャプチャされた変数が、デリゲートに変換された他のラムダまたはローカル関数によってキャプチャされないことがわかっている場合は、ローカル関数を `static` ローカル関数として宣言することで、ヒープに割り当てられないようにすることができます。 この機能は C# 8.0 以降で使用可能であることにご注意ください。

> [!NOTE]
> このメソッドのローカル関数と同等のものも、同じクロージャのクラスを使用します。 ローカル関数のクロージャが `class` として実装される場合でも、実装の詳細が `struct` である場合でも同様です。 ローカル関数は `struct` を使用する場合がありますが、ラムダは常に `class` を使用します。

:::code language="csharp" source="snippets/local-functions/Program.cs" id="AsyncWithLocal" :::

### <a name="usage-of-the-yield-keyword"></a>`yield` キーワードの使用法

この例では説明しませんが、最後の 1 つの利点は値のシーケンスを生成するために `yield return` 構文を使用して、ローカル関数を反復子として実装できることです。

:::code language="csharp" source="snippets/local-functions/Program.cs" id="YieldReturn" :::

`yield return` ステートメントは、ラムダ式では許可されていません。[コンパイラ エラー CS1621](../../misc/cs1621.md) を参照してください。

ローカル関数はラムダ式より冗長に思えるかもしれませんが、実際にはさまざまな目的に役立ち、用途もさまざまです。 ローカル関数は、別のメソッドのコンテキストからのみ呼び出される関数を記述する場合に、より効率が高くなります。

## <a name="see-also"></a>関連項目

- [メソッド](methods.md)
