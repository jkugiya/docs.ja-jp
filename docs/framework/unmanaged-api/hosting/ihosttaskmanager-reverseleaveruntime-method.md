---
description: '詳細について: IHostTaskManager:: ReverseLeaveRuntime メソッド'
title: IHostTaskManager::ReverseLeaveRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseLeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseLeaveRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseLeaveRuntime method [.NET Framework hosting]
- ReverseLeaveRuntime method [.NET Framework hosting]
ms.assetid: 4837d398-16a1-4e32-902c-022cd1aad3ca
topic_type:
- apiref
ms.openlocfilehash: 2fed157f6ea05243270b957cacdb00ba5a47a88f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680865"
---
# <a name="ihosttaskmanagerreverseleaveruntime-method"></a><span data-ttu-id="7d56a-103">IHostTaskManager::ReverseLeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="7d56a-103">IHostTaskManager::ReverseLeaveRuntime Method</span></span>

<span data-ttu-id="7d56a-104">コントロールが共通言語ランタイム (CLR) を離れていること、およびマネージコードから呼び出されたアンマネージ関数を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="7d56a-104">Notifies the host that control is leaving the common language runtime (CLR) and entering an unmanaged function that was, in turn, called from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d56a-105">構文</span><span class="sxs-lookup"><span data-stu-id="7d56a-105">Syntax</span></span>  
  
```cpp  
HRESULT ReverseLeaveRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7d56a-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="7d56a-106">Return Value</span></span>  
  
|<span data-ttu-id="7d56a-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d56a-107">HRESULT</span></span>|<span data-ttu-id="7d56a-108">説明</span><span class="sxs-lookup"><span data-stu-id="7d56a-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d56a-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d56a-109">S_OK</span></span>|<span data-ttu-id="7d56a-110">`ReverseLeaveRuntime` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="7d56a-110">`ReverseLeaveRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="7d56a-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d56a-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d56a-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="7d56a-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d56a-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d56a-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d56a-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="7d56a-114">The call timed out.</span></span>|  
|<span data-ttu-id="7d56a-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d56a-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d56a-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="7d56a-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d56a-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d56a-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d56a-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="7d56a-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d56a-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d56a-119">E_FAIL</span></span>|<span data-ttu-id="7d56a-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7d56a-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d56a-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="7d56a-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d56a-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="7d56a-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7d56a-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7d56a-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7d56a-124">要求されたリソース割り当てを完了するために必要なメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="7d56a-124">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d56a-125">解説</span><span class="sxs-lookup"><span data-stu-id="7d56a-125">Remarks</span></span>  

 <span data-ttu-id="7d56a-126">CLR はを呼び出して、 `ReverseLeaveRuntime` 現在実行中のタスクがアンマネージ関数に制御を返していることをホストに通知します。これは、プラットフォーム呼び出しによってマネージコードから呼び出されたものです。</span><span class="sxs-lookup"><span data-stu-id="7d56a-126">The CLR calls `ReverseLeaveRuntime` to inform the host that the currently executing task is returning control to an unmanaged function that was, in turn, called from managed code through platform invoke.</span></span> <span data-ttu-id="7d56a-127">への各呼び出し `ReverseLeaveRuntime` は、対応する [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)への呼び出しと一致します。</span><span class="sxs-lookup"><span data-stu-id="7d56a-127">Each call to `ReverseLeaveRuntime` matches a corresponding call to [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d56a-128">要件</span><span class="sxs-lookup"><span data-stu-id="7d56a-128">Requirements</span></span>  

 <span data-ttu-id="7d56a-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d56a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d56a-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7d56a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d56a-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7d56a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d56a-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d56a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d56a-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d56a-133">See also</span></span>

- [<span data-ttu-id="7d56a-134">CallNeedsHostHook メソッド</span><span class="sxs-lookup"><span data-stu-id="7d56a-134">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)
- [<span data-ttu-id="7d56a-135">EnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="7d56a-135">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)
- [<span data-ttu-id="7d56a-136">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d56a-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="7d56a-137">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d56a-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="7d56a-138">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d56a-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="7d56a-139">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7d56a-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="7d56a-140">LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="7d56a-140">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
- <span data-ttu-id="7d56a-141">[プラットフォーム呼び出しの詳細](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7d56a-141">[A Closer Look at Platform Invoke](/previous-versions/dotnet/netframework-4.0/0h9e9t7d(v=vs.100))</span></span>
