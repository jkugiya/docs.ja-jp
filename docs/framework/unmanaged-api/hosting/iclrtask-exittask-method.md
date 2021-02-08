---
description: '詳細情報: ICLRTask:: ExitTask メソッド'
title: ICLRTask::ExitTask メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: 267b7f284ccac5b535a72dab425c035b6c689361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784965"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="2c250-103">ICLRTask::ExitTask メソッド</span><span class="sxs-lookup"><span data-stu-id="2c250-103">ICLRTask::ExitTask Method</span></span>

<span data-ttu-id="2c250-104">現在の [ICLRTask](iclrtask-interface.md) インスタンスによって表されるタスクが終了していることを共通言語ランタイム (CLR) に通知し、タスクを正常にシャットダウンすることを試みます。</span><span class="sxs-lookup"><span data-stu-id="2c250-104">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c250-105">構文</span><span class="sxs-lookup"><span data-stu-id="2c250-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2c250-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="2c250-106">Return Value</span></span>  
  
|<span data-ttu-id="2c250-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c250-107">HRESULT</span></span>|<span data-ttu-id="2c250-108">説明</span><span class="sxs-lookup"><span data-stu-id="2c250-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2c250-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="2c250-109">S_OK</span></span>|<span data-ttu-id="2c250-110">`ExitTask` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="2c250-110">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="2c250-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2c250-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2c250-112">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="2c250-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2c250-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2c250-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2c250-114">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2c250-114">The call timed out.</span></span>|  
|<span data-ttu-id="2c250-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2c250-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2c250-116">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2c250-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2c250-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2c250-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2c250-118">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="2c250-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2c250-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2c250-119">E_FAIL</span></span>|<span data-ttu-id="2c250-120">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2c250-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2c250-121">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2c250-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2c250-122">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2c250-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c250-123">解説</span><span class="sxs-lookup"><span data-stu-id="2c250-123">Remarks</span></span>  

 <span data-ttu-id="2c250-124">`ExitTask` アンマネージタイプライブラリからスレッドをデタッチするのと同様の方法で、タスクのクリーンシャットダウンを試みます。</span><span class="sxs-lookup"><span data-stu-id="2c250-124">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c250-125">要件</span><span class="sxs-lookup"><span data-stu-id="2c250-125">Requirements</span></span>  

 <span data-ttu-id="2c250-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c250-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c250-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2c250-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c250-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2c250-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c250-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c250-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c250-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c250-130">See also</span></span>

- [<span data-ttu-id="2c250-131">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c250-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2c250-132">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c250-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2c250-133">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c250-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2c250-134">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c250-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
