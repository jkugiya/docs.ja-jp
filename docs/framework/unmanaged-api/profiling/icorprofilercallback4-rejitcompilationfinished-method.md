---
description: '詳細について: ICorProfilerCallback4:: ReJITCompilationFinished メソッド'
title: ICorProfilerCallback4::ReJITCompilationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: 2d7270b5a8cf31fd81505c148429da5f7025319a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788723"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="ca9cd-103">ICorProfilerCallback4::ReJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="ca9cd-103">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>

<span data-ttu-id="ca9cd-104">Just-in-time (JIT) コンパイラが関数の再コンパイルを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ca9cd-104">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca9cd-105">構文</span><span class="sxs-lookup"><span data-stu-id="ca9cd-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca9cd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ca9cd-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="ca9cd-107">から再コンパイルされた関数の ID。</span><span class="sxs-lookup"><span data-stu-id="ca9cd-107">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="ca9cd-108">[in] JIT 再コンパイルされた関数のID。</span><span class="sxs-lookup"><span data-stu-id="ca9cd-108">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ca9cd-109">からJIT 再コンパイルが成功したかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="ca9cd-109">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="ca9cd-110">[入力] `true` ブロックが原因で、ランタイムが呼び出し元のスレッドがこのコールバックから戻るのを待機する場合があることを示します。 `false` ブロックがランタイムの動作に影響を与えないことを示す場合。</span><span class="sxs-lookup"><span data-stu-id="ca9cd-110">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="ca9cd-111">の値は、 `true` ランタイムには影響しませんが、プロファイルの結果に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ca9cd-111">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca9cd-112">要件</span><span class="sxs-lookup"><span data-stu-id="ca9cd-112">Requirements</span></span>  

 <span data-ttu-id="ca9cd-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca9cd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca9cd-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ca9cd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ca9cd-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca9cd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca9cd-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca9cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca9cd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca9cd-117">See also</span></span>

- [<span data-ttu-id="ca9cd-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca9cd-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ca9cd-119">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca9cd-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="ca9cd-120">JITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="ca9cd-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="ca9cd-121">ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="ca9cd-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
