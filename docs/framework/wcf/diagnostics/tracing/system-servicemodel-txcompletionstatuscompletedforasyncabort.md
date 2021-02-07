---
description: 詳細については、「TxCompletionStatusCompletedForAsyncAbort」を参照してください。
title: System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort
ms.date: 03/30/2017
ms.assetid: 155c3203-2e17-4709-b896-2254e22da45e
ms.openlocfilehash: 892a867607d1c6d34c06a59947cc336db067fb19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735687"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforasyncabort"></a><span data-ttu-id="700cd-103">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="700cd-103">System.ServiceModel.TxCompletionStatusCompletedForAsyncAbort</span></span>

<span data-ttu-id="700cd-104">非同期中止が実行されたため、指定された操作の指定のトランザクションは完了されました。</span><span class="sxs-lookup"><span data-stu-id="700cd-104">The specified transaction for the specified operation was completed due to asynchronous abort.</span></span>  
  
## <a name="description"></a><span data-ttu-id="700cd-105">説明</span><span class="sxs-lookup"><span data-stu-id="700cd-105">Description</span></span>  

 <span data-ttu-id="700cd-106">別の参加要素による中止、タイムアウト、またはトランザクションの参加要素内での別のエラーが発生したため、現在のトランザクションが中止されました。</span><span class="sxs-lookup"><span data-stu-id="700cd-106">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="700cd-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="700cd-107">Troubleshooting</span></span>  

 <span data-ttu-id="700cd-108">予期された中止ではない場合は、すべてのシステム ログを調べて中止の原因を確認してください。</span><span class="sxs-lookup"><span data-stu-id="700cd-108">If this abort is unexpected, check all system logs to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="700cd-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="700cd-109">See also</span></span>

- [<span data-ttu-id="700cd-110">トレース</span><span class="sxs-lookup"><span data-stu-id="700cd-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="700cd-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="700cd-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="700cd-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="700cd-112">Administration and Diagnostics</span></span>](../index.md)
