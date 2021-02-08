---
description: '詳細について: IHostAutoEvent:: Wait メソッド'
title: IHostAutoEvent::Wait メソッド
ms.date: 03/30/2017
api_name:
- IHostAutoEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent::Wait
helpviewer_keywords:
- Wait method, IHostAutoEvent interface [.NET Framework hosting]
- IHostAutoEvent::Wait method [.NET Framework hosting]
ms.assetid: 535d51c5-9112-401b-8c36-85f35d7ee609
topic_type:
- apiref
ms.openlocfilehash: 0b75b44075dda46a3d84850cebd6b8f3851b055c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789477"
---
# <a name="ihostautoeventwait-method"></a><span data-ttu-id="efbe1-103">IHostAutoEvent::Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="efbe1-103">IHostAutoEvent::Wait Method</span></span>

<span data-ttu-id="efbe1-104">現在の [IHostAutoEvent](ihostautoevent-interface.md) インスタンスが所有されるか、指定された時間が経過するまで待機するようにします。</span><span class="sxs-lookup"><span data-stu-id="efbe1-104">Causes the current [IHostAutoEvent](ihostautoevent-interface.md) instance to wait until it is owned or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efbe1-105">構文</span><span class="sxs-lookup"><span data-stu-id="efbe1-105">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efbe1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="efbe1-106">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="efbe1-107">から `IHostAutoEvent` スレッドまたはファイバーが所有権を取得しない場合に、現在のインスタンスがを返す前に待機するミリ秒数。</span><span class="sxs-lookup"><span data-stu-id="efbe1-107">[in] The number of milliseconds the current `IHostAutoEvent` instance should wait before returning, if no thread or fiber takes ownership.</span></span>  
  
 `option`  
 <span data-ttu-id="efbe1-108">から [WAIT_OPTION](wait-option-enumeration.md) 値の1つ。この操作がブロックされた場合にホストが実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="efbe1-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efbe1-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="efbe1-109">Return Value</span></span>  
  
|<span data-ttu-id="efbe1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="efbe1-110">HRESULT</span></span>|<span data-ttu-id="efbe1-111">説明</span><span class="sxs-lookup"><span data-stu-id="efbe1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="efbe1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="efbe1-112">S_OK</span></span>|<span data-ttu-id="efbe1-113">`Wait` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="efbe1-113">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="efbe1-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="efbe1-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="efbe1-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="efbe1-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="efbe1-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="efbe1-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="efbe1-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="efbe1-117">The call timed out.</span></span>|  
|<span data-ttu-id="efbe1-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="efbe1-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="efbe1-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="efbe1-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="efbe1-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="efbe1-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="efbe1-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="efbe1-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="efbe1-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="efbe1-122">E_FAIL</span></span>|<span data-ttu-id="efbe1-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="efbe1-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="efbe1-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="efbe1-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="efbe1-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="efbe1-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="efbe1-126">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="efbe1-126">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="efbe1-127">ホストは待機間隔中にデッドロックを検出し、現在のインスタンスによって表されるイベントをデッドロックの対象として選択しました `IHostAutoEvent` 。</span><span class="sxs-lookup"><span data-stu-id="efbe1-127">The host detected a deadlock during the wait interval, and chose the event represented by the current `IHostAutoEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="efbe1-128">要件</span><span class="sxs-lookup"><span data-stu-id="efbe1-128">Requirements</span></span>  

 <span data-ttu-id="efbe1-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="efbe1-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efbe1-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="efbe1-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="efbe1-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="efbe1-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="efbe1-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efbe1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efbe1-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="efbe1-133">See also</span></span>

- [<span data-ttu-id="efbe1-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="efbe1-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="efbe1-135">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="efbe1-135">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="efbe1-136">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="efbe1-136">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="efbe1-137">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="efbe1-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
