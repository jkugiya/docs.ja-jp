---
title: '破壊的変更: Microsoft.AspNetCore.App 共有フレームワークから削除されたアセンブリ'
description: ASP.NET Core 6.0 の破壊的変更について説明します。Microsoft.AspNetCore.App 共有フレームワークから一部のアセンブリが削除されました。
ms.date: 04/02/2021
ms.openlocfilehash: e6a0aa97dd97eae2cdc5aa8ae64e277840d6a083
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255260"
---
# <a name="assemblies-removed-from-microsoftaspnetcoreapp-shared-framework"></a><span data-ttu-id="eed11-103">Microsoft.AspNetCore.App 共有フレームワークから削除されたアセンブリ</span><span class="sxs-lookup"><span data-stu-id="eed11-103">Assemblies removed from Microsoft.AspNetCore.App shared framework</span></span>

<span data-ttu-id="eed11-104">次の 2 つのアセンブリが ASP.NET Core ターゲット パックから削除されました。</span><span class="sxs-lookup"><span data-stu-id="eed11-104">The following two assemblies were removed from the ASP.NET Core targeting pack:</span></span>

- <span data-ttu-id="eed11-105">System.Security.Permissions</span><span class="sxs-lookup"><span data-stu-id="eed11-105">System.Security.Permissions</span></span>
- <span data-ttu-id="eed11-106">System.Windows.Extensions</span><span class="sxs-lookup"><span data-stu-id="eed11-106">System.Windows.Extensions</span></span>

<span data-ttu-id="eed11-107">さらに、次のアセンブリが ASP.NET Core ランタイム パックから削除されました。</span><span class="sxs-lookup"><span data-stu-id="eed11-107">In addition, the following assemblies were removed from the ASP.NET Core runtime pack:</span></span>

- <span data-ttu-id="eed11-108">Microsoft.Win32.SystemEvents</span><span class="sxs-lookup"><span data-stu-id="eed11-108">Microsoft.Win32.SystemEvents</span></span>
- <span data-ttu-id="eed11-109">System.Drawing.Common</span><span class="sxs-lookup"><span data-stu-id="eed11-109">System.Drawing.Common</span></span>
- <span data-ttu-id="eed11-110">System.Security.Permissions</span><span class="sxs-lookup"><span data-stu-id="eed11-110">System.Security.Permissions</span></span>
- <span data-ttu-id="eed11-111">System.Windows.Extensions</span><span class="sxs-lookup"><span data-stu-id="eed11-111">System.Windows.Extensions</span></span>

## <a name="version-introduced"></a><span data-ttu-id="eed11-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="eed11-112">Version introduced</span></span>

<span data-ttu-id="eed11-113">ASP.NET Core 6.0</span><span class="sxs-lookup"><span data-stu-id="eed11-113">ASP.NET Core 6.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="eed11-114">以前の動作</span><span class="sxs-lookup"><span data-stu-id="eed11-114">Old behavior</span></span>

<span data-ttu-id="eed11-115">アプリケーションでは、[Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) 共有フレームワークを参照して、これらのライブラリによって提供される API を使用できました。</span><span class="sxs-lookup"><span data-stu-id="eed11-115">Applications could use APIs provided by these libraries by referencing the [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="eed11-116">新しい動作</span><span class="sxs-lookup"><span data-stu-id="eed11-116">New behavior</span></span>

<span data-ttu-id="eed11-117">プロジェクト ファイルに [PackageReference](../../../project-sdk/msbuild-props.md#packagereference) を指定せずに、影響を受けるアセンブリから API を使用すると、実行時エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="eed11-117">If you use APIs from the affected assemblies without having a [PackageReference](../../../project-sdk/msbuild-props.md#packagereference) in your project file, you might see run-time errors.</span></span> <span data-ttu-id="eed11-118">たとえば、パッケージへの明示的な参照を追加せずに、リフレクションを使用して、これらのいずれかのアセンブリから API にアクセスするアプリケーションでは、実行時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="eed11-118">For example, an application that uses reflection to access APIs from one of these assemblies without adding an explicit reference to the package will have run-time errors.</span></span> <span data-ttu-id="eed11-119">`PackageReference` により、アプリケーションの出力の一部として、アセンブリが確実に存在します。</span><span class="sxs-lookup"><span data-stu-id="eed11-119">The `PackageReference` ensures that the assemblies are present as part of the application output.</span></span>

<span data-ttu-id="eed11-120">ディスカッションについては、<https://github.com/dotnet/aspnetcore/issues/31007> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed11-120">For discussion, see <https://github.com/dotnet/aspnetcore/issues/31007>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="eed11-121">変更理由</span><span class="sxs-lookup"><span data-stu-id="eed11-121">Reason for change</span></span>

<span data-ttu-id="eed11-122">この変更は、ASP.NET Core 共有フレームワークのサイズを小さくするために導入されました。</span><span class="sxs-lookup"><span data-stu-id="eed11-122">This change was introduced to reduce the size of the ASP.NET Core shared framework.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="eed11-123">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="eed11-123">Recommended action</span></span>

<span data-ttu-id="eed11-124">引き続きプロジェクトでこれらの API を使用するには、[PackageReference](../../../project-sdk/msbuild-props.md#packagereference) を追加します。</span><span class="sxs-lookup"><span data-stu-id="eed11-124">To continue using these APIs in your project, add a [PackageReference](../../../project-sdk/msbuild-props.md#packagereference).</span></span> <span data-ttu-id="eed11-125">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="eed11-125">For example:</span></span>

```xml
<PackageReference Include="System.Security.Permissions" Version="6.0.0" />
```

## <a name="affected-apis"></a><span data-ttu-id="eed11-126">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="eed11-126">Affected APIs</span></span>

- <xref:System.Security.Permissions?displayProperty=fullName>
- <xref:System.Media?displayProperty=fullName>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2UI?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlAccessLevel?displayProperty=fullName>

<!--

## Category

ASP.NET Core

## Affected APIs

- `N:System.Security.Permissions`
- `N:System.Media`
- `N:System.Security.Cryptography.X509Certificates.X509Certificate2UI`
- `N:System.Xaml.Permissions.XamlAccessLevel`

-->
