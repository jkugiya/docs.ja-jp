---
description: '詳細について: IHostGCManager:: SuspensionEnding メソッド'
title: IHostGCManager::SuspensionEnding メソッド
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
ms.openlocfilehash: 43ec3db76e6e6448719f9c40ef2476da4e2ccf9c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708621"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="9933b-103">IHostGCManager::SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="9933b-103">IHostGCManager::SuspensionEnding Method</span></span>

<span data-ttu-id="9933b-104">共通言語ランタイム (CLR) がガベージコレクションのために中断されたスレッドでタスクの実行を再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="9933b-104">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9933b-105">構文</span><span class="sxs-lookup"><span data-stu-id="9933b-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9933b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9933b-106">Parameters</span></span>  

 `generation`  
 <span data-ttu-id="9933b-107">からスレッドが再開される直前に終了するガベージコレクション生成。</span><span class="sxs-lookup"><span data-stu-id="9933b-107">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9933b-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="9933b-108">Return Value</span></span>  
  
|<span data-ttu-id="9933b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9933b-109">HRESULT</span></span>|<span data-ttu-id="9933b-110">説明</span><span class="sxs-lookup"><span data-stu-id="9933b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9933b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9933b-111">S_OK</span></span>|<span data-ttu-id="9933b-112">`SuspensionEnding` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9933b-112">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="9933b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9933b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9933b-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9933b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9933b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9933b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9933b-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9933b-116">The call timed out.</span></span>|  
|<span data-ttu-id="9933b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9933b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9933b-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9933b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9933b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9933b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9933b-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9933b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9933b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9933b-121">E_FAIL</span></span>|<span data-ttu-id="9933b-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9933b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9933b-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9933b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9933b-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9933b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9933b-125">解説</span><span class="sxs-lookup"><span data-stu-id="9933b-125">Remarks</span></span>  

 <span data-ttu-id="9933b-126">CLR は、 `SuspensionEnding` ガベージコレクションを実行した後にを呼び出して、スレッドが実行を再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="9933b-126">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9933b-127">メソッドの呼び出しが行われたスレッドを再スケジュールしないでください。</span><span class="sxs-lookup"><span data-stu-id="9933b-127">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9933b-128">要件</span><span class="sxs-lookup"><span data-stu-id="9933b-128">Requirements</span></span>  

 <span data-ttu-id="9933b-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9933b-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9933b-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9933b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9933b-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9933b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9933b-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9933b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9933b-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="9933b-133">See also</span></span>

- [<span data-ttu-id="9933b-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9933b-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9933b-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9933b-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9933b-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9933b-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9933b-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9933b-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9933b-138">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9933b-138">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
