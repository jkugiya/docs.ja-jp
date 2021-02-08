---
description: 詳細については、「ICLRTaskManager インターフェイス」を参照してください。
title: ICLRTaskManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
ms.openlocfilehash: 0ce3641042725bc2f3acb95933ccd7a5bbe3bc4d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789740"
---
# <a name="iclrtaskmanager-interface"></a><span data-ttu-id="9804a-103">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9804a-103">ICLRTaskManager Interface</span></span>

<span data-ttu-id="9804a-104">ホストが、共通言語ランタイム (CLR) が新しいタスクを作成し、現在実行中のタスクを取得し、タスクの地理的言語とカルチャを設定することを明示的に要求するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9804a-104">Provides methods that allow the host to request explicitly that the common language runtime (CLR) create a new task, get the currently executing task, and set the geographic language and culture for the task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9804a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9804a-105">Methods</span></span>  
  
|<span data-ttu-id="9804a-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9804a-106">Method</span></span>|<span data-ttu-id="9804a-107">説明</span><span class="sxs-lookup"><span data-stu-id="9804a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9804a-108">CreateTask メソッド</span><span class="sxs-lookup"><span data-stu-id="9804a-108">CreateTask Method</span></span>](iclrtaskmanager-createtask-method.md)|<span data-ttu-id="9804a-109">CLR が新しい [ICLRTask](iclrtask-interface.md) インスタンスを作成することを明示的に要求します。</span><span class="sxs-lookup"><span data-stu-id="9804a-109">Requests explicitly that the CLR create a new [ICLRTask](iclrtask-interface.md) instance.</span></span>|  
|[<span data-ttu-id="9804a-110">GetCurrentTask メソッド</span><span class="sxs-lookup"><span data-stu-id="9804a-110">GetCurrentTask Method</span></span>](iclrtaskmanager-getcurrenttask-method.md)|<span data-ttu-id="9804a-111">`ICLRTask`現在実行中のタスクを表すインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="9804a-111">Gets the `ICLRTask` instance that represents the task that is currently executing.</span></span>|  
|[<span data-ttu-id="9804a-112">GetCurrentTaskType メソッド</span><span class="sxs-lookup"><span data-stu-id="9804a-112">GetCurrentTaskType Method</span></span>](iclrtaskmanager-getcurrenttasktype-method.md)|<span data-ttu-id="9804a-113">現在実行中のタスクの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="9804a-113">Gets the type of the task that is currently executing.</span></span>|  
|[<span data-ttu-id="9804a-114">SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="9804a-114">SetLocale Method</span></span>](iclrtaskmanager-setlocale-method.md)|<span data-ttu-id="9804a-115">現在実行中のタスクのロケール識別子がホストによって変更されたことを CLR に通知します。</span><span class="sxs-lookup"><span data-stu-id="9804a-115">Notifies the CLR that the host has modified the locale identifier on the currently executing task.</span></span>|  
|[<span data-ttu-id="9804a-116">SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="9804a-116">SetUILocale Method</span></span>](iclrtaskmanager-setuilocale-method.md)|<span data-ttu-id="9804a-117">現在実行中のタスクのユーザーインターフェイスのロケール識別子がホストによって変更されたことを、共通言語ランタイムに通知します。</span><span class="sxs-lookup"><span data-stu-id="9804a-117">Notifies the common language runtime that the host has modified the user interface locale identifier on the currently executing task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9804a-118">解説</span><span class="sxs-lookup"><span data-stu-id="9804a-118">Remarks</span></span>  

 <span data-ttu-id="9804a-119">ホスト環境で実行されている各タスクは、ホスト側 ( [IHostTask](ihosttask-interface.md)のインスタンス) と CLR 側 ( [ICLRTask](iclrtask-interface.md)のインスタンス) の両方で表現されます。</span><span class="sxs-lookup"><span data-stu-id="9804a-119">Each task that is running in a hosted environment has representations both on the host side (an instance of [IHostTask](ihosttask-interface.md)) and on the CLR side (an instance of [ICLRTask](iclrtask-interface.md)).</span></span> <span data-ttu-id="9804a-120">ホストまたは CLR がタスクの作成を開始することはできますが、ホストと CLR の間でタスクに関して正常に通信できるように、ホスト側表現を対応する CLR 側表現に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="9804a-120">Either the host or the CLR can initiate the creation of a task, but the host-side representation must be associated with a corresponding CLR-side representation to ensure successful communication between the host and the CLR regarding the task.</span></span> <span data-ttu-id="9804a-121">マネージコードをオペレーティングシステムのスレッドで実行するには、2つのオブジェクトを作成してインスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9804a-121">The two objects must be created and instantiated before managed code can execute on an operating system thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9804a-122">要件</span><span class="sxs-lookup"><span data-stu-id="9804a-122">Requirements</span></span>  

 <span data-ttu-id="9804a-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9804a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9804a-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9804a-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9804a-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9804a-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9804a-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9804a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9804a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="9804a-127">See also</span></span>

- [<span data-ttu-id="9804a-128">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9804a-128">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9804a-129">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9804a-129">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9804a-130">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9804a-130">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9804a-131">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9804a-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
