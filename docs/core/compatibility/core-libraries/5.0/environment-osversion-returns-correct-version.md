---
title: 破壊的変更:Environment.OSVersion で正しいオペレーティング システム バージョンが返される
description: Environment.OSVersion から、たとえば、アプリケーションの互換性にために選択されている OS ではなく、オペレーティング システムの実際のバージョンが返されるという、コア .NET ライブラリの .NET 5 破壊的変更について学習します。
ms.date: 11/01/2020
ms.openlocfilehash: 05ec886061263ea43a2d956b8ce0ecc06e2bf3ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257532"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="c19f4-103">Environment.OSVersion で正しいオペレーティング システム バージョンが返される</span><span class="sxs-lookup"><span data-stu-id="c19f4-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="c19f4-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> で、アプリケーションの互換性のために選択される OS などではなく、オペレーティング システム (OS) の実際のバージョンが返されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="c19f4-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="c19f4-105">Change description</span></span>

<span data-ttu-id="c19f4-106">以前のバージョンの .NET では、アプリケーションが Windows 互換モードで実行されている場合、<xref:System.Environment.OSVersion?displayProperty=nameWithType> によって、正しくない可能性がある OS バージョンが返されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="c19f4-107">詳細については、[GetVersionExA 関数の解説](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c19f4-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span> <span data-ttu-id="c19f4-108">macOS では、基になる Darwin カーネルのバージョンが <xref:System.Environment.OSVersion?displayProperty=nameWithType> によって返されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-108">On macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the underlying Darwin kernel version.</span></span>

<span data-ttu-id="c19f4-109">.NET 5 以降では、Windows と macOS のオペレーティング システムの実際のバージョンが <xref:System.Environment.OSVersion?displayProperty=nameWithType> によって返されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-109">Starting in .NET 5, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system for Windows and macOS.</span></span>

<span data-ttu-id="c19f4-110">次の表に、動作の違いを示します。</span><span class="sxs-lookup"><span data-stu-id="c19f4-110">The following table shows the difference in behavior.</span></span>

|  | <span data-ttu-id="c19f4-111">以前の .NET バージョン</span><span class="sxs-lookup"><span data-stu-id="c19f4-111">Previous .NET versions</span></span> | <span data-ttu-id="c19f4-112">.NET 5+</span><span class="sxs-lookup"><span data-stu-id="c19f4-112">.NET 5+</span></span> |
|--|------------------------|---------|
| <span data-ttu-id="c19f4-113">Windows</span><span class="sxs-lookup"><span data-stu-id="c19f4-113">Windows</span></span> | <span data-ttu-id="c19f4-114">6.2.9200.0</span><span class="sxs-lookup"><span data-stu-id="c19f4-114">6.2.9200.0</span></span> | <span data-ttu-id="c19f4-115">10.0.19042.0</span><span class="sxs-lookup"><span data-stu-id="c19f4-115">10.0.19042.0</span></span> |
| <span data-ttu-id="c19f4-116">macOS</span><span class="sxs-lookup"><span data-stu-id="c19f4-116">macOS</span></span> | <span data-ttu-id="c19f4-117">19.6.0.0</span><span class="sxs-lookup"><span data-stu-id="c19f4-117">19.6.0.0</span></span> | <span data-ttu-id="c19f4-118">10.15.7</span><span class="sxs-lookup"><span data-stu-id="c19f4-118">10.15.7</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="c19f4-119">変更理由</span><span class="sxs-lookup"><span data-stu-id="c19f4-119">Reason for change</span></span>

<span data-ttu-id="c19f4-120">このプロパティのユーザーは、オペレーティング システムの実際のバージョンが返されることを期待しています。</span><span class="sxs-lookup"><span data-stu-id="c19f4-120">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="c19f4-121">ほとんどの .NET アプリにより、アプリケーション マニフェストでサポートされているバージョンが指定されないため、dotnet ホストから既定でサポートされているバージョンが取得されます。</span><span class="sxs-lookup"><span data-stu-id="c19f4-121">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="c19f4-122">その結果、実行されているアプリでは互換性 shim はほとんど意味がなくなります。</span><span class="sxs-lookup"><span data-stu-id="c19f4-122">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="c19f4-123">Windows で新しいバージョンがリリースされており、古い dotnet ホストがまだ使用されている場合は、これらのアプリの OS バージョンが正しくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c19f4-123">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="c19f4-124">実際のバージョンを返すことが、この API に対する開発者の期待により沿うことになります。</span><span class="sxs-lookup"><span data-stu-id="c19f4-124">Returning the actual version is more inline with developers' expectations of this API.</span></span>

<span data-ttu-id="c19f4-125">.NET 5 での <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>、<xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>、および <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> の導入により、Windows および macOS で <xref:System.Environment.OSVersion?displayProperty=nameWithType> が整合するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="c19f4-125">With the introduction of <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>, and <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> in .NET 5, <xref:System.Environment.OSVersion?displayProperty=nameWithType> was changed to be consistent for Windows and macOS.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c19f4-126">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="c19f4-126">Version introduced</span></span>

<span data-ttu-id="c19f4-127">5.0</span><span class="sxs-lookup"><span data-stu-id="c19f4-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c19f4-128">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="c19f4-128">Recommended action</span></span>

<span data-ttu-id="c19f4-129"><xref:System.Environment.OSVersion?displayProperty=nameWithType> を使用するコードを確認してテストし、確実に期待どおりに動作するようにします。</span><span class="sxs-lookup"><span data-stu-id="c19f4-129">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c19f4-130">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="c19f4-130">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
