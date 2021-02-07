---
description: '詳細情報: 1 秒あたりの失敗した呼び出し'
title: 1 秒あたりの失敗した呼び出し
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 3961754eb73743a1213922f7c9e1bd164334cd6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759719"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="5c2e1-103">1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="5c2e1-103">Calls Failed Per Second</span></span>

<span data-ttu-id="5c2e1-104">カウンター名 : 1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="5c2e1-104">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="5c2e1-105">説明</span><span class="sxs-lookup"><span data-stu-id="5c2e1-105">Description</span></span>  

 <span data-ttu-id="5c2e1-106">1 秒間にこの操作で未処理の例外が発生した呼び出しの回数です。</span><span class="sxs-lookup"><span data-stu-id="5c2e1-106">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="5c2e1-107">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="5c2e1-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5c2e1-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="5c2e1-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="5c2e1-109">このカウンターは、この操作でハンドルされない例外が発生するたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="5c2e1-109">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c2e1-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c2e1-110">See also</span></span>

- [<span data-ttu-id="5c2e1-111">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="5c2e1-111">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
