---
description: '詳細については、「方法: WAS で WCF サービスをホストする」を参照してください。'
title: '方法: WAS で WCF サービスをホストする'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: dcc5d553cc864050c5d1641fa86effc5a8129d4c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793767"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="349b5-103">方法: WAS で WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="349b5-103">How to: Host a WCF Service in WAS</span></span>

<span data-ttu-id="349b5-104">このトピックでは、Windows プロセスアクティブ化サービス (WAS) でホストされる Windows Communication Foundation (WCF) サービスを作成するために必要な基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="349b5-104">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="349b5-105">WAS は、HTTP 以外のトランスポート プロトコルで動作するインターネット インフォメーション サービス (IIS) 機能を一般化した新しいプロセス アクティブ化サービスです。</span><span class="sxs-lookup"><span data-stu-id="349b5-105">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="349b5-106">WCF では、リスナーアダプターインターフェイスを使用して、WCF でサポートされている HTTP 以外のプロトコル (TCP、名前付きパイプ、メッセージキューなど) を介して受信されるアクティブ化要求を伝達します。</span><span class="sxs-lookup"><span data-stu-id="349b5-106">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="349b5-107">このホスト オプションでは、WAS アクティブ化コンポーネントのインストールと構成が正しく行われている必要がありますが、アプリケーションの一部としてホスト コードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="349b5-107">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="349b5-108">WAS のインストールと構成の詳細については、「 [方法: WCF アクティブ化コンポーネントをインストールおよび構成](how-to-install-and-configure-wcf-activation-components.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="349b5-108">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="349b5-109">Web サーバーの要求処理パイプラインをクラシック モードに設定すると、WAS のアクティブ化がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="349b5-109">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="349b5-110">WAS のアクティブ化を使用する場合は、Web サーバーの要求処理パイプラインを統合モードに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="349b5-110">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="349b5-111">WCF サービスが WAS でホストされている場合、標準のバインドが通常の方法で使用されます。</span><span class="sxs-lookup"><span data-stu-id="349b5-111">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="349b5-112">ただし、WAS でホストされるサービスを <xref:System.ServiceModel.NetTcpBinding> や <xref:System.ServiceModel.NetNamedPipeBinding> を使用して構成する場合は、制限を遵守する必要があります。</span><span class="sxs-lookup"><span data-stu-id="349b5-112">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="349b5-113">つまり、異なるエンドポイントが同じトランスポートを使用する場合、次の 7 つのプロパティでバインディング設定が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="349b5-113">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="349b5-114">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="349b5-114">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="349b5-115">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="349b5-115">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="349b5-116">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="349b5-116">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="349b5-117">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="349b5-117">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="349b5-118">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="349b5-118">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="349b5-119">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="349b5-119">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="349b5-120">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="349b5-120">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="349b5-121">バインディングの設定が一致しない場合、これらのプロパティの値は常に最初に初期化されたエンドポイントによって決定されるため、後で追加されるエンドポイントは <xref:System.ServiceModel.ServiceActivationException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="349b5-121">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="349b5-122">この例のソースコピーについては、「 [TCP Activation](../samples/tcp-activation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="349b5-122">For the source copy of this example, see [TCP Activation](../samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="349b5-123">WAS でホストされる基本サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="349b5-123">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="349b5-124">サービスの種類にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="349b5-124">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="349b5-125">サービス クラスにサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="349b5-125">Implement the service contract in a service class.</span></span> <span data-ttu-id="349b5-126">アドレス情報とバインディング情報はサービスの実装内では指定されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="349b5-126">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="349b5-127">同様に、コードは構成ファイルから情報を取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="349b5-127">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="349b5-128"><xref:System.ServiceModel.NetTcpBinding> エンドポイントによって使用される `CalculatorService` バインディングを定義する Web.config ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="349b5-128">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="349b5-129">次のコードを含む Service.svc ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="349b5-129">Create a Service.svc file that contains the following code.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="349b5-130">IIS 仮想ディレクトリに Service.svc ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="349b5-130">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="349b5-131">サービスを使用するクライアントを作成するには</span><span class="sxs-lookup"><span data-stu-id="349b5-131">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="349b5-132">コマンドラインから [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、サービスメタデータからコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="349b5-132">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="349b5-133">生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="349b5-133">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="349b5-134">生成されたクライアント アプリケーションは `ClientCalculator` も実装します。</span><span class="sxs-lookup"><span data-stu-id="349b5-134">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="349b5-135">このサービスの実装では、アドレス情報とバインディング情報が指定されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="349b5-135">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="349b5-136">同様に、コードは構成ファイルから情報を取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="349b5-136">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="349b5-137"><xref:System.ServiceModel.NetTcpBinding> を使用するクライアントの構成は、Svcutil.exe で生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="349b5-137">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="349b5-138">Visual Studio を使用する場合は、このファイルの名前は App.config ファイル内で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="349b5-138">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="349b5-139">アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="349b5-139">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="349b5-140">クライアントをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="349b5-140">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349b5-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="349b5-141">See also</span></span>

- [<span data-ttu-id="349b5-142">TCP アクティベーション</span><span class="sxs-lookup"><span data-stu-id="349b5-142">TCP Activation</span></span>](../samples/tcp-activation.md)
- <span data-ttu-id="349b5-143">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="349b5-143">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
