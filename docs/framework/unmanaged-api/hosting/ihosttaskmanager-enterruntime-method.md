---
description: '詳細情報: IHostTaskManager:: EnterRuntime メソッド'
title: IHostTaskManager::EnterRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: 924fa18c9acbf02d8c614ffd9bf95657fd73ed14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753836"
---
# <a name="ihosttaskmanagerenterruntime-method"></a><span data-ttu-id="ada9a-103">IHostTaskManager::EnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="ada9a-103">IHostTaskManager::EnterRuntime Method</span></span>

<span data-ttu-id="ada9a-104">プラットフォーム呼び出しメソッドなどのアンマネージメソッドへの呼び出しが実行制御を共通言語ランタイム (CLR) に返すことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="ada9a-104">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada9a-105">構文</span><span class="sxs-lookup"><span data-stu-id="ada9a-105">Syntax</span></span>  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ada9a-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="ada9a-106">Return Value</span></span>  
  
|<span data-ttu-id="ada9a-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ada9a-107">HRESULT</span></span>|<span data-ttu-id="ada9a-108">説明</span><span class="sxs-lookup"><span data-stu-id="ada9a-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ada9a-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ada9a-109">S_OK</span></span>|<span data-ttu-id="ada9a-110">`EnterRuntime` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="ada9a-110">`EnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="ada9a-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ada9a-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ada9a-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ada9a-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ada9a-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ada9a-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ada9a-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ada9a-114">The call timed out.</span></span>|  
|<span data-ttu-id="ada9a-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ada9a-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ada9a-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ada9a-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ada9a-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ada9a-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ada9a-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ada9a-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ada9a-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ada9a-119">E_FAIL</span></span>|<span data-ttu-id="ada9a-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ada9a-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ada9a-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ada9a-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ada9a-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ada9a-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ada9a-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ada9a-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ada9a-124">要求された割り当てを完了するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="ada9a-124">Not enough memory was available to complete the requested allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ada9a-125">解説</span><span class="sxs-lookup"><span data-stu-id="ada9a-125">Remarks</span></span>  

 <span data-ttu-id="ada9a-126">`EnterRuntime` が呼び出され、ホストに対して、以前のバージョンの [最小 Veruntime](ihosttaskmanager-leaveruntime-method.md) メソッドへの呼び出しが行われたこと、実行が終了したこと、およびランタイムに実行制御が返されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="ada9a-126">`EnterRuntime` is called to notify the host that an unmanaged function, for which an earlier call to the [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md) method was made, has finished executing, and is returning execution control to the runtime.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ada9a-127">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) は、以前の呼び出しが行われたアンマネージ関数 `LeaveRuntime` がマネージコードを呼び出していることをホストに通知するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ada9a-127">[ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md) is called to notify the host that an unmanaged function, for which an earlier call to `LeaveRuntime` was made, is making a call into managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada9a-128">要件</span><span class="sxs-lookup"><span data-stu-id="ada9a-128">Requirements</span></span>  

 <span data-ttu-id="ada9a-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ada9a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada9a-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ada9a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ada9a-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ada9a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ada9a-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada9a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada9a-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="ada9a-133">See also</span></span>

- <span data-ttu-id="ada9a-134">[高度な COM 相互運用性](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ada9a-134">[Advanced COM Interoperability](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>
- [<span data-ttu-id="ada9a-135">方法: PInvoke を使用してマネージコードからネイティブ Dll を呼び出す</span><span class="sxs-lookup"><span data-stu-id="ada9a-135">How to: Call Native DLLs from Managed Code Using PInvoke</span></span>](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [<span data-ttu-id="ada9a-136">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ada9a-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ada9a-137">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ada9a-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ada9a-138">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ada9a-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ada9a-139">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ada9a-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="ada9a-140">LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="ada9a-140">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)
