---
description: 詳細については、RegisterParticipantFailure を参照してください。
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e930ee66720a9f397999d729e8d680fce9a37e29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770626"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="93a4e-103">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="93a4e-103">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>

<span data-ttu-id="93a4e-104">WS-AT プロトコル サービスは、制御プロトコルの参加要素の登録に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="93a4e-104">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="93a4e-105">説明</span><span class="sxs-lookup"><span data-stu-id="93a4e-105">Description</span></span>  

 <span data-ttu-id="93a4e-106">MSDTC により無効な登録要求が検出された場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="93a4e-106">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="93a4e-107">これは、複数の完了登録要求や内部エラーによって発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="93a4e-107">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="93a4e-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="93a4e-108">Troubleshooting</span></span>  

 <span data-ttu-id="93a4e-109">完了を複数回登録しないでください。</span><span class="sxs-lookup"><span data-stu-id="93a4e-109">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="93a4e-110">また、トレース メッセージ内のステータス文字列を調べて、アクション可能な項目が存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="93a4e-110">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a4e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="93a4e-111">See also</span></span>

- [<span data-ttu-id="93a4e-112">トレース</span><span class="sxs-lookup"><span data-stu-id="93a4e-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="93a4e-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="93a4e-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="93a4e-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="93a4e-114">Administration and Diagnostics</span></span>](../index.md)
