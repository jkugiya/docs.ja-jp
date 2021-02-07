---
description: 詳細については、「IHostCrst インターフェイス」を参照してください。
title: IHostCrst インターフェイス
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 7945f0087667c1d610a1a2370528b055af74d579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708880"
---
# <a name="ihostcrst-interface"></a><span data-ttu-id="64552-103">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64552-103">IHostCrst Interface</span></span>

<span data-ttu-id="64552-104">スレッド処理のためのクリティカルセクションのホストの表現として機能します。</span><span class="sxs-lookup"><span data-stu-id="64552-104">Serves as the host's representation of a critical section for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="64552-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="64552-105">Methods</span></span>  
  
|<span data-ttu-id="64552-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="64552-106">Method</span></span>|<span data-ttu-id="64552-107">説明</span><span class="sxs-lookup"><span data-stu-id="64552-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="64552-108">Enter メソッド</span><span class="sxs-lookup"><span data-stu-id="64552-108">Enter Method</span></span>](ihostcrst-enter-method.md)|<span data-ttu-id="64552-109">クリティカルセクションに入ります。</span><span class="sxs-lookup"><span data-stu-id="64552-109">Enters the critical section.</span></span>|  
|[<span data-ttu-id="64552-110">Leave メソッド</span><span class="sxs-lookup"><span data-stu-id="64552-110">Leave Method</span></span>](ihostcrst-leave-method.md)|<span data-ttu-id="64552-111">クリティカルセクションを残します。</span><span class="sxs-lookup"><span data-stu-id="64552-111">Leaves the critical section.</span></span>|  
|[<span data-ttu-id="64552-112">SetSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="64552-112">SetSpinCount Method</span></span>](ihostcrst-setspincount-method.md)|<span data-ttu-id="64552-113">クリティカルセクションのスピンカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="64552-113">Sets the spin count for the critical section.</span></span>|  
|[<span data-ttu-id="64552-114">TryEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="64552-114">TryEnter Method</span></span>](ihostcrst-tryenter-method.md)|<span data-ttu-id="64552-115">クリティカルセクションへの入力を試行し、成功または失敗を直ちに報告します。</span><span class="sxs-lookup"><span data-stu-id="64552-115">Attempts to enter the critical section, and reports success or failure immediately.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64552-116">解説</span><span class="sxs-lookup"><span data-stu-id="64552-116">Remarks</span></span>  

 <span data-ttu-id="64552-117">`IHostCrst` またはなどの Win32 関数を使用するのではなく、共通言語ランタイム (CLR) が、クリティカルセクションのホストの表現と直接通信できるようにし `EnterCriticalSection` `LeaveCriticalSection` ます。</span><span class="sxs-lookup"><span data-stu-id="64552-117">`IHostCrst` allows the common language runtime (CLR) to communicate directly with the host's representation of a critical section, rather than using Win32 functions such as `EnterCriticalSection` or `LeaveCriticalSection`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64552-118">要件</span><span class="sxs-lookup"><span data-stu-id="64552-118">Requirements</span></span>  

 <span data-ttu-id="64552-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64552-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64552-120">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="64552-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64552-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="64552-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64552-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64552-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64552-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="64552-123">See also</span></span>

- [<span data-ttu-id="64552-124">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64552-124">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="64552-125">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64552-125">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="64552-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64552-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
