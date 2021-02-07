---
description: '詳細については、「方法: WCF エンドポイントとメッセージキューアプリケーションを使用してメッセージを交換する」を参照してください。'
title: '方法: WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 0b8f315b00960ec87e68e9e2b11ac9b273dbbf93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704616"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="aa913-103">方法: WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="aa913-103">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>

<span data-ttu-id="aa913-104">Msmq 統合バインディングを使用して、既存のメッセージキュー (MSMQ) アプリケーションを Windows Communication Foundation (WCF) アプリケーションと統合し、msmq メッセージを WCF メッセージとの間で変換することができます。</span><span class="sxs-lookup"><span data-stu-id="aa913-104">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="aa913-105">これにより、WCF クライアントから MSMQ 受信アプリケーションを呼び出したり、MSMQ 送信者アプリケーションから WCF サービスを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="aa913-105">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="aa913-106">このセクションでは、 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> (1) WCF クライアントと、(2) msmq アプリケーションクライアントと WCF サービスを使用して記述された msmq アプリケーションサービスの間で、キューに置かれた通信を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aa913-106">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="aa913-107">WCF クライアントから MSMQ 受信アプリケーションを呼び出す方法を示す完全なサンプルについては、「 [Windows Communication Foundation To Message Queuing](../samples/wcf-to-message-queuing.md) sample」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa913-107">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="aa913-108">MSMQ クライアントから WCF サービスを呼び出す方法を示す完全なサンプルについては、「 [Windows Communication Foundation サンプルのメッセージキュー](../samples/message-queuing-to-wcf.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa913-108">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="aa913-109">MSMQ クライアントからのメッセージを受信する WCF サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="aa913-109">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="aa913-110">次のコード例に示すように、MSMQ 送信者アプリケーションからキューに置かれたメッセージを受信する WCF サービスのサービスコントラクトを定義するインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="aa913-110">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="aa913-111">次のコード例に示すように、定義したインターフェイスを実装し、<xref:System.ServiceModel.ServiceBehaviorAttribute> 属性をクラスに適用します。</span><span class="sxs-lookup"><span data-stu-id="aa913-111">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="aa913-112"><xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を指定する構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="aa913-112">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="aa913-113">構成されたバインディングを使用する <xref:System.ServiceModel.ServiceHost> オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="aa913-113">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="aa913-114">MSMQ の受信側アプリケーションにメッセージを送信する WCF クライアントを作成するには</span><span class="sxs-lookup"><span data-stu-id="aa913-114">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="aa913-115">次のコード例に示すように、キューに置かれたメッセージを MSMQ 受信者に送信する WCF クライアントのサービスコントラクトを定義するインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="aa913-115">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="aa913-116">WCF クライアントが MSMQ 受信者を呼び出すために使用するクライアントクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="aa913-116">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="aa913-117">MsmqIntegrationBinding バインディングの使用を指定する構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="aa913-117">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="aa913-118">クライアント クラスのインスタンスを作成し、メッセージ受信サービスによって定義されたメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="aa913-118">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="aa913-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa913-119">See also</span></span>

- [<span data-ttu-id="aa913-120">キューの概要</span><span class="sxs-lookup"><span data-stu-id="aa913-120">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="aa913-121">方法: WCF エンドポイントを使用してキューに置かれたメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="aa913-121">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="aa913-122">Windows Communication Foundation でのメッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="aa913-122">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="aa913-123">メッセージ キュー (MSMQ) のインストール</span><span class="sxs-lookup"><span data-stu-id="aa913-123">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="aa913-124">Windows Communication Foundation へのメッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="aa913-124">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="aa913-125">メッセージ キューを介したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="aa913-125">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
