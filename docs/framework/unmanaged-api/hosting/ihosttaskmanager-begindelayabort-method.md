---
description: '詳細について: IHostTaskManager:: BeginDelayAbort メソッド'
title: IHostTaskManager::BeginDelayAbort メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type:
- apiref
ms.openlocfilehash: f991690af4f7e634c8d845bdbd09f690b4ea3af7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784614"
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a><span data-ttu-id="afddb-103">IHostTaskManager::BeginDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="afddb-103">IHostTaskManager::BeginDelayAbort Method</span></span>

<span data-ttu-id="afddb-104">マネージコードが、現在のタスクを中止できない期間を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="afddb-104">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afddb-105">構文</span><span class="sxs-lookup"><span data-stu-id="afddb-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="afddb-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="afddb-106">Return Value</span></span>  
  
|<span data-ttu-id="afddb-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="afddb-107">HRESULT</span></span>|<span data-ttu-id="afddb-108">説明</span><span class="sxs-lookup"><span data-stu-id="afddb-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="afddb-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="afddb-109">S_OK</span></span>|<span data-ttu-id="afddb-110">`BeginDelayAbort` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="afddb-110">`BeginDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="afddb-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="afddb-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="afddb-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="afddb-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="afddb-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="afddb-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="afddb-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="afddb-114">The call timed out.</span></span>|  
|<span data-ttu-id="afddb-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="afddb-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="afddb-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="afddb-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="afddb-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="afddb-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="afddb-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="afddb-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="afddb-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="afddb-119">E_FAIL</span></span>|<span data-ttu-id="afddb-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="afddb-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="afddb-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="afddb-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="afddb-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="afddb-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="afddb-123">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="afddb-123">E_UNEXPECTED</span></span>|<span data-ttu-id="afddb-124">`BeginDelayAbort` は既に呼び出されていますが、 [Enddelayabort](ihosttaskmanager-enddelayabort-method.md) への対応する呼び出しはまだ受信されていません。</span><span class="sxs-lookup"><span data-stu-id="afddb-124">`BeginDelayAbort` has already been called, but the corresponding call to [EndDelayAbort](ihosttaskmanager-enddelayabort-method.md) has not yet been received.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afddb-125">解説</span><span class="sxs-lookup"><span data-stu-id="afddb-125">Remarks</span></span>  

 <span data-ttu-id="afddb-126">ホストは、が呼び出されるまで、現在のタスクを中止することはできません `EndDelayAbort` 。</span><span class="sxs-lookup"><span data-stu-id="afddb-126">The host must not abort the current task until `EndDelayAbort` is called.</span></span> <span data-ttu-id="afddb-127">の `BeginDelayAbort` 呼び出しが介在せずにの別の呼び出しが行われた場合 `EndDelayAbort` 、ホストはから E_UNEXPECTED を返す必要があり、アクションを実行する必要はあり `BeginDelayAbort` ません。</span><span class="sxs-lookup"><span data-stu-id="afddb-127">If another call to `BeginDelayAbort` is made without an intervening call to `EndDelayAbort`, the host should return E_UNEXPECTED from `BeginDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afddb-128">要件</span><span class="sxs-lookup"><span data-stu-id="afddb-128">Requirements</span></span>  

 <span data-ttu-id="afddb-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afddb-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afddb-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="afddb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afddb-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="afddb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="afddb-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afddb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afddb-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="afddb-133">See also</span></span>

- [<span data-ttu-id="afddb-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="afddb-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="afddb-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="afddb-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="afddb-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="afddb-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
