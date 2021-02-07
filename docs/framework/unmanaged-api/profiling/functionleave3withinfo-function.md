---
description: '詳細情報: FunctionLeave3WithInfo 関数'
title: FunctionLeave3WithInfo 関数
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: 6a861f455e827258368764b80547c3b3e9c986cd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687416"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="0bb23-103">FunctionLeave3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="0bb23-103">FunctionLeave3WithInfo Function</span></span>

<span data-ttu-id="0bb23-104">関数から制御が返されていることをプロファイラーに通知し、スタックフレームと戻り値を取得するために [ICorProfilerInfo3:: GetFunctionLeave3Info メソッド](icorprofilerinfo3-getfunctionleave3info-method.md) に渡すことができるハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="0bb23-104">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bb23-105">構文</span><span class="sxs-lookup"><span data-stu-id="0bb23-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bb23-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0bb23-106">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="0bb23-107">\[in] コントロールが返される関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="0bb23-107">\[in] The identifier of the function from which control is returned.</span></span>

- `eltInfo`

  <span data-ttu-id="0bb23-108">\[in) 特定のスタックフレームに関する情報を表す不透明なハンドル。</span><span class="sxs-lookup"><span data-stu-id="0bb23-108">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="0bb23-109">このハンドルは、渡されるコールバック中にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0bb23-109">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="0bb23-110">解説</span><span class="sxs-lookup"><span data-stu-id="0bb23-110">Remarks</span></span>  

 <span data-ttu-id="0bb23-111">`FunctionLeave3WithInfo`コールバックメソッドは、関数が呼び出されたことをプロファイラーに通知します。また、プロファイラーは[ICorProfilerInfo3:: GetFunctionLeave3Info メソッド](icorprofilerinfo3-getfunctionleave3info-method.md)を使用して、戻り値を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="0bb23-111">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="0bb23-112">戻り値の情報にアクセスするには、 `COR_PRF_ENABLE_FUNCTION_RETVAL` フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bb23-112">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="0bb23-113">プロファイラーは、 [ICorProfilerInfo:: SetEventMask メソッド](icorprofilerinfo-seteventmask-method.md) を使用してイベントフラグを設定し、 [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo メソッド](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) を使用してこの関数の実装を登録できます。</span><span class="sxs-lookup"><span data-stu-id="0bb23-113">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="0bb23-114">`FunctionLeave3WithInfo`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bb23-114">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="0bb23-115">実装では、ストレージクラス属性を使用する必要があり `__declspec(naked)` ます。</span><span class="sxs-lookup"><span data-stu-id="0bb23-115">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="0bb23-116">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="0bb23-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="0bb23-117">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bb23-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="0bb23-118">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bb23-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0bb23-119">の実装では `FunctionLeave3WithInfo` 、ガベージコレクションが遅延するため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="0bb23-119">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="0bb23-120">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bb23-120">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0bb23-121">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionLeave3WithInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="0bb23-121">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="0bb23-122">関数は、 `FunctionLeave3WithInfo` マネージコードを呼び出さないようにするか、マネージメモリの割り当てを任意の方法で発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="0bb23-122">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bb23-123">要件</span><span class="sxs-lookup"><span data-stu-id="0bb23-123">Requirements</span></span>  

 <span data-ttu-id="0bb23-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bb23-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bb23-125">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="0bb23-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0bb23-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bb23-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bb23-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bb23-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb23-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bb23-128">See also</span></span>

- [<span data-ttu-id="0bb23-129">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="0bb23-129">GetFunctionLeave3Info</span></span>](icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="0bb23-130">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="0bb23-130">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="0bb23-131">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="0bb23-131">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="0bb23-132">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="0bb23-132">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="0bb23-133">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0bb23-133">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="0bb23-134">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0bb23-134">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="0bb23-135">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="0bb23-135">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="0bb23-136">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0bb23-136">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="0bb23-137">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="0bb23-137">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="0bb23-138">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="0bb23-138">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="0bb23-139">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="0bb23-139">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
