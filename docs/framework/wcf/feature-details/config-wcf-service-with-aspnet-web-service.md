---
description: '詳細については、「方法: ASP.NET Web サービスクライアントと相互運用するように WCF サービスを構成する」を参照してください。'
title: '方法: WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 180307763054f8dfe5696fb0bbf294ec2b5ee3db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743396"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a><span data-ttu-id="6595c-103">方法: WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する</span><span class="sxs-lookup"><span data-stu-id="6595c-103">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>

<span data-ttu-id="6595c-104">ASP.NET Web サービスクライアントと相互運用できるように Windows Communication Foundation (WCF) サービスエンドポイントを構成するには、 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> サービスエンドポイントのバインドの種類として型を使用します。</span><span class="sxs-lookup"><span data-stu-id="6595c-104">To configure a Windows Communication Foundation (WCF) service endpoint to be interoperable with ASP.NET Web service clients, use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
 <span data-ttu-id="6595c-105">必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。</span><span class="sxs-lookup"><span data-stu-id="6595c-105">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span> <span data-ttu-id="6595c-106">ASP.NET Web サービスクライアントは MTOM メッセージエンコーディングをサポートしていないため、 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> プロパティは既定値 () のままにしておく必要があり <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="6595c-106">ASP.NET Web service clients do not support MTOM message encoding, so the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property should be left as its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6595c-107">ASP.NET Web サービスクライアントでは WS-SECURITY がサポートされていないため、 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> をに設定する必要があり <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> ます。</span><span class="sxs-lookup"><span data-stu-id="6595c-107">ASP.NET Web Service clients do not support WS-Security, so the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> should be set to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span>  
  
 <span data-ttu-id="6595c-108">WCF サービスのメタデータを ASP.NET Web サービスプロキシ生成ツール (つまり、 [web サービス記述言語ツール (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))、 [Web サービス検出ツール (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))、および Visual Studio の [ **web 参照の追加** ] 機能) で使用できるようにするには、HTTP/GET メタデータエンドポイントを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6595c-108">To make the metadata for a WCF service available to ASP.NET Web service proxy generation tools (that is, [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), and the **Add Web Reference** feature in Visual Studio), you should expose an HTTP/GET metadata endpoint.</span></span>  
  
## <a name="add-an-endpoint-in-code"></a><span data-ttu-id="6595c-109">コードにエンドポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="6595c-109">Add an endpoint in code</span></span>  
  
1. <span data-ttu-id="6595c-110">新しい <xref:System.ServiceModel.BasicHttpBinding> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6595c-110">Create a new <xref:System.ServiceModel.BasicHttpBinding> instance</span></span>  
  
2. <span data-ttu-id="6595c-111">必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインディングのトランスポート セキュリティを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6595c-111">Optionally enable transport security for this service endpoint binding by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="6595c-112">詳細については、「 [トランスポートセキュリティ](transport-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595c-112">For details, see [Transport Security](transport-security.md).</span></span>  
  
3. <span data-ttu-id="6595c-113">上で作成したバインディング インスタンスを使用して、サービス ホストに新しいアプリケーション エンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="6595c-113">Add a new application endpoint to your service host using the binding instance that you just created.</span></span> <span data-ttu-id="6595c-114">コードでサービスエンドポイントを追加する方法の詳細については、「 [方法: コードでサービスエンドポイントを作成](how-to-create-a-service-endpoint-in-code.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595c-114">For details about how to add a service endpoint in code, see the [How to: Create a Service Endpoint in Code](how-to-create-a-service-endpoint-in-code.md).</span></span>  
  
4. <span data-ttu-id="6595c-115">サービス用に HTTP/GET メタデータのエンドポイントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6595c-115">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="6595c-116">詳細については [、「方法: コードを使用してサービスのメタデータを公開](how-to-publish-metadata-for-a-service-using-code.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595c-116">For details see [How to: Publish Metadata for a Service Using Code](how-to-publish-metadata-for-a-service-using-code.md).</span></span>  
  
## <a name="add-an-endpoint-in-a-configuration-file"></a><span data-ttu-id="6595c-117">構成ファイルにエンドポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="6595c-117">Add an endpoint in a configuration file</span></span>  
  
1. <span data-ttu-id="6595c-118">新しい <xref:System.ServiceModel.BasicHttpBinding> バインディング構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="6595c-118">Create a new <xref:System.ServiceModel.BasicHttpBinding> binding configuration.</span></span> <span data-ttu-id="6595c-119">詳細については、「 [方法: 構成でサービスバインディングを指定](../how-to-specify-a-service-binding-in-configuration.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595c-119">For details, see the [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
2. <span data-ttu-id="6595c-120">必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインド構成のトランスポート セキュリティを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6595c-120">Optionally enable transport security for this service endpoint binding configuration by setting the security mode for the binding to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span> <span data-ttu-id="6595c-121">詳細については、「 [トランスポートセキュリティ](transport-security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595c-121">For details, see [Transport Security](transport-security.md).</span></span>  
  
3. <span data-ttu-id="6595c-122">上で作成したバインド構成を使用して、サービスに新しいアプリケーション エンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="6595c-122">Configure a new application endpoint for your service using the binding configuration that you just created.</span></span> <span data-ttu-id="6595c-123">構成ファイルにサービスエンドポイントを追加する方法の詳細については、「 [方法: 構成でサービスエンドポイントを作成](how-to-create-a-service-endpoint-in-configuration.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595c-123">For details about how to add a service endpoint in a configuration file, see the [How to: Create a Service Endpoint in Configuration](how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
4. <span data-ttu-id="6595c-124">サービス用に HTTP/GET メタデータのエンドポイントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="6595c-124">Enable an HTTP/GET metadata endpoint for your service.</span></span> <span data-ttu-id="6595c-125">詳細については、「 [方法: 構成ファイルを使用してサービスのメタデータを公開](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595c-125">For details see the [How to: Publish Metadata for a Service Using a Configuration File](how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6595c-126">例</span><span class="sxs-lookup"><span data-stu-id="6595c-126">Example</span></span>  

 <span data-ttu-id="6595c-127">次のコード例は、ASP.NET Web サービスクライアントと互換性のある WCF エンドポイントをコードで、または構成ファイルで追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6595c-127">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and alternatively in configuration files.</span></span>  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]
  
## <a name="see-also"></a><span data-ttu-id="6595c-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="6595c-128">See also</span></span>

- [<span data-ttu-id="6595c-129">方法: コード内にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="6595c-129">How to: Create a Service Endpoint in Code</span></span>](how-to-create-a-service-endpoint-in-code.md)
- [<span data-ttu-id="6595c-130">方法: コードを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="6595c-130">How to: Publish Metadata for a Service Using Code</span></span>](how-to-publish-metadata-for-a-service-using-code.md)
- [<span data-ttu-id="6595c-131">方法: 構成でサービス バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="6595c-131">How to: Specify a Service Binding in Configuration</span></span>](../how-to-specify-a-service-binding-in-configuration.md)
- [<span data-ttu-id="6595c-132">方法: 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="6595c-132">How to: Create a Service Endpoint in Configuration</span></span>](how-to-create-a-service-endpoint-in-configuration.md)
- [<span data-ttu-id="6595c-133">方法: 構成ファイルを使用してサービスのメタデータを公開する</span><span class="sxs-lookup"><span data-stu-id="6595c-133">How to: Publish Metadata for a Service Using a Configuration File</span></span>](how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="6595c-134">トランスポートセキュリティ</span><span class="sxs-lookup"><span data-stu-id="6595c-134">Transport Security</span></span>](transport-security.md)
- [<span data-ttu-id="6595c-135">メタデータを使用する</span><span class="sxs-lookup"><span data-stu-id="6595c-135">Using Metadata</span></span>](using-metadata.md)
