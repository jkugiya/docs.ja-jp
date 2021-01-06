---
title: 破壊的変更:SSE および SSE2 の CompareGreaterThan メソッドで NaN 入力が正しく処理される
description: Core .NET ライブラリでの .NET 5.0 の破壊的変更について学習します。この変更後、SSE と SSE2 の比較メソッドは、NaN 入力を正しく処理するように修正されています。
ms.date: 11/01/2020
ms.openlocfilehash: 4abffa8d8bf2abfa9ef83673db9154de035d952c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759350"
---
# <a name="sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs"></a><span data-ttu-id="66c39-103">SSE および SSE2 の CompareGreaterThan メソッドで NaN 入力が正しく処理される</span><span class="sxs-lookup"><span data-stu-id="66c39-103">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>

<span data-ttu-id="66c39-104">次の <xref:System.Runtime.Intrinsics.X86.Sse?displayProperty=nameWithType> メソッドと <xref:System.Runtime.Intrinsics.X86.Sse2?displayProperty=nameWithType> メソッドが修正され、`NaN` 入力を適切に処理するようになり、<xref:System.Runtime.Intrinsics.X86.Avx?displayProperty=nameWithType> クラスで同等のメソッドのハードウェア動作に一致するようになりました。</span><span class="sxs-lookup"><span data-stu-id="66c39-104">The following <xref:System.Runtime.Intrinsics.X86.Sse?displayProperty=nameWithType> and <xref:System.Runtime.Intrinsics.X86.Sse2?displayProperty=nameWithType> methods have been fixed to properly handle `NaN` inputs and match the hardware behavior of the equivalent methods in the <xref:System.Runtime.Intrinsics.X86.Avx?displayProperty=nameWithType> class:</span></span>

* `CompareGreaterThan`
* `CompareGreaterThanOrEqual`
* `CompareNotGreaterThan`
* `CompareNotGreaterThanOrEqual`
* `CompareScalarGreaterThan`
* `CompareScalarGreaterThanOrEqual`
* `CompareScalarNotGreaterThan`
* `CompareScalarNotGreaterThanOrEqual`

## <a name="change-description"></a><span data-ttu-id="66c39-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="66c39-105">Change description</span></span>

<span data-ttu-id="66c39-106">以前は、一覧にある <xref:System.Runtime.Intrinsics.X86.Sse> メソッドと <xref:System.Runtime.Intrinsics.X86.Sse2> メソッドに `NaN` を入力すると、間違った結果が返されました。</span><span class="sxs-lookup"><span data-stu-id="66c39-106">Previously, `NaN` inputs to the listed <xref:System.Runtime.Intrinsics.X86.Sse> and <xref:System.Runtime.Intrinsics.X86.Sse2> methods returned an incorrect result.</span></span> <span data-ttu-id="66c39-107">また、この結果は、<xref:System.Runtime.Intrinsics.X86.Avx> クラスでこれに相当するメソッドで生成される結果とは違っていました。</span><span class="sxs-lookup"><span data-stu-id="66c39-107">The result also differed from the result generated by the corresponding method in the <xref:System.Runtime.Intrinsics.X86.Avx> class.</span></span>

<span data-ttu-id="66c39-108">.NET 5.0 より、これらのメソッドで `NaN` 入力が正しく処理され、<xref:System.Runtime.Intrinsics.X86.Avx> クラスでこれに相当するメソッドと同じ結果が返されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="66c39-108">Starting in .NET 5.0, these methods correctly handle `NaN` inputs and return the same results as the corresponding methods in the <xref:System.Runtime.Intrinsics.X86.Avx> class.</span></span>

<span data-ttu-id="66c39-109">Streaming SIMD Extensions (SSE) および Streaming SIMD Extensions 2 (SSE2) の業界標準アーキテクチャ (ISA) には、これらの比較メソッドの直接的なハードウェア サポートがありません。そのため、ソフトウェアで実装されます。</span><span class="sxs-lookup"><span data-stu-id="66c39-109">The Streaming SIMD Extensions (SSE) and Streaming SIMD Extensions 2 (SSE2) industry standard architectures (ISAs) don't provide direct hardware support for these comparison methods, so they're implemented in software.</span></span> <span data-ttu-id="66c39-110">以前は、メソッドは不適切に実装され、`NaN` 入力が間違って処理されていました。</span><span class="sxs-lookup"><span data-stu-id="66c39-110">Previously, the methods were improperly implemented, and they incorrectly handled `NaN` inputs.</span></span> <span data-ttu-id="66c39-111">ネイティブから移植されたコードについては、間違った動作からバグが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="66c39-111">For code ported from native, the incorrect behavior may introduce bugs.</span></span> <span data-ttu-id="66c39-112">256 ビット コード パスの場合、これらのメソッドから、<xref:System.Runtime.Intrinsics.X86.Avx> クラスでの同等のメソッドとは異なる結果が生成されることもあります。</span><span class="sxs-lookup"><span data-stu-id="66c39-112">For a 256-bit code path, the methods can also produce different results to the equivalent methods in the <xref:System.Runtime.Intrinsics.X86.Avx> class.</span></span>

<span data-ttu-id="66c39-113">通常の整数に対して `CompareLessThanOrEqual(x,y)` として `CompareNotGreaterThan(x,y)` を実装できるのは、以前、メソッドがいかに間違っていたか示す例です。</span><span class="sxs-lookup"><span data-stu-id="66c39-113">As an example of how the methods were previously incorrect, you can implement `CompareNotGreaterThan(x,y)` as `CompareLessThanOrEqual(x,y)` for regular integers.</span></span> <span data-ttu-id="66c39-114">しかしながら、`NaN` 入力の場合、そのロジックでは間違った結果が計算されます。</span><span class="sxs-lookup"><span data-stu-id="66c39-114">However, for `NaN` inputs, that logic computes the wrong result.</span></span> <span data-ttu-id="66c39-115">代わりに、`CompareNotLessThan(y,x)` を使用すると数値が正しく比較され、"*かつ*"、`NaN` 入力が考慮されます。</span><span class="sxs-lookup"><span data-stu-id="66c39-115">Instead, using `CompareNotLessThan(y,x)` compares the numbers correctly *and* takes `NaN` inputs into consideration.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="66c39-116">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="66c39-116">Version introduced</span></span>

<span data-ttu-id="66c39-117">5.0</span><span class="sxs-lookup"><span data-stu-id="66c39-117">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="66c39-118">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="66c39-118">Recommended action</span></span>

- <span data-ttu-id="66c39-119">以前の動作がバグだった場合、変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="66c39-119">If the previous behavior was a bug, no change is required.</span></span>

- <span data-ttu-id="66c39-120">以前の動作が望まれたものであれば、関連呼び出しを次のように変更し、この動作を維持できます。</span><span class="sxs-lookup"><span data-stu-id="66c39-120">If the previous behavior was desired, you can maintain that behavior by changing the relevant invocation as follows:</span></span>

  * `CompareGreaterThan(x,y)` -> `CompareNotLessThanOrEqual(x,y)`
  * `CompareGreaterThanOrEqual(x,y)` -> `CompareNotLessThan(x,y)`
  * `CompareNotGreaterThan(x,y)` -> `CompareLessThanOrEqual(x,y)`
  * `CompareNotGreaterThanOrEqual(x,y)` -> `CompareLessThan(x,y)`
  * `CompareScalarGreaterThan(x,y)` -> `CompareScalarNotLessThanOrEqual(x,y)`
  * `CompareScalarGreaterThanOrEqual(x,y)` -> `CompareScalarNotLessThan(x,y)`
  * `CompareScalarNotGreaterThan(x,y)` -> `CompareScalarLessThanOrEqual(x,y)`
  * `CompareScalarNotGreaterThanOrEqual(x,y)` -> `CompareScalarLessThan(x,y)`

## <a name="affected-apis"></a><span data-ttu-id="66c39-121">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="66c39-121">Affected APIs</span></span>

- <xref:System.Runtime.Intrinsics.X86.Sse.CompareGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareScalarGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareScalarGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareScalarNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse.CompareScalarNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})?displayProperty=fullName>

- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareScalarGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareScalarGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareScalarNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>
- <xref:System.Runtime.Intrinsics.X86.Sse2.CompareScalarNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Runtime.Intrinsics.X86.Sse.CompareGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareScalarGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareScalarGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareScalarNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`
- `M:System.Runtime.Intrinsics.X86.Sse.CompareScalarNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Single},System.Runtime.Intrinsics.Vector128{System.Single})`

- `M:System.Runtime.Intrinsics.X86.Sse2.CompareGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareScalarGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareScalarGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareScalarNotGreaterThan(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`
- `M:System.Runtime.Intrinsics.X86.Sse2.CompareScalarNotGreaterThanOrEqual(System.Runtime.Intrinsics.Vector128{System.Double},System.Runtime.Intrinsics.Vector128{System.Double})`

-->