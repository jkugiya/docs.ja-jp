---
description: '詳細情報: FunctionLeave3 関数'
title: FunctionLeave3 関数
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
ms.openlocfilehash: 9da68ffa2c54ada1437b3bef8bd6324c0791d610
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687455"
---
# <a name="functionleave3-function"></a><span data-ttu-id="a4afc-103">FunctionLeave3 関数</span><span class="sxs-lookup"><span data-stu-id="a4afc-103">FunctionLeave3 Function</span></span>

<span data-ttu-id="a4afc-104">関数から制御が返されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a4afc-104">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4afc-105">構文</span><span class="sxs-lookup"><span data-stu-id="a4afc-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4afc-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4afc-106">Parameters</span></span>  

- `functionOrRemappedID`

  <span data-ttu-id="a4afc-107">\[in] コントロールが返される関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="a4afc-107">\[in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="a4afc-108">解説</span><span class="sxs-lookup"><span data-stu-id="a4afc-108">Remarks</span></span>  

 <span data-ttu-id="a4afc-109">`FunctionLeave3`コールバック関数は、関数が呼び出されていることをプロファイラーに通知しますが、戻り値の検査はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a4afc-109">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="a4afc-110">[ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 メソッド](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)を使用して、この関数の実装を登録します。</span><span class="sxs-lookup"><span data-stu-id="a4afc-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a4afc-111">`FunctionLeave3`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4afc-111">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="a4afc-112">実装では、ストレージクラス属性を使用する必要があり `__declspec(naked)` ます。</span><span class="sxs-lookup"><span data-stu-id="a4afc-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a4afc-113">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="a4afc-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a4afc-114">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4afc-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a4afc-115">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4afc-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a4afc-116">の実装では `FunctionLeave3` 、ガベージコレクションが遅延するため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="a4afc-116">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="a4afc-117">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4afc-117">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a4afc-118">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionLeave3` ます。</span><span class="sxs-lookup"><span data-stu-id="a4afc-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="a4afc-119">関数は、 `FunctionLeave3` マネージコードを呼び出さないようにするか、マネージメモリの割り当てを任意の方法で発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="a4afc-119">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4afc-120">要件</span><span class="sxs-lookup"><span data-stu-id="a4afc-120">Requirements</span></span>  

 <span data-ttu-id="a4afc-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4afc-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4afc-122">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="a4afc-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a4afc-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4afc-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4afc-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4afc-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4afc-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4afc-125">See also</span></span>

- [<span data-ttu-id="a4afc-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a4afc-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="a4afc-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a4afc-127">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="a4afc-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a4afc-128">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="a4afc-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a4afc-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="a4afc-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a4afc-130">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a4afc-131">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a4afc-131">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="a4afc-132">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a4afc-132">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a4afc-133">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a4afc-133">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a4afc-134">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="a4afc-134">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a4afc-135">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="a4afc-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
