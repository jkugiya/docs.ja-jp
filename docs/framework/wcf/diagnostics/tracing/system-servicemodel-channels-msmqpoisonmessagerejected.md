---
description: 詳細については、「MsmqPoisonMessageRejected」を参照してください。
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 856c28dd313867de0661d4950dd67e6740e2b338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759303"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="5a5b2-103">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="5a5b2-103">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>

<span data-ttu-id="5a5b2-104">有害メッセージは拒否されました。</span><span class="sxs-lookup"><span data-stu-id="5a5b2-104">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5a5b2-105">説明</span><span class="sxs-lookup"><span data-stu-id="5a5b2-105">Description</span></span>  

 <span data-ttu-id="5a5b2-106">このトレースは、有害メッセージが検出され、続いて拒否されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="5a5b2-106">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="5a5b2-107">これは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Reject` に設定されると発生します。</span><span class="sxs-lookup"><span data-stu-id="5a5b2-107">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="5a5b2-108">拒否されたメッセージは、送信側の [配信不能キュー](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)に配信されます。</span><span class="sxs-lookup"><span data-stu-id="5a5b2-108">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="5a5b2-109">メッセージが有害になった場合の詳細、およびメッセージを適切に処理するようにサービスを構成する方法については、「 [有害メッセージの処理](../../feature-details/poison-message-handling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a5b2-109">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="5a5b2-110">MSMQ での拒否されたメッセージの意味の詳細については、「 [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a5b2-110">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5b2-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a5b2-111">See also</span></span>

- [<span data-ttu-id="5a5b2-112">トレース</span><span class="sxs-lookup"><span data-stu-id="5a5b2-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="5a5b2-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5a5b2-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5a5b2-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="5a5b2-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="5a5b2-115">有害メッセージの処理</span><span class="sxs-lookup"><span data-stu-id="5a5b2-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="5a5b2-116">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5a5b2-116">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
