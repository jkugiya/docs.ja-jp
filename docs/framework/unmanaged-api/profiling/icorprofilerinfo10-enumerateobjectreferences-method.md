---
description: '詳細について: ICorProfilerInfo10:: EnumerateObjectReferences メソッド'
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: c18532450e420f38413028a18630dbf3e308fa61
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106723"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="5cf30-103">ICorProfilerInfo10:: EnumerateObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="5cf30-103">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="5cf30-104">ObjectID、callback、および clientData を指定すると、各オブジェクト参照 (存在する場合) が列挙されます。</span><span class="sxs-lookup"><span data-stu-id="5cf30-104">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="5cf30-105">構文</span><span class="sxs-lookup"><span data-stu-id="5cf30-105">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="5cf30-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5cf30-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="5cf30-107">\[in) 参照を列挙するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5cf30-107">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="5cf30-108">\[では、オブジェクトの参照を使用して呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="5cf30-108">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="5cf30-109">\[in) 関数に渡すプロファイラーが提供するデータ `callback` 。</span><span class="sxs-lookup"><span data-stu-id="5cf30-109">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="5cf30-110">解説</span><span class="sxs-lookup"><span data-stu-id="5cf30-110">Remarks</span></span>

<span data-ttu-id="5cf30-111">`EnumerateObjectReferences`メソッドは[ObjectReferences](icorprofilercallback-objectreferences-method.md)に似ていますが、参照を格納するために配列を事前に割り当てるのではなく、プロファイラーの要求時に参照をステップインする点が異なります。</span><span class="sxs-lookup"><span data-stu-id="5cf30-111">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="5cf30-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="5cf30-112">Requirements</span></span>

<span data-ttu-id="5cf30-113">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cf30-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="5cf30-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5cf30-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5cf30-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cf30-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5cf30-116">**.Net のバージョン:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cf30-116">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5cf30-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cf30-117">See also</span></span>

- [<span data-ttu-id="5cf30-118">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5cf30-118">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
