---
description: '詳細情報: メタデータの公開動作'
title: メタデータ公開動作
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 13e52e5f2a8d301eac3100cbf2350cc5a089aa34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752228"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="5594d-103">メタデータ公開動作</span><span class="sxs-lookup"><span data-stu-id="5594d-103">Metadata Publishing Behavior</span></span>

<span data-ttu-id="5594d-104">メタデータ公開動作のサンプルでは、サービスのメタデータ公開機能を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5594d-104">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="5594d-105">機密性の高いサービスメタデータが誤って公開されるのを防ぐために、Windows Communication Foundation (WCF) サービスの既定の構成では、メタデータの公開が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="5594d-105">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="5594d-106">この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ発行の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。</span><span class="sxs-lookup"><span data-stu-id="5594d-106">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5594d-107">このサンプルでは、わかりやすくするために、セキュリティで保護されていないメタデータ公開エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5594d-107">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="5594d-108">このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5594d-108">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="5594d-109">メタデータエンドポイントをセキュリティで保護するサンプルについては、「 [カスタムセキュアメタデータエンドポイント](custom-secure-metadata-endpoint.md) のサンプル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5594d-109">See the [Custom Secure Metadata Endpoint](custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="5594d-110">このサンプルは、サービスコントラクトを実装する [はじめに](getting-started-sample.md)に基づいてい `ICalculator` ます。</span><span class="sxs-lookup"><span data-stu-id="5594d-110">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="5594d-111">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="5594d-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5594d-112">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5594d-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5594d-113">サービスでメタデータを公開するには、サービス上に <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5594d-113">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="5594d-114">この動作が存在する場合は、エンドポイントを構成してメタデータを公開し、<xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを WS-MetadataExchange (MEX) プロトコルの実装として公開できます。</span><span class="sxs-lookup"><span data-stu-id="5594d-114">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="5594d-115">便宜上、このコントラクトには、構成名を略した "IMetadataExchange" という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="5594d-115">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="5594d-116">このサンプルでは、`mexHttpBinding` を使用します。これは使いやすい標準バインディングで、セキュリティ モードが `wsHttpBinding` に設定されている `None` と同等です。</span><span class="sxs-lookup"><span data-stu-id="5594d-116">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="5594d-117">エンドポイントでは、相対アドレス "mex" が使用されます。これは、サービスのベースアドレスに対して解決されると、のエンドポイントアドレスになり `http://localhost/servicemodelsamples/service.svc/mex` ます。</span><span class="sxs-lookup"><span data-stu-id="5594d-117">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="5594d-118">この動作の構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5594d-118">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="5594d-119">MEX エンドポイントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5594d-119">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="5594d-120">このサンプルでは、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定します。これにより、HTTP GET を使用してサービスのメタデータも公開されます。</span><span class="sxs-lookup"><span data-stu-id="5594d-120">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="5594d-121">HTTP GET メタデータのエンドポイントを有効にするには、サービスに HTTP ベース アドレスが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5594d-121">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="5594d-122">クエリ文字列 `?wsdl` は、メタデータにアクセスするサービスのベース アドレスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="5594d-122">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="5594d-123">たとえば、Web ブラウザーでサービスの WSDL を表示するには、アドレスを使用し `http://localhost/servicemodelsamples/service.svc?wsdl` ます。</span><span class="sxs-lookup"><span data-stu-id="5594d-123">For example, to see the WSDL for the service in a Web browser you would use the address `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span> <span data-ttu-id="5594d-124">または、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> を `true` に設定してこの動作を使用することにより、HTTPS を通じてメタデータを公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="5594d-124">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="5594d-125">これには、HTTPS ベース アドレスが必要です。</span><span class="sxs-lookup"><span data-stu-id="5594d-125">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="5594d-126">サービスの MEX エンドポイントにアクセスするには、 [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="5594d-126">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="5594d-127">これにより、サービスのメタデータに基づくクライアントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5594d-127">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="5594d-128">HTTP GET を使用してサービスのメタデータにアクセスするには、ブラウザーでを参照して `http://localhost/servicemodelsamples/service.svc?wsdl` ください。</span><span class="sxs-lookup"><span data-stu-id="5594d-128">To access the service's metadata using HTTP GET, point your browser to `http://localhost/servicemodelsamples/service.svc?wsdl`.</span></span>  
  
 <span data-ttu-id="5594d-129">この動作を削除してサービスを開こうとすると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="5594d-129">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="5594d-130">動作がない場合にこのエラーが発生するのは、`IMetadataExchange` コントラクトを使用して構成されたエンドポイントに実装が存在しないからです。</span><span class="sxs-lookup"><span data-stu-id="5594d-130">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="5594d-131">`HttpGetEnabled` を `false` に設定すると、サービスのメタデータが表示される代わりに CalculatorService ヘルプ ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5594d-131">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5594d-132">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="5594d-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5594d-133">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="5594d-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5594d-134">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5594d-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5594d-135">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5594d-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5594d-136">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5594d-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5594d-137">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5594d-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5594d-138">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="5594d-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5594d-139">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5594d-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
