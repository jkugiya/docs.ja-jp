---
description: '詳細について: IHostSyncManager:: CreateRWLockWriterEvent メソッド'
title: IHostSyncManager::CreateRWLockWriterEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockWriterEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockWriterEvent
helpviewer_keywords:
- CreateRWLockWriterEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockWriterEvent method [.NET Framework hosting]
ms.assetid: 70e488c2-cf53-4dc0-ba52-74372d215c41
topic_type:
- apiref
ms.openlocfilehash: 509f18ff49966e5da3a25e39258d33caf69249a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784757"
---
# <a name="ihostsyncmanagercreaterwlockwriterevent-method"></a><span data-ttu-id="3f76c-103">IHostSyncManager::CreateRWLockWriterEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="3f76c-103">IHostSyncManager::CreateRWLockWriterEvent Method</span></span>

<span data-ttu-id="3f76c-104">ライターロックの実装用の自動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f76c-104">Creates an auto-reset event object for the implementation of a writer lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f76c-105">構文</span><span class="sxs-lookup"><span data-stu-id="3f76c-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockWriterEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f76c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f76c-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="3f76c-107">から自動リセットイベントに関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="3f76c-107">[in] A cookie to associate with the auto-reset event.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="3f76c-108">入出力 [IHostAutoEvent](ihostautoevent-interface.md) インスタンスのアドレスへのポインター。イベントオブジェクトを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="3f76c-108">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f76c-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="3f76c-109">Return Value</span></span>  
  
|<span data-ttu-id="3f76c-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3f76c-110">HRESULT</span></span>|<span data-ttu-id="3f76c-111">説明</span><span class="sxs-lookup"><span data-stu-id="3f76c-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3f76c-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3f76c-112">S_OK</span></span>|<span data-ttu-id="3f76c-113">`CreateRWLockWriterEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3f76c-113">`CreateRWLockWriterEvent` returned successfully.</span></span>|  
|<span data-ttu-id="3f76c-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3f76c-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3f76c-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3f76c-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3f76c-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3f76c-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3f76c-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3f76c-117">The call timed out.</span></span>|  
|<span data-ttu-id="3f76c-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3f76c-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3f76c-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3f76c-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3f76c-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3f76c-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3f76c-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3f76c-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3f76c-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3f76c-122">E_FAIL</span></span>|<span data-ttu-id="3f76c-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3f76c-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3f76c-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3f76c-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3f76c-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3f76c-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3f76c-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3f76c-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3f76c-127">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="3f76c-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f76c-128">解説</span><span class="sxs-lookup"><span data-stu-id="3f76c-128">Remarks</span></span>  

 <span data-ttu-id="3f76c-129">CLR は、メソッドを呼び出して、 `CreateRWLockWriterEvent` `IHostAutoEvent` ライターロックの実装で使用するインスタンスへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="3f76c-129">The CLR calls the `CreateRWLockWriterEvent` method to get a reference to an `IHostAutoEvent` instance to use in its implementation of a writer lock.</span></span> <span data-ttu-id="3f76c-130">ホストは、指定された cookie を使用して、 [ICLRSyncManager](iclrsyncmanager-interface.md) インターフェイスの反復メソッドを呼び出すことによって、ロックを待機しているタスクを判別できます。</span><span class="sxs-lookup"><span data-stu-id="3f76c-130">The host can use the specified cookie to determine which tasks are waiting on the lock by calling the iteration methods of the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f76c-131">要件</span><span class="sxs-lookup"><span data-stu-id="3f76c-131">Requirements</span></span>  

 <span data-ttu-id="3f76c-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f76c-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f76c-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3f76c-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3f76c-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3f76c-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f76c-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f76c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f76c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f76c-136">See also</span></span>

- [<span data-ttu-id="3f76c-137">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f76c-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="3f76c-138">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f76c-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="3f76c-139">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f76c-139">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="3f76c-140">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f76c-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
