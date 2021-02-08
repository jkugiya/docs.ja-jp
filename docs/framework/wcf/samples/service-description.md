---
description: '詳細情報: サービスの説明'
title: サービスの説明
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: 0985933bb48708faac716575f6a95588df1620d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793091"
---
# <a name="service-description"></a><span data-ttu-id="67d70-103">サービスの説明</span><span class="sxs-lookup"><span data-stu-id="67d70-103">Service Description</span></span>

<span data-ttu-id="67d70-104">サービスの説明のサンプルでは、サービスが実行時にそのサービスの説明情報を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="67d70-104">The Service Description sample demonstrates how a service can retrieve its service description information at runtime.</span></span> <span data-ttu-id="67d70-105">このサンプルは、サービスに関する説明的な情報を返すために定義された追加のサービス操作を使用して、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="67d70-105">The sample is based on the [Getting Started](getting-started-sample.md), with an additional service operation defined to return descriptive information about the service.</span></span> <span data-ttu-id="67d70-106">返される情報には、サービスのベース アドレスとエンドポイントが示されます。</span><span class="sxs-lookup"><span data-stu-id="67d70-106">The information that is returned lists the base addresses and endpoints for the service.</span></span> <span data-ttu-id="67d70-107">サービスは、<xref:System.ServiceModel.OperationContext>、<xref:System.ServiceModel.ServiceHost>、および <xref:System.ServiceModel.Description.ServiceDescription> クラスを使用してこの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="67d70-107">The service provides this information using the <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, and <xref:System.ServiceModel.Description.ServiceDescription> classes.</span></span>  
  
 <span data-ttu-id="67d70-108">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="67d70-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67d70-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67d70-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="67d70-110">このサンプルには、`IServiceDescriptionCalculator` という電卓コントラクトの修正バージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="67d70-110">This sample has a modified version of the calculator contract called `IServiceDescriptionCalculator`.</span></span> <span data-ttu-id="67d70-111">このコントラクトでは、`GetServiceDescriptionInfo` という名前の追加サービス操作が定義されています。このサービス操作は、サービスのベース アドレス (1 つまたは複数) とサービス エンドポイント (1 つまたは複数) を説明する、複数行の文字列をクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="67d70-111">The contract defines an additional service operation named `GetServiceDescriptionInfo` that returns a multi-line string to the client that describes the base address or addresses and service endpoint or endpoints for the service.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 <span data-ttu-id="67d70-112">`GetServiceDescriptionInfo` の実装コードには、サービス エンドポイントを示す <xref:System.ServiceModel.Description.ServiceDescription> が使用されています。</span><span class="sxs-lookup"><span data-stu-id="67d70-112">The implementation code for `GetServiceDescriptionInfo` uses the <xref:System.ServiceModel.Description.ServiceDescription> to list the service endpoints.</span></span> <span data-ttu-id="67d70-113">サービス エンドポイントには相対アドレスを指定できるので、最初にサービスのベース アドレスが示されます。</span><span class="sxs-lookup"><span data-stu-id="67d70-113">Because service endpoints can have relative addresses, it first lists the base addresses for the service.</span></span> <span data-ttu-id="67d70-114">この情報をすべて取得するには、コードで <xref:System.ServiceModel.OperationContext.Current%2A> を使用して操作コンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="67d70-114">To get all of this information, the code obtains its operation context using <xref:System.ServiceModel.OperationContext.Current%2A>.</span></span> <span data-ttu-id="67d70-115">その操作コンテキストから、<xref:System.ServiceModel.ServiceHost> とその <xref:System.ServiceModel.Description.ServiceDescription> オブジェクトが取得されます。</span><span class="sxs-lookup"><span data-stu-id="67d70-115">The <xref:System.ServiceModel.ServiceHost> and its <xref:System.ServiceModel.Description.ServiceDescription> object are retrieved from the operation context.</span></span> <span data-ttu-id="67d70-116">サービスのベース エンドポイント一覧を示すには、コードにより、サービス ホストの <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> コレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="67d70-116">To list the base endpoints for the service, the code iterates through the service host's <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> collection.</span></span> <span data-ttu-id="67d70-117">サービスのサービス エンドポイント一覧を示すには、コードにより、サービス説明のエンドポイント コレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="67d70-117">To list the service endpoints for the service, the code iterates through the service description's endpoints collection.</span></span>  
  
```csharp
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 <span data-ttu-id="67d70-118">サンプルを実行すると、電卓操作が表示され、次に `GetServiceDescriptionInfo` 操作によって返されたサービス情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67d70-118">When you run the sample, you see the calculator operations and then the service information returned by the `GetServiceDescriptionInfo` operation.</span></span> <span data-ttu-id="67d70-119">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="67d70-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="67d70-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="67d70-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="67d70-121">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="67d70-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="67d70-122">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="67d70-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="67d70-123">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="67d70-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="67d70-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="67d70-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="67d70-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="67d70-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="67d70-126">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="67d70-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="67d70-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="67d70-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
