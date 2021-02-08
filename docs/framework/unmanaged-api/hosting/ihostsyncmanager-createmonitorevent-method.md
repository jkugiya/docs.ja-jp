---
description: '詳細について: IHostSyncManager:: CreateMonitorEvent メソッド'
title: IHostSyncManager::CreateMonitorEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: b48d0417e614cf04c3ab150f0bdda73408b7a273
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784783"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="38e75-103">IHostSyncManager::CreateMonitorEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="38e75-103">IHostSyncManager::CreateMonitorEvent Method</span></span>

<span data-ttu-id="38e75-104">監視対象の自動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="38e75-104">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38e75-105">構文</span><span class="sxs-lookup"><span data-stu-id="38e75-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38e75-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38e75-106">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="38e75-107">からイベントオブジェクトに関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="38e75-107">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="38e75-108">入出力 [IHostAutoEvent](ihostautoevent-interface.md) インスタンスのアドレスへのポインター。イベントオブジェクトを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="38e75-108">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38e75-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="38e75-109">Return Value</span></span>  
  
|<span data-ttu-id="38e75-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="38e75-110">HRESULT</span></span>|<span data-ttu-id="38e75-111">説明</span><span class="sxs-lookup"><span data-stu-id="38e75-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38e75-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="38e75-112">S_OK</span></span>|<span data-ttu-id="38e75-113">`CreateMonitorEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="38e75-113">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="38e75-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="38e75-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="38e75-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="38e75-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="38e75-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="38e75-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="38e75-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="38e75-117">The call timed out.</span></span>|  
|<span data-ttu-id="38e75-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="38e75-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="38e75-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="38e75-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="38e75-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="38e75-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="38e75-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="38e75-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="38e75-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="38e75-122">E_FAIL</span></span>|<span data-ttu-id="38e75-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="38e75-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="38e75-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="38e75-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="38e75-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="38e75-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="38e75-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="38e75-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="38e75-127">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="38e75-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38e75-128">解説</span><span class="sxs-lookup"><span data-stu-id="38e75-128">Remarks</span></span>  

 <span data-ttu-id="38e75-129">`CreateMonitorEvent``IHostAutoEvent`CLR がマネージ型の実装で使用するを返し <xref:System.Threading.Monitor?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="38e75-129">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="38e75-130">このメソッドは、 `CreateEvent` `false` パラメーターに指定された値を使用して、Win32 関数をミラー化し `bManualReset` ます。</span><span class="sxs-lookup"><span data-stu-id="38e75-130">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="38e75-131">ホストは cookie を使用して、 [ICLRSyncManager:: GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) メソッドを呼び出すことによって、どのタスクがモニターで待機しているかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="38e75-131">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38e75-132">要件</span><span class="sxs-lookup"><span data-stu-id="38e75-132">Requirements</span></span>  

 <span data-ttu-id="38e75-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38e75-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38e75-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="38e75-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="38e75-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="38e75-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38e75-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38e75-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e75-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="38e75-137">See also</span></span>

- [<span data-ttu-id="38e75-138">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38e75-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="38e75-139">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38e75-139">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="38e75-140">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="38e75-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
