---
description: '詳細について: IHostSyncManager:: CreateRWLockReaderEvent メソッド'
title: IHostSyncManager::CreateRWLockReaderEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
ms.openlocfilehash: be20757924aa45d2a44edab9bf921026aa0247a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784770"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="98538-103">IHostSyncManager::CreateRWLockReaderEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="98538-103">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>

<span data-ttu-id="98538-104">リーダーロックの実装のための手動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98538-104">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98538-105">構文</span><span class="sxs-lookup"><span data-stu-id="98538-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98538-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98538-106">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="98538-107">[入力] `true` を `ppEvent` シグナル状態にする必要がある場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="98538-107">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="98538-108">からリーダーロックに関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="98538-108">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="98538-109">入出力 [IHostManualEvent](ihostmanualevent-interface.md) インスタンスのアドレスへのポインター。イベントオブジェクトを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="98538-109">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98538-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="98538-110">Return Value</span></span>  
  
|<span data-ttu-id="98538-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98538-111">HRESULT</span></span>|<span data-ttu-id="98538-112">説明</span><span class="sxs-lookup"><span data-stu-id="98538-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98538-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="98538-113">S_OK</span></span>|<span data-ttu-id="98538-114">`CreateRWLockReaderEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="98538-114">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="98538-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98538-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98538-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="98538-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98538-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98538-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98538-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="98538-118">The call timed out.</span></span>|  
|<span data-ttu-id="98538-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98538-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98538-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="98538-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98538-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98538-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98538-122">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="98538-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98538-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98538-123">E_FAIL</span></span>|<span data-ttu-id="98538-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="98538-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98538-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="98538-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98538-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="98538-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="98538-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="98538-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="98538-128">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="98538-128">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98538-129">解説</span><span class="sxs-lookup"><span data-stu-id="98538-129">Remarks</span></span>  

 <span data-ttu-id="98538-130">CLR は、を呼び出して、 `CreateRWLockReaderEvent` `IHostManualEvent` リーダーロックの実装で使用するインスタンスへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="98538-130">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="98538-131">ホストは cookie を使用して、 [ICLRSyncManager](iclrsyncmanager-interface.md) インターフェイスを照会することによって、リーダーロックを待機しているタスクを特定できます。</span><span class="sxs-lookup"><span data-stu-id="98538-131">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98538-132">要件</span><span class="sxs-lookup"><span data-stu-id="98538-132">Requirements</span></span>  

 <span data-ttu-id="98538-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98538-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98538-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="98538-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98538-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="98538-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98538-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98538-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98538-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="98538-137">See also</span></span>

- [<span data-ttu-id="98538-138">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98538-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="98538-139">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98538-139">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="98538-140">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98538-140">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="98538-141">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98538-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
