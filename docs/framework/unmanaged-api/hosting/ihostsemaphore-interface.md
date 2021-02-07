---
description: 詳細については、「IHostSemaphore インターフェイス」を参照してください。
title: IHostSemaphore インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: 682f1f70925310e93f88f1dc314052e801a5e87b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671348"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="42df1-103">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42df1-103">IHostSemaphore Interface</span></span>

<span data-ttu-id="42df1-104">スレッド処理のためのセマフォのホストの実装を表します。</span><span class="sxs-lookup"><span data-stu-id="42df1-104">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42df1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="42df1-105">Methods</span></span>  
  
|<span data-ttu-id="42df1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="42df1-106">Method</span></span>|<span data-ttu-id="42df1-107">説明</span><span class="sxs-lookup"><span data-stu-id="42df1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42df1-108">ReleaseSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="42df1-108">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="42df1-109">現在のインスタンスの数を `IHostSemaphore` 指定された量だけ増やします。</span><span class="sxs-lookup"><span data-stu-id="42df1-109">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="42df1-110">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="42df1-110">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="42df1-111">現在の `IHostSemaphore` インスタンスが所有されるか、指定された時間が経過するまで待機するようにします。</span><span class="sxs-lookup"><span data-stu-id="42df1-111">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42df1-112">要件</span><span class="sxs-lookup"><span data-stu-id="42df1-112">Requirements</span></span>  

 <span data-ttu-id="42df1-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42df1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42df1-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="42df1-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42df1-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="42df1-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42df1-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42df1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42df1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="42df1-117">See also</span></span>

- [<span data-ttu-id="42df1-118">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42df1-118">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="42df1-119">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42df1-119">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="42df1-120">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42df1-120">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="42df1-121">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42df1-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="42df1-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42df1-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
