---
description: '詳細情報: ICLRTask::Reset メソッド'
title: ICLRTask::Reset メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: d30738b98003e0543c1a2a31c7471b15811efe5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636989"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="5aee4-103">ICLRTask::Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="5aee4-103">ICLRTask::Reset Method</span></span>

<span data-ttu-id="5aee4-104">ホストでタスクを完了したことを共通言語ランタイム (CLR) に通知し、CLR で現在の [ICLRTask](iclrtask-interface.md) インスタンスを再利用して別のタスクを表すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="5aee4-104">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aee4-105">構文</span><span class="sxs-lookup"><span data-stu-id="5aee4-105">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aee4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5aee4-106">Parameters</span></span>  

 `fFull`  
 <span data-ttu-id="5aee4-107">[in] ランタイムで、現在の `ICLRTask` インスタンスに関連するセキュリティおよびロケール情報に加えて、スレッドに関連するすべての静的な値をリセットする必要がある場合は `true`。それ以外の場合は `false`。</span><span class="sxs-lookup"><span data-stu-id="5aee4-107">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="5aee4-108">値が `true` の場合、ランタイムでは、<xref:System.Threading.Thread.AllocateDataSlot%2A> または <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> を使用して格納されたデータがリセットされます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-108">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5aee4-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="5aee4-109">Return Value</span></span>  
  
|<span data-ttu-id="5aee4-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5aee4-110">HRESULT</span></span>|<span data-ttu-id="5aee4-111">説明</span><span class="sxs-lookup"><span data-stu-id="5aee4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5aee4-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5aee4-112">S_OK</span></span>|<span data-ttu-id="5aee4-113">`Reset` が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="5aee4-113">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="5aee4-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5aee4-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5aee4-115">CLR がプロセスに読み込まれていないか、CLR がマネージド コードを実行できないまたは呼び出しを処理できない状態です。</span><span class="sxs-lookup"><span data-stu-id="5aee4-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="5aee4-116">成功</span><span class="sxs-lookup"><span data-stu-id="5aee4-116">successfully</span></span>|  
|<span data-ttu-id="5aee4-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5aee4-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5aee4-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5aee4-118">The call timed out.</span></span>|  
|<span data-ttu-id="5aee4-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5aee4-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5aee4-120">呼び出し元はロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5aee4-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5aee4-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5aee4-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5aee4-122">ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。</span><span class="sxs-lookup"><span data-stu-id="5aee4-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5aee4-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5aee4-123">E_FAIL</span></span>|<span data-ttu-id="5aee4-124">不明な壊滅的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5aee4-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5aee4-125">メソッドにより E_FAIL が返されると、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5aee4-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5aee4-126">ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aee4-127">解説</span><span class="sxs-lookup"><span data-stu-id="5aee4-127">Remarks</span></span>  

 <span data-ttu-id="5aee4-128">CLR では、以前に作成された `ICLRTask` インスタンスをリサイクルして、新しいタスクが必要になるたびに新しいインスタンスを繰り返し作成するオーバーヘッドを回避することができます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-128">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="5aee4-129">ホストでは、タスクを完了したときに [ICLRTask::ExitTask](iclrtask-exittask-method.md) ではなく `ICLRTask::Reset` を呼び出すことで、この機能が有効にされます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-129">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="5aee4-130">`ICLRTask` インスタンスの通常のライフサイクルの概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5aee4-130">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="5aee4-131">ランタイムで新しい `ICLRTask` インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-131">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="5aee4-132">ランタイムで [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) が呼び出され、現在のホスト タスクへの参照が取得されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-132">The runtime calls [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="5aee4-133">ランタイムで、新しいインスタンスをホスト タスクに関連付けるために、[IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-133">The runtime calls [IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="5aee4-134">タスクが実行され、完了します。</span><span class="sxs-lookup"><span data-stu-id="5aee4-134">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="5aee4-135">ホストで、`ICLRTask::ExitTask` を呼び出すことによってタスクが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-135">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="5aee4-136">`Reset` では、このシナリオが次の 2 つの方法で変更されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-136">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="5aee4-137">上記の手順 5 では、ホストで `Reset` が呼び出されてタスクがクリーンな状態にリセットされた後、関連する [IHostTask](ihosttask-interface.md) インスタンスから `ICLRTask` インスタンスが切り離されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-137">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](ihosttask-interface.md) instance.</span></span> <span data-ttu-id="5aee4-138">必要であれば、ホストで `IHostTask` インスタンスをキャッシュして再利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-138">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="5aee4-139">上記の手順 1 では、ランタイムで新しいインスタンスを作成する代わりに、キャッシュからリサイクルされた `ICLRTask` が取得されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-139">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="5aee4-140">この方法は、ホストに再利用可能なワーカー タスクのプールがある場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="5aee4-140">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="5aee4-141">ホストでは、`IHostTask` インスタンスの 1 つが破棄されると、`ExitTask` を呼び出すことによって、対応する `ICLRTask` が破棄されます。</span><span class="sxs-lookup"><span data-stu-id="5aee4-141">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aee4-142">必要条件</span><span class="sxs-lookup"><span data-stu-id="5aee4-142">Requirements</span></span>  

 <span data-ttu-id="5aee4-143">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5aee4-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aee4-144">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5aee4-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5aee4-145">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="5aee4-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5aee4-146">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aee4-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aee4-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="5aee4-147">See also</span></span>

- [<span data-ttu-id="5aee4-148">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5aee4-148">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5aee4-149">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5aee4-149">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5aee4-150">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5aee4-150">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5aee4-151">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5aee4-151">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
