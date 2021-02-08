---
description: 詳細については、「ICorProfilerCallback5 インターフェイス」を参照してください。
title: ICorProfilerCallback5 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: b80b27dc994ad556381228370ece92935d89d293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788658"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="948e7-103">ICorProfilerCallback5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="948e7-103">ICorProfilerCallback5 Interface</span></span>

<span data-ttu-id="948e7-104">[ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md)メソッドまたは[ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md)メソッドと共に[ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md)メソッドと[conditional tableelementreferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)メソッドと共に使用する場合に、プロファイラーがライブオブジェクトの完全なクロージャを識別するのに役立つ補足情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="948e7-104">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="948e7-105">`ICorProfilerCallback5` は、依存ハンドルに関連する通知をサブスクライブするために、マネージド メモリ プロファイラーによって実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="948e7-105">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="948e7-106">解説</span><span class="sxs-lookup"><span data-stu-id="948e7-106">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="948e7-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="948e7-107">Methods</span></span>  
  
|<span data-ttu-id="948e7-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="948e7-108">Method</span></span>|<span data-ttu-id="948e7-109">説明</span><span class="sxs-lookup"><span data-stu-id="948e7-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="948e7-110">ConditionalWeakTableElementReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="948e7-110">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="948e7-111">直接のメンバー フィールド参照および `ConditionalWeakTable` 依存を介してこれらのルーツによって参照されるオブジェクトの推移的終了を識別します。</span><span class="sxs-lookup"><span data-stu-id="948e7-111">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="948e7-112">要件</span><span class="sxs-lookup"><span data-stu-id="948e7-112">Requirements</span></span>  

 <span data-ttu-id="948e7-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="948e7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="948e7-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="948e7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="948e7-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="948e7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="948e7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="948e7-116">See also</span></span>

- [<span data-ttu-id="948e7-117">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="948e7-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="948e7-118">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="948e7-118">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
