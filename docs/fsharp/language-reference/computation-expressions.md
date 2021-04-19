---
title: コンピュテーション式
description: 制御フローのコンストラクトとバインドを使用してシーケンス化および結合できる F# の計算を記述するための便利な構文の作成方法について説明します。
ms.date: 08/15/2020
f1_keywords:
- let!_FS
ms.openlocfilehash: a0a71533ea1bc87b75f028ad0d416326f627672a
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739305"
---
# <a name="computation-expressions"></a>コンピュテーション式

F# のコンピュテーション式には、制御フローのコンストラクトとバインドを使用してシーケンス化および結合できる計算を記述するための便利な構文が用意されています。 コンピュテーション式は、その種類に応じて、モナド、モノイド、モナド変換子、およびアプリカティブ ファンクターを表現する方法と考えることができます。 ただし、他の言語 (Haskell の *do-notation* など) とは異なり、それらは 1 つの抽象化に関連付けられておらず、便利な状況依存の構文を実現するためにマクロやその他の形式のメタプログラミングに依存しません。

## <a name="overview"></a>概要

計算にはさまざまな形式があります。 計算の最も一般的な形式は、理解と変更が簡単なシングルスレッド実行です。 ただし、すべての形式の計算がシングルスレッド実行ほど単純であるとは限りません。 次に例をいくつか示します。

- 非決定的な計算
- 非同期計算
- 有効計算
- 生成的計算

より一般には、アプリケーションの特定の部分で実行する必要がある "*状況依存*" の計算があります。 状況依存のコードを記述することは難しい場合があります。これは、抽象化によって回避しないと特定のコンテキストの外部に計算が "リーク" しやすいからです。 多くの場合、これらの抽象化は自分で記述することが困難です。そのため、F# には **コンピュテーション式** と呼ばれる汎用的な方法が用意されています。

コンピュテーション式により、状況依存の計算をエンコードするための統一された構文と抽象化モデルが提供されます。

すべてのコンピュテーション式は、"*ビルダー*" 型によってサポートされます。 ビルダー型により、コンピュテーション式で使用できる操作が定義されます。 カスタム コンピュテーション式の作成方法を示している「[コンピュテーション式の新しい型の作成](computation-expressions.md#creating-a-new-type-of-computation-expression)」を参照してください。

### <a name="syntax-overview"></a>構文の概要

すべてのコンピュテーション式の形式は次のとおりです。

```fsharp
builder-expr { cexper }
```

ここで、`builder-expr` はコンピュテーション式を定義するビルダー型の名前、`cexper` はコンピュテーション式の式本体です。 たとえば、`async` コンピュテーション式のコードは次のようになります。

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

前の例で示したように、コンピュテーション式内で使用できる特殊な追加の構文があります。 コンピュテーション式では、次の形式の式を使用できます。

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

これらの各キーワードおよびその他の標準 F# キーワードは、バッキング ビルダー型で定義されている場合にのみ、コンピュテーション式で使用できます。 これに対する唯一の例外は `match!` です。これ自体は、`let!` に続いて結果に対するパターン マッチを使用するための糖衣構文です。

ビルダー型は、コンピュテーション式のフラグメントの結合方法を制御する特殊なメソッドを定義するオブジェクトです。つまり、そのメソッドによって、コンピュテーション式の動作が制御されます。 ビルダー クラスは、ループやバインドなど、多くの F# コンストラクトの操作をカスタマイズできるようにするものとして説明することもできます。

### `let!`

`let!` キーワードにより、別のコンピュテーション式の呼び出し結果が名前にバインドされます。

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

`let` を使用してコンピュテーション式の呼び出しをバインドすると、コンピュテーション式の結果は得られません。 代わりに、そのコンピュテーション式に対する "*実現されていない*" 呼び出しの値がバインドされます。 `let!` を使用して結果にバインドします。

`let!` は、ビルダー型の `Bind(x, f)` メンバーによって定義されます。

### `do!`

`do!` キーワードは、`unit` のような型 (ビルダーで `Zero` メンバーによって定義される) を返すコンピュテーション式を呼び出すためのものです。

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

[非同期ワークフロー](asynchronous-workflows.md)の場合、この型は `Async<unit>` です。 その他のコンピュテーション式の場合、型は `CExpType<unit>` になる可能性があります。

`do!` は、ビルダー型の `Bind(x, f)` メンバーによって定義されます。ここで、`f` によって `unit` が生成されます。

### `yield`

`yield` キーワードは、コンピュテーション式から値を返して、<xref:System.Collections.Generic.IEnumerable%601> として使用できるようにするためのものです。

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn $"%d{sq}"
```

ほとんどの場合、呼び出し元では省略できます。 `yield` を省略する最も一般的な方法は、`->` 演算子を使用することです。

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn $"%d{sq}"
```

多くの異なる値を生成する可能性がある複雑な式の場合、場合によってはキーワードを省略するだけで、次のことが可能です。

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

[C# の yield キーワード](../../csharp/language-reference/keywords/yield.md)の場合と同様に、コンピュテーション式の各要素は反復処理されるときに返されます。

`yield` は、ビルダー型の `Yield(x)` メンバーによって定義されます。ここで、`x` は返す項目です。

### `yield!`

`yield!` キーワードは、コンピュテーション式からの値のコレクションをフラット化するためのものです。

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn $"{squaresAndCubes}"  // Prints - 1; 4; 9; 1; 8; 27
```

評価されると、`yield!` によって呼び出されるコンピュテーション式の項目が 1 つずつ返され、結果がフラット化されます。

`yield!` は、ビルダー型の `YieldFrom(x)` メンバーによって定義されます。ここで、`x` は値のコレクションです。

`yield` とは異なり、`yield!` は明示的に指定する必要があります。 コンピュテーション式では、その動作は暗黙的ではありません。

### `return`

`return` キーワードにより、コンピュテーション式に対応する型に値がラップされます。 `yield` を使用したコンピュテーション式とは別に、コンピュテーション式を "完了" するために使用されます。

```fsharp
let req = // 'req' is of type 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` は、ビルダー型の `Return(x)` メンバーによって定義されます。ここで、`x` はラップする項目です。

### `return!`

`return!` キーワードにより、コンピュテーション式の値が認識され、その結果がコンピュテーション式に対応する型にラップされます。

```fsharp
let req = // 'req' is of type 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` は、ビルダー型の `ReturnFrom(x)` メンバーによって定義されます。ここで、`x` は別のコンピュテーション式です。

### `match!`

`match!` キーワードを使用すると、呼び出しを別のコンピュテーション式にインライン化し、結果のパターン マッチを行うことができます。

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

`match!` を使用してコンピュテーション式を呼び出すと、`let!` のような呼び出しの結果が認識されます。 通常、これは、結果が[省略可能](options.md)であるコンピュテーション式を呼び出すときに使用されます。

## <a name="built-in-computation-expressions"></a>組み込みのコンピュテーション式

F# コア ライブラリには、[シーケンス式](sequences.md)、[非同期ワークフロー](asynchronous-workflows.md)、[クエリ式](query-expressions.md)という 3 つの組み込みのコンピュテーション式が定義されています。

## <a name="creating-a-new-type-of-computation-expression"></a>新しい種類のコンピュテーション式の作成

ビルダー クラスを作成し、そのクラスに特定の特殊なメソッドを定義することで、独自のコンピュテーション式の特性を定義できます。 ビルダー クラスでは、次の表に示すように、必要に応じてメソッドを定義できます。

次の表では、ワークフロー ビルダー クラスで使用できるメソッドについて説明します。

|**方法**|**一般的なシグネチャ**|**説明**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|コンピュテーション式で `let!` および `do!` に対して呼び出されます。|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|コンピュテーション式を関数としてラップします。|
|`Return`|`'T -> M<'T>`|コンピュテーション式で `return` に対して呼び出されます。|
|`ReturnFrom`|`M<'T> -> M<'T>`|コンピュテーション式で `return!` に対して呼び出されます。|
|`Run`|`M<'T> -> M<'T>` または<br /><br />`M<'T> -> 'T`|コンピュテーション式を実行します。|
|`Combine`|`M<'T> * M<'T> -> M<'T>` または<br /><br />`M<unit> * M<'T> -> M<'T>`|コンピュテーション式でシーケンス処理を行うために呼び出されます。|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` または<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|コンピュテーション式の `for...do` 式に対して呼び出されます。|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|コンピュテーション式の `try...finally` 式に対して呼び出されます。|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|コンピュテーション式の `try...with` 式に対して呼び出されます。|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|コンピュテーション式の `use` バインディングに対して呼び出されます。|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|コンピュテーション式の `while...do` 式に対して呼び出されます。|
|`Yield`|`'T -> M<'T>`|コンピュテーション式の `yield` 式に対して呼び出されます。|
|`YieldFrom`|`M<'T> -> M<'T>`|コンピュテーション式の `yield!` 式に対して呼び出されます。|
|`Zero`|`unit -> M<'T>`|コンピュテーション式の `if...then` 式の空の `else` 分岐に対して呼び出されます。|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|コンピュテーション式が `Run` メンバーに引用符として渡されることを示します。 計算のすべてのインスタンスを引用符に変換します。|

ビルダー クラスのメソッドの多くは、`M<'T>` コンストラクトを使用して返します。通常、これは非同期ワークフローに対する `Async<'T>` やシーケンス ワークフローに対する `Seq<'T>` など、結合される計算の種類を特徴付ける個別に定義された型です。 これらのメソッドのシグネチャを使用すると、1 つのコンストラクトから返されるワークフロー オブジェクトを次のものに渡すことができるように、それらを組み合わせて入れ子にすることができます。 コンパイラでは、コンピュテーション式を解析するときに、前の表のメソッドとコンピュテーション式内のコードを使用して、式が一連の入れ子になった関数呼び出しに変換されます。

入れ子になった式の形式は次のとおりです。

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

上記のコードで、`Run` と `Delay` は、コンピュテーション式ビルダー クラス内で定義されていない場合に省略されます。 ここでは `{| cexpr |}` と示されているコンピュテーション式の本体は、次の表で説明する変換によって、ビルダー クラスのメソッドを含む呼び出しに変換されます。 コンピュテーション式 `{| cexpr |}` は、これらの変換に従って再帰的に定義されます。ここで、`expr` は F# の式で、`cexpr` はコンピュテーション式です。

|式|翻訳|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

前の表では、`other-expr` は表に記載されていない式について説明しています。 ビルダー クラスでは、必ずしもすべてのメソッドを実装する必要はなく、前の表に一覧表示されているすべての変換がサポートされます。 実装されていないコンストラクトは、その型のコンピュテーション式では使用できません。 たとえば、コンピュテーション式内で `use` キーワードをサポートしない場合は、ビルダー クラス内で `Use` の定義を省略できます。

次のコード例は、一度に 1 ステップずつ評価できる一連のステップとして計算をカプセル化するコンピュテーション式を示しています。 判別共用体型である `OkOrException` により、これまでに評価された式のエラー状態がエンコードされます。 このコードは、一部のビルダー メソッドの定型実装など、コンピュテーション式内で使用できるいくつかの一般的なパターンを示しています。

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res ->
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally
            (whileLoop
                (fun () -> ie.MoveNext())
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn $" x = %d{x}"
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step
```

コンピュテーション式には、式によって返される基になる型があります。 基になる型では、計算された結果または実行可能な遅延計算を表すことができます。また、一部のコレクション型を反復処理する方法が提供される場合もあります。 前の例では、基になる型は **Eventually** でした。 シーケンス式の場合、基になる型は <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> です。 クエリ式の場合、基になる型は <xref:System.Linq.IQueryable?displayProperty=nameWithType> です。 非同期ワークフローの場合、基になる型は [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html) です。 `Async` オブジェクトは、結果を計算するために実行する作業を表します。 たとえば、[`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) を呼び出して計算を実行し、その結果を返します。

## <a name="custom-operations"></a>カスタム操作

コンピュテーション式に対してカスタム操作を定義し、コンピュテーション式内でカスタム操作を演算子として使用することができます。 たとえば、クエリ式にクエリ演算子を含めることができます。 カスタム操作を定義する場合は、コンピュテーション式で Yield および For メソッドを定義する必要があります。 カスタム操作を定義するには、それをコンピュテーション式のビルダー クラスに配置し、[`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html) を適用します。 この属性は、文字列を引数として受け取ります。これはカスタム操作で使用される名前です。 この名前は、コンピュテーション式の左中かっこの先頭にあるスコープに含まれます。 したがって、このブロック内ではカスタム操作と同じ名前を持つ識別子は使用しないでください。 たとえば、クエリ式で `all` や `last` などの識別子を使用しないようにします。

### <a name="extending-existing-builders-with-new-custom-operations"></a>新しいカスタム操作を使用した既存のビルダーの拡張

既にビルダー クラスがある場合は、そのカスタム操作をこのビルダー クラスの外部から拡張できます。 拡張はモジュール内で宣言する必要があります。 名前空間には、同じファイルと、型が定義されている同じ名前空間宣言グループを除き、拡張メンバーを含めることはできません。

次の例は、既存の `FSharp.Linq.QueryBuilder` クラスの拡張を示しています。

```fsharp
type FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [非同期ワークフロー](asynchronous-workflows.md)
- [シーケンス](sequences.md)
- [クエリ式](query-expressions.md)
