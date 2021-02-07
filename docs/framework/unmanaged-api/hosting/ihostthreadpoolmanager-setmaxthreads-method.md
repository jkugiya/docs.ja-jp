---
description: '詳細について: IHostThreadPoolManager:: SetMaxThreads メソッド'
title: IHostThreadPoolManager::SetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 83266b05f639c0aa63e492bca525cbbf09a30775
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671244"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="3b4cb-103">IHostThreadPoolManager::SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="3b4cb-103">IHostThreadPoolManager::SetMaxThreads Method</span></span>

<span data-ttu-id="3b4cb-104">ホストがスレッドプールで保持できるスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-104">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b4cb-105">構文</span><span class="sxs-lookup"><span data-stu-id="3b4cb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b4cb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3b4cb-106">Parameters</span></span>  

 `MaxThreads`  
 <span data-ttu-id="3b4cb-107">スレッド プール内のワーカー スレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-107">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b4cb-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3b4cb-108">Return Value</span></span>  
  
|<span data-ttu-id="3b4cb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b4cb-109">HRESULT</span></span>|<span data-ttu-id="3b4cb-110">説明</span><span class="sxs-lookup"><span data-stu-id="3b4cb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b4cb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b4cb-111">S_OK</span></span>|<span data-ttu-id="3b4cb-112">`SetMaxThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-112">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="3b4cb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3b4cb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3b4cb-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3b4cb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b4cb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3b4cb-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-116">The call timed out.</span></span>|  
|<span data-ttu-id="3b4cb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3b4cb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3b4cb-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3b4cb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3b4cb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3b4cb-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3b4cb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3b4cb-121">E_FAIL</span></span>|<span data-ttu-id="3b4cb-122">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3b4cb-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3b4cb-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3b4cb-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="3b4cb-125">E_NOTIMPL</span></span>|<span data-ttu-id="3b4cb-126">ホストはの実装を提供していません `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-126">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b4cb-127">解説</span><span class="sxs-lookup"><span data-stu-id="3b4cb-127">Remarks</span></span>  

 <span data-ttu-id="3b4cb-128">CLR がスレッドプールのサイズを構成できるようにするために、ホストは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-128">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="3b4cb-129">ホストによっては、実装、パフォーマンス、スケーラビリティなどの理由から、スレッドプールを排他的に制御することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-129">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="3b4cb-130">この場合、ホストは E_NOTIMPL の HRESULT 値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-130">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b4cb-131">要件</span><span class="sxs-lookup"><span data-stu-id="3b4cb-131">Requirements</span></span>  

 <span data-ttu-id="3b4cb-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b4cb-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b4cb-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3b4cb-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b4cb-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3b4cb-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b4cb-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b4cb-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b4cb-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b4cb-136">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="3b4cb-137">GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="3b4cb-137">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="3b4cb-138">SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="3b4cb-138">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="3b4cb-139">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b4cb-139">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
