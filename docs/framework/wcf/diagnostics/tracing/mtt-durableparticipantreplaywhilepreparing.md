---
description: '詳細情報: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing'
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: fcaa50dd4faa548cad8ff085f1c66f94c63bd010
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635663"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="df706-103">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="df706-103">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>

<span data-ttu-id="df706-104">WS-AT プロトコル サービスは、準備メッセージに応答していない永続的な参加要素から、リプレイ メッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="df706-104">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="df706-105">そのため、トランザクションが中止されました。</span><span class="sxs-lookup"><span data-stu-id="df706-105">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="df706-106">説明</span><span class="sxs-lookup"><span data-stu-id="df706-106">Description</span></span>  

 <span data-ttu-id="df706-107">永続的な参加要素がまだ準備している間にリプレイ メッセージが受信された場合は、トレースされます。</span><span class="sxs-lookup"><span data-stu-id="df706-107">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="df706-108">これは、この状態に対して無効なメッセージであり、トランザクションは中止されます。</span><span class="sxs-lookup"><span data-stu-id="df706-108">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="df706-109">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="df706-109">Troubleshooting</span></span>

<span data-ttu-id="df706-110">このエラー メッセージは、永続的な参加要素 (下位トランザクション マネージャーを含む) がエラーから回復したが、トランザクション結果が不明であるため、状態を要求していることを示している場合があります。</span><span class="sxs-lookup"><span data-stu-id="df706-110">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df706-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="df706-111">See also</span></span>

- [<span data-ttu-id="df706-112">トレース</span><span class="sxs-lookup"><span data-stu-id="df706-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="df706-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="df706-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="df706-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="df706-114">Administration and Diagnostics</span></span>](../index.md)
