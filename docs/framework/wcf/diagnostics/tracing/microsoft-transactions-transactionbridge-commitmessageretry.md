---
description: 詳細については、CommitMessageRetry を参照してください。
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.date: 03/30/2017
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
ms.openlocfilehash: 8f45463ac31c210acd8534df2c4e1ef2922f1c8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99720606"
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a><span data-ttu-id="49622-103">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span><span class="sxs-lookup"><span data-stu-id="49622-103">Microsoft.Transactions.TransactionBridge.CommitMessageRetry</span></span>

<span data-ttu-id="49622-104">コミット メッセージの再試行は、応答しない参加要素に送信されました。</span><span class="sxs-lookup"><span data-stu-id="49622-104">A commit message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="49622-105">説明</span><span class="sxs-lookup"><span data-stu-id="49622-105">Description</span></span>  

 <span data-ttu-id="49622-106">ローカル トランザクション マネージャーが一定時間内に応答を受信せず、下位の参加要素にコミット メッセージを再送信する必要があった場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="49622-106">Traced if the local Transaction Manager needed to resend a Commit message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="49622-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="49622-107">Troubleshooting</span></span>  

 <span data-ttu-id="49622-108">応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。</span><span class="sxs-lookup"><span data-stu-id="49622-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="49622-109">このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="49622-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="49622-110">いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="49622-110">Both issues will drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49622-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="49622-111">See also</span></span>

- [<span data-ttu-id="49622-112">トレース</span><span class="sxs-lookup"><span data-stu-id="49622-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="49622-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="49622-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="49622-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="49622-114">Administration and Diagnostics</span></span>](../index.md)
