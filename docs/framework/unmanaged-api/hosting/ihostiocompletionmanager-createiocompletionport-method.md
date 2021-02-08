---
description: '詳細については、次を参照してください: IhohooCreateIoCompletionPort Manager:: メソッド'
title: IHostIoCompletionManager::CreateIoCompletionPort メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: da4cd595e84c341eb15837ff97f4ba23cac23210
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789438"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="f4dc7-103">IHostIoCompletionManager::CreateIoCompletionPort メソッド</span><span class="sxs-lookup"><span data-stu-id="f4dc7-103">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>

<span data-ttu-id="f4dc7-104">ホストが新しい i/o 完了ポートを作成することを要求します。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-104">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4dc7-105">構文</span><span class="sxs-lookup"><span data-stu-id="f4dc7-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4dc7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4dc7-106">Parameters</span></span>  

 `phPort`  
 <span data-ttu-id="f4dc7-107">入出力新しく作成された i/o 完了ポートのハンドルへのポインター。ポートを作成できなかった場合は 0 (ゼロ)。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-107">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4dc7-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f4dc7-108">Return Value</span></span>  
  
|<span data-ttu-id="f4dc7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f4dc7-109">HRESULT</span></span>|<span data-ttu-id="f4dc7-110">説明</span><span class="sxs-lookup"><span data-stu-id="f4dc7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f4dc7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f4dc7-111">S_OK</span></span>|<span data-ttu-id="f4dc7-112">`CreateIoCompletionPort` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-112">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="f4dc7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f4dc7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f4dc7-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f4dc7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f4dc7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f4dc7-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-116">The call timed out.</span></span>|  
|<span data-ttu-id="f4dc7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f4dc7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f4dc7-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f4dc7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f4dc7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f4dc7-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f4dc7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f4dc7-121">E_FAIL</span></span>|<span data-ttu-id="f4dc7-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f4dc7-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f4dc7-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f4dc7-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f4dc7-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f4dc7-126">要求されたリソースを割り当てるのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-126">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4dc7-127">解説</span><span class="sxs-lookup"><span data-stu-id="f4dc7-127">Remarks</span></span>  

 <span data-ttu-id="f4dc7-128">CLR は、メソッドを呼び出して、 `CreateIoCompletionPort` ホストが新しい i/o 完了ポートを作成するように要求します。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-128">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="f4dc7-129">このポートは、 [Ihoを](ihostiocompletionmanager-bind-method.md) 呼び出して、このポートに i/o 操作をバインドします。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-129">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="f4dc7-130">ホストは、 [Iclriocomplete manager:: OnComplete](iclriocompletionmanager-oncomplete-method.md)を呼び出すことによって、状態を CLR に報告します。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-130">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4dc7-131">要件</span><span class="sxs-lookup"><span data-stu-id="f4dc7-131">Requirements</span></span>  

 <span data-ttu-id="f4dc7-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4dc7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4dc7-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f4dc7-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4dc7-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f4dc7-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4dc7-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4dc7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4dc7-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4dc7-136">See also</span></span>

- [<span data-ttu-id="f4dc7-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4dc7-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="f4dc7-138">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4dc7-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
