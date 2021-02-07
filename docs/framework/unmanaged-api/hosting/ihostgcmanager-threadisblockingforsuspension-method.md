---
description: '詳細について: IHostGCManager:: ThreadIsBlockingForSuspension メソッド'
title: IHostGCManager::ThreadIsBlockingForSuspension メソッド
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
ms.openlocfilehash: 9cb07b80fa9aad1ac289bc5a3abb5a4760f2bfc9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708639"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="f1e9f-103">IHostGCManager::ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="f1e9f-103">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="f1e9f-104">メソッド呼び出しが行われたスレッドがガベージコレクションに対してブロックされようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-104">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e9f-105">構文</span><span class="sxs-lookup"><span data-stu-id="f1e9f-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f1e9f-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="f1e9f-106">Return Value</span></span>  
  
|<span data-ttu-id="f1e9f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1e9f-107">HRESULT</span></span>|<span data-ttu-id="f1e9f-108">説明</span><span class="sxs-lookup"><span data-stu-id="f1e9f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1e9f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1e9f-109">S_OK</span></span>|<span data-ttu-id="f1e9f-110">`ThreadIsBlockingForSuspension` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-110">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="f1e9f-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f1e9f-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f1e9f-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f1e9f-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f1e9f-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f1e9f-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-114">The call timed out.</span></span>|  
|<span data-ttu-id="f1e9f-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f1e9f-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f1e9f-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f1e9f-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f1e9f-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f1e9f-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f1e9f-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f1e9f-119">E_FAIL</span></span>|<span data-ttu-id="f1e9f-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f1e9f-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f1e9f-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1e9f-123">解説</span><span class="sxs-lookup"><span data-stu-id="f1e9f-123">Remarks</span></span>  

 <span data-ttu-id="f1e9f-124">CLR は、通常、 `ThreadIsBlockForSuspension` ガベージコレクションの準備としてメソッドを呼び出し、ホストがアンマネージタスクのスレッドを再スケジュールできるようにします。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-124">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f1e9f-125">ホストは、を呼び出した後にのみタスクを再スケジュールでき `ThreadIsBlockingForSuspension` ます。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-125">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="f1e9f-126">ランタイムが [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md)を呼び出した後、ホストはタスクを再スケジュールする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-126">After the runtime calls [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1e9f-127">要件</span><span class="sxs-lookup"><span data-stu-id="f1e9f-127">Requirements</span></span>  

 <span data-ttu-id="f1e9f-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1e9f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1e9f-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f1e9f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1e9f-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f1e9f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1e9f-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1e9f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e9f-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1e9f-132">See also</span></span>

- [<span data-ttu-id="f1e9f-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1e9f-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f1e9f-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1e9f-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f1e9f-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1e9f-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f1e9f-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1e9f-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="f1e9f-137">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1e9f-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
