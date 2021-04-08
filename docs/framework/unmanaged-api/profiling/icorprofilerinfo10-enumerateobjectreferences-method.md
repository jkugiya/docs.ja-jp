---
description: '詳細情報: ICorProfilerInfo10::EnumerateObjectReferences メソッド'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106723"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="f8950-103">ICorProfilerInfo10::EnumerateObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="f8950-103">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="f8950-104">ObjectID、callback、clientData が指定されると、各オブジェクト参照 (存在する場合) を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f8950-104">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="f8950-105">構文</span><span class="sxs-lookup"><span data-stu-id="f8950-105">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="f8950-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8950-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="f8950-107">\[入力] 参照を列挙する対象のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f8950-107">\[in] The object to enumerate references on.</span></span>

- `callback`

  <span data-ttu-id="f8950-108">\[入力] オブジェクトの参照によって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="f8950-108">\[in] The function that will be called with the references for the object.</span></span>

- `clientData`

  <span data-ttu-id="f8950-109">\[入力] `callback` 関数に渡す、プロファイラーによって提供されたデータ。</span><span class="sxs-lookup"><span data-stu-id="f8950-109">\[in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8950-110">解説</span><span class="sxs-lookup"><span data-stu-id="f8950-110">Remarks</span></span>

<span data-ttu-id="f8950-111">`EnumerateObjectReferences` メソッドは [ObjectReferences](icorprofilercallback-objectreferences-method.md) に似ていますが、参照を格納するための配列を事前に割り当てるのではなく、プロファイラーからの要求に応じて参照を走査する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="f8950-111">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8950-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="f8950-112">Requirements</span></span>

<span data-ttu-id="f8950-113">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8950-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="f8950-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8950-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f8950-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8950-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f8950-116">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8950-116">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f8950-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8950-117">See also</span></span>

- [<span data-ttu-id="f8950-118">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8950-118">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
