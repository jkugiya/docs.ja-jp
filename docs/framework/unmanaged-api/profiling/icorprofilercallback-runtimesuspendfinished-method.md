---
description: '詳細について: ICorProfilerCallback:: RuntimeSuspendFinished メソッド'
title: ICorProfilerCallback::RuntimeSuspendFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
ms.openlocfilehash: eab7111f28c77f1440c0e392a36fb2b083c138e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657516"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="0badd-103">ICorProfilerCallback::RuntimeSuspendFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="0badd-103">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>

<span data-ttu-id="0badd-104">ランタイムがすべてのランタイムスレッドの中断を完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0badd-104">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0badd-105">構文</span><span class="sxs-lookup"><span data-stu-id="0badd-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0badd-106">解説</span><span class="sxs-lookup"><span data-stu-id="0badd-106">Remarks</span></span>  

 <span data-ttu-id="0badd-107">アンマネージコード内のすべてのランタイムスレッドは、ランタイムを再入力しようとするまで実行を継続できます。</span><span class="sxs-lookup"><span data-stu-id="0badd-107">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="0badd-108">その時点で、ランタイムが再開されるまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="0badd-108">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="0badd-109">これは、ランタイムに入る新しいスレッドにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="0badd-109">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="0badd-110">ランタイム内のすべてのスレッドは、割り込み可能なコードに既に存在する場合は直ちに中断されます。または、割り込み可能なコードになると中断するように求められます。</span><span class="sxs-lookup"><span data-stu-id="0badd-110">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="0badd-111">`RuntimeSuspendFinished`コールバックは、 [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)コールバックと同じスレッドで行われることが保証されています。</span><span class="sxs-lookup"><span data-stu-id="0badd-111">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0badd-112">要件</span><span class="sxs-lookup"><span data-stu-id="0badd-112">Requirements</span></span>  

 <span data-ttu-id="0badd-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0badd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0badd-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0badd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0badd-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0badd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0badd-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0badd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0badd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0badd-117">See also</span></span>

- [<span data-ttu-id="0badd-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0badd-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0badd-119">RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="0badd-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
