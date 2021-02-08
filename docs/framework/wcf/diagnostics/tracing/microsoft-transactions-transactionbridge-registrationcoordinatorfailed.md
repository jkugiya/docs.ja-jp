---
description: 詳細については、RegistrationCoordinatorFailed を参照してください。
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: f522fb91db6c721c43d2768a9eb79d627fbc2a59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770613"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="548a2-103">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="548a2-103">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>

<span data-ttu-id="548a2-104">WS-AT プロトコル サービスは、Register メッセージをコーディネーターに送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="548a2-104">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="548a2-105">説明</span><span class="sxs-lookup"><span data-stu-id="548a2-105">Description</span></span>  

 <span data-ttu-id="548a2-106">メッセージを送信できないために、ローカルの TransactionManager がその上位の TransactionManager に登録できない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="548a2-106">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="548a2-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="548a2-107">Troubleshooting</span></span>  

 <span data-ttu-id="548a2-108">トレース メッセージを調べて、メッセージの送信エラーの原因となった例外を確認してください。</span><span class="sxs-lookup"><span data-stu-id="548a2-108">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548a2-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="548a2-109">See also</span></span>

- [<span data-ttu-id="548a2-110">トレース</span><span class="sxs-lookup"><span data-stu-id="548a2-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="548a2-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="548a2-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="548a2-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="548a2-112">Administration and Diagnostics</span></span>](../index.md)
