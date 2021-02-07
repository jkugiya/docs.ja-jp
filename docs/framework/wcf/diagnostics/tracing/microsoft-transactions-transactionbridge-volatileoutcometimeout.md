---
description: 詳細については、VolatileOutcomeTimeout を参照してください。
title: Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout
ms.date: 03/30/2017
ms.assetid: 2dbe34c5-57c7-4b64-9257-63021911d03c
ms.openlocfilehash: 5dd6ecce995d315581e1335e4dc83c425a6381b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677237"
---
# <a name="microsofttransactionstransactionbridgevolatileoutcometimeout"></a><span data-ttu-id="d9cdc-103">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span><span class="sxs-lookup"><span data-stu-id="d9cdc-103">Microsoft.Transactions.TransactionBridge.VolatileOutcomeTimeout</span></span>

<span data-ttu-id="d9cdc-104">不安定な参加要素からの結果メッセージに対する応答を受信するのを待機しているときに WS-AT プロトコル サービスがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d9cdc-104">The WS-AT protocol service timed out waiting for a response to an outcome message from a volatile participant.</span></span> <span data-ttu-id="d9cdc-105">受信者が応答した場合、トランザクションの結果が不明である場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9cdc-105">The transaction outcome may be in doubt if the participant returns.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d9cdc-106">説明</span><span class="sxs-lookup"><span data-stu-id="d9cdc-106">Description</span></span>  

 <span data-ttu-id="d9cdc-107">不安定な参加要素がコミットまたは中止を決定したが、一定時間内にコミット要求またはロールバック要求に応答していない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="d9cdc-107">Traced when a Volatile participant has decided to Commit or Abort but has not responded to a Commit or Rollback request within a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d9cdc-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d9cdc-108">Troubleshooting</span></span>  

 <span data-ttu-id="d9cdc-109">不安定な参加要素がすべて一定時間内に応答できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d9cdc-109">Ensure that all Volatile participants are able to respond within the given amount of time.</span></span> <span data-ttu-id="d9cdc-110">既定の時間は 180 秒です。</span><span class="sxs-lookup"><span data-stu-id="d9cdc-110">The default time period is 180 seconds.</span></span>  <span data-ttu-id="d9cdc-111">この時間が不十分な場合は、WS-AT の `VolatileOutcomeDelay` タイマー ポリシーを増やします。</span><span class="sxs-lookup"><span data-stu-id="d9cdc-111">If this is insufficient, increase the `VolatileOutcomeDelay` timer policy for WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9cdc-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d9cdc-112">See also</span></span>

- [<span data-ttu-id="d9cdc-113">トレース</span><span class="sxs-lookup"><span data-stu-id="d9cdc-113">Tracing</span></span>](index.md)
- [<span data-ttu-id="d9cdc-114">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d9cdc-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d9cdc-115">管理と診断</span><span class="sxs-lookup"><span data-stu-id="d9cdc-115">Administration and Diagnostics</span></span>](../index.md)
