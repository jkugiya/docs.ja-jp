---
description: 詳細については、「TxCompletionStatusCompletedForError」を参照してください。
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 83cd5c258b3a60f69cc94426aed7ccc1d27f6013
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735609"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="5aea1-103">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="5aea1-103">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>

<span data-ttu-id="5aea1-104">処理されない実行例外が発生したため、指定された操作の指定されたトランザクションが完了しました。</span><span class="sxs-lookup"><span data-stu-id="5aea1-104">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5aea1-105">説明</span><span class="sxs-lookup"><span data-stu-id="5aea1-105">Description</span></span>  

 <span data-ttu-id="5aea1-106">現在のトランザクションを完了しようとしているときにエラーが発生した場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="5aea1-106">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="5aea1-107">これは、応答またはエラーが呼び出し元に送信される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="5aea1-107">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="5aea1-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5aea1-108">Troubleshooting</span></span>  

 <span data-ttu-id="5aea1-109">トレース メッセージを調べて、例外メッセージとアクション可能な項目を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5aea1-109">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aea1-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5aea1-110">See also</span></span>

- [<span data-ttu-id="5aea1-111">トレース</span><span class="sxs-lookup"><span data-stu-id="5aea1-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="5aea1-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5aea1-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="5aea1-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="5aea1-113">Administration and Diagnostics</span></span>](../index.md)
