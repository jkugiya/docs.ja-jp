---
title: 'NETSDK1080: Microsoft.AspNetCore.App に対する PackageReference は不要です'
description: .NET SDK エラー NETSDK1080 について説明します。これは、プロジェクト ファイル内の不要なエントリについて警告します。
ms.topic: error-reference
ms.date: 02/25/2021
f1_keywords:
- NETSDK1080
ms.openlocfilehash: ebf9484e4a358597a1177f95e92f68330180cd35
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206789"
---
# <a name="netsdk1080-packagereference-to-microsoftaspnetcoreapp-is-not-necessary"></a><span data-ttu-id="deff5-103">NETSDK1080: Microsoft.AspNetCore.App に対する PackageReference は不要です</span><span class="sxs-lookup"><span data-stu-id="deff5-103">NETSDK1080: PackageReference to Microsoft.AspNetCore.App is not necessary</span></span>

<span data-ttu-id="deff5-104">NETSDK1080 は、プロジェクト ファイル内の `Microsoft.AspNetCore.App` に対して `PackageReference` 要素は不要であることを警告します。</span><span class="sxs-lookup"><span data-stu-id="deff5-104">NETSDK1080 warns you that the `PackageReference` element for `Microsoft.AspNetCore.App` in your project file is not necessary.</span></span> <span data-ttu-id="deff5-105">完全なエラー メッセージは、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="deff5-105">The full error message is similar to the following example:</span></span>

> <span data-ttu-id="deff5-106">警告 NETSDK1080: .NET Core 3.0 以降をターゲットとする場合、Microsoft.AspNetCore.App に対する PackageReference は不要です。</span><span class="sxs-lookup"><span data-stu-id="deff5-106">warning NETSDK1080: A PackageReference to Microsoft.AspNetCore.App is not necessary when targeting .NET Core 3.0 or higher.</span></span> <span data-ttu-id="deff5-107">Microsoft.NET.Sdk.Web を使用している場合は、共有フレームワークが自動的に参照されます。</span><span class="sxs-lookup"><span data-stu-id="deff5-107">If Microsoft.NET.Sdk.Web is used, the shared framework will be referenced automatically.</span></span> <span data-ttu-id="deff5-108">それ以外の場合は、PackageReference を FrameworkReference に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="deff5-108">Otherwise, the PackageReference should be replaced with a FrameworkReference.</span></span>

<span data-ttu-id="deff5-109">このエラーは、通常、プロジェクトをプロジェクト ファイル内に `PackageReference` エントリを必要とする以前のバージョンから .NET Core 3.0 以降にアップグレードした後に発生します。</span><span class="sxs-lookup"><span data-stu-id="deff5-109">This error typically occurs after you've upgraded a project to .NET Core 3.0 or later, from an earlier version that required `PackageReference` entries in the project file.</span></span>

## <a name="aspnet-core-project-files"></a><span data-ttu-id="deff5-110">ASP.NET Core プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="deff5-110">ASP.NET Core project files</span></span>

<span data-ttu-id="deff5-111">たとえば、元のプロジェクト ファイルが次の例のようだったとします。</span><span class="sxs-lookup"><span data-stu-id="deff5-111">For example, your original project file might look like this example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp2.2</TargetFramework>
    <AspNetCoreHostingModel>InProcess</AspNetCoreHostingModel>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.App"/>
    <PackageReference Include="Microsoft.AspNetCore.Razor.Design" Version="2.2.0" PrivateAssets="All" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="deff5-112">.NET Core 3.1 に更新すると、同じプロジェクトのプロジェクト ファイルは次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="deff5-112">After updating to .NET Core 3.1 the project file for the same project should look like the following example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="deff5-113">これらの変更を加えて (特に `PackageReference` 要素を削除して)、警告を除去します。</span><span class="sxs-lookup"><span data-stu-id="deff5-113">Make these changes, in particular delete the `PackageReference` element, to eliminate the warning.</span></span> <span data-ttu-id="deff5-114">詳細については、「[古いパッケージ参照の削除](/aspnet/core/migration/22-to-30#remove-obsolete-package-references)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="deff5-114">For more information, see [Remove obsolete package references](/aspnet/core/migration/22-to-30#remove-obsolete-package-references).</span></span>

## <a name="class-library-project"></a><span data-ttu-id="deff5-115">クラス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="deff5-115">Class library project</span></span>

<span data-ttu-id="deff5-116">ASP.NET Core API を使用するクラス ライブラリ プロジェクトで、次の例に示すように、`PackageReference` を `FrameworkReference` に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="deff5-116">In a class library project that uses ASP.NET Core APIs, replace the `PackageReference` with a `FrameworkReference`, as shown in the following example:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <FrameworkReference Include="Microsoft.AspNetCore.App" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="deff5-117">詳細については、「[クラス ライブラリで ASP.NET Core API を使用する](/aspnet/core/fundamentals/target-aspnetcore)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="deff5-117">For more information, see [Use ASP.NET Core APIs in a class library](/aspnet/core/fundamentals/target-aspnetcore).</span></span>
