---
description: '詳細情報: ICLRTask::RudeAbort メソッド'
title: ICLRTask::RudeAbort メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: f152f11ce41018b458ed2cb4df255e486ad54da0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636885"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="94a27-103">ICLRTask::RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="94a27-103">ICLRTask::RudeAbort Method</span></span>

<span data-ttu-id="94a27-104">現在の [ICLRTask インターフェイス](iclrtask-interface.md) インスタンスによって表されるタスクをすぐに無条件で中止するように、共通言語ランタイム (CLR) に指示します。</span><span class="sxs-lookup"><span data-stu-id="94a27-104">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94a27-105">構文</span><span class="sxs-lookup"><span data-stu-id="94a27-105">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="94a27-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="94a27-106">Return Value</span></span>  
  
|<span data-ttu-id="94a27-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94a27-107">HRESULT</span></span>|<span data-ttu-id="94a27-108">説明</span><span class="sxs-lookup"><span data-stu-id="94a27-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94a27-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="94a27-109">S_OK</span></span>|<span data-ttu-id="94a27-110">`RudeAbort` が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="94a27-110">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="94a27-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94a27-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94a27-112">CLR がプロセスに読み込まれていないか、CLR がマネージド コードを実行できないか、呼び出しを正常に処理できない状態です。</span><span class="sxs-lookup"><span data-stu-id="94a27-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="94a27-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="94a27-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="94a27-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="94a27-114">The call timed out.</span></span>|  
|<span data-ttu-id="94a27-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="94a27-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="94a27-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="94a27-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="94a27-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="94a27-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="94a27-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="94a27-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="94a27-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94a27-119">E_FAIL</span></span>|<span data-ttu-id="94a27-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="94a27-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="94a27-121">メソッドにより E_FAIL が返されると、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="94a27-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="94a27-122">ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="94a27-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94a27-123">解説</span><span class="sxs-lookup"><span data-stu-id="94a27-123">Remarks</span></span>  

 <span data-ttu-id="94a27-124">ホストは、タスクをすぐに中止するために `RudeAbort` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="94a27-124">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="94a27-125">ファイナライザーと例外処理ルーチンは、必ずしも実行されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="94a27-125">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94a27-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="94a27-126">Requirements</span></span>  

 <span data-ttu-id="94a27-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94a27-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94a27-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="94a27-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94a27-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれます</span><span class="sxs-lookup"><span data-stu-id="94a27-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94a27-130">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94a27-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a27-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="94a27-131">See also</span></span>

- [<span data-ttu-id="94a27-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94a27-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="94a27-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94a27-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="94a27-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94a27-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="94a27-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94a27-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
