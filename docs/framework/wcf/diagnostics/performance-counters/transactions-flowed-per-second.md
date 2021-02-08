---
description: 詳細については、1秒あたりのトランザクションフロー
title: 1 秒あたりのトランザクション フロー
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: f37c79e89efb8a013719f44350772919b7222a61
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771003"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="cc6b8-103">1 秒あたりのトランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="cc6b8-103">Transactions Flowed Per Second</span></span>

<span data-ttu-id="cc6b8-104">カウンター名 : 1 秒あたりのトランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="cc6b8-104">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="cc6b8-105">説明</span><span class="sxs-lookup"><span data-stu-id="cc6b8-105">Description</span></span>  

 <span data-ttu-id="cc6b8-106">この操作に対して実行された 1 秒あたりのトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="cc6b8-106">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="cc6b8-107">このカウンターは、操作に送信されたメッセージにトランザクション ID が存在する場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="cc6b8-107">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="cc6b8-108">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="cc6b8-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="cc6b8-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="cc6b8-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
