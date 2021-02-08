---
description: '詳細について: IHostSyncManager:: CreateManualEvent メソッド'
title: IHostSyncManager::CreateManualEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 300d6cbf9555eb331a470767cdfb2745da300bb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784796"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="98729-103">IHostSyncManager::CreateManualEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="98729-103">IHostSyncManager::CreateManualEvent Method</span></span>

<span data-ttu-id="98729-104">手動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="98729-104">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98729-105">構文</span><span class="sxs-lookup"><span data-stu-id="98729-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98729-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98729-106">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="98729-107">[in] `true` オブジェクトがシグナル状態の場合は、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="98729-107">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="98729-108">入出力 [IHostManualEvent](ihostmanualevent-interface.md) インスタンスのアドレスへのポインター。イベントを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="98729-108">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98729-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="98729-109">Return Value</span></span>  
  
|<span data-ttu-id="98729-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98729-110">HRESULT</span></span>|<span data-ttu-id="98729-111">説明</span><span class="sxs-lookup"><span data-stu-id="98729-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98729-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="98729-112">S_OK</span></span>|<span data-ttu-id="98729-113">`CreateManualEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="98729-113">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="98729-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98729-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98729-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="98729-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="98729-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="98729-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="98729-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="98729-117">The call timed out.</span></span>|  
|<span data-ttu-id="98729-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="98729-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="98729-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="98729-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="98729-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="98729-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="98729-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="98729-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="98729-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98729-122">E_FAIL</span></span>|<span data-ttu-id="98729-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="98729-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="98729-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="98729-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="98729-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="98729-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="98729-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="98729-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="98729-127">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="98729-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98729-128">解説</span><span class="sxs-lookup"><span data-stu-id="98729-128">Remarks</span></span>  

 <span data-ttu-id="98729-129">`CreateManualEvent``IHostManualEvent` [IHostManualEvent:: reset](ihostmanualevent-reset-method.md)メソッドを呼び出してシグナル状態以外の状態に設定する必要がある、手動リセットイベントオブジェクトのを作成します。</span><span class="sxs-lookup"><span data-stu-id="98729-129">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="98729-130">`CreateManualEvent``CreateEvent` `true` パラメーターに指定された値を使用して、Win32 関数をミラー化し `bManualReset` ます。</span><span class="sxs-lookup"><span data-stu-id="98729-130">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98729-131">要件</span><span class="sxs-lookup"><span data-stu-id="98729-131">Requirements</span></span>  

 <span data-ttu-id="98729-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98729-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98729-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="98729-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98729-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="98729-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98729-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98729-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98729-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="98729-136">See also</span></span>

- [<span data-ttu-id="98729-137">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98729-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="98729-138">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98729-138">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="98729-139">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98729-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
