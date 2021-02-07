---
description: '詳細情報: FunctionLeave2 関数'
title: FunctionLeave2 関数
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: 475def9af448182003ef36782a84d501a9f2661d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687559"
---
# <a name="functionleave2-function"></a><span data-ttu-id="46a50-103">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="46a50-103">FunctionLeave2 Function</span></span>

<span data-ttu-id="46a50-104">関数が呼び出し元に戻り、スタックフレームおよび関数の戻り値に関する情報を提供することをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="46a50-104">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46a50-105">構文</span><span class="sxs-lookup"><span data-stu-id="46a50-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46a50-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="46a50-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="46a50-107">\[in] を返す関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="46a50-107">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="46a50-108">\[in] プロファイラーが以前に [Functionidmapper](functionidmapper-function.md) 関数を使用して指定した、再マップされた関数識別子。</span><span class="sxs-lookup"><span data-stu-id="46a50-108">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="46a50-109">\[in] `COR_PRF_FRAME_INFO` スタックフレームに関する情報を示す値。</span><span class="sxs-lookup"><span data-stu-id="46a50-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="46a50-110">プロファイラーは、これを [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) メソッドの実行エンジンに渡すことができる不透明なハンドルとして処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46a50-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="46a50-111">\[では、関数の戻り値のメモリ位置を指定する [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="46a50-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="46a50-112">戻り値の情報にアクセスするには、 `COR_PRF_ENABLE_FUNCTION_RETVAL` フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46a50-112">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="46a50-113">プロファイラーは、 [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) メソッドを使用してイベントフラグを設定できます。</span><span class="sxs-lookup"><span data-stu-id="46a50-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="46a50-114">解説</span><span class="sxs-lookup"><span data-stu-id="46a50-114">Remarks</span></span>  

 <span data-ttu-id="46a50-115">値が変更さ `func` `retvalRange` `FunctionLeave2` れるか、値が破棄される可能性があるため、関数から制御が戻った後に、パラメーターとパラメーターの値が無効になります。</span><span class="sxs-lookup"><span data-stu-id="46a50-115">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="46a50-116">`FunctionLeave2`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46a50-116">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="46a50-117">実装では、 `__declspec` ( `naked` ) ストレージクラス属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46a50-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="46a50-118">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="46a50-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="46a50-119">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46a50-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="46a50-120">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46a50-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="46a50-121">の実装は、 `FunctionLeave2` ガベージコレクションを遅延させるため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="46a50-121">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="46a50-122">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="46a50-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="46a50-123">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionLeave2` ます。</span><span class="sxs-lookup"><span data-stu-id="46a50-123">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="46a50-124">また、 `FunctionLeave2` 関数はマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="46a50-124">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46a50-125">要件</span><span class="sxs-lookup"><span data-stu-id="46a50-125">Requirements</span></span>  

 <span data-ttu-id="46a50-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46a50-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46a50-127">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="46a50-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="46a50-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46a50-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46a50-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46a50-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a50-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="46a50-130">See also</span></span>

- [<span data-ttu-id="46a50-131">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="46a50-131">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="46a50-132">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="46a50-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="46a50-133">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="46a50-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="46a50-134">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="46a50-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
