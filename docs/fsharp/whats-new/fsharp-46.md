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
# <a name="whats-new-in-f-46"></a><span data-ttu-id="98d0c-103">F# 4.6 の新機能</span><span class="sxs-lookup"><span data-stu-id="98d0c-103">What's new in F# 4.6</span></span>

<span data-ttu-id="98d0c-104">F# 4.6 では、F# 言語に複数の機能強化が加えられています。</span><span class="sxs-lookup"><span data-stu-id="98d0c-104">F# 4.6 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="98d0c-105">開始</span><span class="sxs-lookup"><span data-stu-id="98d0c-105">Get started</span></span>

<span data-ttu-id="98d0c-106">F# 4.6 は、すべての .NET Core ディストリビューションと Visual Studio ツールで使用できます。</span><span class="sxs-lookup"><span data-stu-id="98d0c-106">F# 4.6 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="98d0c-107">詳細については、「[F# の使用を開始する](../get-started/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="98d0c-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="anonymous-records"></a><span data-ttu-id="98d0c-108">匿名レコード</span><span class="sxs-lookup"><span data-stu-id="98d0c-108">Anonymous records</span></span>

<span data-ttu-id="98d0c-109">[匿名レコード](../language-reference/anonymous-records.md)は、F# 4.6 で導入された新しい種類の F# 型です。</span><span class="sxs-lookup"><span data-stu-id="98d0c-109">[Anonymous records](../language-reference/anonymous-records.md) are a new kind of F# type introduced in F# 4.6.</span></span> <span data-ttu-id="98d0c-110">これは、使用前に宣言する必要のない名前付きの値を単純に集めたものです。</span><span class="sxs-lookup"><span data-stu-id="98d0c-110">They are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="98d0c-111">これは、構造体または参照型として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="98d0c-111">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="98d0c-112">既定では、これは参照型です。</span><span class="sxs-lookup"><span data-stu-id="98d0c-112">They're reference types by default.</span></span>

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

<span data-ttu-id="98d0c-113">また、値型をグループ化する必要があり、パフォーマンスを重視するシナリオで機能させる場合は、構造体として宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="98d0c-113">They can also be declared as structs for when you want to group value types and are operating in performance-sensitive scenarios:</span></span>

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

<span data-ttu-id="98d0c-114">これは、非常に強力であり、さまざまなシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="98d0c-114">They're quite powerful and can be used in numerous scenarios.</span></span> <span data-ttu-id="98d0c-115">詳細については、「[匿名レコード](../language-reference/anonymous-records.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="98d0c-115">Learn more at [Anonymous records](../language-reference/anonymous-records.md).</span></span>

## <a name="valueoption-functions"></a><span data-ttu-id="98d0c-116">ValueOption 関数</span><span class="sxs-lookup"><span data-stu-id="98d0c-116">ValueOption functions</span></span>

<span data-ttu-id="98d0c-117">F# 4.5 で追加された ValueOption 型に、Option 型の "モジュールバインド関数パリティ" が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="98d0c-117">The ValueOption type added in F# 4.5 now has "module-bound function parity" with the Option type.</span></span> <span data-ttu-id="98d0c-118">一般的に使用される例には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="98d0c-118">Some of the more commonly-used examples are as follows:</span></span>

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

<span data-ttu-id="98d0c-119">これにより、値型を使用するとパフォーマンスが向上するシナリオで、ValueOption を Option と同じように使用することができます。</span><span class="sxs-lookup"><span data-stu-id="98d0c-119">This allows for ValueOption to be used just like Option in scenarios where having a value type improves performance.</span></span>
