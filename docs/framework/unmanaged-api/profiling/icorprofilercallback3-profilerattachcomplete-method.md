---
description: '詳細について: ICorProfilerCallback3::P rofilerAttachComplete メソッド'
title: ICorProfilerCallback3::ProfilerAttachComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: dcd8ab9fed402593fc955050b0d3be6f8a46730a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788788"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="5367e-103">ICorProfilerCallback3::ProfilerAttachComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="5367e-103">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>

<span data-ttu-id="5367e-104">プロファイラーが [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) および [ICorProfilerInfo3:: enummodules](icorprofilerinfo3-enummodules-method.md) のキャッチアップメソッドを呼び出せるようになったことを示すために、共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5367e-104">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5367e-105">構文</span><span class="sxs-lookup"><span data-stu-id="5367e-105">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5367e-106">解説</span><span class="sxs-lookup"><span data-stu-id="5367e-106">Remarks</span></span>  

 <span data-ttu-id="5367e-107">`ProfilerAttachComplete`コールバックは、 [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md)メソッドが呼び出された後に発行されます。</span><span class="sxs-lookup"><span data-stu-id="5367e-107">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="5367e-108">これは、次のことを示します。</span><span class="sxs-lookup"><span data-stu-id="5367e-108">It indicates the following:</span></span>  
  
- <span data-ttu-id="5367e-109">`InitializeForAttach` でプロファイラーによって要求されたコールバックがアクティブ化されました。</span><span class="sxs-lookup"><span data-stu-id="5367e-109">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="5367e-110">プロファイラーは、通知されないことを心配せずに、関連付けられた ID でキャッチアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="5367e-110">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="5367e-111">CLR はこのコールバックからの戻り値を無視します。</span><span class="sxs-lookup"><span data-stu-id="5367e-111">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5367e-112">要件</span><span class="sxs-lookup"><span data-stu-id="5367e-112">Requirements</span></span>  

 <span data-ttu-id="5367e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5367e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5367e-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5367e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5367e-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5367e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5367e-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5367e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5367e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5367e-117">See also</span></span>

- [<span data-ttu-id="5367e-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5367e-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5367e-119">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5367e-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="5367e-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5367e-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="5367e-121">プロファイル</span><span class="sxs-lookup"><span data-stu-id="5367e-121">Profiling</span></span>](index.md)
