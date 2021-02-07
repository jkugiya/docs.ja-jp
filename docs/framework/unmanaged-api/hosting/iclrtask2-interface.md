---
description: 詳細については、「ICLRTask2 インターフェイス」を参照してください。
title: ICLRTask2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 835b01e1c808c071e9393c5117d5e38415ec8eba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728635"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="2c2ff-103">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c2ff-103">ICLRTask2 Interface</span></span>

<span data-ttu-id="2c2ff-104">には、 [ICLRTask](iclrtask-interface.md) インターフェイスのすべての機能が用意されています。また、には、現在のスレッドでスレッドの中止を遅延させることができるメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-104">Provides all the functionality of the [ICLRTask](iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c2ff-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2c2ff-105">Methods</span></span>  
  
|<span data-ttu-id="2c2ff-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="2c2ff-106">Method</span></span>|<span data-ttu-id="2c2ff-107">説明</span><span class="sxs-lookup"><span data-stu-id="2c2ff-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c2ff-108">BeginPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="2c2ff-108">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="2c2ff-109">現在のスレッドの新しいスレッド中止要求を遅延します。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-109">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="2c2ff-110">EndPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="2c2ff-110">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="2c2ff-111">新しいまたは保留中のスレッド中止要求に対して、現在のスレッドでのスレッドの中止を許可します。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-111">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c2ff-112">解説</span><span class="sxs-lookup"><span data-stu-id="2c2ff-112">Remarks</span></span>  

 <span data-ttu-id="2c2ff-113">インターフェイスは、 `ICLRTask2` インターフェイスを継承 `ICLRTask` し、ホストがスレッドの中止を遅らせて、失敗しないコードの領域を保護できるようにするメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-113">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="2c2ff-114">を呼び出す `BeginPreventAsyncAbort` と、現在のスレッドの遅延スレッド中止カウンターがインクリメントされ、を呼び出すと、 `EndPreventAsyncAbort` そのカウンターがデクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-114">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="2c2ff-115">およびへの呼び出しは入れ子にする `BeginPreventAsyncAbort` `EndPreventAsyncAbort` ことができます。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-115">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="2c2ff-116">カウンターがゼロより大きい限り、現在のスレッドのスレッド中止は遅延されます。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="2c2ff-117">との呼び出し `BeginPreventAsyncAbort` がペアになって `EndPreventAsyncAbort` いない場合、現在のスレッドにスレッド中止を配信できない状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-117">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="2c2ff-118">遅延は、それ自体を中止するスレッドには適用されません。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="2c2ff-119">この機能によって公開されている機能は、仮想マシン (VM) によって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="2c2ff-120">これらの方法を誤用すると、VM で特定できない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="2c2ff-121">たとえば、最初に `EndPreventAsyncAbort` を呼び出しないでを呼び出す `BeginPreventAsyncAbort` と、VM で以前にインクリメントしたカウンターが0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="2c2ff-122">同様に、内部カウンターのオーバーフローはチェックされません。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="2c2ff-123">ホストと VM の両方によってインクリメントされるために整数の制限を超えた場合、結果として得られる動作は指定されません。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="2c2ff-124">から継承されたメンバー `ICLRTask` と、このインターフェイスの他の用途については、「 [ICLRTask](iclrtask-interface.md) インターフェイス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-124">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c2ff-125">要件</span><span class="sxs-lookup"><span data-stu-id="2c2ff-125">Requirements</span></span>  

 <span data-ttu-id="2c2ff-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2ff-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c2ff-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2c2ff-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c2ff-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2c2ff-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c2ff-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c2ff-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c2ff-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c2ff-130">See also</span></span>

- [<span data-ttu-id="2c2ff-131">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c2ff-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2c2ff-132">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c2ff-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2c2ff-133">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c2ff-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2c2ff-134">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c2ff-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="2c2ff-135">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2c2ff-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
