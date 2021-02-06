---
description: '詳細については、次を参照してください: System.servicemodel.。'
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 1b3c15594611726fd4872197b97ad4ed56c085c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635260"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="fd7e4-103">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="fd7e4-103">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>

<span data-ttu-id="fd7e4-104">プールされた接続を再使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="fd7e4-104">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="fd7e4-105">指定されたタイムアウト期間内に再試行します。</span><span class="sxs-lookup"><span data-stu-id="fd7e4-105">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fd7e4-106">説明</span><span class="sxs-lookup"><span data-stu-id="fd7e4-106">Description</span></span>  

 <span data-ttu-id="fd7e4-107">この情報トレースは、プールされた接続の再使用を試みている間にエラーが発生したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="fd7e4-107">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="fd7e4-108">これは、プールされた接続に互換性がない、接続の準備ができていない、または接続がアクティブなままであるために発生します。</span><span class="sxs-lookup"><span data-stu-id="fd7e4-108">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="fd7e4-109">所定のタイムアウト期間内に、他のプールされた接続を再使用する試みがさらに行われ、使用可能な接続が見つからない場合には、新しい接続が作成されます。</span><span class="sxs-lookup"><span data-stu-id="fd7e4-109">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd7e4-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd7e4-110">See also</span></span>

- [<span data-ttu-id="fd7e4-111">トレース</span><span class="sxs-lookup"><span data-stu-id="fd7e4-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="fd7e4-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fd7e4-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fd7e4-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="fd7e4-113">Administration and Diagnostics</span></span>](../index.md)
