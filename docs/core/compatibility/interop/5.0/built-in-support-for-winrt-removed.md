---
title: '破壊的変更: WinRT の組み込みサポートは .NET から削除されています'
description: .NET 5 での相互運用に関する破壊的変更について学習します。この変更により、WinRT の組み込みサポートは .NET から削除されています。
ms.date: 10/13/2020
ms.openlocfilehash: 986b810b74c7e7d7514ec2b734bfab45e29b87fa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256687"
---
# <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="27cca-103">WinRT の組み込みサポートは .NET から削除されています</span><span class="sxs-lookup"><span data-stu-id="27cca-103">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="27cca-104">.NET の [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) API を使用するための組み込みサポートは削除されています。</span><span class="sxs-lookup"><span data-stu-id="27cca-104">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="27cca-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="27cca-105">Version introduced</span></span>

<span data-ttu-id="27cca-106">5.0</span><span class="sxs-lookup"><span data-stu-id="27cca-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="27cca-107">変更の説明</span><span class="sxs-lookup"><span data-stu-id="27cca-107">Change description</span></span>

<span data-ttu-id="27cca-108">以前は、CoreCLR では、[Windows メタデータ (WinMD) ファイル](/uwp/winrt-cref/winmd-files)を使用し、WinRT タイプをアクティブ化し、使用していました。</span><span class="sxs-lookup"><span data-stu-id="27cca-108">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="27cca-109">.NET 5 以降、CoreCLR では、WinMD ファイルを直接使用することができなくなりました。</span><span class="sxs-lookup"><span data-stu-id="27cca-109">Starting in .NET 5, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="27cca-110">サポートされていないアセンブリを参照しようとすると、<xref:System.IO.FileNotFoundException> が表示されます。</span><span class="sxs-lookup"><span data-stu-id="27cca-110">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="27cca-111">WinRT クラスをアクティブ化すると、<xref:System.PlatformNotSupportedException> が表示されます。</span><span class="sxs-lookup"><span data-stu-id="27cca-111">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="27cca-112">この破壊的変更は次の理由から行われました。</span><span class="sxs-lookup"><span data-stu-id="27cca-112">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="27cca-113">WinRT は .NET ランタイムとは別に開発し、改善できるため。</span><span class="sxs-lookup"><span data-stu-id="27cca-113">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="27cca-114">iOS や Android など、他のオペレーティング システムに提供されている相互運用システムと釣り合いを取るため。</span><span class="sxs-lookup"><span data-stu-id="27cca-114">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="27cca-115">C# の機能、中間言語 (IL) のリンク、Ahead Of Time (AOT) コンパイルなど、その他の .NET 機能を活用するため。</span><span class="sxs-lookup"><span data-stu-id="27cca-115">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="27cca-116">.NET ランタイム コードベースを簡略化するため。</span><span class="sxs-lookup"><span data-stu-id="27cca-116">To simplify the .NET runtime codebase.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="27cca-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="27cca-117">Recommended action</span></span>

- <span data-ttu-id="27cca-118">[Microsoft.Windows.SDK.Contracts パッケージ](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)の参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="27cca-118">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span></span>  <span data-ttu-id="27cca-119">代わりに、プロジェクトの `TargetFramework` プロパティ経由でアクセスする Windows API のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="27cca-119">Instead, specify the version of the Windows APIs that you want to access via the `TargetFramework` property of the project.</span></span>  <span data-ttu-id="27cca-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="27cca-120">For example:</span></span>

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- <span data-ttu-id="27cca-121">[C#/WinRT](/windows/uwp/csharp-winrt/) ツール チェーンを使用し、.NET 5 以降のバージョンで WinRT の API と型を生成するか、カスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="27cca-121">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types for .NET 5 and later versions.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="27cca-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="27cca-122">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

### Category

Interop

-->
