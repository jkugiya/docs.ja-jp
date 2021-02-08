---
description: '詳細については、次を参照してください: IHostThreadPoolManager:: Getを参照してください。'
title: IHostThreadPoolManager::GetAvailableThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
ms.openlocfilehash: 95ecaa5757442bb384d303c1f8dafa342bd62f5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789334"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="e772c-103">IHostThreadPoolManager::GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="e772c-103">IHostThreadPoolManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="e772c-104">現在作業項目を処理していないスレッドプール内のスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="e772c-104">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e772c-105">構文</span><span class="sxs-lookup"><span data-stu-id="e772c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e772c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e772c-106">Parameters</span></span>  

 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="e772c-107">入出力現在作業項目を処理していないスレッドプール内のスレッドの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e772c-107">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e772c-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e772c-108">Return Value</span></span>  
  
|<span data-ttu-id="e772c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e772c-109">HRESULT</span></span>|<span data-ttu-id="e772c-110">説明</span><span class="sxs-lookup"><span data-stu-id="e772c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e772c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e772c-111">S_OK</span></span>|<span data-ttu-id="e772c-112">`GetAvailableThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="e772c-112">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="e772c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e772c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e772c-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="e772c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e772c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e772c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e772c-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e772c-116">The call timed out.</span></span>|  
|<span data-ttu-id="e772c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e772c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e772c-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e772c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e772c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e772c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e772c-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="e772c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e772c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e772c-121">E_FAIL</span></span>|<span data-ttu-id="e772c-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e772c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e772c-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e772c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e772c-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="e772c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e772c-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="e772c-125">E_NOTIMPL</span></span>|<span data-ttu-id="e772c-126">ホストはの実装を提供していません `GetAvailableThreads` 。</span><span class="sxs-lookup"><span data-stu-id="e772c-126">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e772c-127">解説</span><span class="sxs-lookup"><span data-stu-id="e772c-127">Remarks</span></span>  

 <span data-ttu-id="e772c-128">ホストがの実装を提供していない場合 `GetAvailableThreads` 、E_NOTIMPL の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="e772c-128">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e772c-129">要件</span><span class="sxs-lookup"><span data-stu-id="e772c-129">Requirements</span></span>  

 <span data-ttu-id="e772c-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e772c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e772c-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e772c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e772c-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e772c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e772c-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e772c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e772c-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="e772c-134">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="e772c-135">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e772c-135">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
