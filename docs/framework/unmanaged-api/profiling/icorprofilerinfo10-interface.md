---
description: 詳細については、「ICorProfilerInfo10 インターフェイス」を参照してください。
title: ICorProfilerInfo10 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: fd24491cb1ca55ad48137522c63e78e6387d33e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753290"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="7f851-103">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f851-103">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="7f851-104">関数 IL の変更、ランタイムからの情報のクエリ、およびランタイムの中断と再開を行うメソッドを提供する [ICorProfilerInfo9](icorprofilerinfo9-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="7f851-104">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="7f851-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7f851-105">Methods</span></span>  

| <span data-ttu-id="7f851-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7f851-106">Method</span></span>|<span data-ttu-id="7f851-107">説明</span><span class="sxs-lookup"><span data-stu-id="7f851-107">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="7f851-108">EnumerateObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="7f851-108">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="7f851-109">ObjectID、callback、および clientData を指定すると、各オブジェクト参照 (存在する場合) が列挙されます。</span><span class="sxs-lookup"><span data-stu-id="7f851-109">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="7f851-110">IsFrozenObject メソッド</span><span class="sxs-lookup"><span data-stu-id="7f851-110">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="7f851-111">ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7f851-111">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="7f851-112">GetLOHObjectSizeThreshold メソッド</span><span class="sxs-lookup"><span data-stu-id="7f851-112">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="7f851-113">構成された LOH しきい値の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="7f851-113">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="7f851-114">RequestReJITWithInliners メソッド</span><span class="sxs-lookup"><span data-stu-id="7f851-114">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="7f851-115">要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。</span><span class="sxs-lookup"><span data-stu-id="7f851-115">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="7f851-116">SuspendRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="7f851-116">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="7f851-117">GC を実行せずにランタイムを中断します。</span><span class="sxs-lookup"><span data-stu-id="7f851-117">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="7f851-118">ResumeRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="7f851-118">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="7f851-119">GC を実行せずにランタイムを再開します。</span><span class="sxs-lookup"><span data-stu-id="7f851-119">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="7f851-120">要件</span><span class="sxs-lookup"><span data-stu-id="7f851-120">Requirements</span></span>  

<span data-ttu-id="7f851-121">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f851-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="7f851-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f851-122">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="7f851-123">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f851-123">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7f851-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f851-124">See also</span></span>

- [<span data-ttu-id="7f851-125">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f851-125">Profiling Interfaces</span></span>](profiling-interfaces.md)
