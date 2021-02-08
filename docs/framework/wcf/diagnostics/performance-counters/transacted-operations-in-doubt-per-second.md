---
description: 詳細については、1秒あたりのインダウトのトランザクション操作に関するページを参照してください。
title: 1 秒あたりの不明なトランザクション操作
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: e4f8b8c9db1c92ea4348763cdc4a633f058dbaf2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771094"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="88f77-103">1 秒あたりの不明なトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="88f77-103">Transacted Operations In Doubt Per Second</span></span>

<span data-ttu-id="88f77-104">カウンター名 : 1 秒あたりの不明なトランザクション操作。</span><span class="sxs-lookup"><span data-stu-id="88f77-104">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="88f77-105">説明</span><span class="sxs-lookup"><span data-stu-id="88f77-105">Description</span></span>  

 <span data-ttu-id="88f77-106">このサービスでの 1 秒あたりの結果が不明なランザクション操作の数です。</span><span class="sxs-lookup"><span data-stu-id="88f77-106">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="88f77-107">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="88f77-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="88f77-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="88f77-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
