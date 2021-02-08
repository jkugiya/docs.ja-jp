---
description: 詳細については、「IHostSyncManager インターフェイス」を参照してください。
title: IHostSyncManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: c3bd2928315567605d320c772de8ff824ad3cd09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784731"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="26c3a-103">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26c3a-103">IHostSyncManager Interface</span></span>

<span data-ttu-id="26c3a-104">Win32 同期関数を使用する代わりに、共通言語ランタイム (CLR) がホストを呼び出して同期プリミティブを作成できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-104">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="26c3a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-105">Methods</span></span>  
  
|<span data-ttu-id="26c3a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-106">Method</span></span>|<span data-ttu-id="26c3a-107">説明</span><span class="sxs-lookup"><span data-stu-id="26c3a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="26c3a-108">CreateAutoEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-108">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="26c3a-109">自動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-109">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="26c3a-110">CreateCrst メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-110">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="26c3a-111">同期のための重要なセクションオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-111">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="26c3a-112">CreateCrstWithSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-112">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="26c3a-113">同期のためにスピンカウントを持つクリティカルセクションオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-113">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="26c3a-114">CreateManualEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-114">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="26c3a-115">手動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-115">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="26c3a-116">CreateMonitorEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-116">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="26c3a-117">監視対象の自動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-117">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="26c3a-118">CreateRWLockReaderEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-118">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="26c3a-119">リーダーロックの実装のための手動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-119">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="26c3a-120">CreateRWLockWriterEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-120">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="26c3a-121">ライターロックの実装用の自動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-121">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="26c3a-122">CreateSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-122">CreateSemaphore Method</span></span>](ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="26c3a-123">CLR が待機イベントのセマフォとして使用する [IHostSemaphore](ihostsemaphore-interface.md) オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-123">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="26c3a-124">SetCLRSyncManager メソッド</span><span class="sxs-lookup"><span data-stu-id="26c3a-124">SetCLRSyncManager Method</span></span>](ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="26c3a-125">現在のインスタンスに関連付ける [ICLRSyncManager](iclrsyncmanager-interface.md) インスタンスを設定 `IHostSyncManager` します。</span><span class="sxs-lookup"><span data-stu-id="26c3a-125">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26c3a-126">解説</span><span class="sxs-lookup"><span data-stu-id="26c3a-126">Remarks</span></span>  

 <span data-ttu-id="26c3a-127">CLR は、 `IHostSyncManager` IID_IHostSyncManager のを使用して [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) メソッドを呼び出すことで、ホストのの実装を検出し `IID` ます。</span><span class="sxs-lookup"><span data-stu-id="26c3a-127">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26c3a-128">要件</span><span class="sxs-lookup"><span data-stu-id="26c3a-128">Requirements</span></span>  

 <span data-ttu-id="26c3a-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26c3a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26c3a-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="26c3a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26c3a-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="26c3a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26c3a-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26c3a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26c3a-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="26c3a-133">See also</span></span>

- [<span data-ttu-id="26c3a-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26c3a-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="26c3a-135">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26c3a-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
