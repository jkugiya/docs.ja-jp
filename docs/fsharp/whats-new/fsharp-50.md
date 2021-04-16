---
title: F# 5.0 の新機能 - F# ガイド
description: F# 5.0 で使用できる新しい機能の概要を説明します。
ms.date: 11/06/2020
ms.openlocfilehash: 9b138e4801a3e599db650990acd53c0f956b78b8
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190729"
---
# <a name="whats-new-in-f-50"></a>F# 5.0 の新機能

F# 5.0 では、F# 言語と F# インタラクティブの機能がいくつかの強化が追加されています。 これは **.NET 5** と一緒にリリースされます。

最新の .NET SDK は [.NET のダウンロード ページ](https://dotnet.microsoft.com/download)でダウンロードできます。

## <a name="get-started"></a>開始

F# 5.0 は、すべての .NET Core ディストリビューションと Visual Studio ツールで使用できます。 詳細については、「[F# の使用を開始する](../get-started/index.md)」をご覧ください。

## <a name="package-references-in-f-scripts"></a>F# スクリプトでのパッケージ参照

F# 5 では、`#r "nuget:..."` 構文による F# スクリプトのパッケージ参照のサポートが提供されます。 たとえば、次のパッケージ参照について考えます。

```fsharp
#r "nuget: Newtonsoft.Json"

open Newtonsoft.Json

let o = {| X = 2; Y = "Hello" |}

printfn $"{JsonConvert.SerializeObject o}"
```

次のように、パッケージの名前の後に明示的なバージョンを指定することもできます。

```fsharp
#r "nuget: Newtonsoft.Json,11.0.1"
```

パッケージ参照では、ML.NET などのネイティブ依存関係を含むパッケージがサポートされます。

パッケージ参照では、依存する `.dll` を参照するための特別な要件があるパッケージもサポートされます。 たとえば、[FParsec](https://www.nuget.org/packages/FParsec/) パッケージの場合、F# インタラクティブで `FParsec.dll` を参照する前に、その依存 `FParsecCS.dll` を参照するようユーザーが手動で確認することが必要でした。 これは不要になったため、次のようにパッケージを参照できます。

```fsharp
#r "nuget: FParsec"

open FParsec

let test p str =
    match run p str with
    | Success(result, _, _)   -> printfn $"Success: {result}"
    | Failure(errorMsg, _, _) -> printfn $"Failure: {errorMsg}"

test pfloat "1.234"
```

この機能は、[F# Tooling RFC FST-1027](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1027-fsi-references.md) を実装したものです。 パッケージ参照の詳細については、[F# インタラクティブ](../tools/fsharp-interactive/index.md)のチュートリアルをご覧ください。

## <a name="string-interpolation"></a>文字列補間

F# の補間された文字列は、文字列リテラル内の "穴" にコードを記述することができるという点で、C# または JavaScript の補間された文字列によく似ています。 基本的な例を次に示します。

```fsharp
let name = "Phillip"
let age = 29
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

ただし、F# の補間された文字列では、`sprintf` 関数と同様に、型指定された補間を使用して、補間されるコンテキスト内の式を強制的に特定の型に準拠させることもできます。 この場合、同じ書式指定子が使用されます。

```fsharp
let name = "Phillip"
let age = 29

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

上記の型指定された補間の例で、`%s` では補間が `string` 型でなければならないのに対し、`%d` では補間が `integer` でなければなりません。

また、1 つまたは複数の任意の F# 式を補間されるコンテキストの側に配置することもできます。 次のように、より複雑な式を記述することもできます。

```fsharp
let str =
    $"""The result of squaring each odd item in {[1..10]} is:
{
    let square x = x * x
    let isOdd x = x % 2 <> 0
    let oddSquares xs =
        xs
        |> List.filter isOdd
        |> List.map square
    oddSquares [1..10]
}
"""
```

ただし、実際にはこれを多用することはお勧めしません。

この機能は、[F# RFC FS-1001](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1001-StringInterpolation.md) を実装したものです。

## <a name="support-for-nameof"></a>nameof のサポート

F# 5 では `nameof` 演算子がサポートされています。これを使用したシンボルは F# ソースで解決されて、その名前が生成されます。 これは、ログ記録などのさまざまなシナリオで役立ち、ソース コードの変更からログ記録が保護されます。

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) (sprintf "Value passed in was %d." month)

    months.[month-1]

printfn $"{lookupMonth 12}"
printfn $"{lookupMonth 1}"
printfn $"{lookupMonth 13}"
```

最後の行では例外がスローされ、エラー メッセージに "month" と表示されます。

ほぼすべての F# コンストラクトの名前を取得できます。

```fsharp
module M =
    let f x = nameof x

printfn $"{M.f 12}"
printfn $"{nameof M}"
printfn $"{nameof M.f}"
```

最後の 3 つの追加は、演算子のしくみに対する変更です。ジェネリック型パラメーターの `nameof<'type-parameter>` 形式が追加され、パターン マッチ式で `nameof` をパターンとして使用できるようになりました。

演算子の名前を指定すると、そのソース文字列が返されます。 コンパイルされた形式が必要な場合は、演算子のコンパイルされた名前を使用します。

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

型パラメーターの名前を指定するには、次のように若干異なる構文が必要です。

```fsharp
type C<'TType> =
    member _.TypeName = nameof<'TType>
```

これは、`typeof<'T>` および `typedefof<'T>` の演算子に似ています。

F# 5 では、`match` 式で使用できる `nameof` パターンのサポートも追加されています。

```fsharp
[<Struct; IsByRefLike>]
type RecordedEvent = { EventType: string; Data: ReadOnlySpan<byte> }

type MyEvent =
    | AData of int
    | BData of string

let deserialize (e: RecordedEvent) : MyEvent =
    match e.EventType with
    | nameof AData -> AData (JsonSerializer.Deserialize<int> e.Data)
    | nameof BData -> BData (JsonSerializer.Deserialize<string> e.Data)
    | t -> failwithf "Invalid EventType: %s" t
```

上記のコードでは、match 式で文字列リテラルではなく、'nameof' を使用しています。

この機能は、[F# RFC FS-1003](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1003-nameof-operator.md) を実装したものです。

## <a name="open-type-declarations"></a>オープン型宣言

F# 5 では、オープン型宣言のサポートも追加されています。 オープン型宣言は、C# で静的クラスをオープンにするのに似ています。ただし、F# セマンティクスに適合させるために、一部の構文と動作が若干異なります。

オープン型宣言を使用すると、任意の型を `open` して、その中の静的コンテンツを公開できます。 また、F# で定義された共用体とレコードを `open` して、そのコンテンツを公開できます。 たとえば、モジュールで共用体が定義されていて、そのケースにアクセスするものの、モジュール全体をオープンにしないようにする場合に役立ちます。

```fsharp
open type System.Math

let x = Min(1.0, 2.0)

module M =
    type DU = A | B | C

    let someOtherFunction x = x + 1

// Open only the type inside the module
open type M.DU

printfn $"{A}"
```

C# とは異なり、同じ名前を持つメンバーを公開する 2 つの型で `open type` する場合、`open` される最後の型のメンバーによってもう一方の名前はシャドウされます。 これは、シャドウ化に関する既存の F# セマンティクスと一貫しています。

この機能は、[F# RFC FS-1068](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1068-open-type-declaration.md) を実装したものです。

## <a name="consistent-slicing-behavior-for-built-in-data-types"></a>組み込みデータ型の一貫性のあるスライス動作

F# 5 より前は、組み込み `FSharp.Core` データ型 (配列、リスト、文字列、2D 配列、3D 配列、4D 配列) をスライスする動作に一貫性がありませんでした。 エッジケースの動作の中には、例外がスローされるものとそうでなかったものがありました。 F# 5 では、すべての組み込み型で、生成できないスライスに対して空のスライスが返されるようになりました。

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

// Before: would return empty list
// F# 5: same
let emptyList = l.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty array
let emptyArray = a.[-2..(-1)]

// Before: would throw exception
// F# 5: returns empty string
let emptyString = s.[-2..(-1)]
```

この機能は、[F# RFC FS-1077](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-tolerant-slicing.md) を実装したものです。

## <a name="fixed-index-slices-for-3d-and-4d-arrays-in-fsharpcore"></a>FSharp.Core 内の 3D および 4D 配列の固定インデックス スライス

F# 5.0 では、組み込み 3D および 4D 配列型で固定インデックスを使用したスライスのサポートが提供されます。

これについて説明するために、次の 3D 配列を考えてみます。

*z = 0*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*
| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

この配列からスライス `[| 4; 5 |]` を抽出する場合はどうすればよいでしょうか? とてもシンプルになりました。

```fsharp
// First, create a 3D array to slice

let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

この機能は、[F# RFC FS-1077b](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1077-3d-4d-fixed-index-slicing.md) を実装したものです。

## <a name="f-quotations-improvements"></a>F# のクォートに関する機能強化

F# の [コード クォート](../language-reference/code-quotations.md)で、型制約の情報を保持できるようになりました。 次の例を確認してください。

```fsharp
open FSharp.Linq.RuntimeHelpers

let eval q = LeafExpressionConverter.EvaluateQuotation q

let inline negate x = -x
// val inline negate: x: ^a ->  ^a when  ^a : (static member ( ~- ) :  ^a ->  ^a)

<@ negate 1.0 @>  |> eval
```

`inline` 関数によって生成される制約は、コード クォートに保持されます。 引用符で囲まれた形式の `negate` 関数を評価できるようになりました。

この機能は、[F# RFC FS-1071](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1071-witness-passing-quotations.md) を実装したものです。

## <a name="applicative-computation-expressions"></a>Applicative コンピュテーション式

[コンピュテーション式 (CE)](../language-reference/computation-expressions.md) は現在、"コンテキスト コンピュテーション "をモデル化するために使用されています。より関数型プログラミングに適した用語ではモナド コンピュテーションと呼ばれます。

F# 5 では、Applicative CE が導入されており、これによって別のコンピュテーション モデルが提供されます。 すべてのコンピュテーションが独立していて、結果が最終的に蓄積される場合には、Applicative CE によってより効率的なコンピュテーションを行うことができます。 コンピュテーション同士が相互に独立している場合は、それらを並列化できることは自明のため、CE の作成者はより効率的なライブラリを記述できるようになります。 ただし、この利点には制限があり、以前に計算された値に依存するコンピュテーションは許可されていません。

次の例は、`Result` 型の基本的な Applicative CE を示しています。

```fsharp
// First, define a 'zip' function
module Result =
    let zip x1 x2 =
        match x1,x2 with
        | Ok x1res, Ok x2res -> Ok (x1res, x2res)
        | Error e, _ -> Error e
        | _, Error e -> Error e

// Next, define a builder with 'MergeSources' and 'BindReturn'
type ResultBuilder() =
    member _.MergeSources(t1: Result<'T,'U>, t2: Result<'T1,'U>) = Result.zip t1 t2
    member _.BindReturn(x: Result<'T,'U>, f) = Result.map f x

let result = ResultBuilder()

let run r1 r2 r3 =
    // And here is our applicative!
    let res1: Result<int, string> =
        result {
            let! a = r1
            and! b = r2
            and! c = r3
            return a + b - c
        }

    match res1 with
    | Ok x -> printfn $"{nameof res1} is: %d{x}"
    | Error e -> printfn $"{nameof res1} is: {e}"

let printApplicatives () =
    let r1 = Ok 2
    let r2 = Ok 3 // Error "fail!"
    let r3 = Ok 4

    run r1 r2 r3
    run r1 (Error "failure!") r3
```

現在ライブラリで CE を公開しているライブラリの作成者には、注意が必要な追加の考慮事項がいくつかあります。

この機能は、[F# RFC FS-1063](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1063-support-letbang-andbang-for-applicative-functors.md) を実装したものです。

## <a name="interfaces-can-be-implemented-at-different-generic-instantiations"></a>インターフェイスはさまざまなジェネリック インスタンス化で実装可能

同じインターフェイスをさまざまなジェネリック インスタンス化で実装できるようになりました。

```fsharp
type IA<'T> =
    abstract member Get : unit -> 'T

type MyClass() =
    interface IA<int> with
        member x.Get() = 1
    interface IA<string> with
        member x.Get() = "hello"

let mc = MyClass()
let iaInt = mc :> IA<int>
let iaString = mc :> IA<string>

iaInt.Get() // 1
iaString.Get() // "hello"
```

この機能は、[F# RFC FS-1031](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1031-Allow%20implementing%20the%20same%20interface%20at%20different%20generic%20instantiations%20in%20the%20same%20type.md) を実装したものです。

## <a name="default-interface-member-consumption"></a>既定のインターフェイス メンバーの使用

F# 5 では、[既定の実装でインターフェイス](../../csharp/tutorials/default-interface-methods-versions.md)を使用できます。

次のように、C# で定義されているインターフェイスについて考えてみましょう。

```csharp
using System;

namespace CSharp
{
    public interface MyDimasd
    {
        public int Z => 0;
    }
}
```

これは、インターフェイスを実装するあらゆる標準的な方法を用いて F# で使用できます。

```fsharp
open CSharp

// You can implement the interface via a class
type MyType() =
    member _.M() = ()

    interface MyDim

let md = MyType() :> MyDim
printfn $"DIM from C#: %d{md.Z}"

// You can also implement it via an object expression
let md' = { new MyDim }
printfn $"DIM from C# but via Object Expression: %d{md'.Z}"
```

これにより、ユーザーが既定の実装を使用できると予期される場合に、最新の C# で記述された C# コードと .NET コンポーネントを安全に利用できます。

この機能は、[F# RFC FS-1074](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1074-default-interface-member-consumption.md) を実装したものです。

## <a name="simplified-interop-with-nullable-value-types"></a>null 許容値型の簡略化された相互運用

[null 許容 (値) 型](/dotnet/api/system.nullable-1) (以前は null 許容型と呼ばれていた) は長い間 F# でサポートされていましたが、これまで、値を渡すたびに `Nullable` または `Nullable<SomeType>` のいずれかのラッパーを構築する必要があったため、これらの型を操作するのは少々面倒でした。 これからは、ターゲットの型が一致する場合、コンパイラによって値の型が `Nullable<ThatValueType>` に暗黙的に変換されるようになります。 次のコードを使用できるようになりました。

```fsharp
#r "nuget: Microsoft.Data.Analysis"

open Microsoft.Data.Analysis

let dateTimes = PrimitiveDataFrameColumn<DateTime>("DateTimes")

// The following line used to fail to compile
dateTimes.Append(DateTime.Parse("2019/01/01"))

// The previous line is now equivalent to this line
dateTimes.Append(Nullable<DateTime>(DateTime.Parse("2019/01/01")))
```

この機能は、[F# RFC FS-1075](https://github.com/fsharp/fslang-design/blob/master/FSharp-5.0/FS-1075-nullable-interop.md) を実装したものです。

## <a name="preview-reverse-indexes"></a>プレビュー: リバース インデックス

F# 5 では、リバース インデックスを使用できるようにするためのプレビューも導入されました。 構文は `^idx` です。 リストの末尾から要素 1 の値を取得する方法を次に示します。

```fsharp
let xs = [1..10]

// Get element 1 from the end:
xs.[^1]

// From the end slices

let lastTwoOldStyle = xs.[(xs.Length-2)..]

let lastTwoNewStyle = xs.[^1..]

lastTwoOldStyle = lastTwoNewStyle // true
```

また、独自の型のリバース インデックスを定義することもできます。 これを行うには、次のメソッドを実装する必要があります。

```fsharp
GetReverseIndex: dimension: int -> offset: int
```

`Span<'T>` 型の例を次に示します。

```fsharp
open System

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

    member sp.GetReverseIndex(_, offset: int) =
        sp.Length - offset

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn $"{arr}"

let run () =
    let sp = [| 1; 2; 3; 4; 5 |].AsSpan()

    // Pre-# 5.0 slicing on a Span<'T>
    printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..3] // [|1; 2; 3|]
    printSpan sp.[1..3] // |2; 3|]

    // Same slices, but only using from-the-end index
    printSpan sp.[..^0] // [|1; 2; 3; 4; 5|]
    printSpan sp.[..^2] // [|1; 2; 3|]
    printSpan sp.[^4..^2] // [|2; 3|]

run() // Prints the same thing twice
```

この機能は、[F# RFC FS-1076](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1076-from-the-end-slicing.md) を実装したものです。

## <a name="preview-overloads-of-custom-keywords-in-computation-expressions"></a>プレビュー: コンピュテーション式におけるカスタム キーワードのオーバーロード

コンピュテーション式は、ライブラリやフレームワークの作成者向けの強力な機能です。 これを使用すると、既知のメンバーを定義したり、作業しているドメインの DSL を形成したりして、コンポーネントの表現力を大幅に向上させることができます。

F# 5 では、コンピュテーション式でカスタム操作をオーバーロードするためのプレビュー サポートが追加されています。 これにより、次のコードを記述して使用することができます。

```fsharp
open System

type InputKind =
    | Text of placeholder:string option
    | Password of placeholder: string option

type InputOptions =
  { Label: string option
    Kind : InputKind
    Validators : (string -> bool) array }

type InputBuilder() =
    member t.Yield(_) =
      { Label = None
        Kind = Text None
        Validators = [||] }

    [<CustomOperation("text")>]
    member this.Text(io, ?placeholder) =
        { io with Kind = Text placeholder }

    [<CustomOperation("password")>]
    member this.Password(io, ?placeholder) =
        { io with Kind = Password placeholder }

    [<CustomOperation("label")>]
    member this.Label(io, label) =
        { io with Label = Some label }

    [<CustomOperation("with_validators")>]
    member this.Validators(io, [<ParamArray>] validators) =
        { io with Validators = validators }

let input = InputBuilder()

let name =
    input {
    label "Name"
    text
    with_validators
        (String.IsNullOrWhiteSpace >> not)
    }

let email =
    input {
    label "Email"
    text "Your email"
    with_validators
        (String.IsNullOrWhiteSpace >> not)
        (fun s -> s.Contains "@")
    }

let password =
    input {
    label "Password"
    password "Must contains at least 6 characters, one number and one uppercase"
    with_validators
        (String.exists Char.IsUpper)
        (String.exists Char.IsDigit)
        (fun s -> s.Length >= 6)
    }
```

この変更の前には、`InputBuilder` 型をこのとおりに記述できましたが、この例に示されている方法で使用することはできませんでした。 オーバーロードと省略可能なパラメーターに加えて、このたび `System.ParamArray` 型が使用できることになったため、すべてが期待どおりに動作します。

この機能は、[F# RFC FS-1056](https://github.com/fsharp/fslang-design/blob/master/preview/FS-1056-allow-custom-operation-overloads.md) を実装したものです。
