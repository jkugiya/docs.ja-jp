---
description: '詳細について: IHostManualEvent:: Reset メソッド'
title: IHostManualEvent::Reset メソッド
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
ms.openlocfilehash: 84debb8b37c2cdfdbf294bff6736b081424f9e52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708074"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="6c9b1-103">IHostManualEvent::Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="6c9b1-103">IHostManualEvent::Reset Method</span></span>

<span data-ttu-id="6c9b1-104">現在の [IHostManualEvent](ihostmanualevent-interface.md) インスタンスを非シグナル状態にリセットします。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-104">Resets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c9b1-105">構文</span><span class="sxs-lookup"><span data-stu-id="6c9b1-105">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6c9b1-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="6c9b1-106">Return Value</span></span>  
  
|<span data-ttu-id="6c9b1-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c9b1-107">HRESULT</span></span>|<span data-ttu-id="6c9b1-108">説明</span><span class="sxs-lookup"><span data-stu-id="6c9b1-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c9b1-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c9b1-109">S_OK</span></span>|<span data-ttu-id="6c9b1-110">`Reset` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-110">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="6c9b1-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c9b1-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c9b1-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c9b1-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c9b1-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c9b1-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-114">The call timed out.</span></span>|  
|<span data-ttu-id="6c9b1-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c9b1-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c9b1-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c9b1-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c9b1-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c9b1-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c9b1-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c9b1-119">E_FAIL</span></span>|<span data-ttu-id="6c9b1-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c9b1-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c9b1-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c9b1-123">要件</span><span class="sxs-lookup"><span data-stu-id="6c9b1-123">Requirements</span></span>  

 <span data-ttu-id="6c9b1-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c9b1-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c9b1-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6c9b1-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c9b1-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6c9b1-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c9b1-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c9b1-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c9b1-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c9b1-128">See also</span></span>

- [<span data-ttu-id="6c9b1-129">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c9b1-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="6c9b1-130">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c9b1-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="6c9b1-131">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c9b1-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="6c9b1-132">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c9b1-132">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="6c9b1-133">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c9b1-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
