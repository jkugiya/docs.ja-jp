---
description: '詳細情報: Windows サービスホスト'
title: Windows サービス ホスト
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 529256675723e556879b8380f514ab1b0a5b7f8f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715133"
---
# <a name="windows-service-host"></a><span data-ttu-id="a778c-103">Windows サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="a778c-103">Windows Service Host</span></span>

<span data-ttu-id="a778c-104">このサンプルでは、マネージ Windows サービスでホストされている Windows Communication Foundation (WCF) サービスを示します。</span><span class="sxs-lookup"><span data-stu-id="a778c-104">This sample demonstrates a Windows Communication Foundation (WCF) service hosted in a managed Windows Service.</span></span> <span data-ttu-id="a778c-105">Windows サービスは **コントロールパネル** の [サービス] アプレットを使用して制御され、システムの再起動後に自動的に起動するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="a778c-105">Windows Services are controlled using the Services applet in **Control Panel** and can be configured to start up automatically after a system reboot.</span></span> <span data-ttu-id="a778c-106">このサンプルは、クライアント プログラムと Windows サービス プログラムで構成されています。</span><span class="sxs-lookup"><span data-stu-id="a778c-106">The sample consists of a client program and an Windows Service program.</span></span> <span data-ttu-id="a778c-107">サービスは .exe プログラムとして実装され、独自のホスティング コードが指定されます。</span><span class="sxs-lookup"><span data-stu-id="a778c-107">The service is implemented as an .exe program and contains its own hosting code.</span></span> <span data-ttu-id="a778c-108">Windows プロセス アクティブ化サービス (WAS) やインターネット インフォメーション サービス (IIS) などの他のホスト環境では、ホスティング コードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a778c-108">In other hosting environments, such as Windows Process Activation Services (WAS) or Internet Information Services (IIS), it is not necessary for you to write hosting code.</span></span>

> [!NOTE]
> <span data-ttu-id="a778c-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a778c-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a778c-110">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a778c-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a778c-111">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a778c-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a778c-112">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="a778c-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a778c-113">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a778c-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 <span data-ttu-id="a778c-114">このサービスをビルドしたら、他の Windows サービスと同様、Installutil.exe ユーティリティを使用してインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a778c-114">After building this service, it must be installed with the Installutil.exe utility like any other Windows Service.</span></span> <span data-ttu-id="a778c-115">サービスを変更する場合は、`installutil /u` を使用して、まずそのサービスをアンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a778c-115">If you are going to make changes to the service, you must first uninstall it with `installutil /u`.</span></span> <span data-ttu-id="a778c-116">このサンプルに含まれている Setup.bat ファイルは Windows Service をインストールして起動するコマンド ファイルです。同様にこのサンプルに含まれている Cleanup.bat ファイルは、Windows サービスをシャットダウンしてアンインストールするコマンド ファイルです。</span><span class="sxs-lookup"><span data-stu-id="a778c-116">The Setup.bat and Cleanup.bat files included in this sample are the commands to install and start up the Windows Service, and to shut down and uninstall the Windows Service.</span></span> <span data-ttu-id="a778c-117">WCF サービスは、Windows サービスが実行されている場合にのみ、クライアントに応答できます。</span><span class="sxs-lookup"><span data-stu-id="a778c-117">The WCF service can only respond to clients if the Windows Service is running.</span></span> <span data-ttu-id="a778c-118">**コントロールパネル** の [サービス] アプレットを使用して Windows サービスを停止し、クライアントを実行すると、 <xref:System.ServiceModel.EndpointNotFoundException> クライアントがサービスにアクセスしようとしたときに例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="a778c-118">If you stop the Windows Service by using the Services applet from **Control Panel** and run the client, a <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="a778c-119">Windows サービスを再起動してクライアントを再実行した場合は、通信が正常に行われます。</span><span class="sxs-lookup"><span data-stu-id="a778c-119">If you restart the Windows Service and rerun the client, communication succeeds.</span></span>  
  
 <span data-ttu-id="a778c-120">サービスコードには、インストーラークラス、ICalculator コントラクトを実装する WCF サービス実装クラス、およびランタイムホストとして機能する Windows サービスクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a778c-120">The service code includes an installer class, a WCF service implementation class which implements the ICalculator contract, and a Windows Service class that acts as the run-time host.</span></span> <span data-ttu-id="a778c-121">インストーラー クラスは <xref:System.Configuration.Install.Installer> を継承します。このクラスを使用すると、Installutil.exe ツールにより、プログラムを NT サービスとしてインストールできます。</span><span class="sxs-lookup"><span data-stu-id="a778c-121">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as an NT service by the Installutil.exe tool.</span></span> <span data-ttu-id="a778c-122">サービス実装クラスは、 `WcfCalculatorService` 基本的なサービスコントラクトを実装する WCF サービスです。</span><span class="sxs-lookup"><span data-stu-id="a778c-122">The service implementation class, `WcfCalculatorService`, is an WCF service that implements a basic service contract.</span></span> <span data-ttu-id="a778c-123">この WCF サービスは、という名前の Windows サービスクラス内でホストされ `WindowsCalculatorService` ます。</span><span class="sxs-lookup"><span data-stu-id="a778c-123">This WCF service is hosted inside a Windows Service class called `WindowsCalculatorService`.</span></span> <span data-ttu-id="a778c-124">Windows サービスとして限定するため、このクラスは <xref:System.ServiceProcess.ServiceBase> を継承し、<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop> メソッドを実装しています。</span><span class="sxs-lookup"><span data-stu-id="a778c-124">To qualify as a Windows Service, the class inherits from <xref:System.ServiceProcess.ServiceBase> and implements the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> and <xref:System.ServiceProcess.ServiceBase.OnStop> methods.</span></span> <span data-ttu-id="a778c-125"><xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> では、<xref:System.ServiceModel.ServiceHost> 型の `WcfCalculatorService` オブジェクトが作成され、開かれます。</span><span class="sxs-lookup"><span data-stu-id="a778c-125">In <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, a <xref:System.ServiceModel.ServiceHost> object is created for the `WcfCalculatorService` type and opened.</span></span> <span data-ttu-id="a778c-126"><xref:System.ServiceProcess.ServiceBase.OnStop> では、<xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> オブジェクトの <xref:System.ServiceModel.ServiceHost> メソッドが呼び出されて ServiceHost が閉じられます。</span><span class="sxs-lookup"><span data-stu-id="a778c-126">In <xref:System.ServiceProcess.ServiceBase.OnStop>, the ServiceHost is closed by calling the <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> method of the <xref:System.ServiceModel.ServiceHost> object.</span></span> <span data-ttu-id="a778c-127">ホストのベースアドレスは、要素の子である要素を使用して構成され [\<add>](../../configure-apps/file-schema/wcf/add-of-baseaddresses.md) [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) [\<host>](../../configure-apps/file-schema/wcf/host.md) ます。これは、要素の子である要素の子です [\<service>](../../configure-apps/file-schema/wcf/service.md) 。</span><span class="sxs-lookup"><span data-stu-id="a778c-127">The host's base address is configured using the [\<add>](../../configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, which is a child of [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md), which is a child of the [\<host>](../../configure-apps/file-schema/wcf/host.md) element, which is a child of the [\<service>](../../configure-apps/file-schema/wcf/service.md) element.</span></span>  
  
 <span data-ttu-id="a778c-128">定義されているエンドポイントは、ベースアドレスとを使用し [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="a778c-128">The endpoint that is defined uses the base address and a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="a778c-129">ベース アドレスの構成と CalculatorService を公開するエンドポイントのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a778c-129">The following sample shows the configuration of the base address as well as the endpoint that exposes the CalculatorService.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 <span data-ttu-id="a778c-130">このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a778c-130">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="a778c-131">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="a778c-131">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a778c-132">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="a778c-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a778c-133">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a778c-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a778c-134">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a778c-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a778c-135">ソリューションがビルドされたら、管理者特権で Visual Studio 2012 コマンドプロンプトから Setup.bat を実行し、Installutil.exe ツールを使用して Windows サービスをインストールします。</span><span class="sxs-lookup"><span data-stu-id="a778c-135">After the solution has been built, run Setup.bat from an elevated Visual Studio 2012 command prompt to install the Windows service using the Installutil.exe tool.</span></span> <span data-ttu-id="a778c-136">このサービスは、[サービス] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a778c-136">The service should appear in Services.</span></span>  
  
4. <span data-ttu-id="a778c-137">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a778c-137">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a778c-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="a778c-138">See also</span></span>

- <span data-ttu-id="a778c-139">[AppFabric のホストおよび永続化のサンプル](/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a778c-139">[AppFabric Hosting and Persistence Samples](/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
