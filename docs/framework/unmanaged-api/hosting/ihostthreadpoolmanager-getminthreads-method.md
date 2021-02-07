---
description: '詳細について: IHostThreadPoolManager:: GetMinThreads メソッド'
title: IHostThreadPoolManager::GetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
ms.openlocfilehash: 2ebb828f9bc6230b4b0237aa1494f428a1834139
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728395"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a><span data-ttu-id="f4aaa-103">IHostThreadPoolManager::GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="f4aaa-103">IHostThreadPoolManager::GetMinThreads Method</span></span>

<span data-ttu-id="f4aaa-104">要求を処理するために、ホストがスレッドプールで保持するアイドル状態のスレッドの最小数を取得します。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-104">Gets the minimum number of idle threads that the host maintains in the thread pool in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4aaa-105">構文</span><span class="sxs-lookup"><span data-stu-id="f4aaa-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4aaa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4aaa-106">Parameters</span></span>  

 `MinThreads`  
 <span data-ttu-id="f4aaa-107">入出力ホストが現在保持しているアイドル状態のワーカースレッドの最小数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-107">[out] A pointer to the minimum number of idle worker threads that the host currently maintains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4aaa-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f4aaa-108">Return Value</span></span>  
  
|<span data-ttu-id="f4aaa-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4aaa-109">HRESULT</span></span>|<span data-ttu-id="f4aaa-110">説明</span><span class="sxs-lookup"><span data-stu-id="f4aaa-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4aaa-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4aaa-111">S_OK</span></span>|<span data-ttu-id="f4aaa-112">`GetMinThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-112">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="f4aaa-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f4aaa-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f4aaa-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f4aaa-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f4aaa-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f4aaa-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-116">The call timed out.</span></span>|  
|<span data-ttu-id="f4aaa-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f4aaa-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f4aaa-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f4aaa-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f4aaa-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f4aaa-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f4aaa-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4aaa-121">E_FAIL</span></span>|<span data-ttu-id="f4aaa-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f4aaa-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f4aaa-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f4aaa-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f4aaa-125">E_NOTIMPL</span></span>|<span data-ttu-id="f4aaa-126">ホストはの実装を提供していません `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-126">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4aaa-127">解説</span><span class="sxs-lookup"><span data-stu-id="f4aaa-127">Remarks</span></span>  

 <span data-ttu-id="f4aaa-128">ホストは、の実装を提供する必要はありません `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-128">The host is not required to provide an implementation of `GetMinThreads`.</span></span> <span data-ttu-id="f4aaa-129">この場合、E_NOTIMPL の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-129">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4aaa-130">要件</span><span class="sxs-lookup"><span data-stu-id="f4aaa-130">Requirements</span></span>  

 <span data-ttu-id="f4aaa-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4aaa-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4aaa-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f4aaa-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4aaa-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f4aaa-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4aaa-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4aaa-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4aaa-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4aaa-135">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="f4aaa-136">GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="f4aaa-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="f4aaa-137">SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="f4aaa-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="f4aaa-138">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4aaa-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
