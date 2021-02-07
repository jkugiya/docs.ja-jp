---
description: '詳細について: ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 メソッド'
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
ms.openlocfilehash: c741054c50fb74afe79f10607e24424a07d2f8c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687026"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a><span data-ttu-id="c5178-103">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 メソッド</span><span class="sxs-lookup"><span data-stu-id="c5178-103">ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 Method</span></span>

<span data-ttu-id="c5178-104">[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、および[FunctionTailcall3](functiontailcall3-function.md)の各関数で呼び出されるプロファイラー実装関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5178-104">Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5178-105">構文</span><span class="sxs-lookup"><span data-stu-id="c5178-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5178-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5178-106">Parameters</span></span>  

 `pFuncEnter3`  
 <span data-ttu-id="c5178-107">からコールバックとして使用される実装へのポインター `FunctionEnter3` 。</span><span class="sxs-lookup"><span data-stu-id="c5178-107">[in] A pointer to the implementation to be used as the `FunctionEnter3` callback.</span></span>  
  
 `pFuncLeave3`  
 <span data-ttu-id="c5178-108">からコールバックとして使用される実装へのポインター `FunctionLeave3` 。</span><span class="sxs-lookup"><span data-stu-id="c5178-108">[in] A pointer to the implementation to be used as the `FunctionLeave3` callback.</span></span>  
  
 `pFuncTailcall3`  
 <span data-ttu-id="c5178-109">からコールバックとして使用される実装へのポインター `FunctionTailcall3` 。</span><span class="sxs-lookup"><span data-stu-id="c5178-109">[in] A pointer to the implementation to be used as the `FunctionTailcall3` callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5178-110">解説</span><span class="sxs-lookup"><span data-stu-id="c5178-110">Remarks</span></span>  

 <span data-ttu-id="c5178-111">[FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、および [FunctionTailcall3](functiontailcall3-function.md) フックは、スタックフレームと引数検査を提供しません。</span><span class="sxs-lookup"><span data-stu-id="c5178-111">[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md) hooks do not provide stack frame and argument inspection.</span></span> <span data-ttu-id="c5178-112">この情報にアクセスするには、 `COR_PRF_ENABLE_FUNCTION_ARGS` 、 `COR_PRF_ENABLE_FUNCTION_RETVAL` 、および/または  `COR_PRF_ENABLE_FRAME_INFO` フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5178-112">To access that information, the `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`, and/or  `COR_PRF_ENABLE_FRAME_INFO` flags have to be set.</span></span> <span data-ttu-id="c5178-113">プロファイラーは、 [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) メソッドを使用してイベントフラグを設定し、 [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) メソッドを使用してこの関数の実装を登録できます。</span><span class="sxs-lookup"><span data-stu-id="c5178-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="c5178-114">コールバックのセットは一度に1つしかアクティブにできません。また、最新バージョンが優先されます。</span><span class="sxs-lookup"><span data-stu-id="c5178-114">Only one set of callbacks may be active at a time, and the newest version takes precedence.</span></span> <span data-ttu-id="c5178-115">したがって、プロファイラーが [SetEnterLeaveFunctionHooks2 メソッド](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) とメソッドの両方を呼び出すと `SetEnterLeaveFunctionHooks3` 、 `SetEnterLeaveFunctionHooks3` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5178-115">Therefore, if a profiler calls both the [SetEnterLeaveFunctionHooks2 Method](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) and the `SetEnterLeaveFunctionHooks3` method, `SetEnterLeaveFunctionHooks3` is used.</span></span>  
  
 <span data-ttu-id="c5178-116">メソッドは、 `SetEnterLeaveFunctionHooks3` プロファイラーの [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) コールバックからのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c5178-116">The `SetEnterLeaveFunctionHooks3` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5178-117">要件</span><span class="sxs-lookup"><span data-stu-id="c5178-117">Requirements</span></span>  

 <span data-ttu-id="c5178-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5178-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5178-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5178-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5178-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5178-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5178-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5178-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5178-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5178-122">See also</span></span>

- [<span data-ttu-id="c5178-123">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c5178-123">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="c5178-124">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="c5178-124">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="c5178-125">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="c5178-125">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="c5178-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="c5178-126">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="c5178-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c5178-127">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="c5178-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c5178-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="c5178-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c5178-129">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="c5178-130">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="c5178-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
- [<span data-ttu-id="c5178-131">ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="c5178-131">ICorProfilerInfo3</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c5178-132">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5178-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c5178-133">プロファイル</span><span class="sxs-lookup"><span data-stu-id="c5178-133">Profiling</span></span>](index.md)
