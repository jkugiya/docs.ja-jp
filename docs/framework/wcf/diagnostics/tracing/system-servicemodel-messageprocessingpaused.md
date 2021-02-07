---
description: 詳細については、「System.servicemodel」を参照してください。
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 77e4742bc5617904136b2ddd9cb90fe886d38b10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716181"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="bcc4c-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="bcc4c-103">System.ServiceModel.MessageProcessingPaused</span></span>

<span data-ttu-id="bcc4c-104">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="bcc4c-104">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="bcc4c-105">説明</span><span class="sxs-lookup"><span data-stu-id="bcc4c-105">Description</span></span>  

 <span data-ttu-id="bcc4c-106">メッセージの処理中にスレッドが切り替わりました。</span><span class="sxs-lookup"><span data-stu-id="bcc4c-106">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="bcc4c-107">メッセージ処理は、次の理由によって一時停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="bcc4c-107">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="bcc4c-108">ConcurrencyMode が単一または再入可能で、サービスが別のメッセージを処理している。</span><span class="sxs-lookup"><span data-stu-id="bcc4c-108">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="bcc4c-109">トランザクションが有効で、サービスが別のトランザクションを処理している。</span><span class="sxs-lookup"><span data-stu-id="bcc4c-109">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="bcc4c-110">同期コンテキストが最新ではない。</span><span class="sxs-lookup"><span data-stu-id="bcc4c-110">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcc4c-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcc4c-111">See also</span></span>

- [<span data-ttu-id="bcc4c-112">トレース</span><span class="sxs-lookup"><span data-stu-id="bcc4c-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="bcc4c-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="bcc4c-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="bcc4c-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="bcc4c-114">Administration and Diagnostics</span></span>](../index.md)
