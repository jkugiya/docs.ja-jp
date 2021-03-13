---
title: 実稼働時に機密情報を保護するために Azure Key Vault を使用する
description: .NET マイクロサービスと Web アプリケーションのセキュリティ - Azure Key Vault は、管理者が完全に制御するアプリケーションのシークレットを処理できる優れた方法です。 管理者は開発値の割り当てや取り消しを行うこともできます。開発者に処理してもらう必要はありません。
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 94243468b35e2db9818ae9afacd5beec0a12075e
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604620"
---
# <a name="use-azure-key-vault-to-protect-secrets-at-production-time"></a><span data-ttu-id="52c2f-104">実稼働時にシークレットを保護するために Azure Key Vault を使用する</span><span class="sxs-lookup"><span data-stu-id="52c2f-104">Use Azure Key Vault to protect secrets at production time</span></span>

<span data-ttu-id="52c2f-105">環境変数として保存されているシークレットまたは Secret Manager ツールによって保存されたシークレットは、マシンのローカルに暗号化されていない状態で保存されています。</span><span class="sxs-lookup"><span data-stu-id="52c2f-105">Secrets stored as environment variables or stored by the Secret Manager tool are still stored locally and unencrypted on the machine.</span></span> <span data-ttu-id="52c2f-106">シークレットを保存する上でより安全な選択肢として [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) があります。Azure Key Vault には、キーとシークレットを保存するためのセキュリティで保護された中央の場所が用意されています。</span><span class="sxs-lookup"><span data-stu-id="52c2f-106">A more secure option for storing secrets is [Azure Key Vault](https://azure.microsoft.com/services/key-vault/), which provides a secure, central location for storing keys and secrets.</span></span>

<span data-ttu-id="52c2f-107">**Azure.Extensions.AspNetCore.Configuration.Secrets** パッケージを使用すると、ASP.NET Core アプリケーションから Azure Key Vault の構成情報を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="52c2f-107">The **Azure.Extensions.AspNetCore.Configuration.Secrets** package allows an ASP.NET Core application to read configuration information from Azure Key Vault.</span></span> <span data-ttu-id="52c2f-108">Azure Key Vault のシークレットを初めて使用する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="52c2f-108">To start using secrets from an Azure Key Vault, you follow these steps:</span></span>

1. <span data-ttu-id="52c2f-109">アプリケーションを Azure AD アプリケーションとして登録します</span><span class="sxs-lookup"><span data-stu-id="52c2f-109">Register your application as an Azure AD application.</span></span> <span data-ttu-id="52c2f-110">(キー コンテナーへのアクセスは Azure AD で管理されます)。この操作は、Azure 管理ポータルで実行できます。</span><span class="sxs-lookup"><span data-stu-id="52c2f-110">(Access to key vaults is managed by Azure AD.) This can be done through the Azure management portal.</span></span>\

   <span data-ttu-id="52c2f-111">または、アプリケーションでパスワードまたはクライアント シークレットの代わりに証明書を使用して認証する場合は、[New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell コマンドレットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="52c2f-111">Alternatively, if you want your application to authenticate using a certificate instead of a password or client secret, you can use the [New-AzADApplication](/powershell/module/az.resources/new-azadapplication) PowerShell cmdlet.</span></span> <span data-ttu-id="52c2f-112">Azure Key Vault に登録する証明書には、公開キーのみが必要です</span><span class="sxs-lookup"><span data-stu-id="52c2f-112">The certificate that you register with Azure Key Vault needs only your public key.</span></span> <span data-ttu-id="52c2f-113">アプリケーションでは秘密キーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="52c2f-113">Your application will use the private key.</span></span>

2. <span data-ttu-id="52c2f-114">新しいサービス プリンシパルを作成して、登録されたアプリケーションにキー コンテナーへのアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="52c2f-114">Give the registered application access to the key vault by creating a new service principal.</span></span> <span data-ttu-id="52c2f-115">この処理を実行するには、次の PowerShell コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="52c2f-115">You can do this using the following PowerShell commands:</span></span>

   ```powershell
   $sp = New-AzADServicePrincipal -ApplicationId "<Application ID guid>"
   Set-AzKeyVaultAccessPolicy -VaultName "<VaultName>" -ServicePrincipalName $sp.ServicePrincipalNames[0] -PermissionsToSecrets all -ResourceGroupName "<KeyVault Resource Group>"
   ```

3. <span data-ttu-id="52c2f-116"><xref:Microsoft.Extensions.Configuration.IConfigurationRoot> インスタンスを作成するときに AzureKeyVaultConfigurationExtensions.AddAzureKeyVault 拡張メソッドを呼び出して、アプリケーションの構成ソースとしてキー コンテナーを含めます。</span><span class="sxs-lookup"><span data-stu-id="52c2f-116">Include the key vault as a configuration source in your application by calling the AzureKeyVaultConfigurationExtensions.AddAzureKeyVault extension method when you create an <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> instance.</span></span>

<span data-ttu-id="52c2f-117">`AddAzureKeyVault` を呼び出すには、前の手順で登録し、キー コンテナーへのアクセス権が付与されたアプリケーション ID が必要です。</span><span class="sxs-lookup"><span data-stu-id="52c2f-117">Note that calling `AddAzureKeyVault` requires the application ID that was registered and given access to the key vault in the previous steps.</span></span> <span data-ttu-id="52c2f-118">または、最初に Azure CLI コマンド `az login` を実行してから、クライアントの代わりに DefaultAzureCredential を受け取る `AddAzureKeyVault` のオーバーロードを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="52c2f-118">Or you can firstly running the Azure CLI command: `az login`, then using an overload of `AddAzureKeyVault` that takes a DefaultAzureCredential in place of the client.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52c2f-119">Azure Key Vault を最後の構成プロバイダーとして登録して、以前のプロバイダーの構成値をオーバーライドできるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="52c2f-119">We recommend that you register Azure Key Vault as the last configuration provider, so it can override configuration values from previous providers.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="52c2f-120">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="52c2f-120">Additional resources</span></span>

- <span data-ttu-id="52c2f-121">**Azure Key Vault を使用したアプリケーション シークレットの保護** </span><span class="sxs-lookup"><span data-stu-id="52c2f-121">**Using Azure Key Vault to protect application secrets** </span></span>\
  [https://docs.microsoft.com/azure/architecture/multitenant-identity](/azure/architecture/multitenant-identity)

- <span data-ttu-id="52c2f-122">**開発中のアプリ シークレットの安全な保存** </span><span class="sxs-lookup"><span data-stu-id="52c2f-122">**Safe storage of app secrets during development** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/app-secrets](/aspnet/core/security/app-secrets)

- <span data-ttu-id="52c2f-123">**データ保護の構成** </span><span class="sxs-lookup"><span data-stu-id="52c2f-123">**Configuring data protection** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/overview](/aspnet/core/security/data-protection/configuration/overview)

- <span data-ttu-id="52c2f-124">**ASP.NET Core でのデータ保護のキー管理と有効期間** </span><span class="sxs-lookup"><span data-stu-id="52c2f-124">**Data Protection key management and lifetime in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/data-protection/configuration/default-settings](/aspnet/core/security/data-protection/configuration/default-settings)

>[!div class="step-by-step"]
><span data-ttu-id="52c2f-125">[前へ](developer-app-secrets-storage.md)
>[次へ](../key-takeaways.md)</span><span class="sxs-lookup"><span data-stu-id="52c2f-125">[Previous](developer-app-secrets-storage.md)
[Next](../key-takeaways.md)</span></span>
