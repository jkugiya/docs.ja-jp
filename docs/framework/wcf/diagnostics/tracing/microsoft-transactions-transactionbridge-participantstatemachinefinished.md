---
description: 詳細については、ParticipantStateMachineFinished を参照してください。
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: f49027b82957969779423d0895ff24a4a36d1f4f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759381"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="690da-103">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="690da-103">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>

<span data-ttu-id="690da-104">参加要素の登録リストのステート マシンは完了状態になりました。</span><span class="sxs-lookup"><span data-stu-id="690da-104">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="690da-105">説明</span><span class="sxs-lookup"><span data-stu-id="690da-105">Description</span></span>  

 <span data-ttu-id="690da-106">下位参加要素登録リストの 2PC 処理が完了したときにトレースされます。</span><span class="sxs-lookup"><span data-stu-id="690da-106">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="690da-107">登録リストの結果は、Committed または Aborted のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="690da-107">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="690da-108">準備中、すべての参加要素を読み取り専用にする場合にもトレースされます。</span><span class="sxs-lookup"><span data-stu-id="690da-108">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="690da-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="690da-109">See also</span></span>

- [<span data-ttu-id="690da-110">トレース</span><span class="sxs-lookup"><span data-stu-id="690da-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="690da-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="690da-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="690da-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="690da-112">Administration and Diagnostics</span></span>](../index.md)
