---
description: '詳細について: IHostTaskManager:: SwitchToTask メソッド'
title: IHostTaskManager::SwitchToTask メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SwitchToTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SwitchToTask
helpviewer_keywords:
- IHostTaskManager::SwitchToTask method [.NET Framework hosting]
- SwitchToTask method [.NET Framework hosting]
ms.assetid: 35d0c27e-4b14-49ce-810d-7ab2120177e8
topic_type:
- apiref
ms.openlocfilehash: 6333dcdf7e1bbe6bde575f53f4743a1300c770f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789360"
---
# <a name="ihosttaskmanagerswitchtotask-method"></a><span data-ttu-id="d8875-103">IHostTaskManager::SwitchToTask メソッド</span><span class="sxs-lookup"><span data-stu-id="d8875-103">IHostTaskManager::SwitchToTask Method</span></span>

<span data-ttu-id="d8875-104">現在のタスクを切り替える必要があることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="d8875-104">Notifies the host that it should switch out the current task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8875-105">構文</span><span class="sxs-lookup"><span data-stu-id="d8875-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchToTask (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8875-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8875-106">Parameters</span></span>  

 `option`  
 <span data-ttu-id="d8875-107">から [WAIT_OPTION](wait-option-enumeration.md) 列挙値の1つ。要求された操作がブロックされた場合にホストが実行するアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="d8875-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating the action the host should take if the requested operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8875-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d8875-108">Return Value</span></span>  
  
|<span data-ttu-id="d8875-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d8875-109">HRESULT</span></span>|<span data-ttu-id="d8875-110">説明</span><span class="sxs-lookup"><span data-stu-id="d8875-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d8875-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d8875-111">S_OK</span></span>|<span data-ttu-id="d8875-112">`SwitchToTask` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d8875-112">`SwitchToTask` returned successfully.</span></span>|  
|<span data-ttu-id="d8875-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d8875-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d8875-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d8875-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d8875-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d8875-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d8875-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d8875-116">The call timed out.</span></span>|  
|<span data-ttu-id="d8875-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d8875-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d8875-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d8875-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d8875-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d8875-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d8875-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d8875-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d8875-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d8875-121">E_FAIL</span></span>|<span data-ttu-id="d8875-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d8875-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d8875-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d8875-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d8875-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d8875-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8875-125">解説</span><span class="sxs-lookup"><span data-stu-id="d8875-125">Remarks</span></span>  

 <span data-ttu-id="d8875-126">ホストは、必要に応じて別のタスクに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="d8875-126">The host can switch in another task as desired or needed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8875-127">`SwitchToTask` では、ホストが切り替える必要があるタスクが指定されていません。これは、切り替え元のタスクだけを指定します。</span><span class="sxs-lookup"><span data-stu-id="d8875-127">`SwitchToTask` does not specify which task the host should switch to; it specifies only the task that it should switch from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8875-128">要件</span><span class="sxs-lookup"><span data-stu-id="d8875-128">Requirements</span></span>  

 <span data-ttu-id="d8875-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8875-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8875-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d8875-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8875-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d8875-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8875-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8875-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8875-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8875-133">See also</span></span>

- [<span data-ttu-id="d8875-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8875-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d8875-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8875-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d8875-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8875-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d8875-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8875-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
