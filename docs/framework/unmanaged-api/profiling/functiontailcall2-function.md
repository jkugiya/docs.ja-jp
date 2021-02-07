---
description: '詳細情報: FunctionTailcall2 関数'
title: FunctionTailcall2 関数
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 03547537d43a76f26d6946666589f38ca4e02ec4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687429"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="653e5-103">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="653e5-103">FunctionTailcall2 Function</span></span>

<span data-ttu-id="653e5-104">現在実行中の関数が別の関数の末尾呼び出しを実行しようとしていることをプロファイラーに通知し、スタックフレームに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="653e5-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="653e5-105">構文</span><span class="sxs-lookup"><span data-stu-id="653e5-105">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="653e5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="653e5-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="653e5-107">\[in] 末尾呼び出しを実行しようとしている現在実行中の関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="653e5-107">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="653e5-108">\[では、現在実行中の関数の末尾呼び出しを実行しようとしているときに、プロファイラーが以前に [Functionidmapper](functionidmapper-function.md)を使用して指定したリマップ関数識別子。</span><span class="sxs-lookup"><span data-stu-id="653e5-108">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="653e5-109">\[in] `COR_PRF_FRAME_INFO` スタックフレームに関する情報を示す値。</span><span class="sxs-lookup"><span data-stu-id="653e5-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="653e5-110">プロファイラーは、これを [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) メソッドの実行エンジンに渡すことができる不透明なハンドルとして処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="653e5-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="653e5-111">解説</span><span class="sxs-lookup"><span data-stu-id="653e5-111">Remarks</span></span>  

 <span data-ttu-id="653e5-112">Tail 呼び出しの対象となる関数は、現在のスタックフレームを使用し、末尾呼び出しを行った関数の呼び出し元に直接戻ります。</span><span class="sxs-lookup"><span data-stu-id="653e5-112">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="653e5-113">つまり、 [FunctionLeave2](functionleave2-function.md) コールバックは、末尾呼び出しのターゲットである関数に対しては発行されません。</span><span class="sxs-lookup"><span data-stu-id="653e5-113">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="653e5-114">`func` `FunctionTailcall2` 値が変更または破棄される可能性があるため、関数がを返すと、パラメーターの値が無効になります。</span><span class="sxs-lookup"><span data-stu-id="653e5-114">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="653e5-115">`FunctionTailcall2`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="653e5-115">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="653e5-116">実装では、 `__declspec` ( `naked` ) ストレージクラス属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="653e5-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="653e5-117">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="653e5-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="653e5-118">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="653e5-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="653e5-119">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="653e5-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="653e5-120">の実装は、 `FunctionTailcall2` ガベージコレクションを遅延させるため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="653e5-120">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="653e5-121">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="653e5-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="653e5-122">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionTailcall2` ます。</span><span class="sxs-lookup"><span data-stu-id="653e5-122">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="653e5-123">また、 `FunctionTailcall2` 関数はマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="653e5-123">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="653e5-124">要件</span><span class="sxs-lookup"><span data-stu-id="653e5-124">Requirements</span></span>  

 <span data-ttu-id="653e5-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="653e5-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="653e5-126">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="653e5-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="653e5-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="653e5-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="653e5-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="653e5-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653e5-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="653e5-129">See also</span></span>

- [<span data-ttu-id="653e5-130">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="653e5-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="653e5-131">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="653e5-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="653e5-132">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="653e5-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="653e5-133">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="653e5-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
