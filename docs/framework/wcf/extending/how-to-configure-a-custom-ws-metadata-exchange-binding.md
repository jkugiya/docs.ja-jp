---
description: '詳細については、「方法: カスタム WS-Metadata Exchange バインディングを構成する」を参照してください。'
title: '方法: カスタム WS-Metadata Exchange バインディングを構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: ae9d1932e7539d25c117a98bd130d1def8e691fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743734"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="8d0dd-103">方法: カスタム WS-Metadata Exchange バインディングを構成する</span><span class="sxs-lookup"><span data-stu-id="8d0dd-103">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>

<span data-ttu-id="8d0dd-104">この記事では、カスタム WS-Metadata exchange バインドを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-104">This article explains how to configure a custom WS-Metadata exchange binding.</span></span> <span data-ttu-id="8d0dd-105">Windows Communication Foundation (WCF) には、4つのシステム定義のメタデータバインドが含まれていますが、必要なバインドを使用してメタデータを公開できます。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-105">Windows Communication Foundation (WCF) includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="8d0dd-106">この記事では、を使用してメタデータを公開する方法について説明し `wsHttpBinding` ます。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-106">This article shows you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="8d0dd-107">このバインディングでは、メタデータをセキュリティで保護して公開することができます。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-107">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="8d0dd-108">この記事のコードは、 [はじめに](../samples/getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-108">The code in this article is based on the [Getting Started](../samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="8d0dd-109">構成ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="8d0dd-109">Using a configuration file</span></span>  
  
1. <span data-ttu-id="8d0dd-110">サービスの構成ファイルで、`serviceMetadata` タグを含んだサービス動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-110">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. <span data-ttu-id="8d0dd-111">この新しい動作を参照する `behaviorConfiguration` 属性をサービス タグに追加します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-111">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior" />
    ```  
  
3. <span data-ttu-id="8d0dd-112">メタデータ エンドポイントを追加し、アドレスに mex、バインディングに `wsHttpBinding`、コントラクトに <xref:System.ServiceModel.Description.IMetadataExchange> をそれぞれ指定します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-112">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. <span data-ttu-id="8d0dd-113">メタデータ交換エンドポイントが正常に機能していることを確認するには、クライアント構成ファイルにエンドポイントタグを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-113">To verify the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. <span data-ttu-id="8d0dd-114">クライアントの Main() メソッドで、新しい <xref:System.ServiceModel.Description.MetadataExchangeClient> インスタンスを作成し、その <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> プロパティを `true` に設定し、<xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> を呼び出して返されるメタデータのコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-114">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="8d0dd-115">コードによる構成</span><span class="sxs-lookup"><span data-stu-id="8d0dd-115">Configuring by code</span></span>  
  
1. <span data-ttu-id="8d0dd-116"><xref:System.ServiceModel.WSHttpBinding> バインディングのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-116">Create a <xref:System.ServiceModel.WSHttpBinding> binding instance:</span></span>  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. <span data-ttu-id="8d0dd-117"><xref:System.ServiceModel.ServiceHost> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-117">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. <span data-ttu-id="8d0dd-118">サービス エンドポイントと <xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-118">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. <span data-ttu-id="8d0dd-119">前に作成した <xref:System.ServiceModel.WSHttpBinding> を指定する Metadata Exchange エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-119">Add a metadata exchange endpoint, specifying the <xref:System.ServiceModel.WSHttpBinding> created earlier:</span></span>  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. <span data-ttu-id="8d0dd-120">Metadata Exchange エンドポイントが適切に動作することを確認するには、クライアントの構成ファイルにエンドポイント タグを追加します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-120">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. <span data-ttu-id="8d0dd-121">クライアントの Main() メソッドで、新しい <xref:System.ServiceModel.Description.MetadataExchangeClient> インスタンスを作成し、その <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> プロパティを `true` に設定し、<xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> を呼び出して返されるメタデータのコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="8d0dd-121">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8d0dd-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d0dd-122">See also</span></span>

- [<span data-ttu-id="8d0dd-123">メタデータ公開動作</span><span class="sxs-lookup"><span data-stu-id="8d0dd-123">Metadata Publishing Behavior</span></span>](../samples/metadata-publishing-behavior.md)
- [<span data-ttu-id="8d0dd-124">メタデータの抽出</span><span class="sxs-lookup"><span data-stu-id="8d0dd-124">Retrieve Metadata</span></span>](../samples/retrieve-metadata.md)
- [<span data-ttu-id="8d0dd-125">Metadata</span><span class="sxs-lookup"><span data-stu-id="8d0dd-125">Metadata</span></span>](../feature-details/metadata.md)
- [<span data-ttu-id="8d0dd-126">メタデータの公開</span><span class="sxs-lookup"><span data-stu-id="8d0dd-126">Publishing Metadata</span></span>](../feature-details/publishing-metadata.md)
- [<span data-ttu-id="8d0dd-127">メタデータ エンドポイントを公開する</span><span class="sxs-lookup"><span data-stu-id="8d0dd-127">Publishing Metadata Endpoints</span></span>](../publishing-metadata-endpoints.md)
