---
description: '詳細情報: FunctionTailcall3 関数'
title: FunctionTailcall3 関数
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
ms.openlocfilehash: 07ab49e8aeccdd82680a677c8b94e8a0c075d242
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687299"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="ecdb9-103">FunctionTailcall3 関数</span><span class="sxs-lookup"><span data-stu-id="ecdb9-103">FunctionTailcall3 Function</span></span>

<span data-ttu-id="ecdb9-104">現在実行中の関数が別の関数の末尾呼び出しを実行しようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-104">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecdb9-105">構文</span><span class="sxs-lookup"><span data-stu-id="ecdb9-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecdb9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ecdb9-106">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="ecdb9-107">\[in] 末尾呼び出しを実行しようとしている現在実行中の関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-107">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="ecdb9-108">解説</span><span class="sxs-lookup"><span data-stu-id="ecdb9-108">Remarks</span></span>  

 <span data-ttu-id="ecdb9-109">`FunctionTailcall3`コールバック関数は、関数が呼び出されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-109">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="ecdb9-110">[ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 メソッド](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)を使用して、この関数の実装を登録します。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-110">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="ecdb9-111">`FunctionTailcall3`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-111">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="ecdb9-112">実装では、ストレージクラス属性を使用する必要があり `__declspec(naked)` ます。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-112">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="ecdb9-113">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="ecdb9-114">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="ecdb9-115">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ecdb9-116">の実装では `FunctionTailcall3` 、ガベージコレクションが遅延するため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-116">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="ecdb9-117">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-117">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ecdb9-118">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionTailcall3` ます。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-118">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="ecdb9-119">関数は、 `FunctionTailcall3` マネージコードを呼び出さないようにするか、マネージメモリの割り当てを任意の方法で発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-119">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecdb9-120">要件</span><span class="sxs-lookup"><span data-stu-id="ecdb9-120">Requirements</span></span>  

 <span data-ttu-id="ecdb9-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecdb9-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecdb9-122">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="ecdb9-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ecdb9-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ecdb9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecdb9-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecdb9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecdb9-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecdb9-125">See also</span></span>

- [<span data-ttu-id="ecdb9-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="ecdb9-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="ecdb9-127">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="ecdb9-127">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="ecdb9-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ecdb9-128">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="ecdb9-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ecdb9-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="ecdb9-130">FunctionTailcall3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="ecdb9-130">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="ecdb9-131">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="ecdb9-131">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="ecdb9-132">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ecdb9-132">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="ecdb9-133">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="ecdb9-133">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="ecdb9-134">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="ecdb9-134">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="ecdb9-135">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="ecdb9-135">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
