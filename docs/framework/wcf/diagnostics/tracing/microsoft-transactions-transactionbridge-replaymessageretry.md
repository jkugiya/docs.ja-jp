---
description: 詳細については、ReplayMessageRetry を参照してください。
title: Microsoft.Transactions.TransactionBridge.ReplayMessageRetry
ms.date: 03/30/2017
ms.assetid: e5b820ae-504d-405a-926a-9effa41d2369
ms.openlocfilehash: e4de1416fab2cf7098d0276b6130999c01ea6e3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803257"
---
# <a name="microsofttransactionstransactionbridgereplaymessageretry"></a><span data-ttu-id="05db5-103">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span><span class="sxs-lookup"><span data-stu-id="05db5-103">Microsoft.Transactions.TransactionBridge.ReplayMessageRetry</span></span>

<span data-ttu-id="05db5-104">リプレイ メッセージの再試行は、応答しないコーディネーターに送信されました。</span><span class="sxs-lookup"><span data-stu-id="05db5-104">A replay message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="05db5-105">説明</span><span class="sxs-lookup"><span data-stu-id="05db5-105">Description</span></span>  

 <span data-ttu-id="05db5-106">ローカル トランザクション マネージャーが一定時間内に応答を受信せず、上位のコーディネーターにリプレイ メッセージを再送信する必要があった場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="05db5-106">Traced if the local Transaction Manager needed to resend a Replay message to a superior coordinator because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="05db5-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="05db5-107">Troubleshooting</span></span>  

 <span data-ttu-id="05db5-108">応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。</span><span class="sxs-lookup"><span data-stu-id="05db5-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="05db5-109">このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="05db5-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="05db5-110">いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="05db5-110">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05db5-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="05db5-111">See also</span></span>

- [<span data-ttu-id="05db5-112">トレース</span><span class="sxs-lookup"><span data-stu-id="05db5-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="05db5-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="05db5-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="05db5-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="05db5-114">Administration and Diagnostics</span></span>](../index.md)
