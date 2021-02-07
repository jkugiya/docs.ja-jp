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
ms.openlocfilehash: 3e31192426ea38e177b636bcc6a4b6e54057801f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737325"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="c2227-103">ICorProfilerInfo10:: EnumerateObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="c2227-103">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="c2227-104">ObjectID、callback、および clientData を指定すると、各オブジェクト参照 (存在する場合) が列挙されます。</span><span class="sxs-lookup"><span data-stu-id="c2227-104">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="c2227-105">構文</span><span class="sxs-lookup"><span data-stu-id="c2227-105">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="c2227-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2227-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="c2227-107">\[in) 参照を列挙するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c2227-107">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="c2227-108">\[では、オブジェクトの参照を使用して呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="c2227-108">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="c2227-109">\[in) 関数に渡すプロファイラーが提供するデータ `callback` 。</span><span class="sxs-lookup"><span data-stu-id="c2227-109">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="c2227-110">解説</span><span class="sxs-lookup"><span data-stu-id="c2227-110">Remarks</span></span>

<span data-ttu-id="c2227-111">`EnumerateObjectReferences`メソッドは[ObjectReferences](icorprofilercallback-objectreferences-method.md)に似ていますが、参照を格納するために配列を事前に割り当てるのではなく、プロファイラーの要求時に参照をステップインする点が異なります。</span><span class="sxs-lookup"><span data-stu-id="c2227-111">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="c2227-112">要件</span><span class="sxs-lookup"><span data-stu-id="c2227-112">Requirements</span></span>

<span data-ttu-id="c2227-113">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2227-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="c2227-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2227-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c2227-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2227-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c2227-116">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2227-116">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c2227-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2227-117">See also</span></span>

- [<span data-ttu-id="c2227-118">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2227-118">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
