---
description: 詳細については、PrepareMessageRetry を参照してください。
title: Microsoft.Transactions.TransactionBridge.PrepareMessageRetry
ms.date: 03/30/2017
ms.assetid: ada4baa5-b60d-46b8-ad46-4d69f8d8a9fa
ms.openlocfilehash: 7555336f1082eb097017f9440015f6ab201cdeae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770782"
---
# <a name="microsofttransactionstransactionbridgepreparemessageretry"></a><span data-ttu-id="0fe19-103">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span><span class="sxs-lookup"><span data-stu-id="0fe19-103">Microsoft.Transactions.TransactionBridge.PrepareMessageRetry</span></span>

<span data-ttu-id="0fe19-104">応答しない参加要素に、準備メッセージの再試行が送信されました。</span><span class="sxs-lookup"><span data-stu-id="0fe19-104">A prepare message retry was sent to an unresponsive participant.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0fe19-105">説明</span><span class="sxs-lookup"><span data-stu-id="0fe19-105">Description</span></span>  

 <span data-ttu-id="0fe19-106">ローカル トランザクション マネージャーが一定時間内に応答を受信せず、下位の参加要素に準備メッセージを再送信する必要があった場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="0fe19-106">Traced if the local Transaction Manager needed to resend a Prepare message to a subordinate participant because it did not receive a response in a given amount of time.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0fe19-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0fe19-107">Troubleshooting</span></span>  

 <span data-ttu-id="0fe19-108">応答が時間どおりに配信されない原因となっている可能性のあるネットワークや製品の問題について調査します。</span><span class="sxs-lookup"><span data-stu-id="0fe19-108">Investigate potential network or product issues that prevent the response from being delivered on time.</span></span>  <span data-ttu-id="0fe19-109">このメッセージが多数表示される場合、インフラストラクチャに問題があるか、または応答時間が異常にかかっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="0fe19-109">If many of these messages are seen, it can indicate infrastructure problems or abnormally long response times.</span></span> <span data-ttu-id="0fe19-110">いずれの問題によっても、システム内のトランザクションのスループットが大幅に低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="0fe19-110">Both issues can drastically reduce the throughput of transactions within the system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe19-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fe19-111">See also</span></span>

- [<span data-ttu-id="0fe19-112">トレース</span><span class="sxs-lookup"><span data-stu-id="0fe19-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="0fe19-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0fe19-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0fe19-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="0fe19-114">Administration and Diagnostics</span></span>](../index.md)
