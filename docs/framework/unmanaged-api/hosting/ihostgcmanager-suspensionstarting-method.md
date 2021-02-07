---
description: '詳細について: IHostGCManager:: SuspensionStarting メソッド'
title: IHostGCManager::SuspensionStarting メソッド
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
ms.openlocfilehash: 3a57d47fea735ab004fd0db293bed1ba4d3314e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708642"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="2f360-103">IHostGCManager::SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="2f360-103">IHostGCManager::SuspensionStarting Method</span></span>

<span data-ttu-id="2f360-104">ガベージコレクションを実行するために、共通言語ランタイム (CLR) がタスクの実行を中断していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="2f360-104">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f360-105">構文</span><span class="sxs-lookup"><span data-stu-id="2f360-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2f360-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="2f360-106">Return Value</span></span>  
  
|<span data-ttu-id="2f360-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f360-107">HRESULT</span></span>|<span data-ttu-id="2f360-108">説明</span><span class="sxs-lookup"><span data-stu-id="2f360-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f360-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f360-109">S_OK</span></span>|<span data-ttu-id="2f360-110">`SuspensionStarting` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="2f360-110">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="2f360-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f360-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f360-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="2f360-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f360-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f360-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f360-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2f360-114">The call timed out.</span></span>|  
|<span data-ttu-id="2f360-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f360-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f360-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2f360-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f360-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f360-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f360-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="2f360-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f360-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f360-119">E_FAIL</span></span>|<span data-ttu-id="2f360-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2f360-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f360-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2f360-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f360-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2f360-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f360-123">解説</span><span class="sxs-lookup"><span data-stu-id="2f360-123">Remarks</span></span>  

 <span data-ttu-id="2f360-124">CLR はを呼び出して `SuspensionStarting` 、ガベージコレクションが発生していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="2f360-124">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2f360-125">このタスクを再スケジュールしないでください。</span><span class="sxs-lookup"><span data-stu-id="2f360-125">Do not reschedule this task.</span></span> <span data-ttu-id="2f360-126">[ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md)が呼び出されたときに、ホストはタスクを再スケジュールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f360-126">The host must reschedule a task when [ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f360-127">要件</span><span class="sxs-lookup"><span data-stu-id="2f360-127">Requirements</span></span>  

 <span data-ttu-id="2f360-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f360-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f360-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2f360-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f360-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2f360-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f360-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f360-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f360-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f360-132">See also</span></span>

- [<span data-ttu-id="2f360-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f360-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2f360-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f360-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2f360-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f360-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2f360-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f360-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="2f360-137">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2f360-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
