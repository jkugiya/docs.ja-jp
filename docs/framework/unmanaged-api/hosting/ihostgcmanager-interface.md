---
description: 詳細については、「IHostGCManager インターフェイス」を参照してください。
title: IHostGCManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
ms.openlocfilehash: da229c04eb5f5a27c34c133b5c88183d00f47c40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708659"
---
# <a name="ihostgcmanager-interface"></a><span data-ttu-id="93f48-103">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93f48-103">IHostGCManager Interface</span></span>

<span data-ttu-id="93f48-104">共通言語ランタイム (CLR) によって実装されるガベージコレクション機構でイベントのホストに通知するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="93f48-104">Provides methods that notify the host of events in the garbage collection mechanism implemented by the common language runtime (CLR).</span></span>  
  
## <a name="members"></a><span data-ttu-id="93f48-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="93f48-105">Members</span></span>  
  
|<span data-ttu-id="93f48-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="93f48-106">Member</span></span>|<span data-ttu-id="93f48-107">説明</span><span class="sxs-lookup"><span data-stu-id="93f48-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93f48-108">SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="93f48-108">SuspensionEnding Method</span></span>](ihostgcmanager-suspensionending-method.md)|<span data-ttu-id="93f48-109">CLR がガベージコレクションのために中断されたスレッドでタスクの実行を再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="93f48-109">Notifies the host that the CLR is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>|  
|[<span data-ttu-id="93f48-110">SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="93f48-110">SuspensionStarting Method</span></span>](ihostgcmanager-suspensionstarting-method.md)|<span data-ttu-id="93f48-111">ガベージコレクションを実行するために、CLR がタスクの実行を中断していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="93f48-111">Notifies the host that the CLR is suspending execution of tasks, to perform a garbage collection.</span></span>|  
|[<span data-ttu-id="93f48-112">ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="93f48-112">ThreadIsBlockingForSuspension Method</span></span>](ihostgcmanager-threadisblockingforsuspension-method.md)|<span data-ttu-id="93f48-113">メソッド呼び出しが行われたスレッドがガベージコレクションに対してブロックされようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="93f48-113">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93f48-114">要件</span><span class="sxs-lookup"><span data-stu-id="93f48-114">Requirements</span></span>  

 <span data-ttu-id="93f48-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93f48-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f48-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="93f48-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93f48-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="93f48-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93f48-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f48-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f48-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="93f48-119">See also</span></span>

- [<span data-ttu-id="93f48-120">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93f48-120">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="93f48-121">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93f48-121">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="93f48-122">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93f48-122">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="93f48-123">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93f48-123">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="93f48-124">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93f48-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
