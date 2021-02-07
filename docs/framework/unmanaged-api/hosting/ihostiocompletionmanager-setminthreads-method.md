---
description: '詳細については、次を参照してください: IhohooSetMinThreads Manager:: メソッド'
title: IHostIoCompletionManager::SetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: aade5ebb9e318d51296e52e7cf1c31c6ea9e4f6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708240"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="4a58c-103">IHostIoCompletionManager::SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="4a58c-103">IHostIoCompletionManager::SetMinThreads Method</span></span>

<span data-ttu-id="4a58c-104">ホストが i/o 完了に割り当てる必要があるスレッドの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="4a58c-104">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a58c-105">構文</span><span class="sxs-lookup"><span data-stu-id="4a58c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a58c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4a58c-106">Parameters</span></span>  

 `dwMinIoCompletionThreads`  
 <span data-ttu-id="4a58c-107">からホストが作成する必要がある i/o 完了スレッドの最小数。</span><span class="sxs-lookup"><span data-stu-id="4a58c-107">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4a58c-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4a58c-108">Return Value</span></span>  
  
|<span data-ttu-id="4a58c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4a58c-109">HRESULT</span></span>|<span data-ttu-id="4a58c-110">説明</span><span class="sxs-lookup"><span data-stu-id="4a58c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a58c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4a58c-111">S_OK</span></span>|<span data-ttu-id="4a58c-112">`SetMinThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="4a58c-112">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="4a58c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4a58c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4a58c-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="4a58c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4a58c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4a58c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4a58c-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4a58c-116">The call timed out.</span></span>|  
|<span data-ttu-id="4a58c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4a58c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4a58c-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4a58c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4a58c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4a58c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4a58c-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="4a58c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4a58c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4a58c-121">E_FAIL</span></span>|<span data-ttu-id="4a58c-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4a58c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4a58c-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4a58c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4a58c-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="4a58c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4a58c-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="4a58c-125">E_NOTIMPL</span></span>|<span data-ttu-id="4a58c-126">ホストはの実装を提供していません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="4a58c-126">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a58c-127">解説</span><span class="sxs-lookup"><span data-stu-id="4a58c-127">Remarks</span></span>  

 <span data-ttu-id="4a58c-128">ホストは、実装、パフォーマンス、スケーラビリティなどの理由から、i/o 要求を処理するために割り当てることができるスレッドの数を排他的に制御することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="4a58c-128">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="4a58c-129">このため、ホストでを実装する必要はありません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="4a58c-129">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="4a58c-130">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a58c-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a58c-131">要件</span><span class="sxs-lookup"><span data-stu-id="4a58c-131">Requirements</span></span>  

 <span data-ttu-id="4a58c-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a58c-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a58c-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4a58c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a58c-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4a58c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a58c-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a58c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a58c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a58c-136">See also</span></span>

- [<span data-ttu-id="4a58c-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a58c-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="4a58c-138">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="4a58c-138">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="4a58c-139">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4a58c-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
