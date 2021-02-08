---
description: '詳細については、「方法: コードを使用してサービスのメタデータを公開する」を参照してください。'
title: '方法: コードを使用してサービスのメタデータを公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 51407e6d-4d87-42d5-be7c-9887b8652006
ms.openlocfilehash: 94939c77b1c66643b0cc378516479e35c41aefbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793689"
---
# <a name="how-to-publish-metadata-for-a-service-using-code"></a><span data-ttu-id="9a2d8-103">方法: コードを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="9a2d8-103">How to: Publish Metadata for a Service Using Code</span></span>

<span data-ttu-id="9a2d8-104">これは、Windows Communication Foundation (WCF) サービスのメタデータの公開について説明する2つの操作方法に関するトピックの1つです。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-104">This is one of two how-to topics that discuss publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="9a2d8-105">構成ファイルとコードを使用して、サービスがメタデータを公開する手段を指定する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-105">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="9a2d8-106">このトピックでは、コードを使用してサービスのメタデータを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-106">This topic shows how to publish metadata for a service using a code.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="9a2d8-107">このトピックでは、セキュリティで保護されていない方法でメタデータを公開する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-107">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="9a2d8-108">クライアントは、サービスからメタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-108">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="9a2d8-109">セキュリティで保護された方法でメタデータを公開するサービスが必要な場合は、</span><span class="sxs-lookup"><span data-stu-id="9a2d8-109">If you require your service to publish metadata in a secure manner.</span></span> <span data-ttu-id="9a2d8-110">「 [カスタムセキュアメタデータエンドポイント](../samples/custom-secure-metadata-endpoint.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-110">see [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="9a2d8-111">構成ファイルでメタデータを公開する方法の詳細については、「 [方法: 構成ファイルを使用してサービスのメタデータを公開](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-111">For more information about publishing metadata in a configuration file, see [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span> <span data-ttu-id="9a2d8-112">メタデータを公開すると、クライアントが `?wsdl` クエリ文字列を使用した WS-Transfer GET 要求または HTTP/GET 要求によりメタデータを取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-112">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="9a2d8-113">コードを機能させるには、基本的な WCF サービスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-113">To be sure that the code is working you must create a basic WCF service.</span></span> <span data-ttu-id="9a2d8-114">次のコードは基本的な自己ホスト型サービスの例です。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-114">A basic self-hosted service is provided in the following code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#0)]
 [!code-vb[htPublishMetadataCode#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#0)]  
  
### <a name="to-publish-metadata-in-code"></a><span data-ttu-id="9a2d8-115">コードでメタデータを公開するには</span><span class="sxs-lookup"><span data-stu-id="9a2d8-115">To publish metadata in code</span></span>  
  
1. <span data-ttu-id="9a2d8-116">コンソール アプリケーションのメイン メソッド内で、サービス型とベース アドレスを渡して <xref:System.ServiceModel.ServiceHost> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-116">Within the main method of a console application, instantiate a <xref:System.ServiceModel.ServiceHost> object by passing in the service type and the base address.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#1)]
     [!code-vb[htPublishMetadataCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#1)]  
  
2. <span data-ttu-id="9a2d8-117">手順 1. のコードのすぐ下に try ブロックを作成します。これにより、サービスの実行中にスローされる例外がすべてキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-117">Create a try block immediately below the code for step 1, this catches any exceptions that get thrown while the service is running.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#2)]
     [!code-vb[htPublishMetadataCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#2)]  
  
     [!code-csharp[htPublishMetadataCode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#3)]
     [!code-vb[htPublishMetadataCode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#3)]  
  
3. <span data-ttu-id="9a2d8-118">サービス ホストに <xref:System.ServiceModel.Description.ServiceMetadataBehavior> が含まれているかどうかを確認し、含まれていない場合は、新しい <xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-118">Check to see whether the service host already contains a <xref:System.ServiceModel.Description.ServiceMetadataBehavior>, if not, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#4)]
     [!code-vb[htPublishMetadataCode#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#4)]  
  
4. <span data-ttu-id="9a2d8-119"><xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true.` に設定します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-119">Set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true.`</span></span>  
  
     [!code-csharp[htPublishMetadataCode#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#5)]
     [!code-vb[htPublishMetadataCode#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#5)]  
  
5. <span data-ttu-id="9a2d8-120"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> には <xref:System.ServiceModel.Description.MetadataExporter> プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-120">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> contains a <xref:System.ServiceModel.Description.MetadataExporter> property.</span></span> <span data-ttu-id="9a2d8-121"><xref:System.ServiceModel.Description.MetadataExporter> には <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-121">The <xref:System.ServiceModel.Description.MetadataExporter> contains a <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property.</span></span> <span data-ttu-id="9a2d8-122"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティの値を <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> に設定します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-122">Set the value of the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A>.</span></span> <span data-ttu-id="9a2d8-123"><xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> プロパティを <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-123">The <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property can also be set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A>.</span></span> <span data-ttu-id="9a2d8-124">に設定すると <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> 、メタデータエクスポーターは、"WS-Policy 1.5 に準拠するメタデータを使用してポリシー情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-124">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy15%2A> the metadata exporter generates policy information with the metadata that" conforms to WS-Policy 1.5.</span></span> <span data-ttu-id="9a2d8-125"><xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> に設定すると、WS-Policy 1.2 に準拠したポリシー情報がメタデータ エクスポーターによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-125">When set to <xref:System.ServiceModel.Description.PolicyVersion.Policy12%2A> the metadata exporter generates policy information that conforms to WS-Policy 1.2.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#6)]
     [!code-vb[htPublishMetadataCode#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#6)]  
  
6. <span data-ttu-id="9a2d8-126"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> インスタンスをサービス ホストの動作コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-126">Add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance to the service host's behaviors collection.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#7)]
     [!code-vb[htPublishMetadataCode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#7)]  
  
7. <span data-ttu-id="9a2d8-127">メタデータ交換エンドポイントをサービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-127">Add the metadata exchange endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#8)]
     [!code-vb[htPublishMetadataCode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#8)]  
  
8. <span data-ttu-id="9a2d8-128">アプリケーション エンドポイントをサービス ホストに追加します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-128">Add an application endpoint to the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#9)]
     [!code-vb[htPublishMetadataCode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#9)]  
  
    > [!NOTE]
    > <span data-ttu-id="9a2d8-129">エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-129">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="9a2d8-130">この例では、サービスには <xref:System.ServiceModel.Description.ServiceMetadataBehavior> に設定された `true` があるので、サービスで公開メタデータも有効化されています。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-130">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, the service has publishing metadata enabled.</span></span> <span data-ttu-id="9a2d8-131">既定のエンドポイントの詳細については、「 [WCF サービスの](../samples/simplified-configuration-for-wcf-services.md)構成と簡略化された構成の[簡略化](../simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-131">For more information about default endpoints, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="9a2d8-132">サービス ホストを開き、受信呼び出しを待ちます。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-132">Open the service host and wait for incoming calls.</span></span> <span data-ttu-id="9a2d8-133">ユーザーが Enter キーを押すと、サービス ホストが終了します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-133">When the user presses ENTER, close the service host.</span></span>  
  
     [!code-csharp[htPublishMetadataCode#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#10)]
     [!code-vb[htPublishMetadataCode#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#10)]  
  
10. <span data-ttu-id="9a2d8-134">コンソール アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-134">Build and run the console application.</span></span>  
  
11. <span data-ttu-id="9a2d8-135">Internet Explorer を使用してサービスのベースアドレス ( `http://localhost:8001/MetadataSample` このサンプルでは) を参照し、メタデータの公開が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-135">Use Internet Explorer to browse to the base address of the service (`http://localhost:8001/MetadataSample` in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="9a2d8-136">上部の "サービスを作成しました" のすぐ下に "Simple Service" と表示された Web ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-136">You should see a Web page displayed that says "Simple Service" at the top and immediately below "You have created a service."</span></span> <span data-ttu-id="9a2d8-137">有効になっていない場合は、"このサービスのメタデータ公開は現在は無効になっています。" というメッセージが結果ページの上部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-137">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a2d8-138">例</span><span class="sxs-lookup"><span data-stu-id="9a2d8-138">Example</span></span>  

 <span data-ttu-id="9a2d8-139">次のコード例は、コードでサービスのメタデータを公開する基本的な WCF サービスの実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="9a2d8-139">The following code example shows the implementation of a basic WCF service that publishes metadata for the service in code.</span></span>  
  
 [!code-csharp[htPublishMetadataCode#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htpublishmetadatacode/cs/program.cs#11)]
 [!code-vb[htPublishMetadataCode#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htpublishmetadatacode/vb/program.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="9a2d8-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a2d8-140">See also</span></span>

- [<span data-ttu-id="9a2d8-141">方法: マネージド アプリケーションで WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="9a2d8-141">How to: Host a WCF Service in a Managed Application</span></span>](../how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="9a2d8-142">自己ホスト</span><span class="sxs-lookup"><span data-stu-id="9a2d8-142">Self-Host</span></span>](../samples/self-host.md)
- [<span data-ttu-id="9a2d8-143">メタデータ アーキテクチャの概要</span><span class="sxs-lookup"><span data-stu-id="9a2d8-143">Metadata Architecture Overview</span></span>](metadata-architecture-overview.md)
- [<span data-ttu-id="9a2d8-144">メタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="9a2d8-144">Using Metadata</span></span>](using-metadata.md)
- [<span data-ttu-id="9a2d8-145">方法: 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="9a2d8-145">How to: Publish Metadata for a Service Using a Configuration File</span></span>](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
