---
description: 詳細については、「ICorProfilerInfo10 インターフェイス」を参照してください。
title: ICorProfilerInfo10 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2fa0115f6894ac737696b63c1f0f00a0cb028ec
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106905"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="3fb97-103">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fb97-103">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="3fb97-104">関数 IL の変更、ランタイムからの情報のクエリ、およびランタイムの中断と再開を行うメソッドを提供する [ICorProfilerInfo9](icorprofilerinfo9-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="3fb97-104">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="3fb97-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb97-105">Methods</span></span>  

| <span data-ttu-id="3fb97-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb97-106">Method</span></span>|<span data-ttu-id="3fb97-107">説明</span><span class="sxs-lookup"><span data-stu-id="3fb97-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="3fb97-108">EnumerateObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb97-108">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="3fb97-109">ObjectID、callback、および clientData を指定すると、各オブジェクト参照 (存在する場合) が列挙されます。</span><span class="sxs-lookup"><span data-stu-id="3fb97-109">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="3fb97-110">IsFrozenObject メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb97-110">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="3fb97-111">ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="3fb97-111">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="3fb97-112">GetLOHObjectSizeThreshold メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb97-112">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="3fb97-113">構成された LOH しきい値の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3fb97-113">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="3fb97-114">RequestReJITWithInliners メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb97-114">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="3fb97-115">要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。</span><span class="sxs-lookup"><span data-stu-id="3fb97-115">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="3fb97-116">SuspendRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb97-116">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="3fb97-117">GC を実行せずにランタイムを中断します。</span><span class="sxs-lookup"><span data-stu-id="3fb97-117">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="3fb97-118">ResumeRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="3fb97-118">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="3fb97-119">GC を実行せずにランタイムを再開します。</span><span class="sxs-lookup"><span data-stu-id="3fb97-119">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="3fb97-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="3fb97-120">Requirements</span></span>  

<span data-ttu-id="3fb97-121">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fb97-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="3fb97-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3fb97-122">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="3fb97-123">**.Net のバージョン:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fb97-123">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3fb97-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fb97-124">See also</span></span>

- [<span data-ttu-id="3fb97-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fb97-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
