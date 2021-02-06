---
description: '詳細について: ICorProfilerCallback:: RuntimeSuspendStarted メソッド'
title: ICorProfilerCallback::RuntimeSuspendStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: 7f7ba6a2a8523589b025d98ea925b77d05d8a59d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657425"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="9ac6e-103">ICorProfilerCallback::RuntimeSuspendStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="9ac6e-103">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>

<span data-ttu-id="9ac6e-104">ランタイムがすべてのランタイムスレッドを中断しようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9ac6e-104">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac6e-105">構文</span><span class="sxs-lookup"><span data-stu-id="9ac6e-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ac6e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ac6e-106">Parameters</span></span>  

 `suspendReason`  
 <span data-ttu-id="9ac6e-107">から中断の理由を示す [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="9ac6e-107">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ac6e-108">解説</span><span class="sxs-lookup"><span data-stu-id="9ac6e-108">Remarks</span></span>  

 <span data-ttu-id="9ac6e-109">アンマネージコード内のすべてのランタイムスレッドは、ランタイムを再入力しようとするまで実行を継続できます。</span><span class="sxs-lookup"><span data-stu-id="9ac6e-109">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="9ac6e-110">その時点で、ランタイムが再開されるまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="9ac6e-110">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="9ac6e-111">これは、ランタイムに入る新しいスレッドにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="9ac6e-111">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="9ac6e-112">ランタイム内のすべてのスレッドは、割り込み可能なコードに既に存在する場合は直ちに中断されます。または、割り込み可能なコードになると中断するように求められます。</span><span class="sxs-lookup"><span data-stu-id="9ac6e-112">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ac6e-113">要件</span><span class="sxs-lookup"><span data-stu-id="9ac6e-113">Requirements</span></span>  

 <span data-ttu-id="9ac6e-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ac6e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ac6e-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9ac6e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9ac6e-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ac6e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ac6e-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ac6e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac6e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ac6e-118">See also</span></span>

- [<span data-ttu-id="9ac6e-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ac6e-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9ac6e-120">RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="9ac6e-120">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="9ac6e-121">RuntimeSuspendFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="9ac6e-121">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
