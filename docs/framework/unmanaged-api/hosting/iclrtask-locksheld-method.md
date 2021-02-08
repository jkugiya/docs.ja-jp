---
description: ': ICLRTask:: LocksHeld メソッドの詳細について説明します。'
title: ICLRTask::LocksHeld メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.LocksHeld
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::LocksHeld
helpviewer_keywords:
- LocksHeld method [.NET Framework hosting]
- ICLRTask::LocksHeld method [.NET Framework hosting]
ms.assetid: e88a4dc3-02cc-4703-a474-292b71c40657
topic_type:
- apiref
ms.openlocfilehash: 5dff0b2a80594e03d61d50c6d9fa52bb12bb42f2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799533"
---
# <a name="iclrtasklocksheld-method"></a><span data-ttu-id="89da4-103">ICLRTask::LocksHeld メソッド</span><span class="sxs-lookup"><span data-stu-id="89da4-103">ICLRTask::LocksHeld Method</span></span>

<span data-ttu-id="89da4-104">タスクに現在保持されているロックの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="89da4-104">Gets the number of locks currently held on the task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89da4-105">構文</span><span class="sxs-lookup"><span data-stu-id="89da4-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeld (  
    [out] SIZE_T *pLockCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89da4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="89da4-106">Parameters</span></span>  

 `pLockCount`  
 <span data-ttu-id="89da4-107">入出力メソッドの呼び出し時にタスクに保持されていたロックの数。</span><span class="sxs-lookup"><span data-stu-id="89da4-107">[out] The number of locks held on the task at the time of the method call.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89da4-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="89da4-108">Return Value</span></span>  
  
|<span data-ttu-id="89da4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89da4-109">HRESULT</span></span>|<span data-ttu-id="89da4-110">説明</span><span class="sxs-lookup"><span data-stu-id="89da4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89da4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="89da4-111">S_OK</span></span>|<span data-ttu-id="89da4-112">`LocksHeld` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="89da4-112">`LocksHeld` returned successfully.</span></span>|  
|<span data-ttu-id="89da4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="89da4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="89da4-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="89da4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="89da4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="89da4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="89da4-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="89da4-116">The call timed out.</span></span>|  
|<span data-ttu-id="89da4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="89da4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="89da4-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="89da4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="89da4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="89da4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="89da4-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="89da4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="89da4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="89da4-121">E_FAIL</span></span>|<span data-ttu-id="89da4-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="89da4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="89da4-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="89da4-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="89da4-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="89da4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89da4-125">要件</span><span class="sxs-lookup"><span data-stu-id="89da4-125">Requirements</span></span>  

 <span data-ttu-id="89da4-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89da4-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89da4-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="89da4-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89da4-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="89da4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89da4-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89da4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89da4-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="89da4-130">See also</span></span>

- [<span data-ttu-id="89da4-131">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89da4-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="89da4-132">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89da4-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="89da4-133">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89da4-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="89da4-134">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="89da4-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
