---
description: '詳細については、次を参照してください: Ihohoo参照マネージャー:: Get持つスレッドメソッド'
title: IHostIoCompletionManager::GetAvailableThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: d50f79716f72b902102a2a97a0bce5dfe645334f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708545"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="0faed-103">IHostIoCompletionManager::GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="0faed-103">IHostIoCompletionManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="0faed-104">ホストによって管理されているスレッドの合計数に対する i/o 完了スレッドの数を取得します。これは現在、要求を処理していません。</span><span class="sxs-lookup"><span data-stu-id="0faed-104">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0faed-105">構文</span><span class="sxs-lookup"><span data-stu-id="0faed-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0faed-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0faed-106">Parameters</span></span>  

 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="0faed-107">入出力現在サービス要求で使用できるホストによって管理されている i/o 完了スレッドの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0faed-107">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0faed-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0faed-108">Return Value</span></span>  
  
|<span data-ttu-id="0faed-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0faed-109">HRESULT</span></span>|<span data-ttu-id="0faed-110">説明</span><span class="sxs-lookup"><span data-stu-id="0faed-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0faed-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0faed-111">S_OK</span></span>|<span data-ttu-id="0faed-112">`GetAvailableThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="0faed-112">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0faed-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0faed-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0faed-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="0faed-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0faed-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0faed-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0faed-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0faed-116">The call timed out.</span></span>|  
|<span data-ttu-id="0faed-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0faed-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0faed-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0faed-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0faed-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0faed-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0faed-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="0faed-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0faed-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0faed-121">E_FAIL</span></span>|<span data-ttu-id="0faed-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0faed-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0faed-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="0faed-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0faed-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="0faed-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0faed-125">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0faed-125">E_NOTIMPL</span></span>|<span data-ttu-id="0faed-126">ホストはの実装を提供していません `GetAvailableThreads` 。</span><span class="sxs-lookup"><span data-stu-id="0faed-126">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0faed-127">解説</span><span class="sxs-lookup"><span data-stu-id="0faed-127">Remarks</span></span>  

 <span data-ttu-id="0faed-128">ホストは、実装、パフォーマンス、スケーラビリティなどの理由から、i/o 完了スレッドプールのサイズを排他的に制御することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="0faed-128">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="0faed-129">したがって、ホストでを実装する必要はありません `GetAvailableThreads` 。</span><span class="sxs-lookup"><span data-stu-id="0faed-129">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="0faed-130">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0faed-130">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0faed-131">要件</span><span class="sxs-lookup"><span data-stu-id="0faed-131">Requirements</span></span>  

 <span data-ttu-id="0faed-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0faed-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0faed-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0faed-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0faed-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0faed-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0faed-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0faed-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faed-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="0faed-136">See also</span></span>

- [<span data-ttu-id="0faed-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0faed-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="0faed-138">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0faed-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
