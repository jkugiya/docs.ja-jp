---
title: .NET Web アプリまたはサービスを Azure App Service に移行する
description: .NET Web アプリまたはサービスをオンプレミスから Azure App Service に移行する方法について説明します。
ms.topic: conceptual
ms.date: 07/08/2020
ms.openlocfilehash: 0e2aaa23aedabef007878901ec7297711f140533
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189253"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a><span data-ttu-id="79c71-103">.NET Web アプリまたはサービスを Azure App Service に移行する</span><span class="sxs-lookup"><span data-stu-id="79c71-103">Migrate your .NET web app or service to Azure App Service</span></span>

<span data-ttu-id="79c71-104">[App Service](/azure/app-service/overview) は、スケーラブルな Web サイトと Web アプリケーションをホストするために最適化された、フル マネージドのコンピューティング プラットフォーム サービスです。</span><span class="sxs-lookup"><span data-stu-id="79c71-104">[App Service](/azure/app-service/overview) is a fully managed compute platform service that's optimized for hosting scalable websites and web applications.</span></span> <span data-ttu-id="79c71-105">この記事では、既存のアプリケーションを Azure App Service にリフトアンドシフトする方法、考慮すべき変更、および[クラウドへの移行](https://azure.microsoft.com/migration/web-applications/)に関するその他のリソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="79c71-105">This article provides information on how to lift-and-shift an existing application to Azure App Service, modifications to consider, and additional resources for [moving to the cloud](https://azure.microsoft.com/migration/web-applications/).</span></span> <span data-ttu-id="79c71-106">ほとんどの ASP.NET Web サイト (WebForms、MVC) とサービス (Web API、WCF) は、変更なしで Azure App Service に直接移行できます。</span><span class="sxs-lookup"><span data-stu-id="79c71-106">Most ASP.NET websites (Webforms, MVC) and services (Web API, WCF) can move directly to Azure App Service with no changes.</span></span> <span data-ttu-id="79c71-107">若干の変更が必要なものもあれば、リファクタリングが必要なものもあります。</span><span class="sxs-lookup"><span data-stu-id="79c71-107">Some may need minor changes while others may need some refactoring.</span></span>

<span data-ttu-id="79c71-108">開始するには、</span><span class="sxs-lookup"><span data-stu-id="79c71-108">Ready to get started?</span></span> <span data-ttu-id="79c71-109">[ASP.NET および SQL アプリケーションを Azure App Service に発行](https://tutorials.visualstudio.com/azure-webapp-migrate/intro)します。</span><span class="sxs-lookup"><span data-stu-id="79c71-109">[Publish your ASP.NET + SQL application to Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).</span></span>

## <a name="considerations"></a><span data-ttu-id="79c71-110">注意事項</span><span class="sxs-lookup"><span data-stu-id="79c71-110">Considerations</span></span>

### <a name="on-premises-resources-including-sql-server"></a><span data-ttu-id="79c71-111">オンプレミスのリソース (SQL Server を含む)</span><span class="sxs-lookup"><span data-stu-id="79c71-111">On-premises resources (including SQL Server)</span></span>

<span data-ttu-id="79c71-112">移行または変更が必要になる可能性のあるオンプレミスのリソースへのアクセスを確認します。</span><span class="sxs-lookup"><span data-stu-id="79c71-112">Verify access to on-premises resources as these may need to be migrated or changed.</span></span> <span data-ttu-id="79c71-113">オンプレミスのリソースへのアクセスを軽減するには、次のような方法があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-113">The following are options for mitigating access to on-premises resources:</span></span>

* <span data-ttu-id="79c71-114">[Azure Virtual Network](/azure/app-service/web-sites-integrate-with-vnet) を使用して、App Service をオンプレミスのリソースに接続する VPN を作成します。</span><span class="sxs-lookup"><span data-stu-id="79c71-114">Create a VPN connecting App Service to on-premises resources using [Azure Virtual Networks](/azure/app-service/web-sites-integrate-with-vnet).</span></span>
* <span data-ttu-id="79c71-115">[Azure Relay](/azure/service-bus-relay/relay-what-is-it) を使用して、ファイアウォールを変更せずに、オンプレミス サービスをクラウドに安全に公開します。</span><span class="sxs-lookup"><span data-stu-id="79c71-115">Securely expose on-premises services to the cloud without firewall changes using [Azure Relay](/azure/service-bus-relay/relay-what-is-it).</span></span>
* <span data-ttu-id="79c71-116">[SQL データベース](./sql.md)などの依存関係を Azure に移行します。</span><span class="sxs-lookup"><span data-stu-id="79c71-116">Migrate dependencies such as a [SQL database](./sql.md) to Azure.</span></span>
* <span data-ttu-id="79c71-117">クラウドのサービスとしてのプラットフォーム サービスを使用して依存関係を減らします。</span><span class="sxs-lookup"><span data-stu-id="79c71-117">Use platform-as-a-service offerings in the cloud to reduce dependencies.</span></span> <span data-ttu-id="79c71-118">たとえば、オンプレミスのメール サーバーに接続するのではなく、[SendGrid](/azure/sendgrid-dotnet-how-to-send-email) を使用することを検討します。</span><span class="sxs-lookup"><span data-stu-id="79c71-118">For example, rather than connect to an on-premises mail server, consider using [SendGrid](/azure/sendgrid-dotnet-how-to-send-email).</span></span>

### <a name="port-bindings"></a><span data-ttu-id="79c71-119">ポートのバインド</span><span class="sxs-lookup"><span data-stu-id="79c71-119">Port Bindings</span></span>

<span data-ttu-id="79c71-120">Azure App Service では、HTTP トラフィック用のポート 80 と、HTTPS トラフィック用のポート 443 がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="79c71-120">Azure App Service supports port 80 for HTTP and port 443 for HTTPS traffic.</span></span>

<span data-ttu-id="79c71-121">WCF では、次のバインドがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="79c71-121">For WCF, the following bindings are supported:</span></span>

| <span data-ttu-id="79c71-122">バインド</span><span class="sxs-lookup"><span data-stu-id="79c71-122">Binding</span></span> | <span data-ttu-id="79c71-123">メモ</span><span class="sxs-lookup"><span data-stu-id="79c71-123">Notes</span></span> |
|--|--|
| `BasicHttp` |  |
| `WSHttp` |  |
| `WSDualHttpBinding` | <span data-ttu-id="79c71-124">[Web ソケットのサポート](/azure/app-service/web-sites-configure)を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-124">[Web socket support](/azure/app-service/web-sites-configure) must be enabled.</span></span> | <span data-ttu-id="79c71-125">[Web ソケットのサポート](/azure/app-service/web-sites-configure)を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-125">[Web socket support](/azure/app-service/web-sites-configure) must be enabled.</span></span> |
| `NetHttpBinding` | <span data-ttu-id="79c71-126">双方向コントラクトに対して、[Web ソケットのサポート](/azure/app-service/web-sites-configure)を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-126">[Web socket support](/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span> | <span data-ttu-id="79c71-127">双方向コントラクトに対して、[Web ソケットのサポート](/azure/app-service/web-sites-configure)を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-127">[Web socket support](/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span> |
| `NetHttpsBinding` | <span data-ttu-id="79c71-128">双方向コントラクトに対して、[Web ソケットのサポート](/azure/app-service/web-sites-configure)を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-128">[Web socket support](/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span> | <span data-ttu-id="79c71-129">双方向コントラクトに対して、[Web ソケットのサポート](/azure/app-service/web-sites-configure)を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-129">[Web socket support](/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span> |
| `BasicHttpContextBinding` |  |
| `WebHttpBinding` |  |
| `WSHttpContextBinding` |  |

### <a name="authentication"></a><span data-ttu-id="79c71-130">認証</span><span class="sxs-lookup"><span data-stu-id="79c71-130">Authentication</span></span>

<span data-ttu-id="79c71-131">Azure App Service では既定で匿名認証がサポートされており、意図した場合はフォーム認証がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="79c71-131">Azure App Service supports anonymous authentication by default and Forms authentication when intended.</span></span> <span data-ttu-id="79c71-132">Windows 認証は、Azure Active Directory および ADFS と統合する場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="79c71-132">Windows authentication can be used by integrating with Azure Active Directory and ADFS only.</span></span> <span data-ttu-id="79c71-133">オンプレミスのディレクトリを Azure Active Directory と統合する方法の詳細については、[こちら](/azure/active-directory/connect/active-directory-aadconnect)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79c71-133">[Learn more about how to integrate your on-premises directories with Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span></span>

### <a name="assemblies-in-the-gac-global-assembly-cache"></a><span data-ttu-id="79c71-134">GAC (グローバル アセンブリ キャッシュ) 内のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="79c71-134">Assemblies in the GAC (Global Assembly Cache)</span></span>

<span data-ttu-id="79c71-135">これはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="79c71-135">This isn't supported.</span></span> <span data-ttu-id="79c71-136">アプリの *\bin* フォルダーに必要なアセンブリをコピーすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="79c71-136">Consider copying required assemblies to the app's *\bin* folder.</span></span> <span data-ttu-id="79c71-137">サーバーにインストールされているカスタム *.msi* ファイル (PDF ジェネレーターなど) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="79c71-137">Custom *.msi* files installed on the server (for example, PDF generators) cannot be used.</span></span>

### <a name="iis-settings"></a><span data-ttu-id="79c71-138">IIS 設定</span><span class="sxs-lookup"><span data-stu-id="79c71-138">IIS settings</span></span>

<span data-ttu-id="79c71-139">従来、アプリケーションの applicationHost.config で構成していたあらゆるものを、Azure Portal で構成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="79c71-139">Everything traditionally configured via applicationHost.config in your application can now be configured through the Azure portal.</span></span> <span data-ttu-id="79c71-140">AppPool のビット、WebSocket の有効化/無効化、マネージド パイプライン バージョン、.NET Framework バージョン (2.0/4.0) などがこれに該当します。</span><span class="sxs-lookup"><span data-stu-id="79c71-140">This applies to AppPool bitness, enable/disable WebSockets, managed pipeline version, .NET Framework version (2.0/4.0), and so on.</span></span> <span data-ttu-id="79c71-141">[アプリケーション設定](/azure/app-service/web-sites-configure)を変更するには、[Azure Portal](https://portal.azure.com) に移動し、Web アプリのブレードを開いて、 **[アプリケーションの設定]** タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="79c71-141">To modify your [application settings](/azure/app-service/web-sites-configure), navigate to the [Azure portal](https://portal.azure.com), open the blade for your web app, and then select the **Application Settings** tab.</span></span>

#### <a name="iis5-compatibility-mode"></a><span data-ttu-id="79c71-142">IIS5 互換モード</span><span class="sxs-lookup"><span data-stu-id="79c71-142">IIS5 Compatibility Mode</span></span>

<span data-ttu-id="79c71-143">IIS5 互換モードはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="79c71-143">IIS5 Compatibility Mode is not supported.</span></span> <span data-ttu-id="79c71-144">Azure App Service では、各 Web App とその下のすべてのアプリケーションが、[アプリケーション プール](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10))の特定のセットを使用して同じワーカー プロセスで実行されます。</span><span class="sxs-lookup"><span data-stu-id="79c71-144">In Azure App Service, each web app and all of the applications under it run in the same worker process with a specific set of [application pools](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10)).</span></span>

#### <a name="iis7-schema-compliance"></a><span data-ttu-id="79c71-145">IIS7+ スキーマ準拠</span><span class="sxs-lookup"><span data-stu-id="79c71-145">IIS7+ schema compliance</span></span>

<span data-ttu-id="79c71-146">Azure App Service IIS スキーマで定義されていない要素と属性があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-146">Some elements and attributes are not defined in the Azure App Service IIS schema.</span></span> <span data-ttu-id="79c71-147">問題が発生した場合は、[XDT 変換](/azure/app-service/configure-common)を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="79c71-147">If you encounter issues, consider using [XDT transforms](/azure/app-service/configure-common).</span></span>

#### <a name="single-application-pool-per-site"></a><span data-ttu-id="79c71-148">サイトごとに 1 つのアプリケーション プール</span><span class="sxs-lookup"><span data-stu-id="79c71-148">Single application pool per site</span></span>

<span data-ttu-id="79c71-149">Azure App Service では、各 Web アプリとその下のすべてのアプリケーションが、同じアプリケーション プールで実行されます。</span><span class="sxs-lookup"><span data-stu-id="79c71-149">In Azure App Service, each web app and all of the applications under it run in the same application pool.</span></span> <span data-ttu-id="79c71-150">一般的な設定で単一のアプリケーション プールを確立するか、アプリケーションごとに個別の Web アプリを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="79c71-150">Consider establishing a single application pool with common settings or creating a separate web app for each application.</span></span>

### <a name="com-and-com-components"></a><span data-ttu-id="79c71-151">COM および COM+ コンポーネント</span><span class="sxs-lookup"><span data-stu-id="79c71-151">COM and COM+ components</span></span>

<span data-ttu-id="79c71-152">Azure App Service では、プラットフォーム上で COM コンポーネントを登録することはできません。</span><span class="sxs-lookup"><span data-stu-id="79c71-152">Azure App Service does not allow the registration of COM components on the platform.</span></span> <span data-ttu-id="79c71-153">アプリで COM コンポーネントを使用する場合は、それらのコンポーネントをマネージド コードで書き換えて、サイトまたはアプリケーショントと共にデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-153">If your app makes use of any COM components, these need to be rewritten in managed code and deployed with the site or application.</span></span>

### <a name="physical-directories"></a><span data-ttu-id="79c71-154">物理ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="79c71-154">Physical directories</span></span>

<span data-ttu-id="79c71-155">Azure App Service では、物理ドライブへのアクセスは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="79c71-155">Azure App Service does not allow physical drive access.</span></span> <span data-ttu-id="79c71-156">[Azure Files](/azure/storage/files/storage-files-introduction) を使用して、SMB 経由でファイルにアクセスすることが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-156">You may need to use [Azure Files](/azure/storage/files/storage-files-introduction) to access files via SMB.</span></span> <span data-ttu-id="79c71-157">HTTPS 経由でアクセスする場合は、[Azure Blob Storage](/azure/storage/blobs/storage-blobs-introduction) にファイルを格納できます。</span><span class="sxs-lookup"><span data-stu-id="79c71-157">[Azure Blob Storage](/azure/storage/blobs/storage-blobs-introduction) can store files for access via HTTPS.</span></span>

### <a name="isapi-filters"></a><span data-ttu-id="79c71-158">ISAPI フィルター</span><span class="sxs-lookup"><span data-stu-id="79c71-158">ISAPI filters</span></span>

<span data-ttu-id="79c71-159">Azure App Service では、ISAPI フィルターの使用をサポートできます。ただし、ISAPI DLL をサイトと共に配置し、web.config を使用して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-159">Azure App Service can support the use of ISAPI Filters, however, the ISAPI DLL must be deployed with your site and registered via web.config.</span></span>

### <a name="https-bindings-and-ssl"></a><span data-ttu-id="79c71-160">HTTPS バインドと SSL</span><span class="sxs-lookup"><span data-stu-id="79c71-160">HTTPS bindings and SSL</span></span>

<span data-ttu-id="79c71-161">HTTPS バインドは移行されず、SSL 証明書も Web サイトに関連付けられません。</span><span class="sxs-lookup"><span data-stu-id="79c71-161">HTTPS bindings are not migrated, nor are the SSL certificates associated with your web sites.</span></span> <span data-ttu-id="79c71-162">ただし、サイトの移行が完了したら、[SSL 証明書を手動でアップロード](/azure/app-service/app-service-web-tutorial-custom-ssl)できます。</span><span class="sxs-lookup"><span data-stu-id="79c71-162">[SSL certificates can be manually uploaded](/azure/app-service/app-service-web-tutorial-custom-ssl) after site migration is completed, however.</span></span>

### <a name="sharepoint-and-frontpage"></a><span data-ttu-id="79c71-163">SharePoint と FrontPage</span><span class="sxs-lookup"><span data-stu-id="79c71-163">SharePoint and FrontPage</span></span>

<span data-ttu-id="79c71-164">SharePoint と FrontPage Server Extensions (FPSE) はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="79c71-164">SharePoint and FrontPage Server Extensions (FPSE) are not supported.</span></span>

### <a name="web-site-size"></a><span data-ttu-id="79c71-165">Web サイトのサイズ</span><span class="sxs-lookup"><span data-stu-id="79c71-165">Web site size</span></span>

<span data-ttu-id="79c71-166">無料サイトのコンテンツのサイズは 1 GB に制限されています。</span><span class="sxs-lookup"><span data-stu-id="79c71-166">Free sites have a size limit of 1 GB of content.</span></span> <span data-ttu-id="79c71-167">サイトが 1 GB を超える場合は、有料の SKU にアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-167">If your site is greater than 1 GB, you must upgrade to a paid SKU.</span></span> <span data-ttu-id="79c71-168">「[App Service の価格](https://azure.microsoft.com/pricing/details/app-service/windows/)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79c71-168">See [App Service pricing](https://azure.microsoft.com/pricing/details/app-service/windows/).</span></span>

### <a name="database-size"></a><span data-ttu-id="79c71-169">データベース サイズ</span><span class="sxs-lookup"><span data-stu-id="79c71-169">Database size</span></span>

<span data-ttu-id="79c71-170">SQL Server データベースについては、現在の [SQL Database の価格](https://azure.microsoft.com/pricing/details/sql-database)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="79c71-170">For SQL Server databases, please check the current [SQL Database pricing](https://azure.microsoft.com/pricing/details/sql-database).</span></span>

### <a name="azure-active-directory-aad-integration"></a><span data-ttu-id="79c71-171">Azure Active Directory (AAD) の統合</span><span class="sxs-lookup"><span data-stu-id="79c71-171">Azure Active Directory (AAD) integration</span></span>

<span data-ttu-id="79c71-172">AAD は無料のアプリでは機能しません。</span><span class="sxs-lookup"><span data-stu-id="79c71-172">AAD does not work with free apps.</span></span> <span data-ttu-id="79c71-173">AAD を使用するには、アプリの SKU をアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-173">To use AAD, you must upgrade the app SKU.</span></span> <span data-ttu-id="79c71-174">「[App Service の価格](https://azure.microsoft.com/pricing/details/app-service/windows/)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79c71-174">See [App Service pricing](https://azure.microsoft.com/pricing/details/app-service/windows/).</span></span>

### <a name="monitoring-and-diagnostics"></a><span data-ttu-id="79c71-175">監視と診断</span><span class="sxs-lookup"><span data-stu-id="79c71-175">Monitoring and diagnostics</span></span>

<span data-ttu-id="79c71-176">監視と診断に現在使用しているオンプレミスのソリューションは、クラウドでは機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-176">Your current on-premises solutions for monitoring and diagnostics are unlikely to work in the cloud.</span></span> <span data-ttu-id="79c71-177">ただし、Web アプリでの問題を特定し、デバッグできるように、Azure には、ログ記録、監視、診断用のツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="79c71-177">However, Azure provides tools for logging, monitoring, and diagnostics so that you can identify and debug issues with web apps.</span></span> <span data-ttu-id="79c71-178">Web アプリの診断は、アプリの構成で簡単に有効にすることができます。また、記録されたログは、Azure Application Insights で表示できます。</span><span class="sxs-lookup"><span data-stu-id="79c71-178">You can easily enable diagnostics for your web app in its configuration, and you can view the logs recorded in Azure Application Insights.</span></span> <span data-ttu-id="79c71-179">Web アプリの診断ログの有効化の詳細については、[こちら](/azure/app-service/web-sites-enable-diagnostic-log)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="79c71-179">[Learn more about enabling diagnostics logging for web apps](/azure/app-service/web-sites-enable-diagnostic-log).</span></span>

### <a name="connection-strings-and-application-settings"></a><span data-ttu-id="79c71-180">接続文字列とアプリケーション設定</span><span class="sxs-lookup"><span data-stu-id="79c71-180">Connection strings and application settings</span></span>

<span data-ttu-id="79c71-181">[Azure KeyVault](/azure/key-vault/) を使用することを検討してください。これは、アプリケーションで使用される機密情報を安全に格納するサービスです。</span><span class="sxs-lookup"><span data-stu-id="79c71-181">Consider using [Azure KeyVault](/azure/key-vault/), a service that securely stores sensitive information used in your application.</span></span> <span data-ttu-id="79c71-182">また、このデータを App Service 設定として保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="79c71-182">Alternatively, you can store this data as an App Service setting.</span></span>

### <a name="dns"></a><span data-ttu-id="79c71-183">DNS</span><span class="sxs-lookup"><span data-stu-id="79c71-183">DNS</span></span>

<span data-ttu-id="79c71-184">アプリケーションの要件に基づいて、DNS 構成を更新することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="79c71-184">You may need to update DNS configurations based on the requirements of your application.</span></span> <span data-ttu-id="79c71-185">これらの DNS 設定は、App Service の[カスタム ドメイン設定](/azure/app-service/app-service-web-tutorial-custom-domain)で構成できます。</span><span class="sxs-lookup"><span data-stu-id="79c71-185">These DNS settings can be configured in the App Service [custom domain settings](/azure/app-service/app-service-web-tutorial-custom-domain).</span></span>

## <a name="azure-app-service-with-windows-containers"></a><span data-ttu-id="79c71-186">Windows コンテナーを使用した Azure App Service</span><span class="sxs-lookup"><span data-stu-id="79c71-186">Azure App Service with Windows Containers</span></span>

<span data-ttu-id="79c71-187">アプリを App Service に直接移行できない場合は、Windows コンテナーを使用した App Service を検討します。これにより、GAC、COM コンポーネント、MSI、.NET FX API へのフル アクセス、DirectX などを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="79c71-187">If your app cannot be migrated directly to App Service, consider App Service using Windows Containers, which enables usage of the GAC, COM components, MSIs, full access to .NET FX APIs, DirectX, and more.</span></span>

## <a name="see-also"></a><span data-ttu-id="79c71-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="79c71-188">See also</span></span>

* [<span data-ttu-id="79c71-189">アプリが App Service に適しているかどうかを判断する方法</span><span class="sxs-lookup"><span data-stu-id="79c71-189">How to determine if your app qualifies for App Service</span></span>](https://appmigration.microsoft.com/)
* [<span data-ttu-id="79c71-190">クラウドへのデータベースの移行</span><span class="sxs-lookup"><span data-stu-id="79c71-190">Moving your database to the cloud</span></span>](sql.md)
* [<span data-ttu-id="79c71-191">Azure Web アプリのサンドボックスの詳細と制限事項</span><span class="sxs-lookup"><span data-stu-id="79c71-191">Azure web app sandbox details and restrictions</span></span>](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
