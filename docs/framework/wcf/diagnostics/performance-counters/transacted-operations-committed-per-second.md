---
description: '詳細情報: 1 秒あたりのコミットされたトランザクション操作'
title: 1 秒あたりのコミットされたトランザクション操作
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 019906cccc527a032d91eb20328eddbb6d9aada8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655085"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="57513-103">1 秒あたりのコミットされたトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="57513-103">Transacted Operations Committed Per Second</span></span>

<span data-ttu-id="57513-104">カウンター名 : 1 秒あたりのコミットされたトランザクション操作。</span><span class="sxs-lookup"><span data-stu-id="57513-104">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="57513-105">説明</span><span class="sxs-lookup"><span data-stu-id="57513-105">Description</span></span>  

 <span data-ttu-id="57513-106">1 秒あたりに、このサービスでコミットされたトランザクション操作の数です。</span><span class="sxs-lookup"><span data-stu-id="57513-106">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="57513-107">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="57513-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="57513-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="57513-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
