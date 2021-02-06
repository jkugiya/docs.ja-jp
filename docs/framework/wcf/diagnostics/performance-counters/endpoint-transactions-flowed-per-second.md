---
description: '詳細情報: エンドポイント: 1 秒あたりのトランザクションフロー数'
title: 'エンドポイント : 1 秒あたりのトランザクション フロー'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 96a122b97bce703b0a0e00c6e74f72c980253652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655358"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="cddb0-103">エンドポイント : 1 秒あたりのトランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="cddb0-103">Endpoint: Transactions Flowed Per Second</span></span>

<span data-ttu-id="cddb0-104">カウンター名 : 1 秒あたりのトランザクション フロー。</span><span class="sxs-lookup"><span data-stu-id="cddb0-104">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="cddb0-105">説明</span><span class="sxs-lookup"><span data-stu-id="cddb0-105">Description</span></span>  

 <span data-ttu-id="cddb0-106">このエンドポイントでの操作に対して実行された 1 秒あたりのトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="cddb0-106">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="cddb0-107">このカウンターは、エンドポイントに送信されたメッセージにトランザクション ID が付与されている場合は常にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="cddb0-107">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="cddb0-108">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="cddb0-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cddb0-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cddb0-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
