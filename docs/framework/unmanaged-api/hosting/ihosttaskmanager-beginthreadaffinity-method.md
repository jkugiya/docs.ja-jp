---
description: '詳細について: IHostTaskManager:: BeginThreadAffinity メソッド'
title: IHostTaskManager::BeginThreadAffinity メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
ms.openlocfilehash: 15ee917f5c81ee605c0cb4df3180041797c18daf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784601"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="50e28-103">IHostTaskManager::BeginThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="50e28-103">IHostTaskManager::BeginThreadAffinity Method</span></span>

<span data-ttu-id="50e28-104">マネージコードが、現在のタスクを別のオペレーティングシステムのスレッドに移動できない期間を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="50e28-104">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50e28-105">構文</span><span class="sxs-lookup"><span data-stu-id="50e28-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="50e28-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="50e28-106">Return Value</span></span>  
  
|<span data-ttu-id="50e28-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50e28-107">HRESULT</span></span>|<span data-ttu-id="50e28-108">説明</span><span class="sxs-lookup"><span data-stu-id="50e28-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50e28-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="50e28-109">S_OK</span></span>|<span data-ttu-id="50e28-110">`BeginThreadAffinity` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="50e28-110">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="50e28-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50e28-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50e28-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="50e28-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50e28-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50e28-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50e28-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="50e28-114">The call timed out.</span></span>|  
|<span data-ttu-id="50e28-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50e28-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50e28-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="50e28-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50e28-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50e28-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50e28-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="50e28-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50e28-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50e28-119">E_FAIL</span></span>|<span data-ttu-id="50e28-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="50e28-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50e28-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="50e28-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50e28-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="50e28-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50e28-123">解説</span><span class="sxs-lookup"><span data-stu-id="50e28-123">Remarks</span></span>  

 <span data-ttu-id="50e28-124">CLR は、通常、 `IHostTaskManager::BeginThreadAffinity` の呼び出しのコンテキストでを呼び出し <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="50e28-124">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="50e28-125">[IHostTaskManager:: EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md)に対応する呼び出しが行われるまで、現在のタスクを再スケジュールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="50e28-125">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="50e28-126">タスクは切り替えることができますが、切り替えられたときには、切り替え元のオペレーティングシステムスレッドに割り当てられている必要があります。 `BeginThreadAffinity` 呼び出しは現在のタスクを参照しているので、の入れ子になった呼び出しは無効です。</span><span class="sxs-lookup"><span data-stu-id="50e28-126">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50e28-127">要件</span><span class="sxs-lookup"><span data-stu-id="50e28-127">Requirements</span></span>  

 <span data-ttu-id="50e28-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50e28-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50e28-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="50e28-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50e28-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="50e28-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50e28-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50e28-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50e28-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="50e28-132">See also</span></span>

- [<span data-ttu-id="50e28-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50e28-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="50e28-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50e28-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="50e28-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50e28-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="50e28-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50e28-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
