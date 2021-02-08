---
description: 詳細については、「ICorProfilerCallback3 インターフェイス」を参照してください。
title: ICorProfilerCallback3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: 70fba8768fef5da411b566d918308989a3f6e863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788801"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="5778f-103">ICorProfilerCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5778f-103">ICorProfilerCallback3 Interface</span></span>

<span data-ttu-id="5778f-104">共通言語ランタイム (CLR) が、プロファイラーにアタッチおよびデタッチ状態情報を伝達するために使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5778f-104">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5778f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5778f-105">Methods</span></span>  
  
|<span data-ttu-id="5778f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="5778f-106">Method</span></span>|<span data-ttu-id="5778f-107">説明</span><span class="sxs-lookup"><span data-stu-id="5778f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5778f-108">InitializeForAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="5778f-108">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="5778f-109">アタッチ操作後にその状態を初期化する機会をプロファイラーに与えるために、CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5778f-109">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="5778f-110">ProfilerAttachComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="5778f-110">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="5778f-111">プロファイラーがキャッチアップメソッドを呼び出せるようになったことを示すために、CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5778f-111">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="5778f-112">ProfilerDetachSucceeded メソッド</span><span class="sxs-lookup"><span data-stu-id="5778f-112">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="5778f-113">共通言語ランタイム (CLR: Common Language Runtime) がプロファイラー DLL をアンロードしようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5778f-113">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5778f-114">解説</span><span class="sxs-lookup"><span data-stu-id="5778f-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5778f-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="5778f-115">Requirements</span></span>  

 <span data-ttu-id="5778f-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5778f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5778f-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5778f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5778f-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5778f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5778f-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5778f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5778f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5778f-120">See also</span></span>

- [<span data-ttu-id="5778f-121">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5778f-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5778f-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5778f-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5778f-123">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5778f-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="5778f-124">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5778f-124">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
