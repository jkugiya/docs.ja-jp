---
description: 詳細については、「IHostManualEvent インターフェイス」を参照してください。
title: IHostManualEvent インターフェイス
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
ms.openlocfilehash: 1c70935568b9ff4080fd5bcdc372c02d354aa06f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708155"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="8bade-103">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bade-103">IHostManualEvent Interface</span></span>

<span data-ttu-id="8bade-104">手動リセットイベントの表現のホストの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="8bade-104">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8bade-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8bade-105">Methods</span></span>  
  
|<span data-ttu-id="8bade-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="8bade-106">Method</span></span>|<span data-ttu-id="8bade-107">説明</span><span class="sxs-lookup"><span data-stu-id="8bade-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8bade-108">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="8bade-108">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="8bade-109">現在の `IHostManualEvent` インスタンスをシグナル状態以外の状態にリセットします。</span><span class="sxs-lookup"><span data-stu-id="8bade-109">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="8bade-110">Set メソッド</span><span class="sxs-lookup"><span data-stu-id="8bade-110">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="8bade-111">現在の `IHostManualEvent` インスタンスをシグナル状態に設定します。</span><span class="sxs-lookup"><span data-stu-id="8bade-111">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="8bade-112">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="8bade-112">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="8bade-113">現在の `IHostManualEvent` インスタンスが所有されるか、指定された時間が経過するまで待機するようにします。</span><span class="sxs-lookup"><span data-stu-id="8bade-113">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bade-114">要件</span><span class="sxs-lookup"><span data-stu-id="8bade-114">Requirements</span></span>  

 <span data-ttu-id="8bade-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8bade-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bade-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8bade-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8bade-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8bade-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bade-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bade-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bade-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bade-119">See also</span></span>

- [<span data-ttu-id="8bade-120">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bade-120">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8bade-121">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bade-121">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8bade-122">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bade-122">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="8bade-123">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bade-123">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="8bade-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bade-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
