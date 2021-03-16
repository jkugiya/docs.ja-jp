---
title: 破壊的変更:Microsoft.DotNet.PlatformAbstractions パッケージの削除
description: Microsoft.DotNet.PlatformAbstractions パッケージが削除されたという、Core .NET ライブラリに含まれる .NET 5 の破壊的変更について説明します。
ms.date: 11/01/2020
ms.openlocfilehash: aff7be816815b016e3ce694c4e9a97410538c08d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257246"
---
# <a name="microsoftdotnetplatformabstractions-package-removed"></a><span data-ttu-id="96f9a-103">Microsoft.DotNet.PlatformAbstractions パッケージの削除</span><span class="sxs-lookup"><span data-stu-id="96f9a-103">Microsoft.DotNet.PlatformAbstractions package removed</span></span>

<span data-ttu-id="96f9a-104">新しいバージョンの [Microsoft.DotNet.PlatformAbstractions NuGet パッケージ](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/)は生成されなくなります。</span><span class="sxs-lookup"><span data-stu-id="96f9a-104">No new versions of the [Microsoft.DotNet.PlatformAbstractions NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) will be produced.</span></span>

## <a name="change-description"></a><span data-ttu-id="96f9a-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="96f9a-105">Change description</span></span>

<span data-ttu-id="96f9a-106">これまで、新しいバージョンの <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> ライブラリは、新しいバージョンの .NET Core と共に生成されていました。</span><span class="sxs-lookup"><span data-stu-id="96f9a-106">Previously, new versions of the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library were produced alongside new versions of .NET Core.</span></span> <span data-ttu-id="96f9a-107">今後は、ライブラリに新機能が追加されなくなり、新しいメジャー バージョンはリリースされなくなります。</span><span class="sxs-lookup"><span data-stu-id="96f9a-107">Going forward, no new functionality will be added to the library, and no new major versions will be released.</span></span> <span data-ttu-id="96f9a-108">しかし、既存のバージョンのライブラリは引き続き動作し、サービスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="96f9a-108">However, existing versions of the library will continue to work and be serviced.</span></span>

<span data-ttu-id="96f9a-109"><xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> ライブラリは、System.\* 名前空間に既に確立されている API と重複します。</span><span class="sxs-lookup"><span data-stu-id="96f9a-109">The <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library overlaps with APIs that are already established in the System.\* namespaces.</span></span> <span data-ttu-id="96f9a-110">また、一部の <xref:Microsoft.DotNet.PlatformAbstractions> API は、System.\*API の他の部分と同じレベルの監視と長期的なサポートを考慮して設計されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="96f9a-110">Also, some <xref:Microsoft.DotNet.PlatformAbstractions> APIs weren't designed with the same level of scrutiny and long-term supportability as the rest of the System.\* APIs.</span></span> <span data-ttu-id="96f9a-111">たとえば、<xref:Microsoft.DotNet.PlatformAbstractions> では、`Platform` 列挙型を使用して、現在のオペレーティング システムのプラットフォームを記述します。</span><span class="sxs-lookup"><span data-stu-id="96f9a-111">For example, <xref:Microsoft.DotNet.PlatformAbstractions> uses the `Platform` enumeration to describe the current operating system platform.</span></span> <span data-ttu-id="96f9a-112">この列挙型の設計は、新しいプラットフォームおよび今後の柔軟性に対応できるように、<xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API が設計されたときに明示的に拒否されました。</span><span class="sxs-lookup"><span data-stu-id="96f9a-112">This enumeration design was explicitly rejected when the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API was designed, to allow for new platforms and future flexibility.</span></span>

<span data-ttu-id="96f9a-113"><xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> ライブラリで有効にされたシナリオは、それがなくても実現できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="96f9a-113">The scenarios enabled by the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library are now possible without it.</span></span> <span data-ttu-id="96f9a-114">既存のバージョンは、.NET 5 以降でも引き続き動作し、以前のバージョンの .NET Core と共にサービスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="96f9a-114">Existing versions will continue to work, even in .NET 5 and later, and will be serviced along with previous versions of .NET Core.</span></span> <span data-ttu-id="96f9a-115">しかし、新機能はライブラリに追加されなくなります。</span><span class="sxs-lookup"><span data-stu-id="96f9a-115">However, new functionality won't be added to the library.</span></span> <span data-ttu-id="96f9a-116">代わりに、他のライブラリと API に新機能が追加されるようになります。</span><span class="sxs-lookup"><span data-stu-id="96f9a-116">Instead, new functionality will be added to other libraries and APIs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="96f9a-117">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="96f9a-117">Version introduced</span></span>

<span data-ttu-id="96f9a-118">5.0</span><span class="sxs-lookup"><span data-stu-id="96f9a-118">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="96f9a-119">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="96f9a-119">Recommended action</span></span>

- <span data-ttu-id="96f9a-120">要件が満たされている場合は、古いバージョンのライブラリを引き続き使用することができます。</span><span class="sxs-lookup"><span data-stu-id="96f9a-120">You can continue to use older versions of the library if they meet your requirements.</span></span>

- <span data-ttu-id="96f9a-121">以前のバージョンで要件が満たされていない場合は、`PlatformAbstractions` API の代わりに推奨される代替を使用してください。</span><span class="sxs-lookup"><span data-stu-id="96f9a-121">If the older versions don't meet your requirements, replace usages of the `PlatformAbstractions` APIs with the recommended replacements.</span></span>

  | <span data-ttu-id="96f9a-122">`PlatformAbstractions` API</span><span class="sxs-lookup"><span data-stu-id="96f9a-122">`PlatformAbstractions` API</span></span> | <span data-ttu-id="96f9a-123">推奨代替</span><span class="sxs-lookup"><span data-stu-id="96f9a-123">Recommended replacement</span></span> |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <span data-ttu-id="96f9a-124"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> および <xref:System.Environment.OSVersion?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="96f9a-124"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> and <xref:System.Environment.OSVersion?displayProperty=nameWithType></span></span> |

  > [!NOTE]
  > <span data-ttu-id="96f9a-125">`RuntimeEnvironment.OperatingSystem` と `RuntimeEnvironment.OperatingSystemVersion` のほとんどのユース ケースは、表示目的で使用されます。たとえば、ユーザー、ログ記録、テレメトリに表示するためのものです。</span><span class="sxs-lookup"><span data-stu-id="96f9a-125">Most use cases for `RuntimeEnvironment.OperatingSystem` and `RuntimeEnvironment.OperatingSystemVersion` are for display purposes, for example, displaying to a user, logging, and telemetry.</span></span> <span data-ttu-id="96f9a-126">オペレーティング システム (OS) のバージョンに基づいて、実行時の決定を行うことはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="96f9a-126">It's not recommended to make run-time decisions based on an operating system (OS) version.</span></span> <span data-ttu-id="96f9a-127"><xref:System.Environment.OSVersion?displayProperty=nameWithType> では、Windows および macOS オペレーティング システムの[正しいバージョンが返される](environment-osversion-returns-correct-version.md)ようになりました。</span><span class="sxs-lookup"><span data-stu-id="96f9a-127"><xref:System.Environment.OSVersion?displayProperty=nameWithType> now [returns the correct version](environment-osversion-returns-correct-version.md) for Windows and macOS operating systems.</span></span> <span data-ttu-id="96f9a-128">しかし、ほとんどの Unix ディストリビューションでは、どのようなものを "OS バージョン" と見なすかは簡単ではありません。</span><span class="sxs-lookup"><span data-stu-id="96f9a-128">However, for most Unix distributions, what is considered to be the "OS version" is not as straightforward.</span></span> <span data-ttu-id="96f9a-129">たとえば、Linux カーネル バージョンの場合もあれば、ディストリビューション バージョンの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="96f9a-129">For example, it could be the Linux kernel version, or it could be the distro version.</span></span> <span data-ttu-id="96f9a-130">ほとんどの Unix プラットフォームでは、<xref:System.Environment.OSVersion?displayProperty=nameWithType> と <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> から、`uname` で返されるバージョンが返されます。</span><span class="sxs-lookup"><span data-stu-id="96f9a-130">For most Unix platforms, <xref:System.Environment.OSVersion?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> return the version that's returned by `uname`.</span></span> <span data-ttu-id="96f9a-131">Linux ディストリビューションの名前とバージョン情報を取得する場合は、 */etc/os-release* ファイルを読み取ることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="96f9a-131">To get the Linux distro name and version information, the recommended approach is to read the */etc/os-release* file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="96f9a-132">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="96f9a-132">Affected APIs</span></span>

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
