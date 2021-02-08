---
description: '詳細について: IHostSyncManager:: CreateCrstWithSpinCount メソッド'
title: IHostSyncManager::CreateCrstWithSpinCount メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
ms.openlocfilehash: 3c43f1a3d52eb7174844ecb4079cf54413f20853
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784822"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a><span data-ttu-id="576c7-103">IHostSyncManager::CreateCrstWithSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="576c7-103">IHostSyncManager::CreateCrstWithSpinCount Method</span></span>

<span data-ttu-id="576c7-104">同期のためにスピンカウントを持つクリティカルセクションオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="576c7-104">Creates a critical section object with spin count for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="576c7-105">構文</span><span class="sxs-lookup"><span data-stu-id="576c7-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="576c7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="576c7-106">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="576c7-107">からクリティカルセクションオブジェクトのスピンカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="576c7-107">[in] Specifies the spin count for the critical section object.</span></span>  
  
 `ppCrst`  
 <span data-ttu-id="576c7-108">入出力 [IHostCrst](ihostcrst-interface.md) インスタンスのアドレスへのポインター。クリティカルセクションを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="576c7-108">[out] A pointer to the address of an [IHostCrst](ihostcrst-interface.md) instance, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="576c7-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="576c7-109">Return Value</span></span>  
  
|<span data-ttu-id="576c7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="576c7-110">HRESULT</span></span>|<span data-ttu-id="576c7-111">説明</span><span class="sxs-lookup"><span data-stu-id="576c7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="576c7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="576c7-112">S_OK</span></span>|<span data-ttu-id="576c7-113">`CreateCrstWithSpinCount` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="576c7-113">`CreateCrstWithSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="576c7-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="576c7-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="576c7-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="576c7-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="576c7-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="576c7-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="576c7-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="576c7-117">The call timed out.</span></span>|  
|<span data-ttu-id="576c7-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="576c7-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="576c7-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="576c7-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="576c7-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="576c7-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="576c7-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="576c7-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="576c7-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="576c7-122">E_FAIL</span></span>|<span data-ttu-id="576c7-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="576c7-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="576c7-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="576c7-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="576c7-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="576c7-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="576c7-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="576c7-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="576c7-127">要求されたクリティカルセクションを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="576c7-127">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="576c7-128">解説</span><span class="sxs-lookup"><span data-stu-id="576c7-128">Remarks</span></span>  

 <span data-ttu-id="576c7-129">スピンカウントは、マルチプロセッサシステムでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="576c7-129">A spin count is used only on a multi-processor system.</span></span> <span data-ttu-id="576c7-130">スピンカウントは、使用できないクリティカルセクションに関連付けられているセマフォで待機操作を実行する前に、呼び出し元のスレッドがスピンする必要がある回数を指定します。</span><span class="sxs-lookup"><span data-stu-id="576c7-130">The spin count specifies the number of times a calling thread must spin before it performs a wait operation on a semaphore that is associated with an unavailable critical section.</span></span> <span data-ttu-id="576c7-131">スピン操作中にクリティカルセクションが解放されると、呼び出し元のスレッドは待機操作を回避します。</span><span class="sxs-lookup"><span data-stu-id="576c7-131">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span> <span data-ttu-id="576c7-132">`CreateCrstWithSpinCount` Win32 関数をミラー化 `InitializeCriticalSectionAndSpinCount` します。</span><span class="sxs-lookup"><span data-stu-id="576c7-132">`CreateCrstWithSpinCount` mirrors the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="576c7-133">要件</span><span class="sxs-lookup"><span data-stu-id="576c7-133">Requirements</span></span>  

 <span data-ttu-id="576c7-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="576c7-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="576c7-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="576c7-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="576c7-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="576c7-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="576c7-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="576c7-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="576c7-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="576c7-138">See also</span></span>

- [<span data-ttu-id="576c7-139">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="576c7-139">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="576c7-140">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="576c7-140">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="576c7-141">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="576c7-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
