---
description: '詳細については、次を参照してください: IHostIoCompletionManager:: Setclrio参照マネージャーメソッド'
title: IHostIoCompletionManager::SetCLRIoCompletionManager メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: 1075c33d6de4f5edf34364d67cbc0a21c4f19802
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708295"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="e9114-103">IHostIoCompletionManager::SetCLRIoCompletionManager メソッド</span><span class="sxs-lookup"><span data-stu-id="e9114-103">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>

<span data-ttu-id="e9114-104">共通言語ランタイム (CLR) によって実装された [Iclrioの](iclriocompletionmanager-interface.md) インスタンスへのインターフェイスポインターをホストに提供します。</span><span class="sxs-lookup"><span data-stu-id="e9114-104">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9114-105">構文</span><span class="sxs-lookup"><span data-stu-id="e9114-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9114-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9114-106">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="e9114-107">から `ICLRIoCompletionManager` CLR によって提供されるインスタンスへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="e9114-107">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9114-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e9114-108">Return Value</span></span>  
  
|<span data-ttu-id="e9114-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9114-109">HRESULT</span></span>|<span data-ttu-id="e9114-110">説明</span><span class="sxs-lookup"><span data-stu-id="e9114-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9114-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9114-111">S_OK</span></span>|<span data-ttu-id="e9114-112">`SetCLRIoCompletionManager` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="e9114-112">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="e9114-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9114-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9114-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="e9114-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9114-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9114-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9114-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e9114-116">The call timed out.</span></span>|  
|<span data-ttu-id="e9114-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9114-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9114-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e9114-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9114-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9114-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9114-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="e9114-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9114-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9114-121">E_FAIL</span></span>|<span data-ttu-id="e9114-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e9114-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9114-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e9114-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9114-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="e9114-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9114-125">解説</span><span class="sxs-lookup"><span data-stu-id="e9114-125">Remarks</span></span>  

 <span data-ttu-id="e9114-126">CLR が呼び出された後 `SetCLRIoCompletionManager` 、ホストは [Iclriocompleted manager:: oncomplete](iclriocompletionmanager-oncomplete-method.md) を呼び出して、i/o 要求が完了したことを clr に通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9114-126">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9114-127">要件</span><span class="sxs-lookup"><span data-stu-id="e9114-127">Requirements</span></span>  

 <span data-ttu-id="e9114-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9114-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9114-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e9114-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9114-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e9114-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9114-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9114-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9114-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9114-132">See also</span></span>

- [<span data-ttu-id="e9114-133">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9114-133">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e9114-134">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9114-134">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
