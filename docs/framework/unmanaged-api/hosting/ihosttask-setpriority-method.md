---
description: '次の情報を参照してください: IHostTask:: SetPriority メソッド'
title: IHostTask::SetPriority メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
ms.openlocfilehash: c3e8fee954e5cbea2d084141a4b2d22d2fa5e95b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784640"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="7c9a4-103">IHostTask::SetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="7c9a4-103">IHostTask::SetPriority Method</span></span>

<span data-ttu-id="7c9a4-104">現在の [IHostTask](ihosttask-interface.md) インスタンスによって表されるタスクのスレッドの優先度レベルをホストが調整するように要求します。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-104">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="7c9a4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c9a4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7c9a4-106">Parameters</span></span>  

 `newPriority`  
 <span data-ttu-id="7c9a4-107">から現在のインスタンスによって表されるタスクについて、要求されたスレッドの優先順位値を表す整数 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-107">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c9a4-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="7c9a4-108">Return Value</span></span>  
  
|<span data-ttu-id="7c9a4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c9a4-109">HRESULT</span></span>|<span data-ttu-id="7c9a4-110">説明</span><span class="sxs-lookup"><span data-stu-id="7c9a4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c9a4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c9a4-111">S_OK</span></span>|<span data-ttu-id="7c9a4-112">`SetPriority` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-112">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="7c9a4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c9a4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c9a4-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c9a4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c9a4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c9a4-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-116">The call timed out.</span></span>|  
|<span data-ttu-id="7c9a4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c9a4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c9a4-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c9a4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c9a4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c9a4-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c9a4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c9a4-121">E_FAIL</span></span>|<span data-ttu-id="7c9a4-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c9a4-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c9a4-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c9a4-125">解説</span><span class="sxs-lookup"><span data-stu-id="7c9a4-125">Remarks</span></span>  

 <span data-ttu-id="7c9a4-126">スレッドには、スレッドの優先度レベルに基づいたラウンドロビンシステムを使用した処理時間が与えられます。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-126">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="7c9a4-127">`SetPriority` CLR が現在のタスクに対して、そのスレッドの優先度レベルを設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-127">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="7c9a4-128">次の `newPriority` 値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-128">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="7c9a4-129">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="7c9a4-129">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="7c9a4-130">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="7c9a4-130">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="7c9a4-131">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="7c9a4-131">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="7c9a4-132">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="7c9a4-132">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="7c9a4-133">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="7c9a4-133">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="7c9a4-134">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="7c9a4-134">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="7c9a4-135">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="7c9a4-135">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="7c9a4-136">CLR は `SetPriority` 、の値 <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> がユーザーコードによって変更されたときにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-136">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="7c9a4-137">ホストは、スレッドの優先度割り当てに対して独自のアルゴリズムを定義でき、この要求を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-137">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c9a4-138">`SetPriority` では、スレッドの優先度レベルが変更されたかどうかは報告されません。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-138">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="7c9a4-139">[IHostTask:: GetPriority](ihosttask-getpriority-method.md)を呼び出して、タスクのスレッド優先度レベルの値を決定します。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-139">Call [IHostTask::GetPriority](ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="7c9a4-140">スレッドの優先度レベルの値は、Win32 関数によって定義され `SetThreadPriority` ます。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-140">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="7c9a4-141">スレッドの優先順位の詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-141">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9a4-142">要件</span><span class="sxs-lookup"><span data-stu-id="7c9a4-142">Requirements</span></span>  

 <span data-ttu-id="7c9a4-143">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7c9a4-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9a4-144">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7c9a4-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c9a4-145">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7c9a4-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c9a4-146">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9a4-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9a4-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c9a4-147">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="7c9a4-148">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c9a4-148">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7c9a4-149">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c9a4-149">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7c9a4-150">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c9a4-150">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7c9a4-151">GetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="7c9a4-151">GetPriority Method</span></span>](ihosttask-getpriority-method.md)
- [<span data-ttu-id="7c9a4-152">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7c9a4-152">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
