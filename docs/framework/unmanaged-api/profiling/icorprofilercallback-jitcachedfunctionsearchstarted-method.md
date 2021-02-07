---
description: '詳細について: ICorProfilerCallback:: JITCachedFunctionSearchStarted メソッド'
title: ICorProfilerCallback::JITCachedFunctionSearchStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 1faaf8fbc1e0fee9ce76850cfedcd4e8cf934371
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705773"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="4ed59-103">ICorProfilerCallback::JITCachedFunctionSearchStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="4ed59-103">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>

<span data-ttu-id="4ed59-104">以前にネイティブイメージジェネレーター (NGen.exe) を使用してコンパイルされた関数に対して検索が開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4ed59-104">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ed59-105">構文</span><span class="sxs-lookup"><span data-stu-id="4ed59-105">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ed59-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4ed59-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="4ed59-107">\[in] 検索を実行する関数の ID。</span><span class="sxs-lookup"><span data-stu-id="4ed59-107">\[in] The ID of the function for which the search is being performed.</span></span>

- `pbUseCachedFunction`

  <span data-ttu-id="4ed59-108">\[out] `true` (使用可能な場合) キャッシュされたバージョンの関数を実行エンジンが使用する必要がある場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="4ed59-108">\[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="4ed59-109">値がの場合、 `false` 実行エンジンは、jit コンパイルされていないバージョンを使用するのではなく、関数を jit コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="4ed59-109">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="4ed59-110">解説</span><span class="sxs-lookup"><span data-stu-id="4ed59-110">Remarks</span></span>  

 <span data-ttu-id="4ed59-111">.NET Framework バージョン2.0 では、 `JITCachedFunctionSearchStarted` 通常の NGen イメージのすべての関数に対して、および [ICorProfilerCallback:: JITCachedFunctionSearchFinished メソッド](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) のコールバックは行われません。</span><span class="sxs-lookup"><span data-stu-id="4ed59-111">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="4ed59-112">プロファイル用に最適化された NGen イメージのみが、イメージ内のすべての関数のコールバックを生成します。</span><span class="sxs-lookup"><span data-stu-id="4ed59-112">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="4ed59-113">ただし、オーバーヘッドが増加するため、プロファイラーは、これらのコールバックを使用して just-in-time (JIT) コンパイルを強制的に実行する場合にのみ、プロファイラーで最適化された NGen イメージを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ed59-113">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="4ed59-114">それ以外の場合、プロファイラーは関数情報を収集するためにレイジー戦略を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ed59-114">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="4ed59-115">プロファイラーは、プロファイルされたアプリケーションの複数のスレッドが同時に同じメソッドを呼び出す場合をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ed59-115">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="4ed59-116">たとえば、スレッド A がを呼び出し、 `JITCachedFunctionSearchStarted` プロファイラーは、 *PBUSECACHEDFUNCTION* を FALSE に設定して JIT コンパイルを強制することで応答します。</span><span class="sxs-lookup"><span data-stu-id="4ed59-116">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction* to FALSE to force JIT compilation.</span></span> <span data-ttu-id="4ed59-117">次に、スレッド A は [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) と [ICorProfilerCallback:: JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4ed59-117">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="4ed59-118">ここで、スレッド B `JITCachedFunctionSearchStarted` は同じ関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4ed59-118">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="4ed59-119">プロファイラーは、関数を JIT コンパイルすることを意図していましたが、プロファイラーは2番目のコールバックを受け取ります。これは、プロファイラーがの呼び出しに応答する前に、スレッド B がコールバックを送信するため `JITCachedFunctionSearchStarted` です。</span><span class="sxs-lookup"><span data-stu-id="4ed59-119">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="4ed59-120">スレッドが呼び出しを行う順序は、スレッドがどのようにスケジュールされているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="4ed59-120">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="4ed59-121">プロファイラーは、重複コールバックを受信するときに、によって参照される値 `pbUseCachedFunction` を、重複するすべてのコールバックについて同じ値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ed59-121">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="4ed59-122">つまり、 `JITCachedFunctionSearchStarted` が同じ値を使用して複数回呼び出された場合、 `functionId` プロファイラーは毎回同じ応答を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ed59-122">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ed59-123">要件</span><span class="sxs-lookup"><span data-stu-id="4ed59-123">Requirements</span></span>  

 <span data-ttu-id="4ed59-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ed59-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ed59-125">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ed59-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ed59-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ed59-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ed59-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ed59-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ed59-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ed59-128">See also</span></span>

- [<span data-ttu-id="4ed59-129">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4ed59-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
