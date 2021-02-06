---
description: '詳細情報: FunctionEnter3WithInfo 関数'
title: FunctionEnter3WithInfo 関数
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: 573326c05275192a7b324377237ba057fb54bffb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648728"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="9b85a-103">FunctionEnter3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="9b85a-103">FunctionEnter3WithInfo Function</span></span>

<span data-ttu-id="9b85a-104">コントロールが関数に渡されていることをプロファイラーに通知し、 [ICorProfilerInfo3:: GetFunctionEnter3Info メソッド](icorprofilerinfo3-getfunctionenter3info-method.md) に渡すことができるハンドルを提供して、スタックフレームと関数の引数を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b85a-104">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b85a-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b85a-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b85a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b85a-106">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="9b85a-107">\[in] コントロールが渡される関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="9b85a-107">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="9b85a-108">\[in) 特定のスタックフレームに関する情報を表す不透明なハンドル。</span><span class="sxs-lookup"><span data-stu-id="9b85a-108">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="9b85a-109">このハンドルは、渡されるコールバック中にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="9b85a-109">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="9b85a-110">解説</span><span class="sxs-lookup"><span data-stu-id="9b85a-110">Remarks</span></span>  

 <span data-ttu-id="9b85a-111">`FunctionEnter3WithInfo`コールバックメソッドは、関数が呼び出されたことをプロファイラーに通知し、プロファイラーが[ICorProfilerInfo3:: GetFunctionEnter3Info メソッド](icorprofilerinfo3-getfunctionenter3info-method.md)を使用して引数値を検査できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9b85a-111">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="9b85a-112">引数情報にアクセスするには、 `COR_PRF_ENABLE_FUNCTION_ARGS` フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b85a-112">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="9b85a-113">プロファイラーは、 [ICorProfilerInfo:: SetEventMask メソッド](icorprofilerinfo-seteventmask-method.md) を使用してイベントフラグを設定し、 [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo メソッド](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) を使用してこの関数の実装を登録できます。</span><span class="sxs-lookup"><span data-stu-id="9b85a-113">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="9b85a-114">`FunctionEnter3WithInfo`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b85a-114">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="9b85a-115">実装では、ストレージクラス属性を使用する必要があり `__declspec(naked)` ます。</span><span class="sxs-lookup"><span data-stu-id="9b85a-115">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="9b85a-116">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="9b85a-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="9b85a-117">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b85a-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="9b85a-118">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b85a-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="9b85a-119">の実装では `FunctionEnter3WithInfo` 、ガベージコレクションが遅延するため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="9b85a-119">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="9b85a-120">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b85a-120">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="9b85a-121">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionEnter3WithInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="9b85a-121">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="9b85a-122">関数は、 `FunctionEnter3WithInfo` マネージコードを呼び出さないようにするか、マネージメモリの割り当てを任意の方法で発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="9b85a-122">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b85a-123">要件</span><span class="sxs-lookup"><span data-stu-id="9b85a-123">Requirements</span></span>  

 <span data-ttu-id="9b85a-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b85a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b85a-125">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="9b85a-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9b85a-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b85a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b85a-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b85a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b85a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b85a-128">See also</span></span>

- [<span data-ttu-id="9b85a-129">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="9b85a-129">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="9b85a-130">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="9b85a-130">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="9b85a-131">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="9b85a-131">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="9b85a-132">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="9b85a-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
