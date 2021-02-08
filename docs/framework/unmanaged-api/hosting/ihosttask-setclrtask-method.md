---
description: ': IHostTask:: SetCLRTask メソッドの詳細について説明します。'
title: IHostTask::SetCLRTask メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: 381b7827f043b6ef1d4a6698f5eb103233c9af55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784679"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="362bd-103">IHostTask::SetCLRTask メソッド</span><span class="sxs-lookup"><span data-stu-id="362bd-103">IHostTask::SetCLRTask Method</span></span>

<span data-ttu-id="362bd-104">インスタンスを `ICLRTask` 現在の [IHostTask](ihosttask-interface.md) インスタンスに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="362bd-104">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="362bd-105">構文</span><span class="sxs-lookup"><span data-stu-id="362bd-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="362bd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="362bd-106">Parameters</span></span>  

 `pCLRTask`  
 <span data-ttu-id="362bd-107">から `ICLRTask` 現在のインスタンスに関連付けられるインスタンスへのインターフェイスポインター `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="362bd-107">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="362bd-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="362bd-108">Return Value</span></span>  
  
|<span data-ttu-id="362bd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="362bd-109">HRESULT</span></span>|<span data-ttu-id="362bd-110">説明</span><span class="sxs-lookup"><span data-stu-id="362bd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="362bd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="362bd-111">S_OK</span></span>|<span data-ttu-id="362bd-112">`SetCLRTask` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="362bd-112">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="362bd-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="362bd-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="362bd-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="362bd-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="362bd-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="362bd-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="362bd-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="362bd-116">The call timed out.</span></span>|  
|<span data-ttu-id="362bd-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="362bd-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="362bd-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="362bd-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="362bd-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="362bd-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="362bd-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="362bd-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="362bd-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="362bd-121">E_FAIL</span></span>|<span data-ttu-id="362bd-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="362bd-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="362bd-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="362bd-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="362bd-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="362bd-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="362bd-125">解説</span><span class="sxs-lookup"><span data-stu-id="362bd-125">Remarks</span></span>  

 <span data-ttu-id="362bd-126">CLR は `SetCLRTask` を呼び出して、インスタンスを現在のインスタンスに関連付けます `ICLRTask` `IHostTask` 。これは [IHostTaskManager:: createtask](ihosttaskmanager-createtask-method.md)の呼び出しによって作成されたものです。</span><span class="sxs-lookup"><span data-stu-id="362bd-126">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="362bd-127">要件</span><span class="sxs-lookup"><span data-stu-id="362bd-127">Requirements</span></span>  

 <span data-ttu-id="362bd-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="362bd-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="362bd-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="362bd-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="362bd-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="362bd-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="362bd-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="362bd-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="362bd-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="362bd-132">See also</span></span>

- [<span data-ttu-id="362bd-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="362bd-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="362bd-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="362bd-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="362bd-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="362bd-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="362bd-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="362bd-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
