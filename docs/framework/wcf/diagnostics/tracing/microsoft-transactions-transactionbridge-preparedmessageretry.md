---
description: 詳細については、PreparedMessageRetry を参照してください。
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.date: 03/30/2017
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
ms.openlocfilehash: 99106493f0eec900875a713b439111fadb150c62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677276"
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a><span data-ttu-id="6d193-103">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span><span class="sxs-lookup"><span data-stu-id="6d193-103">Microsoft.Transactions.TransactionBridge.PreparedMessageRetry</span></span>

<span data-ttu-id="6d193-104">準備メッセージの再試行は、応答しないコーディネーターに送信されました。</span><span class="sxs-lookup"><span data-stu-id="6d193-104">A prepared message retry was sent to an unresponsive coordinator.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6d193-105">説明</span><span class="sxs-lookup"><span data-stu-id="6d193-105">Description</span></span>  

 <span data-ttu-id="6d193-106">ローカル トランザクション マネージャーが一定時間内に応答を受信せず、上位のコーディネーターに準備メッセージを再送信する必要があった場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="6d193-106">Traced if the local Transaction Manager needed to resend a Prepared message to a superior coordinator because it did not receive a response in a given amount of time/</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6d193-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6d193-107">Troubleshooting</span></span>  

 <span data-ttu-id="6d193-108">応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。</span><span class="sxs-lookup"><span data-stu-id="6d193-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="6d193-109">このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="6d193-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="6d193-110">いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="6d193-110">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d193-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d193-111">See also</span></span>

- [<span data-ttu-id="6d193-112">トレース</span><span class="sxs-lookup"><span data-stu-id="6d193-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="6d193-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6d193-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6d193-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="6d193-114">Administration and Diagnostics</span></span>](../index.md)
