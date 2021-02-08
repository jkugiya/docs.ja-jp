---
description: '詳細について: IHostSyncManager:: CreateSemaphore メソッド'
title: IHostSyncManager::CreateSemaphore メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateSemaphore
helpviewer_keywords:
- CreateSemaphore method [.NET Framework hosting]
- IHostSyncManager::CreateSemaphore method [.NET Framework hosting]
ms.assetid: 37679e94-5ff9-4173-8fa5-457febeb89bf
topic_type:
- apiref
ms.openlocfilehash: 5a03ef7532e2ac8357ec015b40cc54942f5420e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784744"
---
# <a name="ihostsyncmanagercreatesemaphore-method"></a><span data-ttu-id="5f7e9-103">IHostSyncManager::CreateSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="5f7e9-103">IHostSyncManager::CreateSemaphore Method</span></span>

<span data-ttu-id="5f7e9-104">待機イベントのセマフォとして使用する共通言語ランタイム (CLR) の [IHostSemaphore](ihostsemaphore-interface.md) オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-104">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the common language runtime (CLR) to use as a semaphore for wait events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f7e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f7e9-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateSemaphore (  
    [in]  DWORD dwInitial,  
    [in]  DWORD dwMax,  
    [out] IHostSemaphore **ppSemaphore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f7e9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f7e9-106">Parameters</span></span>  

 `dwInitial`  
 <span data-ttu-id="5f7e9-107">からの初期カウント `ppSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-107">[in] The initial count for `ppSemaphore`.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="5f7e9-108">からの最大数 `ppSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-108">[in] The maximum count for `ppSemaphore`.</span></span>  
  
 `ppSemaphore`  
 <span data-ttu-id="5f7e9-109">入出力インスタンスのアドレスへのポインター。セマフォを作成できなかった `IHostSemaphore` 場合は null。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-109">[out] A pointer to the address of an `IHostSemaphore` instance, or null if the semaphore could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f7e9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="5f7e9-110">Return Value</span></span>  
  
|<span data-ttu-id="5f7e9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f7e9-111">HRESULT</span></span>|<span data-ttu-id="5f7e9-112">説明</span><span class="sxs-lookup"><span data-stu-id="5f7e9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f7e9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f7e9-113">S_OK</span></span>|<span data-ttu-id="5f7e9-114">`CreateSemaphore` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-114">`CreateSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="5f7e9-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5f7e9-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5f7e9-116">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-116">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5f7e9-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5f7e9-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5f7e9-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-118">The call timed out.</span></span>|  
|<span data-ttu-id="5f7e9-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5f7e9-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5f7e9-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5f7e9-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5f7e9-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5f7e9-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5f7e9-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5f7e9-123">E_FAIL</span></span>|<span data-ttu-id="5f7e9-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5f7e9-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5f7e9-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5f7e9-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5f7e9-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5f7e9-128">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-128">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f7e9-129">解説</span><span class="sxs-lookup"><span data-stu-id="5f7e9-129">Remarks</span></span>  

 <span data-ttu-id="5f7e9-130">`CreateSemaphore` 同じ名前を持つ Win32 関数をミラー化します。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-130">`CreateSemaphore` mirrors the Win32 function that has the same name.</span></span> <span data-ttu-id="5f7e9-131">`dwInitial`パラメーターと `dwMax` パラメーターは、それぞれ、Win32 およびパラメーターと同じセマンティクスを使用し `lInitialCount` `lMaximumCount` ます。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-131">The `dwInitial` and `dwMax` parameters use the same semantics for the semaphore count as the Win32 `lInitialCount` and `lMaximumCount` parameters, respectively.</span></span> <span data-ttu-id="5f7e9-132">`dwInitial` 0からまでの範囲で指定する必要があり `dwMax` ます。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-132">`dwInitial` must be between zero and `dwMax`, inclusive.</span></span> <span data-ttu-id="5f7e9-133">`dwMax` は 0 よりも大きい値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-133">`dwMax` must be greater than zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f7e9-134">要件</span><span class="sxs-lookup"><span data-stu-id="5f7e9-134">Requirements</span></span>  

 <span data-ttu-id="5f7e9-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f7e9-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f7e9-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5f7e9-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f7e9-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5f7e9-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f7e9-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f7e9-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f7e9-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f7e9-139">See also</span></span>

- [<span data-ttu-id="5f7e9-140">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f7e9-140">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="5f7e9-141">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f7e9-141">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="5f7e9-142">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f7e9-142">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
