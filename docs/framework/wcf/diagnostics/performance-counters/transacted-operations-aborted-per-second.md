---
description: '詳細情報: 1 秒あたりの中断されたトランザクション操作'
title: 1 秒あたりの中止されたトランザクション操作
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: de130c18e065e48ed7ac18442b2bc5f82c2f6861
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99771198"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="3d8e1-103">1 秒あたりの中止されたトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="3d8e1-103">Transacted Operations Aborted Per Second</span></span>

<span data-ttu-id="3d8e1-104">カウンター名 : 1 秒あたりの中止されたトランザクション処理数。</span><span class="sxs-lookup"><span data-stu-id="3d8e1-104">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3d8e1-105">説明</span><span class="sxs-lookup"><span data-stu-id="3d8e1-105">Description</span></span>  

 <span data-ttu-id="3d8e1-106">1 秒あたりに、このサービスで中止されたトランザクション処理の数です。</span><span class="sxs-lookup"><span data-stu-id="3d8e1-106">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="3d8e1-107">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="3d8e1-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3d8e1-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="3d8e1-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
