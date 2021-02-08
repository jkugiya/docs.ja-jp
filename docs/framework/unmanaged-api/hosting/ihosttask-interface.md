---
description: ': IHostTask インターフェイスの詳細情報'
title: IHostTask インターフェイス
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
ms.openlocfilehash: c46bbdd2e881c20d1ffd634bec8ddfa3b70b0f82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784666"
---
# <a name="ihosttask-interface"></a><span data-ttu-id="42421-103">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42421-103">IHostTask Interface</span></span>

<span data-ttu-id="42421-104">共通言語ランタイム (CLR) がホストと通信してタスクを管理できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="42421-104">Provides methods that allow the common language runtime (CLR) to communicate with the host to manage tasks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42421-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-105">Methods</span></span>  
  
|<span data-ttu-id="42421-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-106">Method</span></span>|<span data-ttu-id="42421-107">説明</span><span class="sxs-lookup"><span data-stu-id="42421-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42421-108">Alert メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-108">Alert Method</span></span>](ihosttask-alert-method.md)|<span data-ttu-id="42421-109">現在のインスタンスによって表されるタスクをホストがスリープ解除する `IHostTask` ように要求します。これにより、タスクを中止できます。</span><span class="sxs-lookup"><span data-stu-id="42421-109">Requests that the host wake the task represented by the current `IHostTask` instance, so the task can be aborted.</span></span>|  
|[<span data-ttu-id="42421-110">GetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-110">GetPriority Method</span></span>](ihosttask-getpriority-method.md)|<span data-ttu-id="42421-111">現在のインスタンスによって表されるタスクのスレッド優先度レベルを取得し `IHostTask` ます。</span><span class="sxs-lookup"><span data-stu-id="42421-111">Gets the thread priority level of the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="42421-112">Join メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-112">Join Method</span></span>](ihosttask-join-method.md)|<span data-ttu-id="42421-113">現在のインスタンスによって表されるタスクが `IHostTask` 完了するか、指定された時間が経過するか、または [IHostTask:: Alert](ihosttask-alert-method.md) が呼び出されるまで、呼び出し元のタスクをブロックします。</span><span class="sxs-lookup"><span data-stu-id="42421-113">Blocks the calling task until the task represented by the current `IHostTask` instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>|  
|[<span data-ttu-id="42421-114">SetCLRTask メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-114">SetCLRTask Method</span></span>](ihosttask-setclrtask-method.md)|<span data-ttu-id="42421-115">[ICLRTask インターフェイス](iclrtask-interface.md)インスタンスを現在のインスタンスに関連付け `IHostTask` ます。</span><span class="sxs-lookup"><span data-stu-id="42421-115">Associates an [ICLRTask Interface](iclrtask-interface.md) instance with the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="42421-116">SetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-116">SetPriority Method</span></span>](ihosttask-setpriority-method.md)|<span data-ttu-id="42421-117">現在のインスタンスによって表されるタスクのスレッドの優先度レベルをホストが調整するように要求 `IHostTask` します。</span><span class="sxs-lookup"><span data-stu-id="42421-117">Requests that the host adjust the thread priority level for the task represented by the current `IHostTask` instance.</span></span>|  
|[<span data-ttu-id="42421-118">Start メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-118">Start Method</span></span>](ihosttask-start-method.md)|<span data-ttu-id="42421-119">現在のインスタンスによって表されるタスクを中断状態からライブ状態に移行するようホストに要求し `IHostTask` ます。このとき、コードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="42421-119">Requests that the host move the task represented by the current `IHostTask` instance from a suspended state to a live state, in which code can be executed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42421-120">解説</span><span class="sxs-lookup"><span data-stu-id="42421-120">Remarks</span></span>  

 <span data-ttu-id="42421-121">CLR は、によって定義されたメソッドを呼び出して、 `IHostTask` タスクを開始したり、スレッドの優先度レベルを設定したりします。</span><span class="sxs-lookup"><span data-stu-id="42421-121">The CLR calls methods defined by `IHostTask` to start a task, set its thread priority level, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42421-122">要件</span><span class="sxs-lookup"><span data-stu-id="42421-122">Requirements</span></span>  

 <span data-ttu-id="42421-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42421-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42421-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="42421-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42421-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="42421-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42421-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42421-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42421-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="42421-127">See also</span></span>

- [<span data-ttu-id="42421-128">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42421-128">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="42421-129">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42421-129">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="42421-130">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42421-130">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="42421-131">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42421-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
