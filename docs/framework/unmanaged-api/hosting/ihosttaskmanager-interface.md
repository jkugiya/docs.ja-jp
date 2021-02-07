---
description: 詳細については、「IHostTaskManager インターフェイス」を参照してください。
title: IHostTaskManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: 67574550ba26970189ea53b8e6bdb867fea8549b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707480"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="a6fe6-103">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6fe6-103">IHostTaskManager Interface</span></span>

<span data-ttu-id="a6fe6-104">標準のオペレーティングシステムのスレッド処理やファイバー関数を使用する代わりに、共通言語ランタイム (CLR) がホストを通じてタスクを操作できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-104">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a6fe6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-105">Methods</span></span>  
  
|<span data-ttu-id="a6fe6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-106">Method</span></span>|<span data-ttu-id="a6fe6-107">説明</span><span class="sxs-lookup"><span data-stu-id="a6fe6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a6fe6-108">BeginDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-108">BeginDelayAbort Method</span></span>](ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="a6fe6-109">マネージコードが、現在のタスクを中止できない期間を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-109">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="a6fe6-110">BeginThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-110">BeginThreadAffinity Method</span></span>](ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="a6fe6-111">マネージコードが、現在のタスクを別のオペレーティングシステムのスレッドに移動できない期間を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-111">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="a6fe6-112">CallNeedsHostHook メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-112">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="a6fe6-113">共通言語ランタイムがアンマネージ関数に対して指定された呼び出しをインライン展開できるかどうかを指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-113">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="a6fe6-114">CreateTask メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-114">CreateTask Method</span></span>](ihosttaskmanager-createtask-method.md)|<span data-ttu-id="a6fe6-115">ホストが新しいタスクを作成することを要求します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-115">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="a6fe6-116">EndDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-116">EndDelayAbort Method</span></span>](ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="a6fe6-117">を以前に呼び出した後に、マネージコードが現在のタスクを中止できない期間を終了することをホストに通知し `BeginDelayAbort` ます。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-117">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="a6fe6-118">EndThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-118">EndThreadAffinity Method</span></span>](ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="a6fe6-119">以前にを呼び出した後に、マネージコードが、現在のタスクを別のオペレーティングシステムのスレッドに移動できない期間を終了していることをホストに通知し `BeginThreadAffinity` ます。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-119">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="a6fe6-120">EnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-120">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="a6fe6-121">プラットフォーム呼び出しメソッドなどのアンマネージメソッドへの呼び出しが実行制御を CLR に返すことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-121">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="a6fe6-122">GetCurrentTask メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-122">GetCurrentTask Method</span></span>](ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="a6fe6-123">この呼び出しが行われたオペレーティングシステムスレッドで現在実行されているタスクへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-123">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="a6fe6-124">GetStackGuarantee メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-124">GetStackGuarantee Method</span></span>](ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="a6fe6-125">スタック操作が完了した後、プロセスが終了する前に使用可能であることが保証されているスタック領域の量を取得します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-125">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="a6fe6-126">LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-126">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="a6fe6-127">マネージコードがアンマネージ関数の呼び出しを実行しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-127">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="a6fe6-128">ReverseEnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-128">ReverseEnterRuntime Method</span></span>](ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="a6fe6-129">アンマネージコードから共通言語ランタイム (CLR) への呼び出しが行われていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-129">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="a6fe6-130">ReverseLeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-130">ReverseLeaveRuntime Method</span></span>](ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="a6fe6-131">コントロールが CLR から出ていること、およびマネージコードから呼び出されたアンマネージ関数を入力したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-131">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="a6fe6-132">SetCLRTaskManager メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-132">SetCLRTaskManager Method</span></span>](ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="a6fe6-133">CLR によって実装された [ICLRTaskManager](iclrtaskmanager-interface.md) インスタンスへのインターフェイスポインターをホストに提供します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-133">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="a6fe6-134">SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-134">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="a6fe6-135">CLR によって現在のタスクのロケールが変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-135">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="a6fe6-136">SetStackGuarantee メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-136">SetStackGuarantee Method</span></span>](ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="a6fe6-137">内部使用専用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-137">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="a6fe6-138">SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-138">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="a6fe6-139">現在のタスクでユーザーインターフェイスのロケールが変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-139">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="a6fe6-140">Sleep メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-140">Sleep Method</span></span>](ihosttaskmanager-sleep-method.md)|<span data-ttu-id="a6fe6-141">現在のタスクがスリープ状態になることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-141">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="a6fe6-142">SwitchToTask メソッド</span><span class="sxs-lookup"><span data-stu-id="a6fe6-142">SwitchToTask Method</span></span>](ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="a6fe6-143">現在のタスクを切り替える必要があることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-143">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6fe6-144">解説</span><span class="sxs-lookup"><span data-stu-id="a6fe6-144">Remarks</span></span>  

 <span data-ttu-id="a6fe6-145">`IHostTaskManager` CLR がタスクを作成および管理できるようにします。また、コントロールからアンマネージコードへの転送を制御するときにホストがアクションを実行できるようにしたり、コードの実行中にホストが実行できない特定のアクションを指定したりできるようにします。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-145">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6fe6-146">要件</span><span class="sxs-lookup"><span data-stu-id="a6fe6-146">Requirements</span></span>  

 <span data-ttu-id="a6fe6-147">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6fe6-147">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6fe6-148">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a6fe6-148">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6fe6-149">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a6fe6-149">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6fe6-150">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6fe6-150">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6fe6-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6fe6-151">See also</span></span>

- [<span data-ttu-id="a6fe6-152">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6fe6-152">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a6fe6-153">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6fe6-153">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a6fe6-154">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6fe6-154">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a6fe6-155">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6fe6-155">Hosting Interfaces</span></span>](hosting-interfaces.md)
