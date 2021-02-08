---
description: '詳細について: ICLRTask2:: EndPreventAsyncAbort メソッド'
title: ICLRTask2::EndPreventAsyncAbort メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 964a68c1ad6d5aa6a95560d2870e135640283590
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799500"
---
# <a name="iclrtask2endpreventasyncabort-method"></a><span data-ttu-id="b0fe6-103">ICLRTask2::EndPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="b0fe6-103">ICLRTask2::EndPreventAsyncAbort Method</span></span>

<span data-ttu-id="b0fe6-104">新しいまたは保留中のスレッド中止要求に対して、現在のスレッドでのスレッドの中止を許可します。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-104">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0fe6-105">構文</span><span class="sxs-lookup"><span data-stu-id="b0fe6-105">Syntax</span></span>  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b0fe6-106">戻り値</span><span class="sxs-lookup"><span data-stu-id="b0fe6-106">Return Value</span></span>  

 <span data-ttu-id="b0fe6-107">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-107">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b0fe6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0fe6-108">HRESULT</span></span>|<span data-ttu-id="b0fe6-109">説明</span><span class="sxs-lookup"><span data-stu-id="b0fe6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0fe6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0fe6-110">S_OK</span></span>|<span data-ttu-id="b0fe6-111">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-111">The method completed successfully.</span></span>|  
|<span data-ttu-id="b0fe6-112">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="b0fe6-112">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="b0fe6-113">メソッドは、現在のスレッドではないスレッドで呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-113">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0fe6-114">解説</span><span class="sxs-lookup"><span data-stu-id="b0fe6-114">Remarks</span></span>  

 <span data-ttu-id="b0fe6-115">このメソッドを呼び出すと、現在のスレッドの遅延スレッド中止カウンターが1つ減少します。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-115">Calling this method decrements the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="b0fe6-116">[ICLRTask2:: BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md)の呼び出しと `EndPreventAsyncAbort` 入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-116">Calls to [ICLRTask2::BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="b0fe6-117">カウンターがゼロより大きい限り、現在のスレッドのスレッド中止は遅延されます。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-117">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="b0fe6-118">この機能によって公開されている機能は、仮想マシン (VM) によって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="b0fe6-119">これらの方法を誤用すると、VM で特定できない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="b0fe6-120">たとえば、最初に `EndPreventAsyncAbort` を呼び出しないでを呼び出す `BeginPreventAsyncAbort` と、VM で以前にインクリメントしたカウンターが0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="b0fe6-121">同様に、内部カウンターのオーバーフローはチェックされません。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="b0fe6-122">ホストと VM の両方によってインクリメントされるために整数の制限を超えた場合、結果として得られる動作は指定されません。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0fe6-123">要件</span><span class="sxs-lookup"><span data-stu-id="b0fe6-123">Requirements</span></span>  

 <span data-ttu-id="b0fe6-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fe6-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0fe6-125">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b0fe6-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b0fe6-126">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b0fe6-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b0fe6-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0fe6-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0fe6-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0fe6-128">See also</span></span>

- [<span data-ttu-id="b0fe6-129">BeginPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="b0fe6-129">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)
- [<span data-ttu-id="b0fe6-130">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0fe6-130">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="b0fe6-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0fe6-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b0fe6-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0fe6-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b0fe6-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0fe6-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="b0fe6-134">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b0fe6-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
