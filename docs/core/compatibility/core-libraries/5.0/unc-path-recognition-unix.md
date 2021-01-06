---
title: 破壊的変更:Unix での UNC パスの URI 認識
description: Core .NET ライブラリでの .NET 5.0 の破壊的変更について学習します。この変更後、URI クラスにより、2 つのスラッシュで始まる文字列が Unix 上の UNC パスとして認識されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 0d5d9cd8dd869f24e94d15724e5e16eaddf6ed47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759349"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="dda5f-103">Unix での UNC パスの URI 認識</span><span class="sxs-lookup"><span data-stu-id="dda5f-103">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="dda5f-104">Unix オペレーティング システム上で、2 つのスラッシュ (`//`) で始まる文字列が <xref:System.Uri> クラスによって UNC (汎用名前付け規則) パスとして認識されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="dda5f-104">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="dda5f-105">この変更により、すべてのプラットフォームでそのような文字列の動作の一貫性が確保されるようになります。</span><span class="sxs-lookup"><span data-stu-id="dda5f-105">This change makes the behavior for such strings consistent across all platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="dda5f-106">変更の説明</span><span class="sxs-lookup"><span data-stu-id="dda5f-106">Change description</span></span>

<span data-ttu-id="dda5f-107">以前のバージョンの .NET では、Unix オペレーティング システム上で、2 つのスラッシュで始まる文字列 (`//contoso`など) が <xref:System.Uri> クラスによって絶対ファイル パスとして認識されます。</span><span class="sxs-lookup"><span data-stu-id="dda5f-107">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="dda5f-108">ただし、Windows では、そのような文字列は UNC パスとして認識されます。</span><span class="sxs-lookup"><span data-stu-id="dda5f-108">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="dda5f-109">.NET 5.0 以降、Unix を含むすべてのプラットフォーム上で、2 つのスラッシュで始まる文字列は <xref:System.Uri> クラスによって UNC パスとして認識されます。</span><span class="sxs-lookup"><span data-stu-id="dda5f-109">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="dda5f-110">さらに、プロパティは UNC セマンティクスに従って動作します。</span><span class="sxs-lookup"><span data-stu-id="dda5f-110">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="dda5f-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> は、`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="dda5f-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="dda5f-112">パス内の円記号は、スラッシュに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="dda5f-112">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="dda5f-113">たとえば、`//first\second` を `//first/second` にします。</span><span class="sxs-lookup"><span data-stu-id="dda5f-113">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="dda5f-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> によって文字のパーセントエンコードは行われません。</span><span class="sxs-lookup"><span data-stu-id="dda5f-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="dda5f-115">たとえば、`//first/\uFFF0` は `//first/%EF%BF%B0` に変換 "*されません*"。</span><span class="sxs-lookup"><span data-stu-id="dda5f-115">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="dda5f-116">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="dda5f-116">Version introduced</span></span>

<span data-ttu-id="dda5f-117">5.0</span><span class="sxs-lookup"><span data-stu-id="dda5f-117">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="dda5f-118">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="dda5f-118">Recommended action</span></span>

<span data-ttu-id="dda5f-119">開発者側では、何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dda5f-119">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="dda5f-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="dda5f-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->