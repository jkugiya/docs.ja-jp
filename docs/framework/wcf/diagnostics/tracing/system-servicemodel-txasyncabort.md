---
description: 詳細については、「TxAsyncAbort」を参照してください。
title: System.ServiceModel.TxAsyncAbort
ms.date: 03/30/2017
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
ms.openlocfilehash: 461a5e4da21cf3219114ebb4e6db2149fb94ea17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653889"
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="e5fa8-103">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="e5fa8-103">System.ServiceModel.TxAsyncAbort</span></span>

<span data-ttu-id="e5fa8-104">指定したトランザクションが非同期に中止されました。</span><span class="sxs-lookup"><span data-stu-id="e5fa8-104">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e5fa8-105">説明</span><span class="sxs-lookup"><span data-stu-id="e5fa8-105">Description</span></span>  

 <span data-ttu-id="e5fa8-106">別の参加要素による中止、タイムアウト、またはトランザクションの参加要素内での別のエラーが発生したため、現在のトランザクションが中止されました。</span><span class="sxs-lookup"><span data-stu-id="e5fa8-106">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e5fa8-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e5fa8-107">Troubleshooting</span></span>  

 <span data-ttu-id="e5fa8-108">これが予期された中止であるかどうかをすべてのシステム ログで確認し、中止の原因を特定してください。</span><span class="sxs-lookup"><span data-stu-id="e5fa8-108">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5fa8-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5fa8-109">See also</span></span>

- [<span data-ttu-id="e5fa8-110">トレース</span><span class="sxs-lookup"><span data-stu-id="e5fa8-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="e5fa8-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e5fa8-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e5fa8-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="e5fa8-112">Administration and Diagnostics</span></span>](../index.md)
