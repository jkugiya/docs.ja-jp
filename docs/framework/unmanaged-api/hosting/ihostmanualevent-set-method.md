---
description: '詳細情報: IHostManualEvent:: Set メソッド'
title: IHostManualEvent::Set メソッド
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
ms.openlocfilehash: e2de1fde2f8c0f512733ecde43d5240a94f84264
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707931"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="7258f-103">IHostManualEvent::Set メソッド</span><span class="sxs-lookup"><span data-stu-id="7258f-103">IHostManualEvent::Set Method</span></span>

<span data-ttu-id="7258f-104">現在の [IHostManualEvent](ihostmanualevent-interface.md) インスタンスをシグナル状態に設定します。</span><span class="sxs-lookup"><span data-stu-id="7258f-104">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7258f-105">構文</span><span class="sxs-lookup"><span data-stu-id="7258f-105">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7258f-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="7258f-106">Return Value</span></span>  
  
|<span data-ttu-id="7258f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7258f-107">HRESULT</span></span>|<span data-ttu-id="7258f-108">説明</span><span class="sxs-lookup"><span data-stu-id="7258f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7258f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="7258f-109">S_OK</span></span>|<span data-ttu-id="7258f-110">`Set` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="7258f-110">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="7258f-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7258f-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7258f-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="7258f-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7258f-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7258f-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7258f-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="7258f-114">The call timed out.</span></span>|  
|<span data-ttu-id="7258f-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7258f-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7258f-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="7258f-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7258f-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7258f-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7258f-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="7258f-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7258f-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7258f-119">E_FAIL</span></span>|<span data-ttu-id="7258f-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7258f-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7258f-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="7258f-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7258f-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="7258f-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7258f-123">要件</span><span class="sxs-lookup"><span data-stu-id="7258f-123">Requirements</span></span>  

 <span data-ttu-id="7258f-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7258f-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7258f-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7258f-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7258f-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7258f-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7258f-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7258f-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7258f-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="7258f-128">See also</span></span>

- [<span data-ttu-id="7258f-129">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7258f-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="7258f-130">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7258f-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="7258f-131">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7258f-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="7258f-132">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7258f-132">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="7258f-133">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7258f-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
