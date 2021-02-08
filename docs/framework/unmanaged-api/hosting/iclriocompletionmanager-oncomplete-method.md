---
description: '詳細について: Iclriocomplete Manager:: OnComplete メソッド'
title: ICLRIoCompletionManager::OnComplete メソッド
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: d54b189debdfc2959676b53fd3fb51b2c10dce17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789886"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="f598f-103">ICLRIoCompletionManager::OnComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="f598f-103">ICLRIoCompletionManager::OnComplete Method</span></span>

<span data-ttu-id="f598f-104">[Ihohooの](ihostiocompletionmanager-bind-method.md)呼び出しを使用して作成された i/o 要求の状態を共通言語ランタイム (CLR) に通知します:: Bind メソッド。</span><span class="sxs-lookup"><span data-stu-id="f598f-104">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f598f-105">構文</span><span class="sxs-lookup"><span data-stu-id="f598f-105">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f598f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f598f-106">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="f598f-107">からバインド操作の状態を示す HRESULT 値です。</span><span class="sxs-lookup"><span data-stu-id="f598f-107">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="f598f-108">S_OK は、操作が正常に完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="f598f-108">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="f598f-109">HOST_E_INTERRUPTED は、呼び出しが完了前に終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="f598f-109">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="f598f-110">E_FAIL は、不明で回復不可能な重大なエラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="f598f-110">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="f598f-111">からI/o 要求の処理中に転送されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="f598f-111">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="f598f-112">から `OVERLAPPED` メソッドの呼び出しに渡された構造体へのポインター `IHostIoCompletionManager::Bind` 。</span><span class="sxs-lookup"><span data-stu-id="f598f-112">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f598f-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="f598f-113">Return Value</span></span>  
  
|<span data-ttu-id="f598f-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f598f-114">HRESULT</span></span>|<span data-ttu-id="f598f-115">説明</span><span class="sxs-lookup"><span data-stu-id="f598f-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f598f-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="f598f-116">S_OK</span></span>|<span data-ttu-id="f598f-117">`OnComplete` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f598f-117">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="f598f-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f598f-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f598f-119">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f598f-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f598f-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f598f-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f598f-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f598f-121">The call timed out.</span></span>|  
|<span data-ttu-id="f598f-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f598f-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f598f-123">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f598f-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f598f-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f598f-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f598f-125">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f598f-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f598f-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f598f-126">E_FAIL</span></span>|<span data-ttu-id="f598f-127">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f598f-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f598f-128">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f598f-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f598f-129">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f598f-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f598f-130">解説</span><span class="sxs-lookup"><span data-stu-id="f598f-130">Remarks</span></span>  

 <span data-ttu-id="f598f-131">ホストで i/o 完了の抽象化が実装されている場合、CLR は [Iho/ocompletion manager](ihostiocompletionmanager-interface.md)のメソッドを使用して、ホストを介して i/o 要求を行います。</span><span class="sxs-lookup"><span data-stu-id="f598f-131">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="f598f-132">次に、ホストはメソッドを呼び出して、その `OnComplete` ような要求の結果をランタイムに通知します。</span><span class="sxs-lookup"><span data-stu-id="f598f-132">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f598f-133">要件</span><span class="sxs-lookup"><span data-stu-id="f598f-133">Requirements</span></span>  

 <span data-ttu-id="f598f-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f598f-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f598f-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f598f-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f598f-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f598f-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f598f-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f598f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f598f-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="f598f-138">See also</span></span>

- [<span data-ttu-id="f598f-139">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f598f-139">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="f598f-140">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f598f-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="f598f-141">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f598f-141">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
