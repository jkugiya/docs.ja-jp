---
description: '詳細については、次を参照してください: ICLRTask:: SwitchIn メソッド'
title: ICLRTask::SwitchIn メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
ms.openlocfilehash: 0bbcd2b9594a8ce465a1dcd7b5ae3f8a0799826d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636833"
---
# <a name="iclrtaskswitchin-method"></a><span data-ttu-id="4099d-103">ICLRTask::SwitchIn メソッド</span><span class="sxs-lookup"><span data-stu-id="4099d-103">ICLRTask::SwitchIn Method</span></span>

<span data-ttu-id="4099d-104">現在の [ICLRTask](iclrtask-interface.md) インスタンスが表すタスクが操作可能な状態であることを、共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="4099d-104">Notifies the common language runtime (CLR) that the task that the current [ICLRTask](iclrtask-interface.md) instance represents is now in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4099d-105">構文</span><span class="sxs-lookup"><span data-stu-id="4099d-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4099d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4099d-106">Parameters</span></span>  

 `threadHandle`  
 <span data-ttu-id="4099d-107">から現在のインスタンスによって表されるタスクが実行されている物理スレッドへのハンドル `ICLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="4099d-107">[in] A handle to the physical thread on which the task represented by the current `ICLRTask` instance is executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4099d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4099d-108">Return Value</span></span>  
  
|<span data-ttu-id="4099d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4099d-109">HRESULT</span></span>|<span data-ttu-id="4099d-110">説明</span><span class="sxs-lookup"><span data-stu-id="4099d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4099d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4099d-111">S_OK</span></span>|<span data-ttu-id="4099d-112">`SwitchIn` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="4099d-112">`SwitchIn` returned successfully.</span></span>|  
|<span data-ttu-id="4099d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4099d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4099d-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="4099d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4099d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4099d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4099d-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4099d-116">The call timed out.</span></span>|  
|<span data-ttu-id="4099d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4099d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4099d-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4099d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4099d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4099d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4099d-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="4099d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4099d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4099d-121">E_FAIL</span></span>|<span data-ttu-id="4099d-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4099d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4099d-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4099d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4099d-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="4099d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4099d-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="4099d-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="4099d-126">`SwitchIn` は、以前の [Switchout メソッド](iclrtask-switchout-method.md)の呼び出しなしで呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="4099d-126">`SwitchIn` was called without an earlier call to [SwitchOut Method](iclrtask-switchout-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4099d-127">解説</span><span class="sxs-lookup"><span data-stu-id="4099d-127">Remarks</span></span>  

 <span data-ttu-id="4099d-128">パラメーターは、 `threadHandle` 現在のインスタンスによって表されるタスク `ICLRTask` がスケジュールされているオペレーティングシステムスレッドへのハンドルを表します。</span><span class="sxs-lookup"><span data-stu-id="4099d-128">The `threadHandle` parameter represents a handle to the operating system thread on which the task represented by the current `ICLRTask` instance has been scheduled.</span></span> <span data-ttu-id="4099d-129">このスレッドで偽装が発生した場合は、タスクを切り替える前に [IHostSecurityManager:: RevertToSelf](ihostsecuritymanager-reverttoself-method.md) を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4099d-129">If impersonation has occurred on this thread, you must call [IHostSecurityManager::RevertToSelf](ihostsecuritymanager-reverttoself-method.md) before switching in the task.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4099d-130">を呼び出していないを呼び出すと、が `SwitchIn` `SwitchOut` HRESULT 値 HOST_E_INVALIDOPERATION で失敗します。</span><span class="sxs-lookup"><span data-stu-id="4099d-130">A call to `SwitchIn` without an earlier call to `SwitchOut` fails with an HRESULT value of HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4099d-131">要件</span><span class="sxs-lookup"><span data-stu-id="4099d-131">Requirements</span></span>  

 <span data-ttu-id="4099d-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4099d-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4099d-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4099d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4099d-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4099d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4099d-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4099d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4099d-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="4099d-136">See also</span></span>

- [<span data-ttu-id="4099d-137">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4099d-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="4099d-138">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4099d-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="4099d-139">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4099d-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="4099d-140">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4099d-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
