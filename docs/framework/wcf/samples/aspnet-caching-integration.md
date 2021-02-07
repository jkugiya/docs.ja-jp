---
description: 詳細については、「ASP.NET cache Integration」を参照してください。
title: ASP.NET キャッシュ統合
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: c366efdc95cfa67f4fad9b8534edb047ad98ab32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755955"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="bad8a-103">ASP.NET キャッシュ統合</span><span class="sxs-lookup"><span data-stu-id="bad8a-103">ASP.NET Caching Integration</span></span>

<span data-ttu-id="bad8a-104">このサンプルでは、WCF WEB HTTP プログラミング モデルで ASP.NET 出力キャッシュを利用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-104">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="bad8a-105">ここでは、ASP.NET 出力キャッシュ統合機能について集中的に説明します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-105">This topic focuses on the ASP.NET output cache integration feature.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bad8a-106">対象</span><span class="sxs-lookup"><span data-stu-id="bad8a-106">Demonstrates</span></span>

<span data-ttu-id="bad8a-107">ASP.NET 出力キャッシュとの統合</span><span class="sxs-lookup"><span data-stu-id="bad8a-107">Integration with the ASP.NET Output Cache</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bad8a-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="bad8a-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bad8a-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bad8a-109">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="bad8a-110">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="bad8a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bad8a-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-111">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a><span data-ttu-id="bad8a-112">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="bad8a-112">Discussion</span></span>

<span data-ttu-id="bad8a-113">このサンプルでは、を使用して、 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Windows Communication Foundation (WCF) サービスで ASP.NET 出力キャッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-113">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="bad8a-114"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> は、サービス操作に適用される属性で、特定の操作からの応答に適用する構成ファイル内のキャッシュ プロファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>

<span data-ttu-id="bad8a-115">サンプルサービスプロジェクトの Service.cs ファイルでは、 `GetCustomer` 操作と操作の両方 `GetCustomers` が、 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> キャッシュプロファイル名 "CacheFor60Seconds" を提供するに設定されています。</span><span class="sxs-lookup"><span data-stu-id="bad8a-115">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="bad8a-116">サービスプロジェクトの Web.config ファイルでは、<> の <> 要素の下にキャッシュプロファイル "CacheFor60Seconds" が用意されてい `caching` `system.web` ます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-116">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="bad8a-117">このキャッシュプロファイルでは、属性の値 `duration` は "60" なので、このプロファイルに関連付けられている応答は ASP.NET 出力キャッシュに60秒間キャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-117">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="bad8a-118">また、このキャッシュプロファイルでは、 `varmByParam` 属性が "format" に設定されているため、クエリ文字列パラメーターの値が異なる要求の `format` 応答が個別にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-118">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="bad8a-119">最後に、キャッシュプロファイルの `varyByHeader` 属性が "Accept" に設定されているため、accept ヘッダー値が異なる要求の応答は個別にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-119">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>

<span data-ttu-id="bad8a-120">Client プロジェクトの Program.cs では、<xref:System.Net.HttpWebRequest> を使用してこのようなクライアントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-120">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="bad8a-121">これは、WCF サービスにアクセスする 1 つの方法にすぎません。</span><span class="sxs-lookup"><span data-stu-id="bad8a-121">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="bad8a-122">また、WCF チャネルファクトリやなどの他の .NET Framework クラスを使用してサービスにアクセスすることもでき <xref:System.Net.WebClient> ます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-122">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="bad8a-123">SDK のその他のサンプル ( [基本的な HTTP サービス](basic-http-service.md) サンプルなど) は、これらのクラスを使用して WCF サービスと通信する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bad8a-123">Other samples in the SDK (such as the [Basic HTTP Service](basic-http-service.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>

## <a name="to-run-the-sample"></a><span data-ttu-id="bad8a-124">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="bad8a-124">To run the sample</span></span>

<span data-ttu-id="bad8a-125">このサンプルは、3 つのプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-125">The sample consists of three projects:</span></span>

- <span data-ttu-id="bad8a-126">**Service**: ASP.NET でホストされる WCF HTTP サービスを含む Web アプリケーションプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="bad8a-126">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>

- <span data-ttu-id="bad8a-127">**Client**: サービスの呼び出しを行うコンソールアプリケーションプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="bad8a-127">**Client**: A console application project that makes calls to the service.</span></span>

- <span data-ttu-id="bad8a-128">**共通**: クライアントおよびサービスによって使用される顧客の種類を含む共有ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="bad8a-128">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>

<span data-ttu-id="bad8a-129">クライアント コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-129">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>

#### <a name="to-run-the-sample"></a><span data-ttu-id="bad8a-130">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="bad8a-130">To run the sample</span></span>

1. <span data-ttu-id="bad8a-131">ASP.NET キャッシュ統合サンプルのソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-131">Open the solution for the ASP.NET Caching Integration Sample.</span></span>

2. <span data-ttu-id="bad8a-132">Ctrl + Shift + B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="bad8a-132">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="bad8a-133">**ソリューションエクスプローラー** ウィンドウがまだ開いていない場合は、Ctrl + W + S キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-133">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>

4. <span data-ttu-id="bad8a-134">[ **ソリューションエクスプローラー** ] ウィンドウで、 **サービス** プロジェクトを右クリックし、[ **新しいインスタンスを開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-134">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="bad8a-135">これで、サービスをホストする ASP.NET 開発サーバーが起動します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-135">This launches the ASP.NET development server, which hosts the service.</span></span>

5. <span data-ttu-id="bad8a-136">[ **ソリューションエクスプローラー** ] ウィンドウで、 **クライアント** プロジェクトを右クリックし、[ **新しいインスタンスを開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-136">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>

6. <span data-ttu-id="bad8a-137">クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-137">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="bad8a-138">ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-138">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>

7. <span data-ttu-id="bad8a-139">サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="bad8a-139">As the sample runs, the client writes the status of the current activity.</span></span>

8. <span data-ttu-id="bad8a-140">クライアント コンソール アプリケーションを終了するには、任意のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-140">Press any key to terminate the client console application.</span></span>

9. <span data-ttu-id="bad8a-141">サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-141">Press SHIFT+F5 to stop debugging the service.</span></span>

10. <span data-ttu-id="bad8a-142">Windows 通知領域で、ASP.NET development server アイコンを右クリックし、[ **停止**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="bad8a-142">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
