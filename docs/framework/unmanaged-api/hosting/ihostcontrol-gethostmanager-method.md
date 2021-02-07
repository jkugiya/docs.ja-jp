---
description: '詳細について: IHostControl:: GetHostManager メソッド'
title: IHostControl::GetHostManager メソッド
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
ms.openlocfilehash: 7cc118808c8788504da2cc07a8c61c419d3c588f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708905"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="71c7d-103">IHostControl::GetHostManager メソッド</span><span class="sxs-lookup"><span data-stu-id="71c7d-103">IHostControl::GetHostManager Method</span></span>

<span data-ttu-id="71c7d-104">指定したを使用して、ホストのインターフェイスの実装へのインターフェイスポインターを取得し `IID` ます。</span><span class="sxs-lookup"><span data-stu-id="71c7d-104">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71c7d-105">構文</span><span class="sxs-lookup"><span data-stu-id="71c7d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71c7d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71c7d-106">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="71c7d-107">から `IID` 共通言語ランタイム (CLR) が照会しているインターフェイスの。</span><span class="sxs-lookup"><span data-stu-id="71c7d-107">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="71c7d-108">入出力ホストに実装されたインターフェイスへのポインター。ホストがこのインターフェイスをサポートしていない場合は null。</span><span class="sxs-lookup"><span data-stu-id="71c7d-108">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71c7d-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="71c7d-109">Return Value</span></span>  
  
|<span data-ttu-id="71c7d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71c7d-110">HRESULT</span></span>|<span data-ttu-id="71c7d-111">説明</span><span class="sxs-lookup"><span data-stu-id="71c7d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71c7d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="71c7d-112">S_OK</span></span>|<span data-ttu-id="71c7d-113">`GetHostManager` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="71c7d-113">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="71c7d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71c7d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71c7d-115">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="71c7d-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71c7d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71c7d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71c7d-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="71c7d-117">The call timed out.</span></span>|  
|<span data-ttu-id="71c7d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71c7d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71c7d-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="71c7d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71c7d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71c7d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71c7d-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="71c7d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71c7d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71c7d-122">E_FAIL</span></span>|<span data-ttu-id="71c7d-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="71c7d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71c7d-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="71c7d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71c7d-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="71c7d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="71c7d-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="71c7d-126">E_INVALIDARG</span></span>|<span data-ttu-id="71c7d-127">要求された `IID` が無効です。</span><span class="sxs-lookup"><span data-stu-id="71c7d-127">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="71c7d-128">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="71c7d-128">E_NOINTERFACE</span></span>|<span data-ttu-id="71c7d-129">要求されたインターフェイスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="71c7d-129">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71c7d-130">解説</span><span class="sxs-lookup"><span data-stu-id="71c7d-130">Remarks</span></span>  

 <span data-ttu-id="71c7d-131">CLR はホストに対してクエリを実行し、次のインターフェイスの1つまたは複数がサポートされているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="71c7d-131">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="71c7d-132">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-132">IHostMemoryManager</span></span>](ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="71c7d-133">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-133">IHostTaskManager</span></span>](ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="71c7d-134">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-134">IHostThreadPoolManager</span></span>](ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="71c7d-135">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-135">IHostIoCompletionManager</span></span>](ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="71c7d-136">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-136">IHostSyncManager</span></span>](ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="71c7d-137">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-137">IHostAssemblyManager</span></span>](ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="71c7d-138">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-138">IHostGCManager</span></span>](ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="71c7d-139">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-139">IHostPolicyManager</span></span>](ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="71c7d-140">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="71c7d-140">IHostSecurityManager</span></span>](ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="71c7d-141">ホストが指定されたインターフェイスをサポートしている場合は、そのインターフェイス `ppObject` の実装にを設定します。</span><span class="sxs-lookup"><span data-stu-id="71c7d-141">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="71c7d-142">それ以外の場合は、 `ppObject` を null に設定します。</span><span class="sxs-lookup"><span data-stu-id="71c7d-142">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="71c7d-143">ホストマネージャーをシャットダウンした場合でも、CLR はを呼び出しません `Release` 。</span><span class="sxs-lookup"><span data-stu-id="71c7d-143">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71c7d-144">要件</span><span class="sxs-lookup"><span data-stu-id="71c7d-144">Requirements</span></span>  

 <span data-ttu-id="71c7d-145">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71c7d-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71c7d-146">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="71c7d-146">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71c7d-147">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="71c7d-147">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71c7d-148">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71c7d-148">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c7d-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="71c7d-149">See also</span></span>

- [<span data-ttu-id="71c7d-150">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71c7d-150">IHostControl Interface</span></span>](ihostcontrol-interface.md)
