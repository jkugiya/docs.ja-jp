---
description: ': ICLRTask:: YieldTask メソッドの詳細について説明します。'
title: ICLRTask::YieldTask メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.YieldTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::YieldTask
helpviewer_keywords:
- ICLRTask::YieldTask method [.NET Framework hosting]
- YieldTask method [.NET Framework hosting]
ms.assetid: b8eb4095-3a8f-4be3-9446-63e9893dce7d
topic_type:
- apiref
ms.openlocfilehash: b72b31b0a1c10a2b0b1e2ad379b140ff33419fa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784926"
---
# <a name="iclrtaskyieldtask-method"></a><span data-ttu-id="992a8-103">ICLRTask::YieldTask メソッド</span><span class="sxs-lookup"><span data-stu-id="992a8-103">ICLRTask::YieldTask Method</span></span>

<span data-ttu-id="992a8-104">現在の [ICLRTask](iclrtask-interface.md) インスタンスが表すタスクを共通言語ランタイム (CLR) が確保し、他のタスクでプロセッサ時間を使用できるようにすることを要求します。</span><span class="sxs-lookup"><span data-stu-id="992a8-104">Requests that the common language runtime (CLR) put aside the task that the current [ICLRTask](iclrtask-interface.md) instance represents, and make the processor time available to other tasks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="992a8-105">構文</span><span class="sxs-lookup"><span data-stu-id="992a8-105">Syntax</span></span>  
  
```cpp  
HRESULT YieldTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="992a8-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="992a8-106">Return Value</span></span>  
  
|<span data-ttu-id="992a8-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="992a8-107">HRESULT</span></span>|<span data-ttu-id="992a8-108">説明</span><span class="sxs-lookup"><span data-stu-id="992a8-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="992a8-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="992a8-109">S_OK</span></span>|<span data-ttu-id="992a8-110">`YieldTask` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="992a8-110">`YieldTask` returned successfully.</span></span>|  
|<span data-ttu-id="992a8-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="992a8-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="992a8-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="992a8-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="992a8-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="992a8-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="992a8-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="992a8-114">The call timed out.</span></span>|  
|<span data-ttu-id="992a8-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="992a8-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="992a8-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="992a8-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="992a8-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="992a8-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="992a8-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="992a8-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="992a8-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="992a8-119">E_FAIL</span></span>|<span data-ttu-id="992a8-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="992a8-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="992a8-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="992a8-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="992a8-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="992a8-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="992a8-123">解説</span><span class="sxs-lookup"><span data-stu-id="992a8-123">Remarks</span></span>  

 <span data-ttu-id="992a8-124">ホストは、 `YieldTask` 他のタスクまたはプロセスのプロセッサリソースを要求するためにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="992a8-124">A host calls `YieldTask` to request processor resources for other tasks or processes.</span></span> <span data-ttu-id="992a8-125">このメソッドは、主に、長時間実行されるコードが CPU 時間を確保できるようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="992a8-125">This method is primarily intended to allow long-running code to give up CPU time.</span></span> <span data-ttu-id="992a8-126">ランタイムは、現在 `ICLRTask` のインスタンスが処理時間を生成できる状態のタスクを配置しようとしますが、成功は保証されません。</span><span class="sxs-lookup"><span data-stu-id="992a8-126">The runtime attempts to put the task that the current `ICLRTask` instance represents in a state where it can yield processing time, but makes no guarantee of success.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="992a8-127">要件</span><span class="sxs-lookup"><span data-stu-id="992a8-127">Requirements</span></span>  

 <span data-ttu-id="992a8-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="992a8-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="992a8-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="992a8-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="992a8-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="992a8-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="992a8-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="992a8-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992a8-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="992a8-132">See also</span></span>

- [<span data-ttu-id="992a8-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="992a8-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="992a8-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="992a8-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="992a8-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="992a8-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="992a8-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="992a8-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
