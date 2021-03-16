---
title: 破壊的変更:Vector2.Lerp と Vector4.Lerp の動作の変更
description: Core .NET ライブラリでの .NET 5 の破壊的変更について学習します。この変更後、Vector2.Lerp と Vector4.Lerp の実装が、浮動小数点丸め誤差を正しく考慮するように変更されています。
ms.date: 11/01/2020
ms.openlocfilehash: a7014c30f2b102dc9a19e9a58f97b7c0ed8cd648
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256999"
---
# <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a><span data-ttu-id="7312e-103">Vector2.Lerp と Vector4.Lerp の動作の変更</span><span class="sxs-lookup"><span data-stu-id="7312e-103">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>

<span data-ttu-id="7312e-104">浮動小数点の丸め誤差を正しく考慮するように <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> と <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> の実装が変更されました。</span><span class="sxs-lookup"><span data-stu-id="7312e-104">The implementation of <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> changed to correctly account for a floating-point rounding error.</span></span>

## <a name="change-description"></a><span data-ttu-id="7312e-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="7312e-105">Change description</span></span>

<span data-ttu-id="7312e-106">以前は、<xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> と <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> は `value1 + (value2 - value1) * amount` として実装されていました。</span><span class="sxs-lookup"><span data-stu-id="7312e-106">Previously, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> and <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> were implemented as `value1 + (value2 - value1) * amount`.</span></span> <span data-ttu-id="7312e-107">ただし、浮動小数点の丸め誤差のため、`amount` が `1.0f` のとき、このアルゴリズムから `value2` が返されないことがありました。</span><span class="sxs-lookup"><span data-stu-id="7312e-107">However, due to a floating-point rounding error, this algorithm doesn't always return `value2` when `amount` is `1.0f`.</span></span>

<span data-ttu-id="7312e-108">.NET 5 以降では、この実装では、<xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> と同じアルゴリズム、すなわち `(value1 * (1.0f - amount)) + (value2 * amount)` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7312e-108">In .NET 5 and later, the implementation uses the same algorithm as <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType>, which is `(value1 * (1.0f - amount)) + (value2 * amount)`.</span></span> <span data-ttu-id="7312e-109">このアルゴリズムでは、丸め誤差が正しく考慮されます。</span><span class="sxs-lookup"><span data-stu-id="7312e-109">This algorithm correctly accounts for the rounding error.</span></span> <span data-ttu-id="7312e-110">これで、`amount` が `1.0f` のとき、結果は正確に `value2` となります。</span><span class="sxs-lookup"><span data-stu-id="7312e-110">Now, when `amount` is `1.0f`, the result is precisely `value2`.</span></span> <span data-ttu-id="7312e-111">更新後のアルゴリズムではまた、利用できるとき、<xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> を利用してアルゴリズムを自由に最適化できます。</span><span class="sxs-lookup"><span data-stu-id="7312e-111">The updated algorithm also allows the algorithm to be freely optimized using <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> when it's available.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7312e-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="7312e-112">Version introduced</span></span>

<span data-ttu-id="7312e-113">5.0</span><span class="sxs-lookup"><span data-stu-id="7312e-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7312e-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="7312e-114">Recommended action</span></span>

<span data-ttu-id="7312e-115">必要なアクションはありません。</span><span class="sxs-lookup"><span data-stu-id="7312e-115">No action is necessary.</span></span> <span data-ttu-id="7312e-116">ただし、以前の動作を保持する場合、`value1 + (value2 - value1) * amount` の前のアルゴリズムを使用する独自の `Lerp` 関数を実装できます。</span><span class="sxs-lookup"><span data-stu-id="7312e-116">However, if you want to maintain the old behavior, you can implement your own `Lerp` function that uses the previous algorithm of `value1 + (value2 - value1) * amount`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7312e-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="7312e-117">Affected APIs</span></span>

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
