---
description: '詳細について: ICorProfilerCallback4:: ReJITCompilationStarted メソッド'
title: ICorProfilerCallback4::ReJITCompilationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
ms.openlocfilehash: 7656f68ff6b10dcd58e48df212a036a590d0c3b3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788710"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="aa779-103">ICorProfilerCallback4::ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="aa779-103">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>

<span data-ttu-id="aa779-104">Just-in-time (JIT) コンパイラが関数の再コンパイルを開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="aa779-104">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa779-105">構文</span><span class="sxs-lookup"><span data-stu-id="aa779-105">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa779-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa779-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="aa779-107">からJIT コンパイラが再コンパイルを開始した関数の ID。</span><span class="sxs-lookup"><span data-stu-id="aa779-107">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="aa779-108">から関数の新しいバージョンの再コンパイル ID。</span><span class="sxs-lookup"><span data-stu-id="aa779-108">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="aa779-109">[入力] `true` ブロックが原因で、ランタイムが呼び出し元のスレッドがこのコールバックから戻るのを待機する場合があることを示します。 `false` ブロックがランタイムの動作に影響を与えないことを示す場合。</span><span class="sxs-lookup"><span data-stu-id="aa779-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="aa779-110">の値は、 `true` ランタイムには影響しませんが、プロファイルの結果に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa779-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa779-111">解説</span><span class="sxs-lookup"><span data-stu-id="aa779-111">Remarks</span></span>  

 <span data-ttu-id="aa779-112">`ReJITCompilationStarted`ランタイムがクラスコンストラクターを処理する方法によって、各関数に対して複数の And [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)メソッド呼び出しを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="aa779-112">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="aa779-113">たとえば、ランタイムはメソッド A の再コンパイルを開始しますが、クラス B のクラスコンストラクターを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa779-113">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="aa779-114">このため、ランタイムはクラス B のコンストラクターを再コンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="aa779-114">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="aa779-115">コンストラクターが実行されている間、メソッド a が呼び出されます。これにより、メソッド A が再コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="aa779-115">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="aa779-116">このシナリオでは、メソッド A の最初の再コンパイルが停止します。</span><span class="sxs-lookup"><span data-stu-id="aa779-116">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="aa779-117">ただし、メソッド A を再コンパイルしようとすると、JIT 再コンパイルイベントで報告されます。</span><span class="sxs-lookup"><span data-stu-id="aa779-117">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="aa779-118">2つのスレッドが同時にコールバックを作成する場合、プロファイラーは JIT 再コンパイルコールバックのシーケンスをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa779-118">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="aa779-119">たとえば、スレッド A はを呼び出します。ただし、スレッド a が `ReJITCompilationStarted` [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)を呼び出す前に、スレッド B はスレッド a のコールバックからの関数 ID を使用して [ICorProfilerCallback:: exceptionsearchfunctionenter](icorprofilercallback-exceptionsearchfunctionenter-method.md) を呼び出し `ReJITCompilationStarted` ます。 [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) の呼び出しがまだプロファイラーによって受信されていないため、関数 ID がまだ有効ではないように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="aa779-119">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="aa779-120">ただし、この場合、関数 ID は有効です。</span><span class="sxs-lookup"><span data-stu-id="aa779-120">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa779-121">要件</span><span class="sxs-lookup"><span data-stu-id="aa779-121">Requirements</span></span>  

 <span data-ttu-id="aa779-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa779-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa779-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aa779-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aa779-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa779-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa779-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa779-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa779-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa779-126">See also</span></span>

- [<span data-ttu-id="aa779-127">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa779-127">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="aa779-128">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa779-128">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="aa779-129">JITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="aa779-129">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="aa779-130">ReJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="aa779-130">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
