---
description: '詳細情報: IGCThreadControl インターフェイス'
title: IGCThreadControl インターフェイス
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
ms.openlocfilehash: 07c76848668b1525f4ff45ba5de746beefe0e004
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709283"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="19692-103">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19692-103">IGCThreadControl Interface</span></span>

<span data-ttu-id="19692-104">ガベージコレクションに対してブロックされるスレッドのスケジュール設定に参加するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="19692-104">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19692-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="19692-105">Methods</span></span>  
  
|<span data-ttu-id="19692-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="19692-106">Method</span></span>|<span data-ttu-id="19692-107">説明</span><span class="sxs-lookup"><span data-stu-id="19692-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19692-108">SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="19692-108">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="19692-109">ランタイムがガベージコレクションまたはその他の中断後にスレッドを再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="19692-109">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="19692-110">SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="19692-110">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="19692-111">ランタイムがガベージコレクションまたは他の中断のためにスレッドの中断を開始していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="19692-111">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="19692-112">ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="19692-112">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="19692-113">呼び出しを行っているスレッドがブロックしようとしていることをホストに通知します。ガベージコレクションやその他の中断が考えられます。</span><span class="sxs-lookup"><span data-stu-id="19692-113">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="19692-114">要件</span><span class="sxs-lookup"><span data-stu-id="19692-114">Requirements</span></span>  

 <span data-ttu-id="19692-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19692-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19692-116">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="19692-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="19692-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="19692-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19692-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19692-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19692-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="19692-119">See also</span></span>

- [<span data-ttu-id="19692-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19692-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
