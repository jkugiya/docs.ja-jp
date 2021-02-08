---
description: ': ICLRTask:: NeedsPriorityScheduling メソッドの詳細について説明します。'
title: ICLRTask::NeedsPriorityScheduling メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.NeedsPriorityScheduling
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::NeedsPriorityScheduling
helpviewer_keywords:
- ICLRTask::NeedsPriorityScheduling method [.NET Framework hosting]
- NeedsPriorityScheduling method [.NET Framework hosting]
ms.assetid: 9c9db3f3-26bf-4317-88de-5eb926a22a1d
topic_type:
- apiref
ms.openlocfilehash: e6e1b93b38d86259dc2f405f8512ec1063fe7b3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781767"
---
# <a name="iclrtaskneedspriorityscheduling-method"></a><span data-ttu-id="40aee-103">ICLRTask::NeedsPriorityScheduling メソッド</span><span class="sxs-lookup"><span data-stu-id="40aee-103">ICLRTask::NeedsPriorityScheduling Method</span></span>

<span data-ttu-id="40aee-104">現在のタスクが、切り替え先としてマークされている必要があるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="40aee-104">Gets a value that indicates whether the current task, which is being switched out, needs to be marked as a high priority for rescheduling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40aee-105">構文</span><span class="sxs-lookup"><span data-stu-id="40aee-105">Syntax</span></span>  
  
```cpp  
HRESULT NeedsPriorityScheduling (  
    [out] BOOL *pbNeedsPriorityScheduling  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40aee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="40aee-106">Parameters</span></span>  

 `pbNeedsPriorityRescheduling`  
 <span data-ttu-id="40aee-107">[out] `true` 。ホストが現在のタスクインスタンスの再スケジュールをできるだけ早く試行する場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="40aee-107">[out] `true`, if the host should attempt to reschedule the current task instance as soon as possible; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40aee-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="40aee-108">Return Value</span></span>  
  
|<span data-ttu-id="40aee-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40aee-109">HRESULT</span></span>|<span data-ttu-id="40aee-110">説明</span><span class="sxs-lookup"><span data-stu-id="40aee-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="40aee-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="40aee-111">S_OK</span></span>|<span data-ttu-id="40aee-112">`NeedsPriorityRescheduling` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="40aee-112">`NeedsPriorityRescheduling` returned successfully.</span></span>|  
|<span data-ttu-id="40aee-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="40aee-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="40aee-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="40aee-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="40aee-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="40aee-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="40aee-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="40aee-116">The call timed out.</span></span>|  
|<span data-ttu-id="40aee-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="40aee-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="40aee-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="40aee-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="40aee-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="40aee-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="40aee-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="40aee-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="40aee-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="40aee-121">E_FAIL</span></span>|<span data-ttu-id="40aee-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="40aee-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="40aee-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="40aee-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="40aee-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="40aee-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40aee-125">解説</span><span class="sxs-lookup"><span data-stu-id="40aee-125">Remarks</span></span>  

 <span data-ttu-id="40aee-126">ガベージコレクターによってタスクが収集されるのを終了する場合、CLR はの値をに設定して `pbNeedsPriorityScheduling` `true` 、優先度の高い再スケジュールを示します。</span><span class="sxs-lookup"><span data-stu-id="40aee-126">In situations where the task is close to being collected by the garbage collector, the CLR sets the value of `pbNeedsPriorityScheduling` to `true`, indicating high-priority rescheduling.</span></span> <span data-ttu-id="40aee-127">これにより、ホストはタスクを迅速に再スケジュールすることができます。これにより、ガベージコレクションの遅延の可能性が最小限に抑えられ、ホストとランタイムがメモリリソースを節約できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40aee-127">This allows the host to reschedule the task quickly, thereby minimizing the potential for delays in garbage collection, and enabling the host and the runtime to cooperate in conserving memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40aee-128">要件</span><span class="sxs-lookup"><span data-stu-id="40aee-128">Requirements</span></span>  

 <span data-ttu-id="40aee-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40aee-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40aee-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="40aee-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40aee-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="40aee-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40aee-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40aee-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40aee-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="40aee-133">See also</span></span>

- [<span data-ttu-id="40aee-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40aee-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="40aee-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40aee-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="40aee-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40aee-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="40aee-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40aee-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
