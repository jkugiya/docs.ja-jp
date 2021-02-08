---
description: 詳細については、「ICorProfilerCallback4 インターフェイス」を参照してください。
title: ICorProfilerCallback4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 882f234cb94ccd65203b42ed213aab6355250af8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788749"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="20b52-103">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20b52-103">ICorProfilerCallback4 Interface</span></span>

<span data-ttu-id="20b52-104">プロファイラーに情報を伝達するために共通言語ランタイム (CLR) が使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="20b52-104">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="20b52-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="20b52-105">Methods</span></span>  
  
|<span data-ttu-id="20b52-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="20b52-106">Method</span></span>|<span data-ttu-id="20b52-107">説明</span><span class="sxs-lookup"><span data-stu-id="20b52-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="20b52-108">GetReJITParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="20b52-108">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="20b52-109">再コンパイルされた新しいメソッド本体の代替コード生成フラグをコードプロファイラーで設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="20b52-109">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="20b52-110">MovedReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="20b52-110">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="20b52-111">圧縮ガベージコレクションの結果として、ヒープ内のオブジェクトの新しいレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="20b52-111">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="20b52-112">ReJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="20b52-112">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="20b52-113">Just-in-time (JIT) コンパイラが関数の再コンパイルを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="20b52-113">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="20b52-114">ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="20b52-114">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="20b52-115">Just-in-time (JIT) コンパイラが関数の再コンパイルを開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="20b52-115">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="20b52-116">ReJITError メソッド</span><span class="sxs-lookup"><span data-stu-id="20b52-116">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="20b52-117">Recompile 要求の処理中に発生したエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="20b52-117">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="20b52-118">SurvivingReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="20b52-118">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="20b52-119">非圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトのレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="20b52-119">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20b52-120">解説</span><span class="sxs-lookup"><span data-stu-id="20b52-120">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20b52-121">必要条件</span><span class="sxs-lookup"><span data-stu-id="20b52-121">Requirements</span></span>  

 <span data-ttu-id="20b52-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="20b52-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20b52-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="20b52-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="20b52-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20b52-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20b52-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20b52-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b52-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="20b52-126">See also</span></span>

- [<span data-ttu-id="20b52-127">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20b52-127">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="20b52-128">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="20b52-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="20b52-129">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20b52-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
