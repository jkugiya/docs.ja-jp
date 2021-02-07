---
description: '詳細情報: ICLRTaskManager:: CreateTask メソッド'
title: ICLRTaskManager::CreateTask メソッド
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
ms.openlocfilehash: 98a287f10a84b18579ebf2a4294cbb8a67cabc9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728614"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="593c2-103">ICLRTaskManager::CreateTask メソッド</span><span class="sxs-lookup"><span data-stu-id="593c2-103">ICLRTaskManager::CreateTask Method</span></span>

<span data-ttu-id="593c2-104">共通言語ランタイム (CLR) によって新しいタスクが作成されることを明示的に要求します。</span><span class="sxs-lookup"><span data-stu-id="593c2-104">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="593c2-105">構文</span><span class="sxs-lookup"><span data-stu-id="593c2-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="593c2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="593c2-106">Parameters</span></span>  

 `pTask`  
 <span data-ttu-id="593c2-107">入出力新しく作成された [ICLRTask](iclrtask-interface.md)のアドレスへのポインター、またはタスクを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="593c2-107">[out] A pointer to the address of a newly created [ICLRTask](iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="593c2-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="593c2-108">Return Value</span></span>  
  
|<span data-ttu-id="593c2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="593c2-109">HRESULT</span></span>|<span data-ttu-id="593c2-110">説明</span><span class="sxs-lookup"><span data-stu-id="593c2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="593c2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="593c2-111">S_OK</span></span>|<span data-ttu-id="593c2-112">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="593c2-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="593c2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="593c2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="593c2-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="593c2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="593c2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="593c2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="593c2-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="593c2-116">The call timed out.</span></span>|  
|<span data-ttu-id="593c2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="593c2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="593c2-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="593c2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="593c2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="593c2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="593c2-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="593c2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="593c2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="593c2-121">E_FAIL</span></span>|<span data-ttu-id="593c2-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="593c2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="593c2-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="593c2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="593c2-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="593c2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="593c2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="593c2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="593c2-126">要求されたリソースを割り当てるのに十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="593c2-126">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="593c2-127">解説</span><span class="sxs-lookup"><span data-stu-id="593c2-127">Remarks</span></span>  

 <span data-ttu-id="593c2-128">CLR は、初期化時、ユーザーコードが名前空間の型を使用してスレッドを作成するとき、 <xref:System.Threading> またはスレッドプールのサイズが増加したときに、新しいタスクを自動的に作成します。</span><span class="sxs-lookup"><span data-stu-id="593c2-128">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="593c2-129">また、アンマネージコードがマネージ関数を呼び出す場合にも、タスクが作成されます。</span><span class="sxs-lookup"><span data-stu-id="593c2-129">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="593c2-130">`CreateTask` CLR によって新しいタスクが作成されることをホストが明示的に要求できるようにします。</span><span class="sxs-lookup"><span data-stu-id="593c2-130">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="593c2-131">たとえば、ホストはこのメソッドを呼び出して、データ構造を事前に初期化できます。</span><span class="sxs-lookup"><span data-stu-id="593c2-131">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="593c2-132">新しいタスクは中断状態で返され、ホストが明示的に [IHostTask:: Start](ihosttask-start-method.md)を呼び出すまで中断されたままになります。</span><span class="sxs-lookup"><span data-stu-id="593c2-132">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="593c2-133">要件</span><span class="sxs-lookup"><span data-stu-id="593c2-133">Requirements</span></span>  

 <span data-ttu-id="593c2-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="593c2-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="593c2-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="593c2-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="593c2-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="593c2-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="593c2-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="593c2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="593c2-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="593c2-138">See also</span></span>

- [<span data-ttu-id="593c2-139">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="593c2-139">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="593c2-140">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="593c2-140">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="593c2-141">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="593c2-141">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="593c2-142">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="593c2-142">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
