---
description: '詳細については、次を参照してください: ICLRTask:: SwitchOut メソッド'
title: ICLRTask::SwitchOut メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 6c491c4d9005fb850c5adecd025730f1ea71f513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784939"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="9e499-103">ICLRTask::SwitchOut メソッド</span><span class="sxs-lookup"><span data-stu-id="9e499-103">ICLRTask::SwitchOut Method</span></span>

<span data-ttu-id="9e499-104">現在の [ICLRTask](iclrtask-interface.md) インスタンスによって表されるタスクが操作可能な状態ではなくなったことを、共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="9e499-104">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e499-105">構文</span><span class="sxs-lookup"><span data-stu-id="9e499-105">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9e499-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="9e499-106">Return Value</span></span>  
  
|<span data-ttu-id="9e499-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e499-107">HRESULT</span></span>|<span data-ttu-id="9e499-108">説明</span><span class="sxs-lookup"><span data-stu-id="9e499-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e499-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e499-109">S_OK</span></span>|<span data-ttu-id="9e499-110">`SwitchOut` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9e499-110">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="9e499-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e499-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e499-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9e499-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e499-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e499-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e499-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9e499-114">The call timed out.</span></span>|  
|<span data-ttu-id="9e499-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e499-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e499-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9e499-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e499-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e499-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e499-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9e499-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e499-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e499-119">E_FAIL</span></span>|<span data-ttu-id="9e499-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9e499-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e499-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9e499-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e499-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9e499-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e499-123">解説</span><span class="sxs-lookup"><span data-stu-id="9e499-123">Remarks</span></span>  

 <span data-ttu-id="9e499-124">ホストは、 `SwitchOut` 現在のインスタンスが表すタスクの実行を一時的に停止したことを CLR に通知し、タスクを再 `ICLRTask` スケジュールします。</span><span class="sxs-lookup"><span data-stu-id="9e499-124">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e499-125">要件</span><span class="sxs-lookup"><span data-stu-id="9e499-125">Requirements</span></span>  

 <span data-ttu-id="9e499-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e499-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e499-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9e499-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e499-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9e499-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e499-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e499-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e499-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e499-130">See also</span></span>

- [<span data-ttu-id="9e499-131">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e499-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9e499-132">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e499-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9e499-133">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e499-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9e499-134">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9e499-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
