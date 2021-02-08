---
description: 詳細については、「MsmqMessageDropped」を参照してください。
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 41b9c6d5399f0f6b458404ee4b64624e5863c777
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780961"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="108fa-103">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="108fa-103">System.ServiceModel.Channels.MsmqMessageDropped</span></span>

<span data-ttu-id="108fa-104">MSMQ はメッセージを破棄しました。</span><span class="sxs-lookup"><span data-stu-id="108fa-104">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="108fa-105">説明</span><span class="sxs-lookup"><span data-stu-id="108fa-105">Description</span></span>  

 <span data-ttu-id="108fa-106">このトレースは、MSMQ メッセージが破棄されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="108fa-106">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="108fa-107">MSMQ メッセージは Windows Communication Foundation (WCF) (NetMsmqBinding または MsmqIntegrationBinding で使用) が処理できない場合に削除できます。</span><span class="sxs-lookup"><span data-stu-id="108fa-107">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="108fa-108">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="108fa-108">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="108fa-109">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。</span><span class="sxs-lookup"><span data-stu-id="108fa-109">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="108fa-110">破棄されたメッセージはキューから削除され、元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="108fa-110">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="108fa-111">メッセージが有害になった場合の詳細、およびメッセージを適切に処理するようにサービスを構成する方法については、「 [有害メッセージの処理](../../feature-details/poison-message-handling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="108fa-111">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108fa-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="108fa-112">See also</span></span>

- [<span data-ttu-id="108fa-113">トレース</span><span class="sxs-lookup"><span data-stu-id="108fa-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="108fa-114">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="108fa-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="108fa-115">管理と診断</span><span class="sxs-lookup"><span data-stu-id="108fa-115">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="108fa-116">有害メッセージの処理</span><span class="sxs-lookup"><span data-stu-id="108fa-116">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
