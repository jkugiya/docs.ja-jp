---
description: '詳細情報: ICLRDebugManager:: SetConnectionTasks メソッド'
title: ICLRDebugManager::SetConnectionTasks メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
ms.openlocfilehash: 851b3f54cc5599781596314dfb70296a3d86491a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728744"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a><span data-ttu-id="fba6c-103">ICLRDebugManager::SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="fba6c-103">ICLRDebugManager::SetConnectionTasks Method</span></span>

<span data-ttu-id="fba6c-104">[ICLRTask](iclrtask-interface.md)インスタンスのリストを識別子とフレンドリ名に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="fba6c-104">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fba6c-105">構文</span><span class="sxs-lookup"><span data-stu-id="fba6c-105">Syntax</span></span>  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fba6c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fba6c-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="fba6c-107">から配列を関連付ける接続のホスト固有の識別子 `ppCLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="fba6c-107">[in] The host-specific identifier for the connection with which to associate the `ppCLRTask` array.</span></span>  
  
 `dwCount`  
 <span data-ttu-id="fba6c-108">からのメンバーの数 `ppCLRTask` 。</span><span class="sxs-lookup"><span data-stu-id="fba6c-108">[in] The number of members of `ppCLRTask`.</span></span> <span data-ttu-id="fba6c-109">この値は0より大きくなければなりません。</span><span class="sxs-lookup"><span data-stu-id="fba6c-109">This number must be greater than zero.</span></span>  
  
 `ppCLRTask`  
 <span data-ttu-id="fba6c-110">から `ICLRTask` によって識別される接続に関連付けるポインターの配列 `id` 。</span><span class="sxs-lookup"><span data-stu-id="fba6c-110">[in] An array of `ICLRTask` pointers to associate with the connection identified by `id`.</span></span> <span data-ttu-id="fba6c-111">この配列には、少なくとも1つのメンバーが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="fba6c-111">This array must contain at least one member.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fba6c-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="fba6c-112">Return Value</span></span>  
  
|<span data-ttu-id="fba6c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fba6c-113">HRESULT</span></span>|<span data-ttu-id="fba6c-114">説明</span><span class="sxs-lookup"><span data-stu-id="fba6c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fba6c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="fba6c-115">S_OK</span></span>|<span data-ttu-id="fba6c-116">`SetConnectionTasks` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="fba6c-116">`SetConnectionTasks` returned successfully.</span></span>|  
|<span data-ttu-id="fba6c-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fba6c-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fba6c-118">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="fba6c-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fba6c-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fba6c-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fba6c-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="fba6c-120">The call timed out.</span></span>|  
|<span data-ttu-id="fba6c-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fba6c-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fba6c-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="fba6c-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fba6c-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fba6c-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fba6c-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="fba6c-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fba6c-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fba6c-125">E_FAIL</span></span>|<span data-ttu-id="fba6c-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="fba6c-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fba6c-127">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fba6c-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fba6c-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="fba6c-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fba6c-129">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fba6c-129">E_INVALIDARG</span></span>|<span data-ttu-id="fba6c-130">[Beginconnection](iclrdebugmanager-beginconnection-method.md) がこの値を使用して呼び出されていないか、 `id` `dwCount` またはが0であるか、または `id` の要素の1つが `ppCLRTask` null です。</span><span class="sxs-lookup"><span data-stu-id="fba6c-130">[BeginConnection](iclrdebugmanager-beginconnection-method.md) has not been called using this value of `id`, or `dwCount` or `id` is zero, or one of the elements of `ppCLRTask` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fba6c-131">解説</span><span class="sxs-lookup"><span data-stu-id="fba6c-131">Remarks</span></span>  

 <span data-ttu-id="fba6c-132">[ICLRDebugManager](iclrdebugmanager-interface.md)では、、、および endconnection という3つのメソッドを使用し `BeginConnection` `SetConnectionTasks` て、タスクリストを識別子とフレンドリ名に関連付けることができます。 [](iclrdebugmanager-endconnection-method.md)</span><span class="sxs-lookup"><span data-stu-id="fba6c-132">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, `SetConnectionTasks`, and [EndConnection](iclrdebugmanager-endconnection-method.md), for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fba6c-133">これら3つのメソッドは、一連のタスクごとに特定の順序で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="fba6c-133">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="fba6c-134">`BeginConnection` は、新しい接続を確立するために最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="fba6c-134">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="fba6c-135">`SetConnectionTasks` は、その接続に関連する一連のタスクを提供するために、次に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="fba6c-135">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="fba6c-136">`EndConnection` は、タスク一覧と識別子とフレンドリ名の間の関連付けを削除するために最後に呼び出されます。ただし、異なる接続の呼び出しは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="fba6c-136">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fba6c-137">要件</span><span class="sxs-lookup"><span data-stu-id="fba6c-137">Requirements</span></span>  

 <span data-ttu-id="fba6c-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fba6c-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fba6c-139">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fba6c-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fba6c-140">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fba6c-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fba6c-141">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fba6c-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba6c-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="fba6c-142">See also</span></span>

- [<span data-ttu-id="fba6c-143">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fba6c-143">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="fba6c-144">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fba6c-144">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="fba6c-145">BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="fba6c-145">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="fba6c-146">EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="fba6c-146">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)
- [<span data-ttu-id="fba6c-147">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fba6c-147">IHostControl Interface</span></span>](ihostcontrol-interface.md)
