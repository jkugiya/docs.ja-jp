---
description: '詳細について: ICorProfilerInfo4:: InitializeCurrentThread メソッド'
title: ICorProfilerInfo4::InitializeCurrentThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: a78816c736507a4a59da3ea1c75b078b54c34125
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781405"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="f8bf6-103">ICorProfilerInfo4::InitializeCurrentThread メソッド</span><span class="sxs-lookup"><span data-stu-id="f8bf6-103">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>

<span data-ttu-id="f8bf6-104">デッドロックを回避できるように、同じスレッドで、後続のプロファイラー API 呼び出しの前に現在のスレッドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="f8bf6-104">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8bf6-105">構文</span><span class="sxs-lookup"><span data-stu-id="f8bf6-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f8bf6-106">解説</span><span class="sxs-lookup"><span data-stu-id="f8bf6-106">Remarks</span></span>  

 <span data-ttu-id="f8bf6-107">中断された `InitializeCurrentThread` スレッドがある間は、PROFILER API を呼び出すスレッドでを呼び出すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f8bf6-107">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="f8bf6-108">このメソッドは、通常、 [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) メソッドを呼び出して、ターゲットスレッドが中断されている間にスタックウォークを実行する独自のスレッドを作成する、サンプリングプロファイラーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="f8bf6-108">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="f8bf6-109">プロファイラーでは、最初にサンプリングスレッドを作成するときにを呼び出すことによって `InitializeCurrentThread` 、 `DoStackSnapshot` 他のスレッドが中断されていないときに、CLR がの最初の呼び出し時に実行する、スレッドごとの遅延初期化を安全に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f8bf6-109">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8bf6-110">`InitializeCurrentThread` は、ロックを受け取るタスクを完了するために事前に初期化し、デッドロックが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f8bf6-110">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="f8bf6-111">`InitializeCurrentThread`中断されたスレッドが存在しない場合にのみ、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f8bf6-111">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8bf6-112">要件</span><span class="sxs-lookup"><span data-stu-id="f8bf6-112">Requirements</span></span>  

 <span data-ttu-id="f8bf6-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8bf6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8bf6-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8bf6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8bf6-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8bf6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8bf6-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8bf6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bf6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8bf6-117">See also</span></span>

- [<span data-ttu-id="f8bf6-118">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8bf6-118">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="f8bf6-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8bf6-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f8bf6-120">プロファイル</span><span class="sxs-lookup"><span data-stu-id="f8bf6-120">Profiling</span></span>](index.md)
