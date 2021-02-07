---
description: '詳細について: ICorProfilerInfo4:: RequestRevert メソッド'
title: ICorProfilerInfo4::RequestRevert メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: 24a6a86f32bb9657e62a4433edcb5835e16b9754
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737299"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="54291-103">ICorProfilerInfo4::RequestRevert メソッド</span><span class="sxs-lookup"><span data-stu-id="54291-103">ICorProfilerInfo4::RequestRevert Method</span></span>

<span data-ttu-id="54291-104">指定された関数のすべてのインスタンスを元のバージョンに戻します。</span><span class="sxs-lookup"><span data-stu-id="54291-104">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54291-105">構文</span><span class="sxs-lookup"><span data-stu-id="54291-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54291-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="54291-106">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="54291-107">[in] 元に戻す関数の数。</span><span class="sxs-lookup"><span data-stu-id="54291-107">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="54291-108">[in] 元に戻す関数を識別する (`module`、`methodDef`) ペアの `moduleId` の部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="54291-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="54291-109">[in] 元に戻す関数を識別する (`module`、`methodDef`) ペアの `methodId` の部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="54291-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="54291-110">[out] このトピックの「状態 HRESULT」のセクションで後述する HRESULT の配列。</span><span class="sxs-lookup"><span data-stu-id="54291-110">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="54291-111">各 HRESULT は、並列配列 `moduleIds` と `methodIds` で指定された各関数を元に戻す操作の成功または失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="54291-111">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54291-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="54291-112">Return Value</span></span>  

 <span data-ttu-id="54291-113">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="54291-113">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="54291-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="54291-114">HRESULT</span></span>|<span data-ttu-id="54291-115">説明</span><span class="sxs-lookup"><span data-stu-id="54291-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="54291-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="54291-116">S_OK</span></span>|<span data-ttu-id="54291-117">すべての要求を元に戻す操作が試行されました。ただし、返された状態配列を確認して、どの関数が正常に元に戻されたかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54291-117">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="54291-118">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="54291-118">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="54291-119">プロファイラーは、この呼び出しがサポートされるように、 [ICorProfilerCallback4](icorprofilercallback4-interface.md) インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54291-119">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="54291-120">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="54291-120">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="54291-121">JIT 再コンパイルが有効になっていませんでした。</span><span class="sxs-lookup"><span data-stu-id="54291-121">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="54291-122">[ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)メソッドを使用してフラグを設定することにより、初期化中に JIT 再コンパイルを有効にする必要があり `COR_PRF_ENABLE_REJIT` ます。</span><span class="sxs-lookup"><span data-stu-id="54291-122">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="54291-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="54291-123">E_INVALIDARG</span></span>|<span data-ttu-id="54291-124">`cFunctions` が 0 であるか、`moduleIds` または `methodIds` が `NULL` です。</span><span class="sxs-lookup"><span data-stu-id="54291-124">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="54291-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="54291-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="54291-126">メモリが不足しているために、CLR は要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="54291-126">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="54291-127">状態 HRESULT</span><span class="sxs-lookup"><span data-stu-id="54291-127">Status HRESULTS</span></span>  
  
|<span data-ttu-id="54291-128">状態配列 HRESULT</span><span class="sxs-lookup"><span data-stu-id="54291-128">Status array HRESULT</span></span>|<span data-ttu-id="54291-129">説明</span><span class="sxs-lookup"><span data-stu-id="54291-129">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="54291-130">S_OK</span><span class="sxs-lookup"><span data-stu-id="54291-130">S_OK</span></span>|<span data-ttu-id="54291-131">対応する関数は正常に元に戻されました。</span><span class="sxs-lookup"><span data-stu-id="54291-131">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="54291-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="54291-132">E_INVALIDARG</span></span>|<span data-ttu-id="54291-133">`moduleID` パラメーターまたは `methodDef` パラメーターが `NULL` です。</span><span class="sxs-lookup"><span data-stu-id="54291-133">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="54291-134">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="54291-134">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="54291-135">モジュールが完全に読み込まれていないか、またはアンロード中です。</span><span class="sxs-lookup"><span data-stu-id="54291-135">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="54291-136">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="54291-136">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="54291-137">指定されたモジュールは (`Reflection.Emit` などにより) 動的に生成されました。</span><span class="sxs-lookup"><span data-stu-id="54291-137">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="54291-138">したがって、このメソッドではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="54291-138">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="54291-139">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="54291-139">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="54291-140">CLR は、対応するアクティブな再コンパイル要求が見つからなかったために、指定された関数を元に戻すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="54291-140">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="54291-141">再コンパイルが要求されていないか、または関数は既に元に戻されています。</span><span class="sxs-lookup"><span data-stu-id="54291-141">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="54291-142">その他</span><span class="sxs-lookup"><span data-stu-id="54291-142">Other</span></span>|<span data-ttu-id="54291-143">オペレーティング システムは、CLR 制御範囲外のエラーを返しました。</span><span class="sxs-lookup"><span data-stu-id="54291-143">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="54291-144">たとえば、メモリ ページのアクセスの保護を変更するシステム コールに失敗した場合、オペレーティング システムのエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="54291-144">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54291-145">解説</span><span class="sxs-lookup"><span data-stu-id="54291-145">Remarks</span></span>  

 <span data-ttu-id="54291-146">次に、元に戻された関数のいずれかのインスタンスが呼び出されると、その関数の元のバージョンが実行されます。</span><span class="sxs-lookup"><span data-stu-id="54291-146">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="54291-147">既に実行中の関数は、実行中のバージョンの実行を完了させます。</span><span class="sxs-lookup"><span data-stu-id="54291-147">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54291-148">要件</span><span class="sxs-lookup"><span data-stu-id="54291-148">Requirements</span></span>  

 <span data-ttu-id="54291-149">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54291-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54291-150">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54291-150">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54291-151">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54291-151">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54291-152">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54291-152">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54291-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="54291-153">See also</span></span>

- [<span data-ttu-id="54291-154">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54291-154">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="54291-155">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="54291-155">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="54291-156">プロファイル</span><span class="sxs-lookup"><span data-stu-id="54291-156">Profiling</span></span>](index.md)
