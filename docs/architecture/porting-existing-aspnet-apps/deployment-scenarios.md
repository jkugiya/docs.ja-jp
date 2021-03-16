---
title: ASP.NET Core に移行する場合の展開シナリオ
description: ASP.NET から ASP.NET Core に移植するときに使用できるさまざまな展開手法の概要について説明します。これにより、サイドバイサイドおよび段階的な移行が可能になります。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 589acd8c66baacc3aef5833dfaa24e2dcc5c1ee5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401386"
---
# <a name="deployment-scenarios-when-migrating-to-aspnet-core"></a><span data-ttu-id="cb433-103">ASP.NET Core に移行する場合の展開シナリオ</span><span class="sxs-lookup"><span data-stu-id="cb433-103">Deployment scenarios when migrating to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="cb433-104">既存の ASP.NET MVC および Web API アプリは、IIS と Windows 上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="cb433-104">Existing ASP.NET MVC and Web API apps run on IIS and Windows.</span></span> <span data-ttu-id="cb433-105">ASP.NET Core に移植するときは、大規模なアプリで段階的またはサイドバイサイドのアプローチが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb433-105">Large apps may require a phased or side-by-side approach when porting to ASP.NET Core.</span></span> <span data-ttu-id="cb433-106">前の章では、大規模な .NET Framework アプリを段階的に ASP.NET Core に移行するためのいくつかの方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="cb433-106">In previous chapters, you learned a number of strategies for migrating large .NET Framework apps to ASP.NET Core in phases.</span></span> <span data-ttu-id="cb433-107">この章では、その一部を移行するときに、元のアプリを運用環境で維持する必要がある場合に、さまざまな展開シナリオを実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb433-107">In this chapter, you will see how different deployment scenarios can be achieved when there is a need to maintain the original app in production while migrating portions of it.</span></span>

## <a name="split-a-large-web-app"></a><span data-ttu-id="cb433-108">大規模な web アプリを分割する</span><span class="sxs-lookup"><span data-stu-id="cb433-108">Split a large web app</span></span>

<span data-ttu-id="cb433-109">現在、単一の web サイトの IIS でホストされている大規模な web アプリの一般的なシナリオを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="cb433-109">Consider the common scenario of a large web app that currently is hosted on IIS in a single web site.</span></span> <span data-ttu-id="cb433-110">大規模なアプリでは、機能は別のルートやディレクトリに分割されます。</span><span class="sxs-lookup"><span data-stu-id="cb433-110">Within the large app, functionality is segmented into different routes and/or directories.</span></span> <span data-ttu-id="cb433-111">アプリは、MVC ビューと API エンドポイントを組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="cb433-111">The app is a mix of MVC views and API endpoints.</span></span> <span data-ttu-id="cb433-112">MVC ルートには、機能に基づいたさまざまなパスが含まれており、そのすべてが標準ルートテンプレートを使用してアプリのルートから開始され `/{controller}/{action}/{id?}` ます。</span><span class="sxs-lookup"><span data-stu-id="cb433-112">The MVC routes include many different paths based on functionality and all start from the root of the app using the standard `/{controller}/{action}/{id?}` route template.</span></span> <span data-ttu-id="cb433-113">API エンドポイントは同様のパターンに従いますが、すべてがルートの下にあり `/api` ます。</span><span class="sxs-lookup"><span data-stu-id="cb433-113">The API endpoints follow a similar pattern, but are all under an `/api` root.</span></span>

<span data-ttu-id="cb433-114">MVC 機能または API 機能が最初に ASP.NET Core に移行されるように、アプリを移植するタスクが分割されていると仮定した場合、元のサイトは、別の場所で実行されている新しい ASP.NET Core アプリとシームレスに連携して動作しますか。</span><span class="sxs-lookup"><span data-stu-id="cb433-114">Assuming the task of porting the app is split such that either the MVC functionality or the API functionality is migrated to ASP.NET Core first, how would the original site continue to function seamlessly with the new ASP.NET Core app running somewhere else?</span></span> <span data-ttu-id="cb433-115">システムのユーザーは、移行前と同じ Url を引き続き表示する必要があります。ただし、変更する必要がある場合は除きます。</span><span class="sxs-lookup"><span data-stu-id="cb433-115">Users of the system should continue to see the same URLs they did prior to the migration, unless it's absolutely necessary to change them.</span></span>

<span data-ttu-id="cb433-116">幸いなことに、IIS は非常に機能豊富な web サーバーであり、しばらくの間、 [URL 書き換えモジュールとアプリケーション要求ルーティングと](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)いう2つの機能がありました。</span><span class="sxs-lookup"><span data-stu-id="cb433-116">Fortunately, IIS is a very feature-rich web server, and two features it has had for some time are its [URL Rewrite module and Application Request Routing](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing).</span></span> <span data-ttu-id="cb433-117">これらの機能を使用して、IIS は [リバースプロキシ](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)として機能し、適切なバックエンド web アプリにクライアント要求をルーティングすることができます。</span><span class="sxs-lookup"><span data-stu-id="cb433-117">Using these features, IIS can act as a [reverse proxy](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing), routing client requests to the appropriate back-end web app.</span></span> <span data-ttu-id="cb433-118">IIS をリバースプロキシとして構成するには、アプリケーション要求ルーティング機能の [ **プロキシを有効** にする] チェックボックスをオンにし、次のような URL 書き換え規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb433-118">To configure IIS as a reverse proxy, check the **Enable proxy** checkbox in the Application Request Routing feature, then add a URL Rewrite rule like this one:</span></span>

```xml
<rule name="NetCoreProxy">
  <match url="(.*)> />
  <action type="Rewrite" url="http://servername/{R:1}" />
</rule>
```

<span data-ttu-id="cb433-119">リバースプロキシとして、IIS では、特定のパターンに一致するトラフィックを、異なるサーバー上のすべてのアプリに分離することができます。</span><span class="sxs-lookup"><span data-stu-id="cb433-119">As a reverse proxy, IIS can route traffic matching certain patterns to entirely separate apps, potentially on different servers.</span></span>

<span data-ttu-id="cb433-120">URL 書き換えモジュールだけを使用して (おそらくホストヘッダーと組み合わせて)、IIS では複数の web サイトを簡単にサポートでき、それぞれ異なるバージョンの .NET が実行される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cb433-120">Using just the URL Rewrite module (perhaps combined with host headers), IIS can easily support multiple web sites, each potentially running different versions of .NET.</span></span> <span data-ttu-id="cb433-121">大規模な web アプリは個々のサイトのコレクションとして、それぞれ異なる IP アドレスまたはホストヘッダーに対応している場合もあれば、特定の URL パスに応答する1つ以上のサブアプリケーションを含む単一の web サイトとして展開される場合もあります (URL の書き換えは必要ありません)。</span><span class="sxs-lookup"><span data-stu-id="cb433-121">A large web app might be deployed as a collection of individual sites, each responding to different IP addresses and/or host headers, or as a single web site with one or more sub-applications in it responding to certain URL paths (which doesn't even require URL Rewrite).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cb433-122">サブドメインは、通常、上位2つのレベルの前にあるドメインの部分を参照します。</span><span class="sxs-lookup"><span data-stu-id="cb433-122">Subdomains typically refer to the portion of a domain preceding the top two levels.</span></span> <span data-ttu-id="cb433-123">たとえば、ドメインでは、 `api.contoso.com` `api` はドメインのサブドメインです `contoso.com` (それ自体がドメイン `contoso` 名と `.com` トップレベルドメインまたは TLD で構成されています)。</span><span class="sxs-lookup"><span data-stu-id="cb433-123">For example, in the domain `api.contoso.com`, `api` is a subdomain of the `contoso.com` domain (which itself is composed of the `contoso` domain name and the `.com` top-level domain or TLD).</span></span> <span data-ttu-id="cb433-124">URL パスは、で始まるドメイン名の後の URL の部分を参照し `/` ます。</span><span class="sxs-lookup"><span data-stu-id="cb433-124">URL paths refer to portion of the URL that follows the domain name, starting with a `/`.</span></span> <span data-ttu-id="cb433-125">URL の `https://contoso.com/api` パスは `/api` です。</span><span class="sxs-lookup"><span data-stu-id="cb433-125">The URL `https://contoso.com/api` has a path of `/api`.</span></span>

<span data-ttu-id="cb433-126">同じまたは異なるサブドメイン (およびドメイン) を使用して1つのアプリをホストすると、長所と短所があります。</span><span class="sxs-lookup"><span data-stu-id="cb433-126">There are pros and cons to using the same or different subdomains (and domains) to host a single app.</span></span> <span data-ttu-id="cb433-127">Cookie や、 [CORS](/aspnet/core/security/cors) のようなメカニズムを使用したアプリ内通信などの機能では、分散アプリで適切に機能するためにより多くの構成が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cb433-127">Features like cookies and intra-app communication using mechanisms like [CORS](/aspnet/core/security/cors) may require more configuration to work properly in distributed apps.</span></span> <span data-ttu-id="cb433-128">ただし、異なるサブドメインを使用するアプリでは、DNS を使用して要求を完全に異なるネットワーク宛先にルーティングできるため、IIS をリバースプロキシとして動作させることなく、さまざまなサーバー (仮想またはそれ以外) に簡単に展開できます。</span><span class="sxs-lookup"><span data-stu-id="cb433-128">However, apps that use different subdomains can more easily use DNS to route requests to entirely different network destinations, and so can more easily be deployed to many different servers (virtual or otherwise) without the need for IIS to act as a reverse proxy.</span></span>

<span data-ttu-id="cb433-129">前に説明した例では、API エンドポイントが ASP.NET Core に移植されるアプリの最初の部分として指定されているとします。</span><span class="sxs-lookup"><span data-stu-id="cb433-129">In the example described above, assume the API endpoints are designated as the first part of the app to be ported to ASP.NET Core.</span></span> <span data-ttu-id="cb433-130">この場合、新しい ASP.NET Core アプリが作成され、既存の ASP.NET MVC web *サイト* 内の別の web *アプリケーション* として IIS でホストされます。</span><span class="sxs-lookup"><span data-stu-id="cb433-130">In this case, a new ASP.NET Core app is created and hosted in IIS as a separate web *application* within the existing ASP.NET MVC web *site*.</span></span> <span data-ttu-id="cb433-131">元の web サイトの子として追加され、 *api* という名前が付けられるため、既定のルートはで始まらなくなり `api/` ます。</span><span class="sxs-lookup"><span data-stu-id="cb433-131">Since it will be added as a child of the original web site and will be named *api*, its default route should no longer begin with `api/`.</span></span> <span data-ttu-id="cb433-132">これを維持すると、フォームの Url と一致するようになり `/api/api/endpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="cb433-132">Keeping this would result in it matching URLs of the form `/api/api/endpoint`.</span></span>

<span data-ttu-id="cb433-133">図5-1 は、既存の *DotNetMvcApp* サイトの一部として IIS マネージャーに ASP.NET Core 2.1 *api* アプリがどのように表示されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="cb433-133">Figure 5-1 shows how the ASP.NET Core 2.1 *api* app appears in IIS Manager as a part of the existing *DotNetMvcApp* site.</span></span>

![.NET Framework サイト内に api アプリを表示している IIS マネージャー](./media/Figure5-1.png)

<span data-ttu-id="cb433-135">**図 5-1**.</span><span class="sxs-lookup"><span data-stu-id="cb433-135">**Figure 5-1**.</span></span> <span data-ttu-id="cb433-136">IIS で .NET Core アプリを使用してサイトを .NET Framework します。</span><span class="sxs-lookup"><span data-stu-id="cb433-136">.NET Framework Site with .NET Core app in IIS.</span></span>

<span data-ttu-id="cb433-137">*DotNetMvcApp* サイトは、.NET Framework 4.7.2 で実行される MVC 5 アプリとしてホストされます。</span><span class="sxs-lookup"><span data-stu-id="cb433-137">The *DotNetMvcApp* site is hosted as an MVC 5 app running on .NET Framework 4.7.2.</span></span> <span data-ttu-id="cb433-138">独自の IIS アプリプールが統合モードで構成され、.NET CLR バージョン v4.0.30319 が実行されています。</span><span class="sxs-lookup"><span data-stu-id="cb433-138">It has its own IIS app pool configured in integrated mode and running .NET CLR version 4.0.30319.</span></span> <span data-ttu-id="cb433-139">*Api* アプリは、.NET Framework 4.6.1 () で実行される ASP.NET Core アプリです `net461` 。</span><span class="sxs-lookup"><span data-stu-id="cb433-139">The *api* app is an ASP.NET Core app running on .NET Framework 4.6.1 (`net461`).</span></span> <span data-ttu-id="cb433-140">新しい IIS アプリケーションとして *DotNetMvcApp* に追加され、独自のアプリケーションプールを使用するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="cb433-140">It was added to the *DotNetMvcApp* as a new IIS app and configured to use its own Application Pool.</span></span> <span data-ttu-id="cb433-141">このアプリケーションプールは統合モードでも実行されていますが、 [ASP.NET Core モジュール](/aspnet/core/host-and-deploy/aspnet-core-module?preserve-view=true&view=aspnetcore-2.1)を使用して実行されるため、**マネージコードのない**.net CLR バージョンで構成されています。</span><span class="sxs-lookup"><span data-stu-id="cb433-141">Its Application Pool is also running in integrated mode but is configured with a .NET CLR version of **No Managed Code** since it will be executed using the [ASP.NET Core Module](/aspnet/core/host-and-deploy/aspnet-core-module?preserve-view=true&view=aspnetcore-2.1).</span></span> <span data-ttu-id="cb433-142">ASP.NET Core アプリのバージョンはほんの一例です。</span><span class="sxs-lookup"><span data-stu-id="cb433-142">The version of the ASP.NET Core app is just an example.</span></span> <span data-ttu-id="cb433-143">また、.NET Core 3.1 または .NET 5.0 で実行されるように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb433-143">It could also be configured to run on .NET Core 3.1 or .NET 5.0.</span></span> <span data-ttu-id="cb433-144">ただし、その時点では、.NET Framework ライブラリをターゲットにすることはできなくなります (「 [適切な .Net Core バージョンを選択](choose-net-core-version.md)する」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="cb433-144">Though at that point, it would no longer be able to target .NET Framework libraries (see [Choose the Right .NET Core Version](choose-net-core-version.md))</span></span>

<span data-ttu-id="cb433-145">このように構成した場合、ASP.NET Core アプリの Api を適切にルーティングするために必要な変更は、既定のルートテンプレートをからに変更することだけです `[Route("[api/controller]")]` `[Route("[controller]")]` 。</span><span class="sxs-lookup"><span data-stu-id="cb433-145">Configured in this manner, the only change that must be made in order for the ASP.NET Core app's APIs to be routed properly is to change its default route template from `[Route("[api/controller]")]` to `[Route("[controller]")]`.</span></span>

<span data-ttu-id="cb433-146">また、IIS の別のトップレベル web サイトに ASP.NET Core アプリを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb433-146">Alternately the ASP.NET Core app can be another top-level web site in IIS.</span></span> <span data-ttu-id="cb433-147">この場合、パスがで始まる場合に他のアプリにリダイレクトされる書き換え規則 ( [URL リライト](https://www.iis.net/downloads/microsoft/url-rewrite)) を使用するように、元のサイトを構成することができ `/api` ます。</span><span class="sxs-lookup"><span data-stu-id="cb433-147">In this case, you can configure the original site to use a rewrite rule (with [URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite)) that will redirect to the other app if the path starts with `/api`.</span></span> <span data-ttu-id="cb433-148">ASP.NET Core アプリは、ルートに別のホストヘッダーを使用して、メインアプリと競合しないようにすることができますが、ルートベースのルートを使用して要求に応答できます。</span><span class="sxs-lookup"><span data-stu-id="cb433-148">The ASP.NET Core app can use a different host header for its route so that it doesn't conflict with the main app but can still respond to requests using root-based routes.</span></span>

<span data-ttu-id="cb433-149">例として、図5-1 で使用したのと同じ ASP.NET Core アプリを、IIS web サイトとして構成されている別のフォルダーに配置できます。</span><span class="sxs-lookup"><span data-stu-id="cb433-149">As an example, the same ASP.NET Core app used in Figure 5-1 can be deployed to another folder configured as an IIS web site.</span></span> <span data-ttu-id="cb433-150">サイトでは、以前と同じように構成されたアプリプールを使用する必要があります。マネージコードは使用し **ません**。</span><span class="sxs-lookup"><span data-stu-id="cb433-150">The site should use an app pool configured just as before, with **No Managed Code**.</span></span> <span data-ttu-id="cb433-151">など、サーバー上の一意のホスト名に応答するようにバインドを構成し `api.contoso.com` ます。</span><span class="sxs-lookup"><span data-stu-id="cb433-151">Configure its bindings to respond to a unique host name on the server, such as `api.contoso.com`.</span></span> <span data-ttu-id="cb433-152">`/api`IIS サーバー (または個々のサイト) レベルで新しい受信規則を追加するだけで、一致する要求を再書き込みするように URL を書き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="cb433-152">To configure URL Rewrite to rewrite requests matching `/api` just add a new inbound rule at the IIS server (or individual site) level.</span></span> <span data-ttu-id="cb433-153">パターンに一致し、 `^/api(.*)` アクションの種類との書き換え URL を指定し `Rewrite` `api.contoso.com/{R:1}` ます。</span><span class="sxs-lookup"><span data-stu-id="cb433-153">Match the pattern `^/api(.*)` and specify an Action type of `Rewrite` and a Rewrite URL of `api.contoso.com/{R:1}`.</span></span> <span data-ttu-id="cb433-154">照合パターンでを使用し、 `(.*)` `{R:1}` リライト URL でを組み合わせることにより、パスの残りの部分が新しい url で使用されるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb433-154">The combination of using `(.*)` in the matching pattern and `{R:1}` in the rewrite URL will ensure the rest of the path gets used with the new URL.</span></span> <span data-ttu-id="cb433-155">これを使用すると、同じ IIS サーバー上の個別のサイトで別々のバージョンの .NET を共存させることができますが、インターネットには1つの web アプリとして表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="cb433-155">With this in place, separate sites on the same IIS server can coexist running separate versions of .NET, but they can be made to appear to the Internet as one web app.</span></span> <span data-ttu-id="cb433-156">図5-2 は、IIS で構成されている、個別の web サイトと書き換え規則を示しています。</span><span class="sxs-lookup"><span data-stu-id="cb433-156">Figure 5-2 shows the rewrite rule as configured in IIS with the separate web site.</span></span>

![サブフォルダーの要求を別の web サイトにルーティングするための URL 書き換えルールを示す IIS マネージャー](./media/Figure5-2.png)

<span data-ttu-id="cb433-158">**図 5-2**</span><span class="sxs-lookup"><span data-stu-id="cb433-158">**Figure 5-2**.</span></span> <span data-ttu-id="cb433-159">サブフォルダーの要求を別の web サイトに書き直す規則を書き換えます。</span><span class="sxs-lookup"><span data-stu-id="cb433-159">Rewrite rule to rewrite subfolder requests to another web site.</span></span>

<span data-ttu-id="cb433-160">異なるサイトまたは IIS 内のアプリの間でシングルサインオンが必要なアプリの場合は、このシナリオをサポートするための詳細な手順について、 [ASP.NET アプリ間で認証 cookie を共有する方法](/aspnet/core/host-and-deploy/iis/) に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb433-160">If your app requires single sign-on between different sites or apps within IIS, refer to the documentation on [how to share authentication cookies among ASP.NET apps](/aspnet/core/host-and-deploy/iis/) for detailed instructions on supporting this scenario.</span></span>

## <a name="summary"></a><span data-ttu-id="cb433-161">まとめ</span><span class="sxs-lookup"><span data-stu-id="cb433-161">Summary</span></span>

<span data-ttu-id="cb433-162">大規模なアプリを .NET Framework から ASP.NET Core に移植する一般的な方法は、アプリの個々の部分を選択して1つずつ移行することです。</span><span class="sxs-lookup"><span data-stu-id="cb433-162">A common approach to porting large apps from .NET Framework to ASP.NET Core is to choose individual portions of the app to migrate one by one.</span></span> <span data-ttu-id="cb433-163">アプリの各部分が移植されると、アプリ全体が実行され、使用可能になります。元の構成で実行される部分と、.NET Core の一部のバージョンで実行されているその他の部分が実行されます。</span><span class="sxs-lookup"><span data-stu-id="cb433-163">As each piece of the app is ported, the entire app remains running and usable, with some parts of it running in its original configuration and other parts running on some version of .NET Core.</span></span> <span data-ttu-id="cb433-164">このアプローチに従うことで、大規模なアプリの移行を段階的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="cb433-164">By following this approach, a large app migration can be performed incrementally.</span></span> <span data-ttu-id="cb433-165">このアプローチでは、より迅速なフィードバックを提供し、テストに関係する総領域を減らすことで、リスクを制限します。</span><span class="sxs-lookup"><span data-stu-id="cb433-165">This approach results in limiting risk by providing more rapid feedback and reducing total surface area involved in testing.</span></span> <span data-ttu-id="cb433-166">また、パフォーマンスの向上など、.NET Core の利点をより迅速に実現できます。</span><span class="sxs-lookup"><span data-stu-id="cb433-166">It also allows for more rapid realization of benefits of .NET Core, such as performance increases.</span></span> <span data-ttu-id="cb433-167">ASP.NET Core のアプリは IIS でホストする必要がなくなりましたが、IIS は非常に柔軟で強力な web サーバーとして機能します。これは、.NET Framework と ASP.NET Core の両方のアプリを同じ IIS インスタンス上で、または異なるサーバー上でホストされているさまざまなホスティングシナリオをサポートするように構成できます。</span><span class="sxs-lookup"><span data-stu-id="cb433-167">Although ASP.NET Core apps are no longer required to be hosted on IIS, IIS remains a very flexible and powerful web server that can be configured to support a variety of hosting scenarios involving both .NET Framework and ASP.NET Core apps on the same IIS instance or even hosted on different servers.</span></span>

## <a name="references"></a><span data-ttu-id="cb433-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb433-168">References</span></span>

- [<span data-ttu-id="cb433-169">IIS を使用した Windows での ASP.NET Core のホスト</span><span class="sxs-lookup"><span data-stu-id="cb433-169">Host ASP.NET Core on Windows with IIS</span></span>](/aspnet/core/host-and-deploy/iis/)
- [<span data-ttu-id="cb433-170">URL 書き換えモジュールとアプリケーション要求ルーティング</span><span class="sxs-lookup"><span data-stu-id="cb433-170">URL Rewrite module and Application Request Routing</span></span>](/iis/extensions/url-rewrite-module/reverse-proxy-with-url-rewrite-v2-and-application-request-routing)
- [<span data-ttu-id="cb433-171">URL 書き換え</span><span class="sxs-lookup"><span data-stu-id="cb433-171">URL Rewrite</span></span>](https://www.iis.net/downloads/microsoft/url-rewrite)
- [<span data-ttu-id="cb433-172">ASP.NET Core モジュール</span><span class="sxs-lookup"><span data-stu-id="cb433-172">ASP.NET Core Module</span></span>](/aspnet/core/host-and-deploy/aspnet-core-module?preserve-view=true&view=aspnetcore-2.1)
- [<span data-ttu-id="cb433-173">ASP.NET アプリ間で認証 cookie を共有する</span><span class="sxs-lookup"><span data-stu-id="cb433-173">Share authentication cookies among ASP.NET apps</span></span>](/aspnet/core/host-and-deploy/iis/)
- [<span data-ttu-id="cb433-174">このセクションで使用するサンプル</span><span class="sxs-lookup"><span data-stu-id="cb433-174">Samples used in this section</span></span>](https://github.com/ardalis/MigrateDotNetWithIIS)

>[!div class="step-by-step"]
><span data-ttu-id="cb433-175">[前へ](more-migration-scenarios.md)
>[次へ](summary.md)</span><span class="sxs-lookup"><span data-stu-id="cb433-175">[Previous](more-migration-scenarios.md)
[Next](summary.md)</span></span>