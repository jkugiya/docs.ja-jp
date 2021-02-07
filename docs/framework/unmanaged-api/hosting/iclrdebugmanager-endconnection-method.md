---
description: '詳細情報: ICLRDebugManager:: EndConnection メソッド'
title: ICLRDebugManager::EndConnection メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: 06dc9e20ec02c3e3040090babcc443a2ae59848b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746053"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="4f3c0-103">ICLRDebugManager::EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="4f3c0-103">ICLRDebugManager::EndConnection Method</span></span>

<span data-ttu-id="4f3c0-104">タスクのリストと id とフレンドリ名の間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-104">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f3c0-105">構文</span><span class="sxs-lookup"><span data-stu-id="4f3c0-105">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f3c0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f3c0-106">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="4f3c0-107">から接続のホスト固有の識別子と、関連付けられている共通言語ランタイム (CLR) タスクのリスト。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-107">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f3c0-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="4f3c0-108">Return Value</span></span>  
  
|<span data-ttu-id="4f3c0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f3c0-109">HRESULT</span></span>|<span data-ttu-id="4f3c0-110">説明</span><span class="sxs-lookup"><span data-stu-id="4f3c0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f3c0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f3c0-111">S_OK</span></span>|<span data-ttu-id="4f3c0-112">`EndConnection` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-112">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="4f3c0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4f3c0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4f3c0-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4f3c0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4f3c0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4f3c0-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-116">The call timed out.</span></span>|  
|<span data-ttu-id="4f3c0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4f3c0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4f3c0-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4f3c0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4f3c0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4f3c0-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4f3c0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4f3c0-121">E_FAIL</span></span>|<span data-ttu-id="4f3c0-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4f3c0-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4f3c0-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4f3c0-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4f3c0-125">E_INVALIDARG</span></span>|<span data-ttu-id="4f3c0-126">[Beginconnection](iclrdebugmanager-beginconnection-method.md) がを使用して呼び出されていない `dwConnectionId` か、または `dwConnectionId` が0でした。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-126">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f3c0-127">解説</span><span class="sxs-lookup"><span data-stu-id="4f3c0-127">Remarks</span></span>  

 <span data-ttu-id="4f3c0-128">[ICLRDebugManager](iclrdebugmanager-interface.md)には、、setconnectiontasks、およびの3つのメソッドが用意されており、 `BeginConnection` [](iclrdebugmanager-setconnectiontasks-method.md) `EndConnection` タスクリストを識別子と表示名に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-128">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4f3c0-129">これら3つのメソッドは、一連のタスクごとに特定の順序で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-129">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="4f3c0-130">`BeginConnection` は、新しい接続を確立するために最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-130">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="4f3c0-131">`SetConnectionTasks` は、その接続に関連する一連のタスクを提供するために、次に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-131">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="4f3c0-132">`EndConnection` は、タスク一覧と識別子とフレンドリ名の間の関連付けを削除するために最後に呼び出されます。ただし、異なる接続の呼び出しは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-132">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f3c0-133">要件</span><span class="sxs-lookup"><span data-stu-id="4f3c0-133">Requirements</span></span>  

 <span data-ttu-id="4f3c0-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f3c0-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f3c0-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4f3c0-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f3c0-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4f3c0-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f3c0-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f3c0-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f3c0-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f3c0-138">See also</span></span>

- [<span data-ttu-id="4f3c0-139">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f3c0-139">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4f3c0-140">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f3c0-140">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="4f3c0-141">BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="4f3c0-141">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="4f3c0-142">SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="4f3c0-142">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="4f3c0-143">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f3c0-143">IHostControl Interface</span></span>](ihostcontrol-interface.md)
