---
description: '詳細について: ICorProfilerInfo4:: RequestReJIT メソッド'
title: ICorProfilerInfo4::RequestReJIT メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: 2da65c2db5722f689f1a8588169ea099aff71be6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799019"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="64d7a-103">ICorProfilerInfo4::RequestReJIT メソッド</span><span class="sxs-lookup"><span data-stu-id="64d7a-103">ICorProfilerInfo4::RequestReJIT Method</span></span>

<span data-ttu-id="64d7a-104">指定された関数のすべてのインスタンスの JIT 再コンパイルを要求します。</span><span class="sxs-lookup"><span data-stu-id="64d7a-104">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d7a-105">構文</span><span class="sxs-lookup"><span data-stu-id="64d7a-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d7a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64d7a-106">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="64d7a-107">[in] 再コンパイルする関数の数。</span><span class="sxs-lookup"><span data-stu-id="64d7a-107">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="64d7a-108">[in] 再コンパイルする関数を識別する (`module`、`methodDef`) ペアの `moduleId` の部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="64d7a-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="64d7a-109">[in] 再コンパイルする関数を識別する (`module`、`methodDef`) ペアの `methodId` の部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="64d7a-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64d7a-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="64d7a-110">Return Value</span></span>  

 <span data-ttu-id="64d7a-111">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="64d7a-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="64d7a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="64d7a-112">HRESULT</span></span>|<span data-ttu-id="64d7a-113">説明</span><span class="sxs-lookup"><span data-stu-id="64d7a-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64d7a-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="64d7a-114">S_OK</span></span>|<span data-ttu-id="64d7a-115">すべてのメソッドを JIT 再コンパイル対象としてマークする操作が試行されました。</span><span class="sxs-lookup"><span data-stu-id="64d7a-115">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="64d7a-116">プロファイラーは、 [ICorProfilerCallback4:: ReJITError](icorprofilercallback4-rejiterror-method.md) メソッドを実装して、JIT 再コンパイルのために正常にマークされたメソッドを特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64d7a-116">The profiler must implement the [ICorProfilerCallback4::ReJITError](icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="64d7a-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="64d7a-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="64d7a-118">プロファイラーは、この呼び出しがサポートされるように、 [ICorProfilerCallback4](icorprofilercallback4-interface.md) インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="64d7a-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="64d7a-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="64d7a-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="64d7a-120">JIT 再コンパイルが有効になっていませんでした。</span><span class="sxs-lookup"><span data-stu-id="64d7a-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="64d7a-121">[ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)メソッドを使用してフラグを設定することにより、初期化中に JIT 再コンパイルを有効にする必要があり `COR_PRF_ENABLE_REJIT` ます。</span><span class="sxs-lookup"><span data-stu-id="64d7a-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="64d7a-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="64d7a-122">E_INVALIDARG</span></span>|<span data-ttu-id="64d7a-123">`cFunctions` が 0 であるか、`moduleIds` または `methodIds` が `NULL` です。</span><span class="sxs-lookup"><span data-stu-id="64d7a-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="64d7a-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="64d7a-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="64d7a-125">メモリが不足しているために、CLR は要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="64d7a-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64d7a-126">解説</span><span class="sxs-lookup"><span data-stu-id="64d7a-126">Remarks</span></span>  

 <span data-ttu-id="64d7a-127">指定された一連の関数をこのラインタイムで再コンパイルするため、`RequestReJIT` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="64d7a-127">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="64d7a-128">コードプロファイラーは、 [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) インターフェイスを使用して、関数の再コンパイル時に生成されるコードを調整できます。</span><span class="sxs-lookup"><span data-stu-id="64d7a-128">A code profiler can then use the [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="64d7a-129">これは、今後の関数呼び出しにのみ影響し、現在実行中の関数には影響しません。</span><span class="sxs-lookup"><span data-stu-id="64d7a-129">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="64d7a-130">指定されている関数のいずれかが以前に JIT 再コンパイルされている場合、再コンパイルを要求する操作は、関数を元に戻して再コンパイルする操作と同等です。</span><span class="sxs-lookup"><span data-stu-id="64d7a-130">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="64d7a-131">可逆性を維持するため、JIT コンパイラは関数の元のバージョンのコンパイル時に、インライン処理の決定のために呼び出し先の元のバージョンだけを考慮します。</span><span class="sxs-lookup"><span data-stu-id="64d7a-131">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="64d7a-132">JIT コンパイラは関数の再コンパイル時に、インライン処理のためにその呼び出し先の現行バージョン (再コンパイル バージョンまたは元のバージョン) を考慮します。</span><span class="sxs-lookup"><span data-stu-id="64d7a-132">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="64d7a-133">プロファイラーは一般に、プロファイラーが 1 つ以上のメソッドをインストルメント化することを求めるユーザー入力に対応して `RequestReJIT` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="64d7a-133">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="64d7a-134">`RequestReJIT` は一般に、一部の処理を実行するためにランタイムを一時停止します。また、ガベージ コレクションをトリガーする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64d7a-134">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="64d7a-135">このためプロファイラーは、現在プロファイラー コールバックを実行している CLR 作成スレッドではなく、以前に作成したスレッドから `RequestReJIT` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="64d7a-135">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d7a-136">要件</span><span class="sxs-lookup"><span data-stu-id="64d7a-136">Requirements</span></span>  

 <span data-ttu-id="64d7a-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64d7a-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d7a-138">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64d7a-138">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64d7a-139">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64d7a-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64d7a-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64d7a-140">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64d7a-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="64d7a-141">See also</span></span>

- [<span data-ttu-id="64d7a-142">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64d7a-142">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="64d7a-143">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="64d7a-143">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="64d7a-144">プロファイル</span><span class="sxs-lookup"><span data-stu-id="64d7a-144">Profiling</span></span>](index.md)
