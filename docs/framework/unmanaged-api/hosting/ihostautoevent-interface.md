---
description: 詳細については、「IHostAutoEvent インターフェイス」を参照してください。
title: IHostAutoEvent インターフェイス
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
ms.openlocfilehash: 4aea282dbe2067d50214b237650ba01fb8bf22a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789490"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="10ffa-103">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10ffa-103">IHostAutoEvent Interface</span></span>

<span data-ttu-id="10ffa-104">自動リセットイベントのホストの実装の表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="10ffa-104">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10ffa-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="10ffa-105">Methods</span></span>  
  
|<span data-ttu-id="10ffa-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="10ffa-106">Method</span></span>|<span data-ttu-id="10ffa-107">説明</span><span class="sxs-lookup"><span data-stu-id="10ffa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10ffa-108">Set メソッド</span><span class="sxs-lookup"><span data-stu-id="10ffa-108">Set Method</span></span>](ihostautoevent-set-method.md)|<span data-ttu-id="10ffa-109">現在の `IHostAutoEvent` インスタンスをシグナル状態に設定します。</span><span class="sxs-lookup"><span data-stu-id="10ffa-109">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="10ffa-110">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="10ffa-110">Wait Method</span></span>](ihostautoevent-wait-method.md)|<span data-ttu-id="10ffa-111">`IHostAutoEvent`イベントが所有されるか、指定した時間が経過するまで、現在のインスタンスを待機させます。</span><span class="sxs-lookup"><span data-stu-id="10ffa-111">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10ffa-112">要件</span><span class="sxs-lookup"><span data-stu-id="10ffa-112">Requirements</span></span>  

 <span data-ttu-id="10ffa-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10ffa-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10ffa-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="10ffa-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10ffa-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="10ffa-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10ffa-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10ffa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10ffa-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="10ffa-117">See also</span></span>

- [<span data-ttu-id="10ffa-118">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10ffa-118">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="10ffa-119">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10ffa-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="10ffa-120">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10ffa-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="10ffa-121">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10ffa-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
