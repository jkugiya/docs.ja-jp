---
description: '詳細について: ICorProfilerCallback:: RuntimeSuspendAborted メソッド'
title: ICorProfilerCallback::RuntimeSuspendAborted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: 892de7ce0b4537f5526a58b6e70f66cd295be2df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788827"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="a67fd-103">ICorProfilerCallback::RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="a67fd-103">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>

<span data-ttu-id="a67fd-104">実行中のランタイムの中断をランタイムが中止したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a67fd-104">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a67fd-105">構文</span><span class="sxs-lookup"><span data-stu-id="a67fd-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a67fd-106">解説</span><span class="sxs-lookup"><span data-stu-id="a67fd-106">Remarks</span></span>  

 <span data-ttu-id="a67fd-107">2つのスレッドが同時にランタイムを中断しようとすると、実行時の中断が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a67fd-107">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="a67fd-108">[ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)コールバックまたは `RuntimeSuspendAborted` コールバックは、 [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)コールバックの後に1つのスレッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="a67fd-108">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="a67fd-109">コールバックは、 `RuntimeSuspendAborted` コールバックと同じスレッドで行われることが保証され `RuntimeSuspendStarted` ます。</span><span class="sxs-lookup"><span data-stu-id="a67fd-109">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a67fd-110">要件</span><span class="sxs-lookup"><span data-stu-id="a67fd-110">Requirements</span></span>  

 <span data-ttu-id="a67fd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a67fd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a67fd-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a67fd-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a67fd-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a67fd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a67fd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a67fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a67fd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a67fd-115">See also</span></span>

- [<span data-ttu-id="a67fd-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a67fd-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
