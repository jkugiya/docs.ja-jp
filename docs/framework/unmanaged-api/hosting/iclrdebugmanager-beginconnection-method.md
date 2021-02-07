---
description: '詳細情報: ICLRDebugManager:: BeginConnection メソッド'
title: ICLRDebugManager::BeginConnection メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: 9b4ee64ad96bddfd5d7d650b657c6691b27d8c69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746140"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a><span data-ttu-id="296c8-103">ICLRDebugManager::BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="296c8-103">ICLRDebugManager::BeginConnection Method</span></span>

<span data-ttu-id="296c8-104">ホストとデバッガーの間の新しい接続を確立して、タスクの一覧を識別子とフレンドリ名に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="296c8-104">Establishes a new connection between the host and the debugger to associate a list of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="296c8-105">構文</span><span class="sxs-lookup"><span data-stu-id="296c8-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="296c8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="296c8-106">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="296c8-107">から共通言語ランタイム (CLR) タスクのリストに関連付ける識別子。</span><span class="sxs-lookup"><span data-stu-id="296c8-107">[in] An identifier to associate with the list of common language runtime (CLR) tasks.</span></span>  
  
 `szConnectionName`  
 <span data-ttu-id="296c8-108">からCLR タスクの一覧に関連付けるフレンドリ名。</span><span class="sxs-lookup"><span data-stu-id="296c8-108">[in] A friendly name to associate with the list of CLR tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="296c8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="296c8-109">Return Value</span></span>  
  
|<span data-ttu-id="296c8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="296c8-110">HRESULT</span></span>|<span data-ttu-id="296c8-111">説明</span><span class="sxs-lookup"><span data-stu-id="296c8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="296c8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="296c8-112">S_OK</span></span>|<span data-ttu-id="296c8-113">`BeginConnection` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="296c8-113">`BeginConnection` returned successfully.</span></span>|  
|<span data-ttu-id="296c8-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="296c8-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="296c8-115">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="296c8-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="296c8-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="296c8-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="296c8-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="296c8-117">The call timed out.</span></span>|  
|<span data-ttu-id="296c8-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="296c8-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="296c8-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="296c8-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="296c8-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="296c8-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="296c8-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="296c8-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="296c8-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="296c8-122">E_FAIL</span></span>|<span data-ttu-id="296c8-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="296c8-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="296c8-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="296c8-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="296c8-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="296c8-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="296c8-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="296c8-126">E_INVALIDARG</span></span>|<span data-ttu-id="296c8-127">`dwConnectionId` が0であるか、 `BeginConnection` 既にこの値を使用して呼び出されたか `dwConnectionId` 、または `szConnectionName` が null でした。</span><span class="sxs-lookup"><span data-stu-id="296c8-127">`dwConnectionId` was zero, or `BeginConnection` was already called using this `dwConnectionId` value, or `szConnectionName` was null.</span></span>|  
|<span data-ttu-id="296c8-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="296c8-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="296c8-129">この接続に関連付けられたタスクの一覧を保持するために十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="296c8-129">Not enough memory could be allocated to hold the list of tasks associated with this connection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="296c8-130">解説</span><span class="sxs-lookup"><span data-stu-id="296c8-130">Remarks</span></span>  

 <span data-ttu-id="296c8-131">[ICLRDebugManager](iclrdebugmanager-interface.md) には `BeginConnection` 、、 [Setconnectiontasks](iclrdebugmanager-setconnectiontasks-method.md)、 [endconnection](iclrdebugmanager-endconnection-method.md)という3つのメソッドが用意されており、タスクリストを識別子と表示名に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="296c8-131">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="296c8-132">これら3つのメソッドは、一連のタスクごとに特定の順序で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="296c8-132">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="296c8-133">`BeginConnection` は、新しい接続を確立するために最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="296c8-133">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="296c8-134">`SetConnectionTasks` は、その接続に関連する一連のタスクを提供するために、次に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="296c8-134">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="296c8-135">`EndConnection` は、タスク一覧と識別子とフレンドリ名の間の関連付けを削除するために最後に呼び出されます。ただし、異なる接続の呼び出しは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="296c8-135">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="296c8-136">要件</span><span class="sxs-lookup"><span data-stu-id="296c8-136">Requirements</span></span>  

 <span data-ttu-id="296c8-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="296c8-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="296c8-138">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="296c8-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="296c8-139">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="296c8-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="296c8-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="296c8-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="296c8-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="296c8-141">See also</span></span>

- [<span data-ttu-id="296c8-142">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="296c8-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="296c8-143">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="296c8-143">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="296c8-144">EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="296c8-144">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="296c8-145">SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="296c8-145">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="296c8-146">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="296c8-146">IHostControl Interface</span></span>](ihostcontrol-interface.md)
