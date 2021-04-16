---
description: '詳細情報: System.ServiceModel.ManualFlowThrottleLimitReached'
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 90c911131259ea02023eb05a97793f00f3eb43fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99633336"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="c7887-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="c7887-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>

<span data-ttu-id="c7887-104">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="c7887-104">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="c7887-105">説明</span><span class="sxs-lookup"><span data-stu-id="c7887-105">Description</span></span>  

 <span data-ttu-id="c7887-106">システムは ManualFlowControlLimit スロットルに設定された制限値に達しました。</span><span class="sxs-lookup"><span data-stu-id="c7887-106">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="c7887-107">スロットル値を変更するには、ServiceHost または InstanceContext の ManualFlowControlLimit プロパティを適宜変更します。</span><span class="sxs-lookup"><span data-stu-id="c7887-107">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="c7887-108">このトレースは、マニュアル フロー制御制限が初めて 0 に減少したときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c7887-108">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="c7887-109">それ以降は、0 に変更されてもトレースされません。</span><span class="sxs-lookup"><span data-stu-id="c7887-109">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="c7887-110">インスタンス コンテキストに対するフロー制御制限は、コンテキストごとに 1 回トレースされます。</span><span class="sxs-lookup"><span data-stu-id="c7887-110">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7887-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7887-111">See also</span></span>

- [<span data-ttu-id="c7887-112">トレース</span><span class="sxs-lookup"><span data-stu-id="c7887-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="c7887-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c7887-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c7887-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="c7887-114">Administration and Diagnostics</span></span>](../index.md)
