---
title: '破壊的変更: FrameworkDescription の値が .NET Core ではなく .NET になる'
description: Core .NET ライブラリでの .NET 5 に関する破壊的変更について学習します。この変更により、RuntimeInformation.FrameworkDescription は、".NET Core" ではなく、".NET" を返すようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 18aa9a30a149b3c38d4bbfe4a0c99446f4372f07
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257519"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="01857-103">FrameworkDescription の値が .NET Core ではなく .NET になる</span><span class="sxs-lookup"><span data-stu-id="01857-103">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="01857-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、".NET Core" ではなく ".NET" が返されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="01857-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

## <a name="change-description"></a><span data-ttu-id="01857-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="01857-105">Change description</span></span>

<span data-ttu-id="01857-106">以前のバージョンの .NET では、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、説明文字列の一部として ".NET Core" が返されます。たとえば、`.NET Core 3.1.1` です。</span><span class="sxs-lookup"><span data-stu-id="01857-106">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="01857-107">.NET 5 以降は、<xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> によって、説明文字列の一部として ".NET" が返されます。たとえば、`.NET 5.0.0` です。</span><span class="sxs-lookup"><span data-stu-id="01857-107">Starting in .NET 5, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="01857-108">変更理由</span><span class="sxs-lookup"><span data-stu-id="01857-108">Reason for change</span></span>

<span data-ttu-id="01857-109">.NET 5 では、`netcoreapp` は、短いターゲット フレームワーク モニカーとして `net` に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="01857-109">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="01857-110">一貫性を確保するために、フレームワークの説明も更新されています。</span><span class="sxs-lookup"><span data-stu-id="01857-110">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="01857-111">`FrameworkName` は <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> プロパティ以外の場所ではエンコードされないため、変更は表面的なものになります。</span><span class="sxs-lookup"><span data-stu-id="01857-111">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="01857-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="01857-112">Version introduced</span></span>

<span data-ttu-id="01857-113">5.0</span><span class="sxs-lookup"><span data-stu-id="01857-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="01857-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="01857-114">Recommended action</span></span>

<span data-ttu-id="01857-115"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> によって返される文字列で ".NET Core" を検索するすべてのコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="01857-115">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="01857-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="01857-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
