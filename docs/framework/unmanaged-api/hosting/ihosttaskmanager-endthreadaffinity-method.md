---
description: '詳細について: IHostTaskManager:: EndThreadAffinity メソッド'
title: IHostTaskManager::EndThreadAffinity メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: 0bbe42d8e14d20fb5be18fe7ebb266100ae72fd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789425"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="fae83-103">IHostTaskManager::EndThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="fae83-103">IHostTaskManager::EndThreadAffinity Method</span></span>

<span data-ttu-id="fae83-104">以前に [IHostTaskManager:: BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md)を呼び出した後に、マネージコードが、現在のタスクを別のオペレーティングシステムのスレッドに移動できない期間を終了していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="fae83-104">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae83-105">構文</span><span class="sxs-lookup"><span data-stu-id="fae83-105">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fae83-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="fae83-106">Return Value</span></span>  
  
|<span data-ttu-id="fae83-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fae83-107">HRESULT</span></span>|<span data-ttu-id="fae83-108">説明</span><span class="sxs-lookup"><span data-stu-id="fae83-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fae83-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="fae83-109">S_OK</span></span>|<span data-ttu-id="fae83-110">`EndThreadAffinity` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="fae83-110">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="fae83-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fae83-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fae83-112">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="fae83-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fae83-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fae83-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fae83-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="fae83-114">The call timed out.</span></span>|  
|<span data-ttu-id="fae83-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fae83-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fae83-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="fae83-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fae83-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fae83-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fae83-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="fae83-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fae83-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fae83-119">E_FAIL</span></span>|<span data-ttu-id="fae83-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="fae83-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fae83-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fae83-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fae83-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="fae83-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fae83-123">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="fae83-123">E_UNEXPECTED</span></span>|<span data-ttu-id="fae83-124">`EndThreadAffinity` は、以前に対応するへの呼び出しなしで呼び出されました `BeginThreadAffinity` 。</span><span class="sxs-lookup"><span data-stu-id="fae83-124">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fae83-125">解説</span><span class="sxs-lookup"><span data-stu-id="fae83-125">Remarks</span></span>  

 <span data-ttu-id="fae83-126">CLR は、を `BeginThreadAffinity` 呼び出す前に、現在のタスクに対して、に対応する呼び出しを行い `EndThreadAffinity` ます。</span><span class="sxs-lookup"><span data-stu-id="fae83-126">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="fae83-127">このような対応する呼び出しがない場合、ホストの [IHostTaskManager](ihosttaskmanager-interface.md) の実装は E_UNEXPECTED を返し、アクションを実行しません。</span><span class="sxs-lookup"><span data-stu-id="fae83-127">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fae83-128">要件</span><span class="sxs-lookup"><span data-stu-id="fae83-128">Requirements</span></span>  

 <span data-ttu-id="fae83-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fae83-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fae83-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fae83-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fae83-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fae83-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fae83-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fae83-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae83-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="fae83-133">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="fae83-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fae83-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fae83-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fae83-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fae83-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fae83-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fae83-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fae83-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
