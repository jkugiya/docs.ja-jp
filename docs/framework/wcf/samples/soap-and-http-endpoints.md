---
description: 詳細については、「SOAP と HTTP エンドポイント」を参照してください。
title: SOAP エンドポイントおよび HTTP エンドポイント
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: e07f2d33656b6f697d25a684e49e60d748badc2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703537"
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="daf08-103">SOAP エンドポイントおよび HTTP エンドポイント</span><span class="sxs-lookup"><span data-stu-id="daf08-103">SOAP and HTTP Endpoints</span></span>

<span data-ttu-id="daf08-104">このサンプルでは、WCF Web プログラミングモデルを使用して、RPC ベースのサービスを実装し、SOAP 形式および "Plain Old XML" (POX) 形式で公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="daf08-104">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the WCF Web Programming model.</span></span> <span data-ttu-id="daf08-105">サービスの HTTP バインディングの詳細については、「 [基本的な Http サービス](basic-http-service.md) のサンプル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="daf08-105">See the [Basic HTTP Service](basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="daf08-106">このサンプルでは、さまざまなバインドを使用して SOAP および HTTP で RPC ベースのサービスを公開する方法について詳しく示します。</span><span class="sxs-lookup"><span data-stu-id="daf08-106">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="daf08-107">対象</span><span class="sxs-lookup"><span data-stu-id="daf08-107">Demonstrates</span></span>  

 <span data-ttu-id="daf08-108">WCF を使用して SOAP および HTTP 経由で RPC サービスを公開する。</span><span class="sxs-lookup"><span data-stu-id="daf08-108">Exposing an RPC service over SOAP and HTTP using WCF.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="daf08-109">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="daf08-109">Discussion</span></span>  

 <span data-ttu-id="daf08-110">このサンプルは2つのコンポーネントで構成されています。 WCF サービスを含む Web アプリケーションプロジェクト (サービス) と、SOAP および HTTP バインディングを使用してサービス操作を呼び出すコンソールアプリケーション (クライアント) です。</span><span class="sxs-lookup"><span data-stu-id="daf08-110">This sample consists of two components: a Web Application project (Service) that contains a WCF service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="daf08-111">WCF サービスは、 `GetData` `PutData` 入力として渡された文字列をエコーする2つの操作 (と) を公開します。</span><span class="sxs-lookup"><span data-stu-id="daf08-111">The WCF service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="daf08-112">サービス操作には、<xref:System.ServiceModel.Web.WebGetAttribute> および <xref:System.ServiceModel.Web.WebInvokeAttribute> を使用して注釈が付けられます。</span><span class="sxs-lookup"><span data-stu-id="daf08-112">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="daf08-113">これらの属性は、これらの操作の HTTP 投影を制御します。</span><span class="sxs-lookup"><span data-stu-id="daf08-113">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="daf08-114">また、サービス操作には、<xref:System.ServiceModel.OperationContractAttribute> を使用して注釈が付けられます。この属性では、サービス操作を SOAP バインディングで公開できます。</span><span class="sxs-lookup"><span data-stu-id="daf08-114">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="daf08-115">サービスの `PutData` メソッドは <xref:System.ServiceModel.Web.WebFaultException> をスローします。この例外は、HTTP では HTTP ステータス コードを使用して返送され、SOAP では SOAP エラーとして返送されます。</span><span class="sxs-lookup"><span data-stu-id="daf08-115">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="daf08-116">Web.config ファイルは、3つのエンドポイントを使用して WCF サービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="daf08-116">The Web.config file configures the WCF service with 3 endpoints:</span></span>  
  
- <span data-ttu-id="daf08-117">SOAP ベースのクライアントからアクセスするためのサービス メタデータを公開する ~/service.svc/mex エンドポイント</span><span class="sxs-lookup"><span data-stu-id="daf08-117">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
- <span data-ttu-id="daf08-118">クライアントが HTTP バインディングを使用してサービスにアクセスできる ~/service.svc/http エンドポイント</span><span class="sxs-lookup"><span data-stu-id="daf08-118">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
- <span data-ttu-id="daf08-119">クライアントが HTTP バインディングで SOAP を使用してサービスにアクセスできる ~/service.svc/soap endpoint エンドポイント</span><span class="sxs-lookup"><span data-stu-id="daf08-119">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="daf08-120">HTTP エンドポイントは、<> 標準エンドポイントで構成され、がに設定されてい `webHttp` `helpEnabled` `true` ます。</span><span class="sxs-lookup"><span data-stu-id="daf08-120">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="daf08-121">その結果、サービスは、HTTP ベースのクライアントがサービスにアクセスするために使用できる、XHTML ベースのヘルプ ページ (~/service.svc/http/help) を公開します。</span><span class="sxs-lookup"><span data-stu-id="daf08-121">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="daf08-122">クライアントプロジェクトは、( **サービス参照の追加** によって生成された) SOAP プロキシを使用してサービスにアクセスし、を使用してサービスにアクセスする方法を示して <xref:System.Net.WebClient> います。</span><span class="sxs-lookup"><span data-stu-id="daf08-122">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="daf08-123">サンプルは、1 つの Web ホスト サービスと 1 つのコンソール アプリケーションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="daf08-123">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="daf08-124">コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="daf08-124">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="daf08-125">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="daf08-125">To run the sample</span></span>  
  
1. <span data-ttu-id="daf08-126">SOAP および HTTP エンドポイント サンプルのソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="daf08-126">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2. <span data-ttu-id="daf08-127">Ctrl + Shift + B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="daf08-127">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3. <span data-ttu-id="daf08-128">まだ開いていない場合は、CTRL + W、S キーを押して、[ **ソリューションエクスプローラー** ] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="daf08-128">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4. <span data-ttu-id="daf08-129">[ **ソリューションエクスプローラー** ] ウィンドウで **サービス** プロジェクトを右クリックし、[ **デバッグ** ] コンテキストメニューオプションの上にカーソルを置き、[ **新しいインスタンスを開始** ] コンテキストメニューが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="daf08-129">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="daf08-130">[ **新しいインスタンスを開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="daf08-130">Click **Start New Instance**.</span></span> <span data-ttu-id="daf08-131">これで、サービスをホストする ASP.NET 開発サーバーが起動します。</span><span class="sxs-lookup"><span data-stu-id="daf08-131">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5. <span data-ttu-id="daf08-132">ソリューションエクスプローラーウィンドウで、クライアントプロジェクトを右クリックし、[ **デバッグ** ] コンテキストメニューオプションの上にカーソルを置き、[ **新しいインスタンスを開始** ] コンテキストメニューが表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="daf08-132">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="daf08-133">[ **新しいインスタンスを開始**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="daf08-133">Click **Start New Instance**.</span></span>  
  
6. <span data-ttu-id="daf08-134">クライアント コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。</span><span class="sxs-lookup"><span data-stu-id="daf08-134">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="daf08-135">ブラウザーでヘルプ ページの URI を入力することで、いつでも HTML ヘルプ ページを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="daf08-135">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7. <span data-ttu-id="daf08-136">サンプルが実行されると、クライアントは現在のアクティビティのステータスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="daf08-136">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8. <span data-ttu-id="daf08-137">クライアント コンソール アプリケーションを終了するには、任意のキーを押します。</span><span class="sxs-lookup"><span data-stu-id="daf08-137">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="daf08-138">サービスのデバッグを停止するには、Shift キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="daf08-138">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="daf08-139">Windows 通知領域で、ASP.NET development サーバーアイコンを右クリックし、コンテキストメニューの [ **停止** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="daf08-139">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="daf08-140">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="daf08-140">The samples may already be installed on your machine.</span></span> <span data-ttu-id="daf08-141">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="daf08-141">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="daf08-142">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="daf08-142">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="daf08-143">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="daf08-143">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
