---
description: '詳細について: ICLRTask:: Reset メソッド'
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
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636989"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="48a36-103">ICLRTask::Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="48a36-103">ICLRTask::Reset Method</span></span>

<span data-ttu-id="48a36-104">ホストがタスクを完了したことを共通言語ランタイム (CLR) に通知し、CLR が現在の [ICLRTask](iclrtask-interface.md) インスタンスを再利用して別のタスクを表すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="48a36-104">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48a36-105">構文</span><span class="sxs-lookup"><span data-stu-id="48a36-105">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48a36-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48a36-106">Parameters</span></span>  

 `fFull`  
 <span data-ttu-id="48a36-107">[in] `true` 。ランタイムが、現在のインスタンスに関連するセキュリティおよびロケール情報に加えて、スレッドに関連するすべての静的な値をリセットする必要がある場合は `ICLRTask` 。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="48a36-107">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="48a36-108">値がの場合 `true` 、ランタイムはまたはを使用して格納されたデータをリセットし <xref:System.Threading.Thread.AllocateDataSlot%2A> <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="48a36-108">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48a36-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="48a36-109">Return Value</span></span>  
  
|<span data-ttu-id="48a36-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="48a36-110">HRESULT</span></span>|<span data-ttu-id="48a36-111">説明</span><span class="sxs-lookup"><span data-stu-id="48a36-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="48a36-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="48a36-112">S_OK</span></span>|<span data-ttu-id="48a36-113">`Reset` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="48a36-113">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="48a36-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="48a36-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="48a36-115">CLR がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しを処理できません。</span><span class="sxs-lookup"><span data-stu-id="48a36-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="48a36-116">なく</span><span class="sxs-lookup"><span data-stu-id="48a36-116">successfully</span></span>|  
|<span data-ttu-id="48a36-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="48a36-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="48a36-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="48a36-118">The call timed out.</span></span>|  
|<span data-ttu-id="48a36-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="48a36-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="48a36-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="48a36-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="48a36-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="48a36-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="48a36-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="48a36-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="48a36-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="48a36-123">E_FAIL</span></span>|<span data-ttu-id="48a36-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="48a36-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="48a36-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="48a36-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="48a36-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="48a36-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48a36-127">解説</span><span class="sxs-lookup"><span data-stu-id="48a36-127">Remarks</span></span>  

 <span data-ttu-id="48a36-128">CLR では、 `ICLRTask` 新しいタスクが必要になるたびに新しいインスタンスを繰り返し作成するオーバーヘッドを回避するために、以前に作成されたインスタンスをリサイクルできます。</span><span class="sxs-lookup"><span data-stu-id="48a36-128">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="48a36-129">ホストは、 `ICLRTask::Reset` タスクを完了したときに、 [ICLRTask:: exittask](iclrtask-exittask-method.md) ではなくを呼び出すことにより、この機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="48a36-129">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="48a36-130">インスタンスの通常のライフサイクルの概要を次に示し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="48a36-130">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="48a36-131">ランタイムは、新しいインスタンスを作成し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="48a36-131">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="48a36-132">ランタイムは、 [IHostTaskManager:: GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) を呼び出して、現在のホストタスクへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="48a36-132">The runtime calls [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="48a36-133">ランタイムは、新しいインスタンスをホストタスクに関連付けるために、 [IHostTask:: SetCLRTask](ihosttask-setclrtask-method.md) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="48a36-133">The runtime calls [IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="48a36-134">タスクが実行され、完了します。</span><span class="sxs-lookup"><span data-stu-id="48a36-134">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="48a36-135">ホストは、を呼び出すことによってタスクを破棄し `ICLRTask::ExitTask` ます。</span><span class="sxs-lookup"><span data-stu-id="48a36-135">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="48a36-136">`Reset` では、このシナリオを次の2つの方法で変更します。</span><span class="sxs-lookup"><span data-stu-id="48a36-136">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="48a36-137">上記の手順5では、ホストがを呼び出して `Reset` タスクをクリーンな状態にリセットし、その `ICLRTask` インスタンスを関連する [IHostTask](ihosttask-interface.md) インスタンスから切り離します。</span><span class="sxs-lookup"><span data-stu-id="48a36-137">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](ihosttask-interface.md) instance.</span></span> <span data-ttu-id="48a36-138">必要に応じて、ホストはインスタンスをキャッシュして再利用することもでき `IHostTask` ます。</span><span class="sxs-lookup"><span data-stu-id="48a36-138">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="48a36-139">上記の手順 1. では、ランタイムは、 `ICLRTask` 新しいインスタンスを作成する代わりに、キャッシュからリサイクルしたを取得します。</span><span class="sxs-lookup"><span data-stu-id="48a36-139">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="48a36-140">この方法は、ホストに再利用可能なワーカータスクのプールがある場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="48a36-140">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="48a36-141">ホストがそのインスタンスの1つを破棄すると、を `IHostTask` `ICLRTask` 呼び出すことによって、対応するを破棄し `ExitTask` ます。</span><span class="sxs-lookup"><span data-stu-id="48a36-141">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48a36-142">要件</span><span class="sxs-lookup"><span data-stu-id="48a36-142">Requirements</span></span>  

 <span data-ttu-id="48a36-143">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48a36-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48a36-144">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="48a36-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48a36-145">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="48a36-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48a36-146">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48a36-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a36-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="48a36-147">See also</span></span>

- [<span data-ttu-id="48a36-148">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48a36-148">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="48a36-149">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48a36-149">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="48a36-150">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48a36-150">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="48a36-151">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48a36-151">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
