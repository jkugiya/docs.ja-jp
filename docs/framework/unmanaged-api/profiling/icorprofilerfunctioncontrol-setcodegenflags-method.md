---
description: '詳細について: ICorProfilerFunctionControl:: SetCodegenFlags メソッド'
title: ICorProfilerFunctionControl::SetCodegenFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
ms.openlocfilehash: 61fa8be0993a06a3b2d352af408ac47b7b30e385
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781624"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="2a1fb-103">ICorProfilerFunctionControl::SetCodegenFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="2a1fb-103">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>

<span data-ttu-id="2a1fb-104">[COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md)列挙型の1つ以上のフラグを設定して、JUST-IN-TIME (JIT) 再コンパイル関数のコード生成を制御します。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-104">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="2a1fb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a1fb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2a1fb-106">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="2a1fb-107">から [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) 列挙体の1つ以上のフラグ。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-107">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a1fb-108">解説</span><span class="sxs-lookup"><span data-stu-id="2a1fb-108">Remarks</span></span>  

 <span data-ttu-id="2a1fb-109">プロファイラーは、 [ICorProfilerCallback4:: GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) コールバックを使用して、このインターフェイスのインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-109">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="2a1fb-110">`SetCodegenFlags` プロファイラーが再コンパイルされた関数のコード生成を制御できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-110">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="2a1fb-111">他のすべての JIT 再コンパイルパラメーターと同様に、コード生成フラグは関数のすべてのインスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-111">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="2a1fb-112">JIT コンパイラは、関数をコンパイルするときに、これらのコンパイルフラグを他のソースによって指定された他のフラグと共に考慮します。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-112">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="2a1fb-113">その他のソースには、デバッガー、 [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) メソッド (値と) を使用した起動時のプロファイラーによって設定されたグローバルフラグ、 `COR_PRF_DISABLE_INLINING` `COR_PRF_DISABLE_OPTIMIZATIONS` およびプロファイラーの [ICorProfilerCallback:: JITInlining](icorprofilercallback-jitinlining-method.md) コールバックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-113">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="2a1fb-114">JIT コンパイラは、最小限の最適化を要求するソースに優先順位を付けます。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-114">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="2a1fb-115">たとえば、プロファイラーが起動時にを指定し、 `COR_PRF_DISABLE_INLINING` `COR_PRF_CODEGEN_DISABLE_INLINING` [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) コールバックでを指定していない場合でも、インライン展開は無効になります。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-115">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="2a1fb-116">同様に、プロファイラーででを指定せず、 `COR_PRF_CODEGEN_DISABLE_INLINING` `SetCodegenFlags` [ICorProfilerCallback:: JITInlining](icorprofilercallback-jitinlining-method.md) コールバックを使用してインライン展開を無効にした場合は、インライン展開が無効になります。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-116">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a1fb-117">要件</span><span class="sxs-lookup"><span data-stu-id="2a1fb-117">Requirements</span></span>  

 <span data-ttu-id="2a1fb-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a1fb-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a1fb-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a1fb-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a1fb-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a1fb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a1fb-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a1fb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a1fb-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a1fb-122">See also</span></span>

- [<span data-ttu-id="2a1fb-123">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a1fb-123">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
