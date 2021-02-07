---
description: '詳細情報: 1 秒あたりのキュー破棄メッセージ数'
title: 1 秒あたりの破棄されたメッセージのキュー
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: e5959b76795514dec03d6ae4d08ac248994777fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759550"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="940e4-103">1 秒あたりの破棄されたメッセージのキュー</span><span class="sxs-lookup"><span data-stu-id="940e4-103">Queue Dropped Messages Per Second</span></span>

<span data-ttu-id="940e4-104">カウンター名: 1 秒あたりの破棄されたメッセージのキュー。</span><span class="sxs-lookup"><span data-stu-id="940e4-104">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="940e4-105">説明</span><span class="sxs-lookup"><span data-stu-id="940e4-105">Description</span></span>  

 <span data-ttu-id="940e4-106">このサービスでキューに置かれたトランスポートによって 1 秒あたりに破棄されたメッセージの数です。</span><span class="sxs-lookup"><span data-stu-id="940e4-106">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="940e4-107">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="940e4-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="940e4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="940e4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
