---
description: '詳細情報: FunctionEnter2 関数'
title: FunctionEnter2 関数
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 8b8061b213d02efd845e214c1177db4e5351869b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788983"
---
# <a name="functionenter2-function"></a><span data-ttu-id="0890c-103">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="0890c-103">FunctionEnter2 Function</span></span>

<span data-ttu-id="0890c-104">コントロールが関数に渡されていることをプロファイラーに通知し、スタックフレームと関数の引数に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0890c-104">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="0890c-105">この関数は、 [Functionenter](functionenter-function.md) 関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="0890c-105">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0890c-106">構文</span><span class="sxs-lookup"><span data-stu-id="0890c-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0890c-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0890c-107">Parameters</span></span>

- `funcId`

  <span data-ttu-id="0890c-108">\[in] コントロールが渡される関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="0890c-108">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="0890c-109">\[では、マップされた関数の識別子。これは、プロファイラーが以前に [Functionidmapper](functionidmapper-function.md) 関数を使用して指定したものです。</span><span class="sxs-lookup"><span data-stu-id="0890c-109">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="0890c-110">\[in] `COR_PRF_FRAME_INFO` スタックフレームに関する情報を示す値。</span><span class="sxs-lookup"><span data-stu-id="0890c-110">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="0890c-111">プロファイラーは、これを [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) メソッドの実行エンジンに渡すことができる不透明なハンドルとして処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0890c-111">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="0890c-112">\[では、関数の引数のメモリ内の場所を指定する [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0890c-112">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="0890c-113">引数情報にアクセスするには、 `COR_PRF_ENABLE_FUNCTION_ARGS` フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0890c-113">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="0890c-114">プロファイラーは、 [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) メソッドを使用してイベントフラグを設定できます。</span><span class="sxs-lookup"><span data-stu-id="0890c-114">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="0890c-115">解説</span><span class="sxs-lookup"><span data-stu-id="0890c-115">Remarks</span></span>  

 <span data-ttu-id="0890c-116">値が変更さ `func` `argumentInfo` `FunctionEnter2` れるか、値が破棄される可能性があるため、関数から制御が戻った後に、パラメーターとパラメーターの値が無効になります。</span><span class="sxs-lookup"><span data-stu-id="0890c-116">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="0890c-117">`FunctionEnter2`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0890c-117">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="0890c-118">実装では、 `__declspec` ( `naked` ) ストレージクラス属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0890c-118">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="0890c-119">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="0890c-119">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="0890c-120">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0890c-120">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="0890c-121">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0890c-121">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0890c-122">の実装は、 `FunctionEnter2` ガベージコレクションを遅延させるため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="0890c-122">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="0890c-123">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0890c-123">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0890c-124">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionEnter2` ます。</span><span class="sxs-lookup"><span data-stu-id="0890c-124">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="0890c-125">また、 `FunctionEnter2` 関数はマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="0890c-125">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0890c-126">要件</span><span class="sxs-lookup"><span data-stu-id="0890c-126">Requirements</span></span>  

 <span data-ttu-id="0890c-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0890c-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0890c-128">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="0890c-128">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0890c-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0890c-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0890c-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0890c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0890c-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="0890c-131">See also</span></span>

- [<span data-ttu-id="0890c-132">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="0890c-132">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="0890c-133">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="0890c-133">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="0890c-134">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0890c-134">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="0890c-135">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="0890c-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
