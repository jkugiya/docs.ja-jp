---
description: '詳細について: IHostThreadPoolManager:: SetMinThreads メソッド'
title: IHostThreadPoolManager::SetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: 00d6bd8212ee95318bbe546da80ca34bff7d1324
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753758"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="49ba8-103">IHostThreadPoolManager::SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="49ba8-103">IHostThreadPoolManager::SetMinThreads Method</span></span>

<span data-ttu-id="49ba8-104">ホストが要求を見越して保持する必要があるアイドル状態のスレッドの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="49ba8-104">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49ba8-105">構文</span><span class="sxs-lookup"><span data-stu-id="49ba8-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49ba8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49ba8-106">Parameters</span></span>  

 `MinThreads`  
 <span data-ttu-id="49ba8-107">からホストが保持する必要があるスレッドの新しい最小数。</span><span class="sxs-lookup"><span data-stu-id="49ba8-107">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49ba8-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="49ba8-108">Return Value</span></span>  
  
|<span data-ttu-id="49ba8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49ba8-109">HRESULT</span></span>|<span data-ttu-id="49ba8-110">説明</span><span class="sxs-lookup"><span data-stu-id="49ba8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49ba8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="49ba8-111">S_OK</span></span>|<span data-ttu-id="49ba8-112">`SetMinThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="49ba8-112">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="49ba8-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49ba8-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49ba8-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="49ba8-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49ba8-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49ba8-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49ba8-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="49ba8-116">The call timed out.</span></span>|  
|<span data-ttu-id="49ba8-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49ba8-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49ba8-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="49ba8-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49ba8-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49ba8-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49ba8-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="49ba8-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49ba8-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49ba8-121">E_FAIL</span></span>|<span data-ttu-id="49ba8-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="49ba8-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49ba8-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="49ba8-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49ba8-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="49ba8-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="49ba8-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="49ba8-125">E_NOTIMPL</span></span>|<span data-ttu-id="49ba8-126">ホストはの実装を提供していません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="49ba8-126">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49ba8-127">解説</span><span class="sxs-lookup"><span data-stu-id="49ba8-127">Remarks</span></span>  

 <span data-ttu-id="49ba8-128">ホストは、の実装を提供する必要はありません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="49ba8-128">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="49ba8-129">この場合、E_NOTIMPL の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="49ba8-129">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49ba8-130">要件</span><span class="sxs-lookup"><span data-stu-id="49ba8-130">Requirements</span></span>  

 <span data-ttu-id="49ba8-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49ba8-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49ba8-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="49ba8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49ba8-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="49ba8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49ba8-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49ba8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49ba8-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="49ba8-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="49ba8-136">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="49ba8-136">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="49ba8-137">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="49ba8-137">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="49ba8-138">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49ba8-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
