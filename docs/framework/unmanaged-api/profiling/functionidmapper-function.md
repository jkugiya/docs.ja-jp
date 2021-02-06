---
description: '詳細情報: FunctionIDMapper 関数'
title: FunctionIDMapper 関数
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: dca39d9d5269148fda12c50130f35bdeb10cb19d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648650"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="7bb50-103">FunctionIDMapper 関数</span><span class="sxs-lookup"><span data-stu-id="7bb50-103">FunctionIDMapper Function</span></span>

<span data-ttu-id="7bb50-104">関数の特定の識別子が、その関数の [FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)、および [FunctionTailcall2](functiontailcall2-function.md) コールバックで使用される代替 ID に再マップされる可能性があることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7bb50-104">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="7bb50-105">また `FunctionIDMapper` により、プロファイラーはその関数のコールバックを受信するかどうかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="7bb50-105">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb50-106">構文</span><span class="sxs-lookup"><span data-stu-id="7bb50-106">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bb50-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7bb50-107">Parameters</span></span>

- `funcId`

  <span data-ttu-id="7bb50-108">\[in) 再マップする関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="7bb50-108">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="7bb50-109">\[out] プロファイラーが、、の各コールバックを受信する場合は、に設定する値へのポインター `true` `FunctionEnter2` `FunctionLeave2` `FunctionTailcall2` 。それ以外の場合は、この値をに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="7bb50-109">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7bb50-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="7bb50-110">Return Value</span></span>  

 <span data-ttu-id="7bb50-111">プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。</span><span class="sxs-lookup"><span data-stu-id="7bb50-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="7bb50-112">`false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="7bb50-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="7bb50-113">それ以外の場合、null 値が返されると、処理が停止する可能性があるなど、予測できない結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7bb50-113">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bb50-114">解説</span><span class="sxs-lookup"><span data-stu-id="7bb50-114">Remarks</span></span>  

 <span data-ttu-id="7bb50-115">`FunctionIDMapper`関数はコールバックです。</span><span class="sxs-lookup"><span data-stu-id="7bb50-115">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="7bb50-116">プロファイラーによって実装され、関数 ID を他の識別子にマップし直すことができます。これは、プロファイラーにとって便利です。</span><span class="sxs-lookup"><span data-stu-id="7bb50-116">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="7bb50-117">は、指定された `FunctionIDMapper` 関数に使用される代替 ID を返します。</span><span class="sxs-lookup"><span data-stu-id="7bb50-117">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="7bb50-118">次に、実行エンジンは、従来の関数 ID に加えて、この代替 ID を `clientData` 、、、およびフックのパラメーターでプロファイラーに渡して `FunctionEnter2` 、 `FunctionLeave2` フックが呼び出されている関数を識別することによって、プロファイラーの要求を受け入れ `FunctionTailcall2` ます。</span><span class="sxs-lookup"><span data-stu-id="7bb50-118">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="7bb50-119">[ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)メソッドを使用して、関数の実装を指定でき `FunctionIDMapper` ます。</span><span class="sxs-lookup"><span data-stu-id="7bb50-119">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="7bb50-120">メソッドを呼び出すことができるのは1回だけです。このメソッドは、 `ICorProfilerInfo::SetFunctionIDMapper` [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) コールバックで行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7bb50-120">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="7bb50-121">既定では、 [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)を使用して COR_PRF_MONITOR_ENTERLEAVE フラグを設定し、 [ICorProfilerInfo:: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) または [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)を介してフックを設定するプロファイラーは `FunctionEnter2` 、 `FunctionLeave2` `FunctionTailcall2` すべての関数に対して、、およびのコールバックを受け取る必要があると想定されています。</span><span class="sxs-lookup"><span data-stu-id="7bb50-121">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="7bb50-122">ただし、 `FunctionIDMapper` をに設定することにより、特定の関数に対してこれらのコールバックが受信されないように、を実装する場合があり `pbHookFunction` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="7bb50-122">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="7bb50-123">プロファイラーは、プロファイルされたアプリケーションの複数のスレッドが同時に同じメソッドまたは関数を呼び出す場合を許容します。</span><span class="sxs-lookup"><span data-stu-id="7bb50-123">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="7bb50-124">このような場合、プロファイラーは同じに `FunctionIDMapper` 対して複数のコールバックを受け取ることがあり `FunctionID` ます。</span><span class="sxs-lookup"><span data-stu-id="7bb50-124">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="7bb50-125">プロファイラーは、同じを使用して複数回呼び出された場合に、このコールバックから同じ値を返すようにする必要があり `FunctionID` ます。</span><span class="sxs-lookup"><span data-stu-id="7bb50-125">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bb50-126">要件</span><span class="sxs-lookup"><span data-stu-id="7bb50-126">Requirements</span></span>  

 <span data-ttu-id="7bb50-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7bb50-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb50-128">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="7bb50-128">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7bb50-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bb50-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bb50-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb50-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb50-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bb50-131">See also</span></span>

- [<span data-ttu-id="7bb50-132">SetFunctionIDMapper メソッド</span><span class="sxs-lookup"><span data-stu-id="7bb50-132">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="7bb50-133">FunctionIDMapper2 関数</span><span class="sxs-lookup"><span data-stu-id="7bb50-133">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="7bb50-134">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="7bb50-134">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="7bb50-135">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="7bb50-135">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="7bb50-136">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="7bb50-136">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="7bb50-137">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="7bb50-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
