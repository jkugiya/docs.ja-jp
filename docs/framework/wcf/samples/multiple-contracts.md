---
description: '詳細情報: 複数のコントラクト'
title: 複数のコントラクト
ms.date: 03/30/2017
ms.assetid: 2bef319b-fe9c-4d49-ac6c-dfb23eb35099
ms.openlocfilehash: b83a2d333cda05525fbe286f2eb6c385d7942092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752231"
---
# <a name="multiple-contracts"></a><span data-ttu-id="d3344-103">複数のコントラクト</span><span class="sxs-lookup"><span data-stu-id="d3344-103">Multiple Contracts</span></span>

<span data-ttu-id="d3344-104">この複数のコントラクトのサンプルでは、複数のコントラクトを 1 つのサービスに実装する方法と、実装された各コントラクトと通信を行うためにエンドポイントを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d3344-104">The Multiple Contracts sample demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span> <span data-ttu-id="d3344-105">このサンプルは、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d3344-105">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="d3344-106">サービスは、`ICalculator` コントラクトおよび `ICalculatorSession` コントラクトという、2 つのコントラクトを定義するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="d3344-106">The service has been modified to define two contracts, the `ICalculator` contract and the `ICalculatorSession` contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d3344-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3344-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d3344-108">サービス クラスは、`ICalculator` と `ICalculatorSession` コントラクトの両方を実装しています。</span><span class="sxs-lookup"><span data-stu-id="d3344-108">The service class implements both the `ICalculator` and `ICalculatorSession` contracts.</span></span> <span data-ttu-id="d3344-109">いずれかのコントラクトでセッションが必要なので、サービスは <xref:System.ServiceModel.InstanceContextMode.PerSession> インスタンス モードを使用して、セッションの有効期間中、状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="d3344-109">Because one of the contracts requires a session, the service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the state over the lifetime of the session.</span></span>  
  
 <span data-ttu-id="d3344-110">サービス構成は、各コントラクトを公開する 2 つのエンドポイントを定義するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="d3344-110">The service configuration has been modified to define two endpoints to expose each contract.</span></span> <span data-ttu-id="d3344-111">`ICalculator` エンドポイントは、`basicHttpBinding` を使用してベース アドレスで公開されます。</span><span class="sxs-lookup"><span data-stu-id="d3344-111">The `ICalculator` endpoint is exposed at the base address using a `basicHttpBinding`.</span></span> <span data-ttu-id="d3344-112">`ICalculatorSession` エンドポイントは、`wsHttpBinding` 属性が `bindingConfiguration` に設定された `BindingWithSession` を使用して、ベース アドレスまたはセッションで公開されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3344-112">The `ICalculatorSession` endpoint is exposed at the baseaddress/session using a `wsHttpBinding` with the `bindingConfiguration` attribute set to `BindingWithSession`, as shown in the following sample configuration.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- ICalculator endpoint is exposed using BasicBinding at the base  
       address provided by host:   
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- ICalculatorSession endpoint is exposed using BindingWithSession  
       at {baseaddress}/session:  
       http://localhost/servicemodelsamples/service.svc/session -->  
  <endpoint address="session"  
            binding="wsHttpBinding"  
            bindingConfiguration="BindingWithSession"
           contract="Microsoft.ServiceModel.Samples.ICalculatorSession" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="d3344-113">生成されたクライアント コードには、元の `ICalculator` コントラクトと新しい `ICalculatorSession` コントラクトの両方のクライアント クラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3344-113">The generated client code now includes a client class for both the original `ICalculator` contract and the new `ICalculatorSession` contract.</span></span> <span data-ttu-id="d3344-114">クライアント構成とコードは、適切なサービス エンドポイントで各コントラクトと通信するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="d3344-114">The client configuration and code have been modified to communicate with each contract at the appropriate service endpoint.</span></span>  
  
 <span data-ttu-id="d3344-115">クライアントは Windows コンソール アプリケーション (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="d3344-115">The client is a console windows application (.exe).</span></span> <span data-ttu-id="d3344-116">サービスは、インターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="d3344-116">The service is hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="d3344-117">クライアント コンソール ウィンドウには、最初に基本のエンドポイント、次にセキュリティで保護されたエンドポイントの順に、各エンドポイントに送信された操作が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d3344-117">The client console window displays the operations sent to each of the endpoints, first the basic endpoint, followed by the secure endpoint.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d3344-118">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="d3344-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d3344-119">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d3344-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d3344-120">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d3344-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d3344-121">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d3344-121">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d3344-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d3344-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d3344-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d3344-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d3344-124">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="d3344-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d3344-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d3344-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleContracts`  
