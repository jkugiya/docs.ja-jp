---
description: '詳細については、次を参照してください: Ihohoo参照マネージャー:: GetMaxThreads メソッド'
title: IHostIoCompletionManager::GetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: 10c36c058f5161330842fa9d71813c4520d4655c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708531"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="024b5-103">IHostIoCompletionManager::GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="024b5-103">IHostIoCompletionManager::GetMaxThreads Method</span></span>

<span data-ttu-id="024b5-104">ホストがサービス i/o 要求に割り当てることができるスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="024b5-104">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="024b5-105">構文</span><span class="sxs-lookup"><span data-stu-id="024b5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="024b5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="024b5-106">Parameters</span></span>  

 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="024b5-107">入出力ホストが i/o 要求を処理するために割り当てることができるスレッドプール内のスレッドの最大数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="024b5-107">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="024b5-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="024b5-108">Return Value</span></span>  
  
|<span data-ttu-id="024b5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="024b5-109">HRESULT</span></span>|<span data-ttu-id="024b5-110">説明</span><span class="sxs-lookup"><span data-stu-id="024b5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="024b5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="024b5-111">S_OK</span></span>|<span data-ttu-id="024b5-112">`GetMaxThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="024b5-112">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="024b5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="024b5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="024b5-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="024b5-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="024b5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="024b5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="024b5-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="024b5-116">The call timed out.</span></span>|  
|<span data-ttu-id="024b5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="024b5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="024b5-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="024b5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="024b5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="024b5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="024b5-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="024b5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="024b5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="024b5-121">E_FAIL</span></span>|<span data-ttu-id="024b5-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="024b5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="024b5-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="024b5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="024b5-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="024b5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="024b5-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="024b5-125">E_NOTIMPL</span></span>|<span data-ttu-id="024b5-126">ホストはの実装を提供していません `GetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="024b5-126">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="024b5-127">解説</span><span class="sxs-lookup"><span data-stu-id="024b5-127">Remarks</span></span>  

 <span data-ttu-id="024b5-128">ホストは、実装、パフォーマンス、スケーラビリティなどの理由から、i/o 要求を処理するために割り当てることができるスレッドの数を排他的に制御することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="024b5-128">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="024b5-129">このため、ホストでを実装する必要はありません `GetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="024b5-129">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="024b5-130">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="024b5-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="024b5-131">要件</span><span class="sxs-lookup"><span data-stu-id="024b5-131">Requirements</span></span>  

 <span data-ttu-id="024b5-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="024b5-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="024b5-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="024b5-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="024b5-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="024b5-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="024b5-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="024b5-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024b5-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="024b5-136">See also</span></span>

- [<span data-ttu-id="024b5-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="024b5-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="024b5-138">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="024b5-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
