---
description: 詳細については、「MsmqMessageRejected」を参照してください。
title: System.ServiceModel.Channels.MsmqMessageRejected
ms.date: 03/30/2017
ms.assetid: 9b7c10a7-2af6-44a2-8b1a-90bba0c7cf26
ms.openlocfilehash: 4400519c814627fd2a2f2585359d6d6376798ac0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780948"
---
# <a name="systemservicemodelchannelsmsmqmessagerejected"></a><span data-ttu-id="69846-103">System.ServiceModel.Channels.MsmqMessageRejected</span><span class="sxs-lookup"><span data-stu-id="69846-103">System.ServiceModel.Channels.MsmqMessageRejected</span></span>

<span data-ttu-id="69846-104">MSMQ はメッセージを拒否しました。</span><span class="sxs-lookup"><span data-stu-id="69846-104">MSMQ rejected the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="69846-105">説明</span><span class="sxs-lookup"><span data-stu-id="69846-105">Description</span></span>  

 <span data-ttu-id="69846-106">このトレースは、MSMQ メッセージが拒否されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="69846-106">This trace indicates that an MSMQ message was rejected.</span></span>  
  
 <span data-ttu-id="69846-107">MSMQ メッセージは、Windows Communication Foundation (WCF) (NetMsmqBinding または MsmqIntegrationBinding で使用される) が処理できない場合に拒否されることがあります。</span><span class="sxs-lookup"><span data-stu-id="69846-107">MSMQ messages can be rejected when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="69846-108">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="69846-108">Such messages are referred to as poison messages.</span></span> <span data-ttu-id="69846-109">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると拒否されます。</span><span class="sxs-lookup"><span data-stu-id="69846-109">A poison message is rejected when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="69846-110">拒否されたメッセージは、送信側の [配信不能キュー](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)に配信されます。</span><span class="sxs-lookup"><span data-stu-id="69846-110">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="69846-111">メッセージが有害になった場合の詳細、およびメッセージを適切に処理するようにサービスを構成する方法については、「 [有害メッセージの処理](../../feature-details/poison-message-handling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69846-111">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
 <span data-ttu-id="69846-112">MSMQ での拒否されたメッセージの意味の詳細については、「 [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="69846-112">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69846-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="69846-113">See also</span></span>

- [<span data-ttu-id="69846-114">トレース</span><span class="sxs-lookup"><span data-stu-id="69846-114">Tracing</span></span>](index.md)
- [<span data-ttu-id="69846-115">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="69846-115">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="69846-116">管理と診断</span><span class="sxs-lookup"><span data-stu-id="69846-116">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="69846-117">有害メッセージの処理</span><span class="sxs-lookup"><span data-stu-id="69846-117">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="69846-118">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="69846-118">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
