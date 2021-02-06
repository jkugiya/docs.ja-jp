---
description: '詳細について: ICorProfilerCallback:: RuntimeThreadSuspended メソッド'
title: ICorProfilerCallback::RuntimeThreadSuspended メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: f7c2f5baf5a320375d9a2606ca05b13d522336be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657334"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="2895f-103">ICorProfilerCallback::RuntimeThreadSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="2895f-103">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>

<span data-ttu-id="2895f-104">指定されたスレッドが中断されたか、中断されようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2895f-104">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2895f-105">構文</span><span class="sxs-lookup"><span data-stu-id="2895f-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2895f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2895f-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="2895f-107">から中断されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="2895f-107">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2895f-108">解説</span><span class="sxs-lookup"><span data-stu-id="2895f-108">Remarks</span></span>  

 <span data-ttu-id="2895f-109">通知は、 `RuntimeThreadSuspended` [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) と、関連付けられている [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) コールバックの間でいつでも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2895f-109">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="2895f-110">[ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)との間で発生する通知 `RuntimeResumeStarted` は、アンマネージコードで実行されていて、ランタイムへの入力時に中断されたスレッド用です。</span><span class="sxs-lookup"><span data-stu-id="2895f-110">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="2895f-111">通常、このコールバックは、スレッドが中断された直後に発生します。</span><span class="sxs-lookup"><span data-stu-id="2895f-111">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="2895f-112">ただし、現在実行中のスレッド (このコールバックを呼び出したスレッド) が中断されているスレッドである場合、このコールバックはスレッドが中断される直前に発生します。</span><span class="sxs-lookup"><span data-stu-id="2895f-112">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2895f-113">要件</span><span class="sxs-lookup"><span data-stu-id="2895f-113">Requirements</span></span>  

 <span data-ttu-id="2895f-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2895f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2895f-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2895f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2895f-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2895f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2895f-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2895f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2895f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2895f-118">See also</span></span>

- [<span data-ttu-id="2895f-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2895f-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2895f-120">RuntimeThreadResumed メソッド</span><span class="sxs-lookup"><span data-stu-id="2895f-120">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
