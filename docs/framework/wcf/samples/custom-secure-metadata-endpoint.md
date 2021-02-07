---
description: 詳細については、「カスタムセキュアメタデータエンドポイント」を参照してください。
title: カスタム セキュア メタデータ エンドポイント
ms.date: 03/30/2017
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
ms.openlocfilehash: 11b8439fda74924ff17a101d3aa0b0db948ff8dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752458"
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="fb313-103">カスタム セキュア メタデータ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="fb313-103">Custom Secure Metadata Endpoint</span></span>

<span data-ttu-id="fb313-104">このサンプルでは、メタデータ以外の交換バインドの1つを使用するセキュリティで保護されたメタデータエンドポイントを使用してサービスを実装する方法と、 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) またはクライアントを構成して、そのようなメタデータエンドポイントからメタデータをフェッチする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fb313-104">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="fb313-105">メタデータ エンドポイントを公開する場合に使用できるシステム指定のバインディングには、mexHttpBinding と mexHttpsBinding の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="fb313-105">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="fb313-106">mexHttpBinding は、メタデータ エンドポイントをセキュリティ保護されない HTTP を介して公開する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="fb313-106">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="fb313-107">mexHttpsBinding は、メタデータ エンドポイントをセキュリティ保護される HTTPS を介して公開する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="fb313-107">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="fb313-108">このサンプルでは、<xref:System.ServiceModel.WSHttpBinding> を使用してセキュア メタデータ エンドポイントを公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fb313-108">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="fb313-109">この方法は、HTTPS を使用せずにバインディングのセキュリティ設定を変更する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="fb313-109">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="fb313-110">mexHttpsBinding を使用すると、メタデータ エンドポイントがセキュリティ保護されますが、バインディング設定を変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fb313-110">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb313-111">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb313-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="fb313-112">サービス</span><span class="sxs-lookup"><span data-stu-id="fb313-112">Service</span></span>  

 <span data-ttu-id="fb313-113">このサンプルのサービスには 2 つのエンドポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="fb313-113">The service in this sample has two endpoints.</span></span> <span data-ttu-id="fb313-114">アプリケーション エンドポイントは、`ICalculator` が有効で証明書による `WSHttpBinding` セキュリティを使用する `ReliableSession` に、`Message` コントラクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="fb313-114">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="fb313-115">メタデータ エンドポイントでも、同じセキュリティが設定されている `WSHttpBinding` を使用しますが、`ReliableSession` は無効です。</span><span class="sxs-lookup"><span data-stu-id="fb313-115">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="fb313-116">関連する構成は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fb313-116">Here is the relevant configuration:</span></span>  
  
```xml  
<services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="fb313-117">他の多くのサンプルでは、メタデータ エンドポイントには、セキュリティ保護されていない既定の `mexHttpBinding` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fb313-117">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="fb313-118">このサンプルのメタデータは、`WSHttpBinding` セキュリティが設定されている `Message` を使用してセキュリティ保護されます。</span><span class="sxs-lookup"><span data-stu-id="fb313-118">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="fb313-119">メタデータ クライアントがこのメタデータを取得するには、照合バインディングを使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb313-119">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="fb313-120">このサンプルでは、こうした 2 つのクライアントを示します。</span><span class="sxs-lookup"><span data-stu-id="fb313-120">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="fb313-121">最初のクライアントでは Svcutil.exe を使用し、デザイン時にメタデータを取得してクライアント コードと構成を生成します。</span><span class="sxs-lookup"><span data-stu-id="fb313-121">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="fb313-122">サービスはメタデータの既定以外のバインディングを使用するので、Svcutil.exe ツールはこのバインディングを使用してサービスからメタデータを取得できるよう、特に構成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb313-122">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="fb313-123">2 番目のクライアントでは `MetadataResolver` を使用し、既知のコントラクトのメタデータを動的にフェッチして、動的に生成されたクライアントでの操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fb313-123">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="fb313-124">Svcutil クライアント</span><span class="sxs-lookup"><span data-stu-id="fb313-124">Svcutil client</span></span>  

 <span data-ttu-id="fb313-125">既定のバインディングを使用して `IMetadataExchange` エンドポイントをホストする場合、このエンドポイントのアドレスを使用して次のように Svcutil.exe を実行できます。</span><span class="sxs-lookup"><span data-stu-id="fb313-125">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="fb313-126">これでツールが動作します。</span><span class="sxs-lookup"><span data-stu-id="fb313-126">and it works.</span></span> <span data-ttu-id="fb313-127">ただしこのサンプルのサーバーでは、メタデータをホストするときに既定以外のエンドポイントを使用しています。</span><span class="sxs-lookup"><span data-stu-id="fb313-127">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="fb313-128">そのため、正しいバインディングが使用されるように Svcutil.exe を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb313-128">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="fb313-129">これは、Svcutil.exe.config ファイルを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="fb313-129">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="fb313-130">Svcutil.exe.config ファイルは、通常のクライアント構成ファイルに似ています。</span><span class="sxs-lookup"><span data-stu-id="fb313-130">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="fb313-131">異なる点は、次に示すようにクライアントのエンドポイント名とエンドポイント コントラクトだけです。</span><span class="sxs-lookup"><span data-stu-id="fb313-131">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="fb313-132">エンドポイント名は、メタデータがホストされるアドレスのスキーマの名前である必要があります。また、エンドポイント コントラクトは `IMetadataExchange` であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="fb313-132">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="fb313-133">したがって、Svcutil.exe をコマンド ラインで実行する場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fb313-133">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```console  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="fb313-134">ここでは、"http" という名前のエンドポイントと、このメタデータ エンドポイントとの通信交換のバインディングと動作を構成するコントラクト `IMetadataExchange` が検索されます。</span><span class="sxs-lookup"><span data-stu-id="fb313-134">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="fb313-135">このサンプルでは、Svcutil.exe.config ファイルの残りの部分でバインド構成と動作の資格情報を指定して、サーバーのメタデータ エンドポイントの構成と照合します。</span><span class="sxs-lookup"><span data-stu-id="fb313-135">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="fb313-136">Svcutil.exe が Svcutil.exe.config の構成を使用するには、Svcutil.exe がこの構成ファイルと同じディレクトリにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb313-136">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="fb313-137">したがって、Svcutil.exe をインストール場所から Svcutil.exe.config ファイルが含まれるディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb313-137">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="fb313-138">その後、そのディレクトリで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-138">Then from that directory, run the following command:</span></span>  
  
```console  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="fb313-139">先頭の ". \\ "このディレクトリ (対応する Svcutil.exe.config があるもの) の Svcutil.exe のコピーが実行されることを保証します。</span><span class="sxs-lookup"><span data-stu-id="fb313-139">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="fb313-140">MetadataResolver クライアント</span><span class="sxs-lookup"><span data-stu-id="fb313-140">MetadataResolver client</span></span>  

 <span data-ttu-id="fb313-141">クライアントで、コントラクトおよびメタデータと対話する方法がデザイン時に認識されている場合、クライアントは `MetadataResolver` を使用してアプリケーション エンドポイントのバインディングとアドレスを動的に検索することができます。</span><span class="sxs-lookup"><span data-stu-id="fb313-141">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="fb313-142">その例として、このクライアントのサンプルでは、`MetadataResolver` を作成して構成することにより、`MetadataExchangeClient` で使用されるバインディングと資格情報を構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fb313-142">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="fb313-143">Svcutil.exe.config には、同じバインディングと資格情報についての情報が示されており、`MetadataExchangeClient` でこれを次のように強制的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="fb313-143">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```csharp  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="fb313-144">`mexClient` が構成されている場合、次のように必要なコントラクトを列挙し、`MetadataResolver` を使用してこれらのコントラクトが含まれるエンドポイントの一覧をフェッチできます。</span><span class="sxs-lookup"><span data-stu-id="fb313-144">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```csharp  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts = new Collection<ContractDescription>();  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints = MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="fb313-145">最後に、こうしたエンドポイントからの情報を使用して、アプリケーション エンドポイントと通信するチャネルの作成に使用される、`ChannelFactory` のバインディングとアドレスを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="fb313-145">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```csharp  
ChannelFactory<ICalculator> cf = new ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="fb313-146">このクライアント サンプルで重要な点は、`MetadataResolver` を使用しているときにメタデータ交換通信用のカスタム バインドまたはカスタム動作を指定する必要がある場合に、`MetadataExchangeClient` を使用すればこうしたカスタム設定を指定できるということです。</span><span class="sxs-lookup"><span data-stu-id="fb313-146">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="fb313-147">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="fb313-147">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="fb313-148">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="fb313-148">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fb313-149">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="fb313-149">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="fb313-150">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="fb313-150">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="fb313-151">Setup.bat をサンプルのインストール フォルダーで実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-151">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="fb313-152">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="fb313-152">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="fb313-153">Setup.bat は、 [Windows Communication Foundation のサンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)から setupCertTool.bat を実行することによってインストールされる FindPrivateKey.exe ツールを使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fb313-153">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="fb313-154">\MetadataResolverClient\bin または \SvcutilClient\bin でクライアント アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-154">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="fb313-155">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fb313-155">Client activity is displayed on the client console application.</span></span>  
  
3. <span data-ttu-id="fb313-156">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb313-156">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
4. <span data-ttu-id="fb313-157">サンプルの使用が終わったら、Cleanup.bat を実行して証明書を削除してください。</span><span class="sxs-lookup"><span data-stu-id="fb313-157">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="fb313-158">他のセキュリティ サンプルでも同じ証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="fb313-158">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="fb313-159">サンプルを複数コンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="fb313-159">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="fb313-160">サーバーで `setup.bat service` を実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-160">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="fb313-161">引数を指定してを実行する `setup.bat` `service` と、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、service .cer という名前のファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="fb313-161">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2. <span data-ttu-id="fb313-162">サーバーで、Web.config を編集して新しい証明書の名前を反映します。</span><span class="sxs-lookup"><span data-stu-id="fb313-162">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="fb313-163">つまり、 `findValue` 要素の属性を [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) コンピューターの完全修飾ドメイン名に変更します。</span><span class="sxs-lookup"><span data-stu-id="fb313-163">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3. <span data-ttu-id="fb313-164">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="fb313-164">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4. <span data-ttu-id="fb313-165">クライアントで `setup.bat client` を実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-165">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="fb313-166">引数を指定してを実行する `setup.bat` `client` と、Client.com という名前のクライアント証明書が作成され、クライアント証明書がクライアント .cer という名前のファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="fb313-166">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5. <span data-ttu-id="fb313-167">クライアント コンピューターにある `MetadataResolverClient` の App.config ファイルで、MEX エンドポイントのアドレス値をサービスの新しいアドレスに合わせて変更します。</span><span class="sxs-lookup"><span data-stu-id="fb313-167">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="fb313-168">そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fb313-168">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="fb313-169">さらに、metadataResolverClient.cs ファイルに記述されている "localhost" を、新しいサービス証明書の名前 (サーバーの完全修飾ドメイン名) に変更します。</span><span class="sxs-lookup"><span data-stu-id="fb313-169">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="fb313-170">SvcutilClient プロジェクトの App.config に対して、同様の手順を行います。</span><span class="sxs-lookup"><span data-stu-id="fb313-170">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6. <span data-ttu-id="fb313-171">Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="fb313-171">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7. <span data-ttu-id="fb313-172">クライアントで `ImportServiceCert.bat` を実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-172">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="fb313-173">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="fb313-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8. <span data-ttu-id="fb313-174">サーバーで `ImportClientCert.bat` を実行します。これにより、クライアント証明書が Client.cer ファイルから LocalMachine - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="fb313-174">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="fb313-175">サービス コンピューターで、Visual Studio でサービス プロジェクトをビルドし、それが実行されていることを Web ブラウザーでヘルプ ページを選択することにより検証します。</span><span class="sxs-lookup"><span data-stu-id="fb313-175">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="fb313-176">クライアント コンピューター上の VS で、MetadataResolverClient または SvcutilClient を実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-176">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1. <span data-ttu-id="fb313-177">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb313-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="fb313-178">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="fb313-178">To clean up after the sample</span></span>  
  
- <span data-ttu-id="fb313-179">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-179">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="fb313-180">このサンプルを別のマシンで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="fb313-180">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="fb313-181">コンピューター間で証明書を使用する Windows Communication Foundation (WCF) サンプルを実行した場合は、CurrentUser-TrustedPeople ストアにインストールされているサービス証明書を必ずオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="fb313-181">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="fb313-182">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。</span><span class="sxs-lookup"><span data-stu-id="fb313-182">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="fb313-183">たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` のように指定します。</span><span class="sxs-lookup"><span data-stu-id="fb313-183">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fb313-184">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="fb313-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fb313-185">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fb313-185">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="fb313-186">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="fb313-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fb313-187">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="fb313-187">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`
