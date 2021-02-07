---
description: '詳細について: IHostThreadPoolManager:: GetMaxThreads メソッド'
title: IHostThreadPoolManager::GetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
ms.openlocfilehash: e8cae2aa29a50ef58a5b87deba9e275a441d43ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728382"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="286f7-103">IHostThreadPoolManager::GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="286f7-103">IHostThreadPoolManager::GetMaxThreads Method</span></span>

<span data-ttu-id="286f7-104">ホストがスレッドプール内で同時に保持するスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="286f7-104">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="286f7-105">構文</span><span class="sxs-lookup"><span data-stu-id="286f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="286f7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="286f7-106">Parameters</span></span>  

 `pdwMaxWorkerThreads`  
 <span data-ttu-id="286f7-107">入出力ホストがスレッドプールで保持するスレッドの最大数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="286f7-107">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="286f7-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="286f7-108">Return Value</span></span>  
  
|<span data-ttu-id="286f7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="286f7-109">HRESULT</span></span>|<span data-ttu-id="286f7-110">説明</span><span class="sxs-lookup"><span data-stu-id="286f7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="286f7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="286f7-111">S_OK</span></span>|<span data-ttu-id="286f7-112">`GetMaxThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="286f7-112">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="286f7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="286f7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="286f7-114">共通言語ランタイム (CLR (プロセスに読み込まれていない)、または CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="286f7-114">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="286f7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="286f7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="286f7-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="286f7-116">The call timed out.</span></span>|  
|<span data-ttu-id="286f7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="286f7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="286f7-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="286f7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="286f7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="286f7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="286f7-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="286f7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="286f7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="286f7-121">E_FAIL</span></span>|<span data-ttu-id="286f7-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="286f7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="286f7-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="286f7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="286f7-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="286f7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="286f7-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="286f7-125">E_NOTIMPL</span></span>|<span data-ttu-id="286f7-126">ホストはの実装を提供していません `GetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="286f7-126">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="286f7-127">解説</span><span class="sxs-lookup"><span data-stu-id="286f7-127">Remarks</span></span>  

 <span data-ttu-id="286f7-128">CLR はを呼び出して、 `GetMaxThreads` スレッドプール内のスレッドの合計数を確認します。</span><span class="sxs-lookup"><span data-stu-id="286f7-128">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="286f7-129">[Get利用スレッド](ihostthreadpoolmanager-getavailablethreads-method.md)メソッドは、現在作業項目を処理していないスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="286f7-129">The [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="286f7-130">パラメーターの戻り値を超えるすべての要求は `pdwMaxWorkerThreads` 、スレッドが使用可能になるまでキューに置かれたままになります。</span><span class="sxs-lookup"><span data-stu-id="286f7-130">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="286f7-131">ホストがの実装を提供していない場合 `GetMaxThreads` 、E_NOTIMPL の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="286f7-131">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="286f7-132">要件</span><span class="sxs-lookup"><span data-stu-id="286f7-132">Requirements</span></span>  

 <span data-ttu-id="286f7-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="286f7-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="286f7-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="286f7-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="286f7-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="286f7-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="286f7-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="286f7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286f7-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="286f7-137">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="286f7-138">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="286f7-138">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="286f7-139">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="286f7-139">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="286f7-140">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="286f7-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
