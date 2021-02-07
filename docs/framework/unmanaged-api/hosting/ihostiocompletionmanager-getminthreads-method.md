---
description: '詳細については、次を参照してください: IhohooGetMinThreads Manager:: メソッド'
title: IHostIoCompletionManager::GetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: 73b8d8cbff3777fe6aa956f282d3da5d4ac1b5c8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708505"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="2987f-103">IHostIoCompletionManager::GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="2987f-103">IHostIoCompletionManager::GetMinThreads Method</span></span>

<span data-ttu-id="2987f-104">ホストが i/o 要求を処理するために提供するスレッドの最小数を取得します。</span><span class="sxs-lookup"><span data-stu-id="2987f-104">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2987f-105">構文</span><span class="sxs-lookup"><span data-stu-id="2987f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2987f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2987f-106">Parameters</span></span>  

 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="2987f-107">入出力I/o 要求を処理するためにホストが提供するスレッドの最小数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2987f-107">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2987f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="2987f-108">Return Value</span></span>  
  
|<span data-ttu-id="2987f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2987f-109">HRESULT</span></span>|<span data-ttu-id="2987f-110">説明</span><span class="sxs-lookup"><span data-stu-id="2987f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2987f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2987f-111">S_OK</span></span>|<span data-ttu-id="2987f-112">`GetMinThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="2987f-112">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="2987f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2987f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2987f-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="2987f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2987f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2987f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2987f-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2987f-116">The call timed out.</span></span>|  
|<span data-ttu-id="2987f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2987f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2987f-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2987f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2987f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2987f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2987f-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="2987f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2987f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2987f-121">E_FAIL</span></span>|<span data-ttu-id="2987f-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2987f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2987f-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2987f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2987f-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2987f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2987f-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="2987f-125">E_NOTIMPL</span></span>|<span data-ttu-id="2987f-126">ホストはの実装を提供していません `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="2987f-126">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2987f-127">解説</span><span class="sxs-lookup"><span data-stu-id="2987f-127">Remarks</span></span>  

 <span data-ttu-id="2987f-128">ホストは、実装、パフォーマンス、スケーラビリティなどの理由から、サービス i/o 要求に割り当てられたスレッド数を排他的に制御することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2987f-128">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="2987f-129">このため、ホストでを実装する必要はありません `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="2987f-129">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="2987f-130">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2987f-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2987f-131">要件</span><span class="sxs-lookup"><span data-stu-id="2987f-131">Requirements</span></span>  

 <span data-ttu-id="2987f-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2987f-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2987f-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2987f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2987f-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2987f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2987f-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2987f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2987f-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="2987f-136">See also</span></span>

- [<span data-ttu-id="2987f-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2987f-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="2987f-138">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2987f-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
