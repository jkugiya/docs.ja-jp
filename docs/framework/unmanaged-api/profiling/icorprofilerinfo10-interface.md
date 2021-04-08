---
description: '詳細情報: ICorProfilerInfo10 インターフェイス'
title: ICorProfilerInfo10 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2fa0115f6894ac737696b63c1f0f00a0cb028ec
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106905"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="eb6ea-103">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb6ea-103">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="eb6ea-104">関数 IL の変更、ランタイムからの情報のクエリ、およびランタイムの一時停止と再開のためのメソッドを提供する [ICorProfilerInfo9](icorprofilerinfo9-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="eb6ea-104">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="eb6ea-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="eb6ea-105">Methods</span></span>  

| <span data-ttu-id="eb6ea-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="eb6ea-106">Method</span></span>|<span data-ttu-id="eb6ea-107">説明</span><span class="sxs-lookup"><span data-stu-id="eb6ea-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="eb6ea-108">EnumerateObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="eb6ea-108">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="eb6ea-109">ObjectID、callback、clientData が指定されると、各オブジェクト参照 (存在する場合) を列挙します。</span><span class="sxs-lookup"><span data-stu-id="eb6ea-109">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="eb6ea-110">IsFrozenObject メソッド</span><span class="sxs-lookup"><span data-stu-id="eb6ea-110">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="eb6ea-111">ObjectID が指定されると、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="eb6ea-111">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="eb6ea-112">GetLOHObjectSizeThreshold メソッド</span><span class="sxs-lookup"><span data-stu-id="eb6ea-112">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="eb6ea-113">構成されている LOH しきい値の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="eb6ea-113">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="eb6ea-114">RequestReJITWithInliners メソッド</span><span class="sxs-lookup"><span data-stu-id="eb6ea-114">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="eb6ea-115">要求されたメソッドに加えて、要求されたメソッドのすべてのインライナも ReJIT します。</span><span class="sxs-lookup"><span data-stu-id="eb6ea-115">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="eb6ea-116">SuspendRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="eb6ea-116">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="eb6ea-117">GC を実行せずにランタイムを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="eb6ea-117">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="eb6ea-118">ResumeRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="eb6ea-118">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="eb6ea-119">GC を実行せずにランタイムを再開します。</span><span class="sxs-lookup"><span data-stu-id="eb6ea-119">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="eb6ea-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="eb6ea-120">Requirements</span></span>  

<span data-ttu-id="eb6ea-121">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb6ea-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="eb6ea-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb6ea-122">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="eb6ea-123">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb6ea-123">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="eb6ea-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb6ea-124">See also</span></span>

- [<span data-ttu-id="eb6ea-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb6ea-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
