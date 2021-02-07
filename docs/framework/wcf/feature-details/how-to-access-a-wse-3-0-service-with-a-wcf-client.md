---
description: '詳細については、「方法: WCF クライアントを使用して WSE 3.0 サービスにアクセスする」を参照してください。'
title: '方法 : WCF クライアントで WSE 3.0 サービスにアクセスする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 5a117b4c3d743d783c37ed3e27e3cf11e44abec3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742928"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a><span data-ttu-id="dbb4b-103">方法 : WCF クライアントで WSE 3.0 サービスにアクセスする</span><span class="sxs-lookup"><span data-stu-id="dbb4b-103">How to: Access a WSE 3.0 Service with a WCF Client</span></span>

<span data-ttu-id="dbb4b-104">Windows Communication Foundation (WCF) クライアントは、WS-Addressing 仕様の8月2004バージョンを使用するように WCF クライアントが構成されている場合、Microsoft .NET サービスの Web サービス拡張 (WSE) 3.0 とのワイヤレベルの互換性があります。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-104">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements (WSE) 3.0 for Microsoft .NET services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span> <span data-ttu-id="dbb4b-105">ただし、WSE 3.0 サービスでは、metadata exchange (MEX) プロトコルがサポートされていないため、 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して wcf クライアントクラスを作成すると、生成された wcf クライアントにセキュリティ設定が適用されません。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-105">However, WSE 3.0 services do not support the metadata exchange (MEX) protocol, so when you use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client class, the security settings are not applied to the generated WCF client.</span></span> <span data-ttu-id="dbb4b-106">そのため、WCF クライアントが生成された後に、WSE 3.0 サービスが必要とするセキュリティ設定を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-106">Therefore, you must specify the security settings that the WSE 3.0 service requires after the WCF client is generated.</span></span>  
  
 <span data-ttu-id="dbb4b-107">これらのセキュリティ設定を適用するには、カスタムバインディングを使用して WSE 3.0 サービスの要件と、WSE 3.0 サービスと WCF クライアントの間の相互運用可能な要件を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-107">You can apply these security settings by using a custom binding to take into account the WSE 3.0 service's requirements and the interoperable requirements between a WSE 3.0 service and a WCF client.</span></span> <span data-ttu-id="dbb4b-108">これらの相互運用性要件には、前述の 2004 年 8 月版 WS-Addressing 仕様の使用と、WSE 3.0 の既定のメッセージ保護が <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> であることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-108">These interoperability requirements include the aforementioned use of the August 2004 WS-Addressing specification and the  WSE 3.0default message protection of <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span></span> <span data-ttu-id="dbb4b-109">WCF の既定のメッセージ保護は <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> です。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-109">The default message protection for WCF is <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="dbb4b-110">このトピックでは、WSE 3.0 サービスと相互運用する WCF バインドを作成する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-110">This topic details how to create a WCF binding that interoperates with a WSE 3.0 service.</span></span> <span data-ttu-id="dbb4b-111">また、WCF には、このバインディングが組み込まれたサンプルも用意されています。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-111">WCF also provides a sample that incorporates this binding.</span></span> <span data-ttu-id="dbb4b-112">このサンプルの詳細については、「 [ASMX Web サービスとの相互運用](../samples/interoperating-with-asmx-web-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-112">For more information about this sample, see [Interoperating with ASMX Web Services](../samples/interoperating-with-asmx-web-services.md).</span></span>  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a><span data-ttu-id="dbb4b-113">WCF クライアントで WSE 3.0 サービスにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="dbb4b-113">To access a WSE 3.0 Web service with a WCF client</span></span>  
  
1. <span data-ttu-id="dbb4b-114">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を実行して、WSE 3.0 Web サービス用の WCF クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-114">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="dbb4b-115">WSE 3.0 Web サービスの場合、WCF クライアントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-115">For a WSE 3.0 Web service, a WCF client is created.</span></span> <span data-ttu-id="dbb4b-116">WSE 3.0 は MEX プロトコルをサポートしていないため、このツールを使用して Web サービスのセキュリティ要件を取得することはできません。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-116">Because WSE 3.0 does not support the MEX protocol, you cannot use the tool to retrieve the security requirements for the Web service.</span></span> <span data-ttu-id="dbb4b-117">アプリケーション開発者は、クライアントのセキュリティ設定を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-117">The application developer must add the security settings for the client.</span></span>  
  
     <span data-ttu-id="dbb4b-118">WCF クライアントの作成の詳細については、「 [方法: クライアントを作成](../how-to-create-a-wcf-client.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-118">For more information about creating a WCF client, see the [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="dbb4b-119">WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-119">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="dbb4b-120">次のクラスは、 [WSE との相互運用](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90)) のサンプルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-120">The following class is part of the [Interoperating with WSE](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90)) sample:</span></span>  
  
    1. <span data-ttu-id="dbb4b-121"><xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-121">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="dbb4b-122">`WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-122">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="dbb4b-123">WSE サービスで使用する WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定を指定するプロパティを、このクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-123">Add properties to the class that specify the WSE turnkey assertion used by the WSE service, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span> <span data-ttu-id="dbb4b-124">WSE 3.0 では、ターンキーアサーションでクライアントまたは Web サービスのセキュリティ要件を指定します。 WCF でのバインディングの認証モードに似ています。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-124">In WSE 3.0, a turnkey assertion specifies the security requirements for a client or Web service—similar to the authentication mode of a binding in WCF.</span></span>  
  
         <span data-ttu-id="dbb4b-125">WSE 設定不要アサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定をそれぞれ指定する、`SecurityAssertion`、`RequireDerivedKeys`、`EstablishSecurityContext`、および `MessageProtectionOrder` の各プロパティを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-125">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="dbb4b-126"><xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドをオーバーライドして、バインディング プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-126">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="dbb4b-127">`SecurityAssertion` プロパティと `MessageProtectionOrder` プロパティの値を取得することで、トランスポート、メッセージ エンコーディング、メッセージ保護設定を指定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-127">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="dbb4b-128">クライアントのアプリケーション コードでは、コードを追加してバインディングのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-128">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="dbb4b-129">次のコード例では、WCF クライアントで、WSE 3.0 のターンキーセキュリティアサーションによる定義に従ってメッセージの保護と認証を使用する必要があることを指定し `AnonymousForCertificate` ます。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-129">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="dbb4b-130">また、セキュリティで保護されたセッションと派生キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-130">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="dbb4b-131">例</span><span class="sxs-lookup"><span data-stu-id="dbb4b-131">Example</span></span>  

 <span data-ttu-id="dbb4b-132">WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-132">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="dbb4b-133">次に、という名前のカスタムバインディングを使用して、 `WseHttpBinding` WSSecurityAnonymous WSE 3.0 クイックスタートサンプルと通信する WCF クライアントのバインディングプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="dbb4b-133">That custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client that communicates with the WSSecurityAnonymous WSE 3.0 QuickStart sample.</span></span>  

## <a name="see-also"></a><span data-ttu-id="dbb4b-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbb4b-134">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <span data-ttu-id="dbb4b-135">[WSE との相互運用](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="dbb4b-135">[Interoperating with WSE](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90))</span></span>
