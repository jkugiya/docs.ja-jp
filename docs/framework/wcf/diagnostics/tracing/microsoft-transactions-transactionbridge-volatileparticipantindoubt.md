---
description: 詳細については、VolatileParticipantInDoubt を参照してください。
title: Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt
ms.date: 03/30/2017
ms.assetid: 3e8fc825-9f22-47e7-9c16-d64ef291c932
ms.openlocfilehash: c9d95285e09d017aa82c86e7c5c6f9fd758b9f80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803244"
---
# <a name="microsofttransactionstransactionbridgevolatileparticipantindoubt"></a><span data-ttu-id="f4b10-103">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span><span class="sxs-lookup"><span data-stu-id="f4b10-103">Microsoft.Transactions.TransactionBridge.VolatileParticipantInDoubt</span></span>

<span data-ttu-id="f4b10-104">WS-AT プロトコル サービスは、認識されない不安定な参加要素からの準備メッセージまたはリプレイ メッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="f4b10-104">The WS-AT protocol service received a Prepared or Replay message from an unrecognized volatile participant.</span></span> <span data-ttu-id="f4b10-105">参加要素にエラーが返されました。この結果、トランザクションの結果が不明であると宣言します。</span><span class="sxs-lookup"><span data-stu-id="f4b10-105">A fault was returned to the participant, declares that the transaction's outcome is in doubt.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f4b10-106">説明</span><span class="sxs-lookup"><span data-stu-id="f4b10-106">Description</span></span>  

 <span data-ttu-id="f4b10-107">ローカル トランザクション マネージャーが、既に認識していない揮発性参加リストからの準備メッセージまたはリプレイ メッセージを受信するとトレースされます。</span><span class="sxs-lookup"><span data-stu-id="f4b10-107">Traced when the local Transaction Manager receives a Prepared or Replay message from a Volatile enlistment that it has already forgotten.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f4b10-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f4b10-108">Troubleshooting</span></span>  

 <span data-ttu-id="f4b10-109">不安定な参加要素からメッセージが遅れて届く原因を調査してください。</span><span class="sxs-lookup"><span data-stu-id="f4b10-109">Investigate potential causes of late messages coming from the Volatile participant.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b10-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4b10-110">See also</span></span>

- [<span data-ttu-id="f4b10-111">トレース</span><span class="sxs-lookup"><span data-stu-id="f4b10-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="f4b10-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f4b10-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f4b10-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="f4b10-113">Administration and Diagnostics</span></span>](../index.md)
