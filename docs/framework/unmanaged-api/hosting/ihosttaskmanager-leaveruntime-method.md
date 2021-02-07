---
description: '詳細について: IHostTaskManager:: 最小 Veruntime メソッド'
title: IHostTaskManager::LeaveRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
ms.openlocfilehash: 7b18bdc17b9cfd52b68309a07c6714fd1efa66cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707438"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a><span data-ttu-id="d4e0f-103">IHostTaskManager::LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="d4e0f-103">IHostTaskManager::LeaveRuntime Method</span></span>

<span data-ttu-id="d4e0f-104">現在実行中のタスクが共通言語ランタイム (CLR) を終了しようとしていることをホストに通知し、アンマネージコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-104">Notifies the host that the currently executing task is about to leave the common language runtime (CLR) and enter unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d4e0f-105">[IHostTaskManager:: EnterRuntime](ihosttaskmanager-enterruntime-method.md)への対応する呼び出しは、現在実行中のタスクがマネージコードを再要求していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-105">A corresponding call to [IHostTaskManager::EnterRuntime](ihosttaskmanager-enterruntime-method.md) notifies the host that the currently executing task is reentering managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e0f-106">構文</span><span class="sxs-lookup"><span data-stu-id="d4e0f-106">Syntax</span></span>  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4e0f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4e0f-107">Parameters</span></span>  

 `target`  
 <span data-ttu-id="d4e0f-108">から呼び出されるアンマネージ関数の、マップされた移植可能な実行可能ファイル内のアドレス。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-108">[in] The address within the mapped portable executable file of the unmanaged function to be called.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4e0f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d4e0f-109">Return Value</span></span>  
  
|<span data-ttu-id="d4e0f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4e0f-110">HRESULT</span></span>|<span data-ttu-id="d4e0f-111">説明</span><span class="sxs-lookup"><span data-stu-id="d4e0f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4e0f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4e0f-112">S_OK</span></span>|<span data-ttu-id="d4e0f-113">`LeaveRuntime` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-113">`LeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="d4e0f-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d4e0f-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d4e0f-115">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d4e0f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d4e0f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d4e0f-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-117">The call timed out.</span></span>|  
|<span data-ttu-id="d4e0f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d4e0f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d4e0f-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d4e0f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d4e0f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d4e0f-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d4e0f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4e0f-122">E_FAIL</span></span>|<span data-ttu-id="d4e0f-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d4e0f-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d4e0f-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d4e0f-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d4e0f-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d4e0f-127">要求された割り当てを完了するために必要なメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-127">Not enough memory is available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4e0f-128">解説</span><span class="sxs-lookup"><span data-stu-id="d4e0f-128">Remarks</span></span>  

 <span data-ttu-id="d4e0f-129">アンマネージコードとの間の呼び出しシーケンスは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-129">Call sequences to and from unmanaged code can be nested.</span></span> <span data-ttu-id="d4e0f-130">たとえば、次の一覧は、 `LeaveRuntime` 、 [IHostTaskManager:: ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)、 [IHostTaskManager:: ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)に対する呼び出しのシーケンスによって、 `IHostTaskManager::EnterRuntime` ホストが入れ子になったレイヤーを識別できるようにする仮定の状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-130">For example, the list below describes a hypothetical situation in which the sequence of calls to `LeaveRuntime`, [IHostTaskManager::ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager::ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md), and `IHostTaskManager::EnterRuntime` allows the host to identify the nested layers.</span></span>  
  
|<span data-ttu-id="d4e0f-131">操作</span><span class="sxs-lookup"><span data-stu-id="d4e0f-131">Action</span></span>|<span data-ttu-id="d4e0f-132">対応するメソッド呼び出し</span><span class="sxs-lookup"><span data-stu-id="d4e0f-132">Corresponding Method Call</span></span>|  
|------------|-------------------------------|  
|<span data-ttu-id="d4e0f-133">マネージ Visual Basic 実行可能ファイルは、プラットフォーム呼び出しを使用して C で記述されたアンマネージ関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-133">A managed Visual Basic executable calls an unmanaged function written in C by using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="d4e0f-134">アンマネージ C 関数は、C# で記述されたマネージ DLL 内のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-134">The unmanaged C function calls a method in a managed DLL written in C#.</span></span>|`IHostTaskManager::ReverseEnterRuntime`|  
|<span data-ttu-id="d4e0f-135">マネージ C# 関数は、C で記述された別のアンマネージ関数を呼び出します。これは、プラットフォーム呼び出しを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-135">The managed C# function calls another unmanaged function written in C, also using platform invoke.</span></span>|`IHostTaskManager::LeaveRuntime`|  
|<span data-ttu-id="d4e0f-136">2番目のアンマネージ関数は、C# 関数に実行を返します。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-136">The second unmanaged function returns execution to the C# function.</span></span>|`IHostTaskManager::EnterRuntime`|  
|<span data-ttu-id="d4e0f-137">C# 関数は、最初のアンマネージ関数に実行を返します。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-137">The C# function returns execution to the first unmanaged function.</span></span>|`IHostTaskManager::ReverseLeaveRuntime`|  
|<span data-ttu-id="d4e0f-138">最初のアンマネージ関数は、実行を Visual Basic プログラムに返します。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-138">The first unmanaged function returns execution to the Visual Basic program.</span></span>|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a><span data-ttu-id="d4e0f-139">要件</span><span class="sxs-lookup"><span data-stu-id="d4e0f-139">Requirements</span></span>  

 <span data-ttu-id="d4e0f-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4e0f-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4e0f-141">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d4e0f-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4e0f-142">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d4e0f-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4e0f-143">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4e0f-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e0f-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4e0f-144">See also</span></span>

- [<span data-ttu-id="d4e0f-145">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4e0f-145">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d4e0f-146">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4e0f-146">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d4e0f-147">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4e0f-147">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d4e0f-148">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4e0f-148">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
