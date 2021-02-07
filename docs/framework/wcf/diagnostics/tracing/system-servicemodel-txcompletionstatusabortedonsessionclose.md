---
description: 詳細については、「TxCompletionStatusAbortedOnSessionClose」を参照してください。
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: d47dc1a87c7f44b58f70f9590b4233f1e0a9074e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735713"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="6501d-103">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="6501d-103">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>

<span data-ttu-id="6501d-104">指定されたトランザクションは、セッションが終了したときにまだ完了しておらず、TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute が false に設定されているため、中止されました。</span><span class="sxs-lookup"><span data-stu-id="6501d-104">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6501d-105">説明</span><span class="sxs-lookup"><span data-stu-id="6501d-105">Description</span></span>  

 <span data-ttu-id="6501d-106">現在のアクティブなセッションが終了した時点でトランザクションが完了しておらず、TransactionAutoCompleteOnSessionClose が `false` に設定されている場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="6501d-106">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="6501d-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6501d-107">Troubleshooting</span></span>  

 <span data-ttu-id="6501d-108">このトレースは、アプリケーションに調査が必要なバグが含まれている可能性があることを示します。</span><span class="sxs-lookup"><span data-stu-id="6501d-108">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6501d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="6501d-109">See also</span></span>

- [<span data-ttu-id="6501d-110">トレース</span><span class="sxs-lookup"><span data-stu-id="6501d-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="6501d-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6501d-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="6501d-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="6501d-112">Administration and Diagnostics</span></span>](../index.md)
