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
# <a name="netsdk1080-packagereference-to-microsoftaspnetcoreapp-is-not-necessary"></a>NETSDK1080: Microsoft.AspNetCore.App に対する PackageReference は不要です

NETSDK1080 は、プロジェクト ファイル内の `Microsoft.AspNetCore.App` に対して `PackageReference` 要素は不要であることを警告します。 完全なエラー メッセージは、次の例のようになります。

> 警告 NETSDK1080: .NET Core 3.0 以降をターゲットとする場合、Microsoft.AspNetCore.App に対する PackageReference は不要です。 Microsoft.NET.Sdk.Web を使用している場合は、共有フレームワークが自動的に参照されます。 それ以外の場合は、PackageReference を FrameworkReference に置き換える必要があります。

このエラーは、通常、プロジェクトをプロジェクト ファイル内に `PackageReference` エントリを必要とする以前のバージョンから .NET Core 3.0 以降にアップグレードした後に発生します。

## <a name="aspnet-core-project-files"></a>ASP.NET Core プロジェクト ファイル

たとえば、元のプロジェクト ファイルが次の例のようだったとします。

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

.NET Core 3.1 に更新すると、同じプロジェクトのプロジェクト ファイルは次の例のようになります。

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

</Project>
```

これらの変更を加えて (特に `PackageReference` 要素を削除して)、警告を除去します。 詳細については、「[古いパッケージ参照の削除](/aspnet/core/migration/22-to-30#remove-obsolete-package-references)」を参照してください。

## <a name="class-library-project"></a>クラス ライブラリ プロジェクト

ASP.NET Core API を使用するクラス ライブラリ プロジェクトで、次の例に示すように、`PackageReference` を `FrameworkReference` に置き換えます。

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

詳細については、「[クラス ライブラリで ASP.NET Core API を使用する](/aspnet/core/fundamentals/target-aspnetcore)」を参照してください。
