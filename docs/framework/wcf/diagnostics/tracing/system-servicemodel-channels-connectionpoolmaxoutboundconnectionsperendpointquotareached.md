---
description: 詳細については、EnlistTransactionFailure を参照してください。
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: f0645d0f7bfc2787f4bce254ea8d6e3143dc0406
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644607"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="b8cd2-103">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="b8cd2-103">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>

<span data-ttu-id="b8cd2-104">WS-AT プロトコル サービスは、指定されたコーディネーション コンテキストを使用してトランザクションに参加することができませんでした。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-104">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b8cd2-105">説明</span><span class="sxs-lookup"><span data-stu-id="b8cd2-105">Description</span></span>  

 <span data-ttu-id="b8cd2-106">指定された 2PC プロトコルのトランザクションに MSDTC が参加できない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-106">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="b8cd2-107">これは、トランザクションが存在しなくなった場合、参加が許可されなくなった場合、または既に参加が多すぎる場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-107">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b8cd2-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b8cd2-108">Troubleshooting</span></span>  

 <span data-ttu-id="b8cd2-109">トレース メッセージ内のステータス文字列を調べて、アクション可能な項目が存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b8cd2-109">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8cd2-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8cd2-110">See also</span></span>

- [<span data-ttu-id="b8cd2-111">トレース</span><span class="sxs-lookup"><span data-stu-id="b8cd2-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="b8cd2-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b8cd2-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b8cd2-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="b8cd2-113">Administration and Diagnostics</span></span>](../index.md)
