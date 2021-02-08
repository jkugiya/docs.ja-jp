---
description: '詳細情報: IHostTask:: Join メソッド'
title: IHostTask::Join メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: 8231401ab01ee040f225b78a52b61eb7d59af1d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784653"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="01509-103">IHostTask::Join メソッド</span><span class="sxs-lookup"><span data-stu-id="01509-103">IHostTask::Join Method</span></span>

<span data-ttu-id="01509-104">現在の [IHostTask](ihosttask-interface.md) インスタンスによって表されるタスクが完了するまで、または指定された時間が経過するか、または [IHostTask:: Alert](ihosttask-alert-method.md) が呼び出されるまで、呼び出し元のタスクをブロックします。</span><span class="sxs-lookup"><span data-stu-id="01509-104">Blocks the calling task until the task represented by the current [IHostTask](ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01509-105">構文</span><span class="sxs-lookup"><span data-stu-id="01509-105">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01509-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="01509-106">Parameters</span></span>  

 `milliseconds`  
 <span data-ttu-id="01509-107">からタスクの終了を待機する時間間隔 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="01509-107">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="01509-108">タスクが終了する前にこの間隔が経過すると、呼び出し元のタスクがブロック解除されます。</span><span class="sxs-lookup"><span data-stu-id="01509-108">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="01509-109">から [WAIT_OPTION](wait-option-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="01509-109">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="01509-110">値 WAIT_ALERTABLE `Alert` は、が経過する前にが呼び出された場合に、タスクをウェイクアップするようにホストに指示 `milliseconds` します。</span><span class="sxs-lookup"><span data-stu-id="01509-110">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01509-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="01509-111">Return Value</span></span>  
  
|<span data-ttu-id="01509-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01509-112">HRESULT</span></span>|<span data-ttu-id="01509-113">説明</span><span class="sxs-lookup"><span data-stu-id="01509-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01509-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="01509-114">S_OK</span></span>|<span data-ttu-id="01509-115">`Join` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="01509-115">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="01509-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01509-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01509-117">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="01509-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01509-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01509-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01509-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="01509-119">The call timed out.</span></span>|  
|<span data-ttu-id="01509-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01509-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01509-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="01509-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01509-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01509-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01509-123">ブロックされたスレッドまたはファイバーが待機中であるか、または現在の `IHostTask` インスタンスがタスクに関連付けられていないときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="01509-123">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="01509-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01509-124">E_FAIL</span></span>|<span data-ttu-id="01509-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="01509-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01509-126">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="01509-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01509-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="01509-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="01509-128">要件</span><span class="sxs-lookup"><span data-stu-id="01509-128">Requirements</span></span>  

 <span data-ttu-id="01509-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01509-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01509-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="01509-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01509-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="01509-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01509-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01509-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01509-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="01509-133">See also</span></span>

- [<span data-ttu-id="01509-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01509-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="01509-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01509-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="01509-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01509-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="01509-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="01509-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="01509-138">WAIT_OPTION 列挙型</span><span class="sxs-lookup"><span data-stu-id="01509-138">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
