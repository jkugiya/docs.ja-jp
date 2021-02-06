---
description: 詳細については、「WS-I Basic Profile 1.1 相互運用可能なサービスの作成」を参照してください。
title: WS-I Basic Profile 1.1 の相互運用可能サービスの作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 46e2d925dfe431957198b1d53b40d28adf6fb1c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646180"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="4c821-103">WS-I Basic Profile 1.1 の相互運用可能サービスの作成</span><span class="sxs-lookup"><span data-stu-id="4c821-103">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>

<span data-ttu-id="4c821-104">ASP.NET Web サービスクライアントと相互運用できるように WCF サービスエンドポイントを構成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4c821-104">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="4c821-105">サービス エンドポイントのバインディングの種類として <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> を使用する。</span><span class="sxs-lookup"><span data-stu-id="4c821-105">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="4c821-106">コールバック コントラクト機能とセッション コントラクト機能の使用、およびトランザクション動作のサービス エンドポイントでの使用をいずれも行わない。</span><span class="sxs-lookup"><span data-stu-id="4c821-106">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="4c821-107">必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。</span><span class="sxs-lookup"><span data-stu-id="4c821-107">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="4c821-108"><xref:System.ServiceModel.BasicHttpBinding> クラスの次の機能を使用する場合、WS-I Basic Profile 1.1 の機能では十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="4c821-108">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="4c821-109"><xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> プロパティで制御される MTOM (Message Transmission Optimization Mechanism) メッセージ エンコーディング。</span><span class="sxs-lookup"><span data-stu-id="4c821-109">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="4c821-110">MTOM を使用しない場合は、このプロパティを既定値 (<xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>) のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="4c821-110">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="4c821-111"><xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 値によって制御されるメッセージ セキュリティでは、WS-I Basic Security Profile 1.0 に準拠した WS-Security がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="4c821-111">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="4c821-112">WS-Security を使用しない場合は、このプロパティを既定値 (<xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType>) のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="4c821-112">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="4c821-113">WCF サービスのメタデータを ASP.NET で使用できるようにするには、web サービスクライアント生成ツール (web サービス [記述言語ツール) (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))、 [Web サービス検出ツール (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))、および Visual Studio の [ **web 参照の追加** ] 機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c821-113">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="4c821-114">メタデータの公開を有効にします。</span><span class="sxs-lookup"><span data-stu-id="4c821-114">Enable metadata publication.</span></span> <span data-ttu-id="4c821-115">詳細については、「 [メタデータエンドポイントの公開](publishing-metadata-endpoints.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c821-115">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c821-116">例</span><span class="sxs-lookup"><span data-stu-id="4c821-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4c821-117">説明</span><span class="sxs-lookup"><span data-stu-id="4c821-117">Description</span></span>  

 <span data-ttu-id="4c821-118">次のコード例は、ASP.NET Web サービスクライアントと互換性のある WCF エンドポイントをコードで、または構成ファイルで追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4c821-118">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4c821-119">コード</span><span class="sxs-lookup"><span data-stu-id="4c821-119">Code</span></span>  

 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4c821-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c821-120">See also</span></span>

- [<span data-ttu-id="4c821-121">ASP.NET Web サービスとの相互運用</span><span class="sxs-lookup"><span data-stu-id="4c821-121">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
