---
title: F# 4.6 の新機能 - F# ガイド
description: F# 4.6 で使用できる新しい機能の概要を説明します。
ms.date: 11/27/2019
ms.openlocfilehash: 620c1edd8ea212fee306a02d5844b6b322808251
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980393"
---
# <a name="whats-new-in-f-46"></a>F# 4.6 の新機能

F# 4.6 では、F# 言語に複数の機能強化が加えられています。

## <a name="get-started"></a>開始

F# 4.6 は、すべての .NET Core ディストリビューションと Visual Studio ツールで使用できます。 詳細については、「[F# の使用を開始する](../get-started/index.md)」をご覧ください。

## <a name="anonymous-records"></a>匿名レコード

[匿名レコード](../language-reference/anonymous-records.md)は、F# 4.6 で導入された新しい種類の F# 型です。 これは、使用前に宣言する必要のない名前付きの値を単純に集めたものです。 これは、構造体または参照型として宣言できます。 既定では、これは参照型です。

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

また、値型をグループ化する必要があり、パフォーマンスを重視するシナリオで機能させる場合は、構造体として宣言することもできます。

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    struct {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

これは、非常に強力であり、さまざまなシナリオで使用できます。 詳細については、「[匿名レコード](../language-reference/anonymous-records.md)」をご覧ください。

## <a name="valueoption-functions"></a>ValueOption 関数

F# 4.5 で追加された ValueOption 型に、Option 型の "モジュールバインド関数パリティ" が含まれるようになりました。 一般的に使用される例には、次のようなものがあります。

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> ValueNone
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> ValueSome

let reversedString = strOpt |> ValueOption.bind reverse
```

これにより、値型を使用するとパフォーマンスが向上するシナリオで、ValueOption を Option と同じように使用することができます。
