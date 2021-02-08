---
description: '詳細については、「方法: WSE 3.0 サービスと相互運用するように WCF クライアントを構成する」を参照してください。'
title: '方法: WCF クライアントと WSE3.0 サービスを相互運用するために構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 97de90c491a29cdacf881a92013a11db6aea416f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780129"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="cb2d0-103">方法: WCF クライアントと WSE3.0 サービスを相互運用するために構成する</span><span class="sxs-lookup"><span data-stu-id="cb2d0-103">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>

<span data-ttu-id="cb2d0-104">Windows Communication Foundation (WCF) クライアントは、WS-Addressing 仕様の8月2004バージョンを使用するように WCF クライアントが構成されている場合に、Web サービス拡張 Microsoft .NET 3.0 (WSE) サービスとのワイヤレベルの互換性があります。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-104">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="cb2d0-105">WSE 3.0 Web サービスと相互運用するように WCF クライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="cb2d0-105">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="cb2d0-106">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を実行して、WSE 3.0 Web サービス用の WCF クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-106">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="cb2d0-107">WSE Web サービスの場合は、WCF クライアントクラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-107">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="cb2d0-108">WCF クライアントの作成の詳細については、「 [方法: クライアントを作成](../how-to-create-a-wcf-client.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-108">For details about creating a WCF client, see the [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="cb2d0-109">WSE 3.0 Web サービスと通信できるバインディングを表すクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-109">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="cb2d0-110">次のクラスは、 [WSE との相互運用](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90)) のサンプルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-110">The following class is part of the [Interoperating with WSE](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90)) sample.</span></span>  
  
    1. <span data-ttu-id="cb2d0-111"><xref:System.ServiceModel.Channels.Binding> クラスから派生するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-111">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="cb2d0-112">`WseHttpBinding` クラスから派生する、<xref:System.ServiceModel.Channels.Binding> という名前のクラスを作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-112">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="cb2d0-113">WSE の設定不要アサーションを指定するクラスに、派生キーが必要か、セキュリティで保護されたセッションが使用されるか、署名の確認が必要かどうかの指定、およびメッセージ保護設定などのプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-113">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="cb2d0-114">次のコード例では `SecurityAssertion` 、、、、およびの各プロパティを定義し `RequireDerivedKeys` `EstablishSecurityContext` `MessageProtectionOrder` ます。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-114">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="cb2d0-115">WSE のターンキーアサーション、派生キーが必要かどうか、セキュリティで保護されたセッションを使用するかどうか、署名の確認が必要かどうか、およびメッセージ保護設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-115">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="cb2d0-116"><xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> メソッドをオーバーライドして、バインディング プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-116">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="cb2d0-117">`SecurityAssertion` プロパティと `MessageProtectionOrder` プロパティの値を取得することで、トランスポート、メッセージ エンコーディング、メッセージ保護設定を指定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-117">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="cb2d0-118">クライアントのアプリケーション コードでは、コードを追加してバインディングのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-118">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="cb2d0-119">次のコード例では、WCF クライアントで、WSE 3.0 のターンキーセキュリティアサーションによる定義に従ってメッセージの保護と認証を使用する必要があることを指定し `AnonymousForCertificate` ます。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-119">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="cb2d0-120">また、セキュリティで保護されたセッションと派生キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-120">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="cb2d0-121">例</span><span class="sxs-lookup"><span data-stu-id="cb2d0-121">Example</span></span>  

 <span data-ttu-id="cb2d0-122">WSE 3.0 の設定不要のセキュリティ アサーションのプロパティに対応するプロパティを公開するカスタムのバインディングを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-122">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="cb2d0-123">次に、という名前のカスタムバインディングを使用して、 `WseHttpBinding` WCF クライアントのバインディングプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="cb2d0-123">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="cb2d0-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb2d0-124">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <span data-ttu-id="cb2d0-125">[WSE との相互運用](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="cb2d0-125">[Interoperating with WSE](/previous-versions/dotnet/netframework-3.5/ms752257(v=vs.90))</span></span>
