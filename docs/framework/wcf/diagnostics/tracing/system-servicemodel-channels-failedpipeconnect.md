---
description: 詳細については、「FailedPipeConnect」を参照してください。
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: dbbb3ba2848eaefe70a6d6308daecf84e0a8c7a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644477"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="afbaf-103">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="afbaf-103">System.ServiceModel.Channels.FailedPipeConnect</span></span>

<span data-ttu-id="afbaf-104">名前付きパイプ エンドポイントに接続しようとして失敗しました。</span><span class="sxs-lookup"><span data-stu-id="afbaf-104">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="afbaf-105">指定されたタイムアウト期間内に再試行します。</span><span class="sxs-lookup"><span data-stu-id="afbaf-105">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="afbaf-106">説明</span><span class="sxs-lookup"><span data-stu-id="afbaf-106">Description</span></span>  

 <span data-ttu-id="afbaf-107">この情報トレースは、名前付きパイプ エンドポイントへの接続に失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="afbaf-107">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="afbaf-108">これは、名前付きパイプ エンドポイントが見つからなかったか、ビジーであった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="afbaf-108">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="afbaf-109">接続に成功するか、OpenTimeout の有効期間が切れるまで、短い間隔を置いて再試行が繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="afbaf-109">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbaf-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="afbaf-110">See also</span></span>

- [<span data-ttu-id="afbaf-111">トレース</span><span class="sxs-lookup"><span data-stu-id="afbaf-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="afbaf-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="afbaf-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="afbaf-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="afbaf-113">Administration and Diagnostics</span></span>](../index.md)
