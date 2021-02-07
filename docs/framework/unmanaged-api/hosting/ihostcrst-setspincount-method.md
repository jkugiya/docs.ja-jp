---
description: '詳細について: IHostCrst:: SetSpinCount メソッド'
title: IHostCrst::SetSpinCount メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: f04281d2649f210e64fc4c0585eb7d52be3e8ec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721230"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="41fbb-103">IHostCrst::SetSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="41fbb-103">IHostCrst::SetSpinCount Method</span></span>

<span data-ttu-id="41fbb-104">現在の [IHostCrst](ihostcrst-interface.md) インスタンスのスピンカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="41fbb-104">Sets the spin count for the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41fbb-105">構文</span><span class="sxs-lookup"><span data-stu-id="41fbb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41fbb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41fbb-106">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="41fbb-107">から現在のインスタンスの新しいスピンカウント `IHostCrst` 。</span><span class="sxs-lookup"><span data-stu-id="41fbb-107">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41fbb-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="41fbb-108">Return Value</span></span>  
  
|<span data-ttu-id="41fbb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="41fbb-109">HRESULT</span></span>|<span data-ttu-id="41fbb-110">説明</span><span class="sxs-lookup"><span data-stu-id="41fbb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41fbb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="41fbb-111">S_OK</span></span>|<span data-ttu-id="41fbb-112">`SetSpinCount` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="41fbb-112">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="41fbb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="41fbb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="41fbb-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="41fbb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="41fbb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="41fbb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="41fbb-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="41fbb-116">The call timed out.</span></span>|  
|<span data-ttu-id="41fbb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="41fbb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="41fbb-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="41fbb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="41fbb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="41fbb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="41fbb-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="41fbb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="41fbb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="41fbb-121">E_FAIL</span></span>|<span data-ttu-id="41fbb-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="41fbb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="41fbb-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="41fbb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="41fbb-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="41fbb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41fbb-125">解説</span><span class="sxs-lookup"><span data-stu-id="41fbb-125">Remarks</span></span>  

 <span data-ttu-id="41fbb-126">マルチプロセッサシステムでは、現在のインスタンスによって表されるクリティカルセクション `IHostCrst` が使用できない場合、呼び出し元のスレッドは、 `dwSpinCount` クリティカルセクションに関連付けられているセマフォで [IHostSemaphore:: Wait](ihostsemaphore-wait-method.md) を呼び出す前に時間をスピンします。</span><span class="sxs-lookup"><span data-stu-id="41fbb-126">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="41fbb-127">スピン操作中にクリティカルセクションが解放されると、呼び出し元のスレッドは待機操作を回避します。</span><span class="sxs-lookup"><span data-stu-id="41fbb-127">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="41fbb-128">の使用方法 `dwSpinCount` は、Win32 関数で同じ名前のパラメーターを使用する場合と同じです `InitializeCriticalSectionAndSpinCount` 。</span><span class="sxs-lookup"><span data-stu-id="41fbb-128">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41fbb-129">要件</span><span class="sxs-lookup"><span data-stu-id="41fbb-129">Requirements</span></span>  

 <span data-ttu-id="41fbb-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41fbb-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41fbb-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="41fbb-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41fbb-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="41fbb-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41fbb-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41fbb-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41fbb-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="41fbb-134">See also</span></span>

- [<span data-ttu-id="41fbb-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41fbb-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="41fbb-136">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41fbb-136">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="41fbb-137">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41fbb-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
