---
title: '破壊的変更: Azure: Microsoft というプレフィックスが付いた Azure 統合パッケージが削除された'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Azure: Microsoft というプレフィックスが付いた Azure 統合パッケージが削除された'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: be7b2eeb6b12d033517c15ecb29e0d5364d64817
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498231"
---
# <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="343a9-103">Azure: Microsoft というプレフィックスが付いた Azure 統合パッケージが削除された</span><span class="sxs-lookup"><span data-stu-id="343a9-103">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="343a9-104">ASP.NET Core と Azure SDK の統合を提供する次の `Microsoft.*` パッケージは、ASP.NET Core 5.0 に含まれていません。</span><span class="sxs-lookup"><span data-stu-id="343a9-104">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="343a9-105">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/)。[Azure Key Vault](/azure/key-vault/) を[構成システム](/aspnet/core/fundamentals/configuration/)に統合します。</span><span class="sxs-lookup"><span data-stu-id="343a9-105">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="343a9-106">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/)。Azure Key Vault を [ASP.NET Core データ保護システム](/aspnet/core/security/data-protection/introduction)に統合します。</span><span class="sxs-lookup"><span data-stu-id="343a9-106">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="343a9-107">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)。[Azure Blob Storage](/azure/storage/blobs/) を ASP.NET Core データ保護システムに統合します。</span><span class="sxs-lookup"><span data-stu-id="343a9-107">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="343a9-108">この問題に関するディスカッションについては、[dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="343a9-108">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="343a9-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="343a9-109">Version introduced</span></span>

<span data-ttu-id="343a9-110">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="343a9-110">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="343a9-111">以前の動作</span><span class="sxs-lookup"><span data-stu-id="343a9-111">Old behavior</span></span>

<span data-ttu-id="343a9-112">`Microsoft.*` パッケージにより、Azure サービスと構成 API およびデータ保護 API が統合されていました。</span><span class="sxs-lookup"><span data-stu-id="343a9-112">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="343a9-113">新しい動作</span><span class="sxs-lookup"><span data-stu-id="343a9-113">New behavior</span></span>

<span data-ttu-id="343a9-114">新しい `Azure.*` パッケージにより、Azure サービスと構成 API およびデータ保護 API が統合されます。</span><span class="sxs-lookup"><span data-stu-id="343a9-114">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="343a9-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="343a9-115">Reason for change</span></span>

<span data-ttu-id="343a9-116">この変更は、`Microsoft.*` パッケージが以下であるために行われました。</span><span class="sxs-lookup"><span data-stu-id="343a9-116">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="343a9-117">古いバージョンの Azure SDK を使用していました。</span><span class="sxs-lookup"><span data-stu-id="343a9-117">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="343a9-118">新しいバージョンの Azure SDK には破壊的変更が含まれていたため、単純な更新はできませんでした。</span><span class="sxs-lookup"><span data-stu-id="343a9-118">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="343a9-119">.NET Core のリリース スケジュールに拘束されていました。</span><span class="sxs-lookup"><span data-stu-id="343a9-119">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="343a9-120">パッケージの所有権を Azure SDK チームに譲渡すると、Azure SDK が更新されるときにパッケージを更新できます。</span><span class="sxs-lookup"><span data-stu-id="343a9-120">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="343a9-121">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="343a9-121">Recommended action</span></span>

<span data-ttu-id="343a9-122">ASP.NET Core 2.1 以降のプロジェクトでは、古い `Microsoft.*` パッケージを新しい `Azure.*` パッケージに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="343a9-122">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="343a9-123">旧</span><span class="sxs-lookup"><span data-stu-id="343a9-123">Old</span></span> | <span data-ttu-id="343a9-124">新規作成</span><span class="sxs-lookup"><span data-stu-id="343a9-124">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="343a9-125">Azure.Extensions.AspNetCore.DataProtection.Keys</span><span class="sxs-lookup"><span data-stu-id="343a9-125">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="343a9-126">Azure.Extensions.AspNetCore.DataProtection.Blobs</span><span class="sxs-lookup"><span data-stu-id="343a9-126">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="343a9-127">Azure.Extensions.AspNetCore.Configuration.Secrets</span><span class="sxs-lookup"><span data-stu-id="343a9-127">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="343a9-128">新しいパッケージでは、破壊的変更が含まれる新しいバージョンの Azure SDK が使用されています。</span><span class="sxs-lookup"><span data-stu-id="343a9-128">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="343a9-129">一般的な使用パターンは変更されません。</span><span class="sxs-lookup"><span data-stu-id="343a9-129">The general usage patterns are unchanged.</span></span> <span data-ttu-id="343a9-130">基になっている Azure SDK API での変更に対応するため、一部のオーバーロードとオプションが異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="343a9-130">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="343a9-131">古いパッケージは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="343a9-131">The old packages will:</span></span>

* <span data-ttu-id="343a9-132">.NET Core 2.1 および 3.1 の有効期間中は、ASP.NET Core チームによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="343a9-132">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="343a9-133">.NET 5 には含まれません。</span><span class="sxs-lookup"><span data-stu-id="343a9-133">Not be included in .NET 5.</span></span>

<span data-ttu-id="343a9-134">プロジェクトを .NET 5 にアップグレードするときは、サポートを維持するため `Azure.*` パッケージに切り替えてください。</span><span class="sxs-lookup"><span data-stu-id="343a9-134">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="343a9-135">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="343a9-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
