---
description: '詳細について: IHostSyncManager:: CreateAutoEvent メソッド'
title: IHostSyncManager::CreateAutoEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
ms.openlocfilehash: 69767f1e01ead93c874eecf01c3167a5dc0e4b82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784848"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="c9360-103">IHostSyncManager::CreateAutoEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="c9360-103">IHostSyncManager::CreateAutoEvent Method</span></span>

<span data-ttu-id="c9360-104">自動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9360-104">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9360-105">構文</span><span class="sxs-lookup"><span data-stu-id="c9360-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9360-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9360-106">Parameters</span></span>  

 `ppEvent`  
 <span data-ttu-id="c9360-107">入出力ホストによって実装されている [IHostAutoEvent](ihostautoevent-interface.md) インスタンスのアドレスへのポインター。イベントオブジェクトを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="c9360-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9360-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="c9360-108">Return Value</span></span>  
  
|<span data-ttu-id="c9360-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9360-109">HRESULT</span></span>|<span data-ttu-id="c9360-110">説明</span><span class="sxs-lookup"><span data-stu-id="c9360-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9360-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9360-111">S_OK</span></span>|<span data-ttu-id="c9360-112">`CreateAutoEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="c9360-112">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c9360-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c9360-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c9360-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="c9360-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c9360-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c9360-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c9360-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c9360-116">The call timed out.</span></span>|  
|<span data-ttu-id="c9360-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c9360-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c9360-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c9360-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c9360-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c9360-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c9360-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="c9360-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c9360-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c9360-121">E_FAIL</span></span>|<span data-ttu-id="c9360-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c9360-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c9360-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c9360-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c9360-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="c9360-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c9360-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="c9360-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="c9360-126">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="c9360-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9360-127">解説</span><span class="sxs-lookup"><span data-stu-id="c9360-127">Remarks</span></span>  

 <span data-ttu-id="c9360-128">`CreateAutoEvent` 待機中のスレッドが解放された後に、状態が自動的に非シグナルに変更される自動イベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c9360-128">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="c9360-129">このメソッドは、 `CreateEvent` `false` パラメーターに指定された値を使用して、Win32 関数をミラー化します。 `bManualReset`</span><span class="sxs-lookup"><span data-stu-id="c9360-129">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9360-130">要件</span><span class="sxs-lookup"><span data-stu-id="c9360-130">Requirements</span></span>  

 <span data-ttu-id="c9360-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9360-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9360-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c9360-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c9360-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c9360-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9360-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9360-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9360-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9360-135">See also</span></span>

- [<span data-ttu-id="c9360-136">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9360-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="c9360-137">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9360-137">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="c9360-138">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9360-138">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="c9360-139">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c9360-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
