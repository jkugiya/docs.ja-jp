---
description: '詳細情報: サービス: 1 秒あたりの失敗した呼び出し'
title: 'サービス : 1 秒あたりの失敗した呼び出し'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: b271d5076d0f0c89c4d33b124e0184584795466a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803361"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="3f317-103">サービス : 1 秒あたりの失敗した呼び出し</span><span class="sxs-lookup"><span data-stu-id="3f317-103">Service: Calls Failed Per Second</span></span>

<span data-ttu-id="3f317-104">カウンター名 : 1 秒あたりの失敗した呼び出し。</span><span class="sxs-lookup"><span data-stu-id="3f317-104">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3f317-105">説明</span><span class="sxs-lookup"><span data-stu-id="3f317-105">Description</span></span>  

 <span data-ttu-id="3f317-106">このサービスが 1 秒間に受信した未処理の例外を含む呼び出しの回数。</span><span class="sxs-lookup"><span data-stu-id="3f317-106">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="3f317-107">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="3f317-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3f317-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="3f317-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="3f317-109">マネージド コードでは、エラー条件が発生すると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="3f317-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="3f317-110">マネージド コードでは、エラー条件が発生すると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="3f317-110">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="3f317-111">このカウンターは、このサービスで未処理の例外が発生するたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="3f317-111">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f317-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f317-112">See also</span></span>

- [<span data-ttu-id="3f317-113">コントラクトおよびサービスのエラーの指定と処理</span><span class="sxs-lookup"><span data-stu-id="3f317-113">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
