---
description: '詳細について: ICorProfilerInfo3:: SetFunctionIDMapper2 メソッド'
title: ICorProfilerInfo3::SetFunctionIDMapper2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 4847d3bd7b8bf6142da0f32c3558016b2c758087
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686987"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="3122f-103">ICorProfilerInfo3::SetFunctionIDMapper2 メソッド</span><span class="sxs-lookup"><span data-stu-id="3122f-103">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>

<span data-ttu-id="3122f-104">`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。</span><span class="sxs-lookup"><span data-stu-id="3122f-104">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="3122f-105">このメソッドは、追加のデータパラメーターを使用して [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) メソッドを拡張します。これは、プロファイラーがランタイムを明確に区別するために使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3122f-105">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3122f-106">構文</span><span class="sxs-lookup"><span data-stu-id="3122f-106">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3122f-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3122f-107">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="3122f-108">から[](functionidmapper2-function.md) `FunctionID` 値を代替値にマップするために呼び出される FunctionIDMapper2 実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3122f-108">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="3122f-109">から現在のランタイムによって行われたすべての [FunctionIDMapper2](functionidmapper2-function.md) 関数呼び出しに渡されるポインター。</span><span class="sxs-lookup"><span data-stu-id="3122f-109">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="3122f-110">プロファイラーはこの情報を使用して、ランタイム間を明確に区別できます。</span><span class="sxs-lookup"><span data-stu-id="3122f-110">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3122f-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="3122f-111">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3122f-112">解説</span><span class="sxs-lookup"><span data-stu-id="3122f-112">Remarks</span></span>  

 <span data-ttu-id="3122f-113">FunctionID 値の代替手段は、 [FunctionLeave3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)または[FunctionTailcall3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)メソッドによって指定されたプロファイラーの関数の開始/終了フック ([FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、 [FunctionTailcall3](functiontailcall3-function.md)、 [FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [SetEnterLeaveFunctionHooks3](functionleave3withinfo-function.md)、および[SetEnterLeaveFunctionHooks3WithInfo](functiontailcall3withinfo-function.md)) に渡されます。</span><span class="sxs-lookup"><span data-stu-id="3122f-113">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="3122f-114">`FunctionIDMapper2`メソッドを設定できるのは1回だけです。 [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)コールバックで設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3122f-114">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3122f-115">要件</span><span class="sxs-lookup"><span data-stu-id="3122f-115">Requirements</span></span>  

 <span data-ttu-id="3122f-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3122f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3122f-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3122f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3122f-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3122f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3122f-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3122f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3122f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3122f-120">See also</span></span>

- [<span data-ttu-id="3122f-121">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="3122f-121">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="3122f-122">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3122f-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3122f-123">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3122f-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3122f-124">プロファイル</span><span class="sxs-lookup"><span data-stu-id="3122f-124">Profiling</span></span>](index.md)
