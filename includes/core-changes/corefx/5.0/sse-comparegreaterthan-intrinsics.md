---
ms.openlocfilehash: 251b8df571dc08ab8362a6e8551f0f9f62c25a11
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702508"
---
### <a name="sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs"></a><span data-ttu-id="8d917-101">SSE および SSE2 の CompareGreaterThan メソッドで NaN 入力が正しく処理される</span><span class="sxs-lookup"><span data-stu-id="8d917-101">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>

<span data-ttu-id="8d917-102">次の <xref:System.Runtime.Intrinsics.X86.Sse?displayProperty=nameWithType> メソッドと <xref:System.Runtime.Intrinsics.X86.Sse2?displayProperty=nameWithType> メソッドが修正され、`NaN` 入力を適切に処理するようになり、<xref:System.Runtime.Intrinsics.X86.Avx?displayProperty=nameWithType> クラスで同等のメソッドのハードウェア動作に一致するようになりました。</span><span class="sxs-lookup"><span data-stu-id="8d917-102">The following <xref:System.Runtime.Intrinsics.X86.Sse?displayProperty=nameWithType> and <xref:System.Runtime.Intrinsics.X86.Sse2?displayProperty=nameWithType> methods have been fixed to properly handle `NaN` inputs and match the hardware behavior of the equivalent methods in the <xref:System.Runtime.Intrinsics.X86.Avx?displayProperty=nameWithType> class:</span></span>

* `CompareGreaterThan`
* `CompareGreaterThanOrEqual`
* `CompareNotGreaterThan`
* `CompareNotGreaterThanOrEqual`
* `CompareScalarGreaterThan`
* `CompareScalarGreaterThanOrEqual`
* `CompareScalarNotGreaterThan`
* `CompareScalarNotGreaterThanOrEqual`

#### <a name="change-description"></a><span data-ttu-id="8d917-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="8d917-103">Change description</span></span>

<span data-ttu-id="8d917-104">以前は、一覧にある <xref:System.Runtime.Intrinsics.X86.Sse> メソッドと <xref:System.Runtime.Intrinsics.X86.Sse2> メソッドに `NaN` を入力すると、間違った結果が返されました。</span><span class="sxs-lookup"><span data-stu-id="8d917-104">Previously, `NaN` inputs to the listed <xref:System.Runtime.Intrinsics.X86.Sse> and <xref:System.Runtime.Intrinsics.X86.Sse2> methods returned an incorrect result.</span></span> <span data-ttu-id="8d917-105">また、この結果は、<xref:System.Runtime.Intrinsics.X86.Avx> クラスでこれに相当するメソッドで生成される結果とは違っていました。</span><span class="sxs-lookup"><span data-stu-id="8d917-105">The result also differed from the result generated by the corresponding method in the <xref:System.Runtime.Intrinsics.X86.Avx> class.</span></span>

<span data-ttu-id="8d917-106">.NET 5.0 より、これらのメソッドで `NaN` 入力が正しく処理され、<xref:System.Runtime.Intrinsics.X86.Avx> クラスでこれに相当するメソッドと同じ結果が返されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8d917-106">Starting in .NET 5.0, these methods correctly handle `NaN` inputs and return the same results as the corresponding methods in the <xref:System.Runtime.Intrinsics.X86.Avx> class.</span></span>

<span data-ttu-id="8d917-107">Streaming SIMD Extensions (SSE) および Streaming SIMD Extensions 2 (SSE2) の業界標準アーキテクチャ (ISA) には、これらの比較メソッドの直接的なハードウェア サポートがありません。そのため、ソフトウェアで実装されます。</span><span class="sxs-lookup"><span data-stu-id="8d917-107">The Streaming SIMD Extensions (SSE) and Streaming SIMD Extensions 2 (SSE2) industry standard architectures (ISAs) don't provide direct hardware support for these comparison methods, so they're implemented in software.</span></span> <span data-ttu-id="8d917-108">以前は、メソッドは不適切に実装され、`NaN` 入力が間違って処理されていました。</span><span class="sxs-lookup"><span data-stu-id="8d917-108">Previously, the methods were improperly implemented, and they incorrectly handled `NaN` inputs.</span></span> <span data-ttu-id="8d917-109">ネイティブから移植されたコードについては、間違った動作からバグが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="8d917-109">For code ported from native, the incorrect behavior may introduce bugs.</span></span> <span data-ttu-id="8d917-110">256 ビット コード パスの場合、これらのメソッドから、<xref:System.Runtime.Intrinsics.X86.Avx> クラスでの同等のメソッドとは異なる結果が生成されることもあります。</span><span class="sxs-lookup"><span data-stu-id="8d917-110">For a 256-bit code path, the methods can also produce different results to the equivalent methods in the <xref:System.Runtime.Intrinsics.X86.Avx> class.</span></span>

<span data-ttu-id="8d917-111">通常の整数に対して `CompareLessThanOrEqual(x,y)` として `CompareNotGreaterThan(x,y)` を実装できるのは、以前、メソッドがいかに間違っていたか示す例です。</span><span class="sxs-lookup"><span data-stu-id="8d917-111">As an example of how the methods were previously incorrect, you can implement `CompareNotGreaterThan(x,y)` as `CompareLessThanOrEqual(x,y)` for regular integers.</span></span> <span data-ttu-id="8d917-112">しかしながら、`NaN` 入力の場合、そのロジックでは間違った結果が計算されます。</span><span class="sxs-lookup"><span data-stu-id="8d917-112">However, for `NaN` inputs, that logic computes the wrong result.</span></span> <span data-ttu-id="8d917-113">代わりに、`CompareNotLessThan(y,x)` を使用すると数値が正しく比較され、"*かつ*"、`NaN` 入力が考慮されます。</span><span class="sxs-lookup"><span data-stu-id="8d917-113">Instead, using `CompareNotLessThan(y,x)` compares the numbers correctly *and* takes `NaN` inputs into consideration.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8d917-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8d917-114">Version introduced</span></span>

<span data-ttu-id="8d917-115">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="8d917-115">5.0 Preview 4</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8d917-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="8d917-116">Recommended action</span></span>

- <span data-ttu-id="8d917-117">以前の動作がバグだった場合、変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8d917-117">If the previous behavior was a bug, no change is required.</span></span>

- <span data-ttu-id="8d917-118">以前の動作が望まれたものであれば、関連呼び出しを次のように変更し、この動作を維持できます。</span><span class="sxs-lookup"><span data-stu-id="8d917-118">If the previous behavior was desired, you can maintain that behavior by changing the relevant invocation as follows:</span></span>

  * `CompareGreaterThan(x,y)` -> `CompareNotLessThanOrEqual(x,y)`
  * `CompareGreaterThanOrEqual(x,y)` -> `CompareNotLessThan(x,y)`
  * `CompareNotGreaterThan(x,y)` -> `CompareLessThanOrEqual(x,y)`
  * `CompareNotGreaterThanOrEqual(x,y)` -> `CompareLessThan(x,y)`
  * `CompareScalarGreaterThan(x,y)` -> `CompareScalarNotLessThanOrEqual(x,y)`
  * `CompareScalarGreaterThanOrEqual(x,y)` -> `CompareScalarNotLessThan(x,y)`
  * `CompareScalarNotGreaterThan(x,y)` -> `CompareScalarLessThanOrEqual(x,y)`
  * `CompareScalarNotGreaterThanOrEqual(x,y)` -> `CompareScalarLessThan(x,y)`

#### <a name="category"></a><span data-ttu-id="8d917-119">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="8d917-119">Category</span></span>

<span data-ttu-id="8d917-120">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="8d917-120">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8d917-121">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8d917-121">Affected APIs</span></span>

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

#### Affected APIs

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