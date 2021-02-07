---
description: '詳細について: IHostSemaphore:: ReleaseSemaphore メソッド'
title: IHostSemaphore::ReleaseSemaphore メソッド
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
ms.openlocfilehash: 368dc5ebe3017e03c0d6e8c57d0f122bc48d439f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707440"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="8bf46-103">IHostSemaphore::ReleaseSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="8bf46-103">IHostSemaphore::ReleaseSemaphore Method</span></span>

<span data-ttu-id="8bf46-104">現在の [IHostSemaphore](ihostsemaphore-interface.md) インスタンスの数を指定された量だけ増やします。</span><span class="sxs-lookup"><span data-stu-id="8bf46-104">Increases the count of the current [IHostSemaphore](ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf46-105">構文</span><span class="sxs-lookup"><span data-stu-id="8bf46-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bf46-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8bf46-106">Parameters</span></span>  

 `lReleaseCount`  
 <span data-ttu-id="8bf46-107">から現在のインスタンスの数を増やす量 `IHostSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="8bf46-107">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="8bf46-108">この値は0より大きくなければなりません。</span><span class="sxs-lookup"><span data-stu-id="8bf46-108">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="8bf46-109">入出力前のカウントへのポインター。呼び出し元が前のカウントを必要としない場合は null。</span><span class="sxs-lookup"><span data-stu-id="8bf46-109">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bf46-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="8bf46-110">Return Value</span></span>  
  
|<span data-ttu-id="8bf46-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8bf46-111">HRESULT</span></span>|<span data-ttu-id="8bf46-112">説明</span><span class="sxs-lookup"><span data-stu-id="8bf46-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8bf46-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="8bf46-113">S_OK</span></span>|<span data-ttu-id="8bf46-114">`ReleaseSemaphore` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="8bf46-114">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="8bf46-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8bf46-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8bf46-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="8bf46-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8bf46-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8bf46-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8bf46-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8bf46-118">The call timed out.</span></span>|  
|<span data-ttu-id="8bf46-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8bf46-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8bf46-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8bf46-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8bf46-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8bf46-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8bf46-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="8bf46-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8bf46-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8bf46-123">E_FAIL</span></span>|<span data-ttu-id="8bf46-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8bf46-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8bf46-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8bf46-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8bf46-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="8bf46-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bf46-127">解説</span><span class="sxs-lookup"><span data-stu-id="8bf46-127">Remarks</span></span>  

 <span data-ttu-id="8bf46-128">CLR は、通常、を呼び出して、 `ReleaseSemaphore` リソースを使用して終了したことをホストに通知し、パラメーターに値1を渡し `lReleaseCount` ます。</span><span class="sxs-lookup"><span data-stu-id="8bf46-128">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bf46-129">要件</span><span class="sxs-lookup"><span data-stu-id="8bf46-129">Requirements</span></span>  

 <span data-ttu-id="8bf46-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8bf46-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf46-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8bf46-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8bf46-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8bf46-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8bf46-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf46-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf46-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bf46-134">See also</span></span>

- [<span data-ttu-id="8bf46-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bf46-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8bf46-136">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bf46-136">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8bf46-137">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bf46-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="8bf46-138">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bf46-138">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="8bf46-139">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bf46-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
