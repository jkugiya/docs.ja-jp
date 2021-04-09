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
ms.openlocfilehash: bcd374aec2944977a0745177995ba8adf0cce9b7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759418"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a><span data-ttu-id="b878a-103">ICorProfilerInfo10::EnumerateObjectReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="b878a-103">ICorProfilerInfo10::EnumerateObjectReferences Method</span></span>

<span data-ttu-id="b878a-104">ObjectID、callback、clientData が指定されると、各オブジェクト参照 (存在する場合) を列挙します。</span><span class="sxs-lookup"><span data-stu-id="b878a-104">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span>

## <a name="syntax"></a><span data-ttu-id="b878a-105">構文</span><span class="sxs-lookup"><span data-stu-id="b878a-105">Syntax</span></span>

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a><span data-ttu-id="b878a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b878a-106">Parameters</span></span>

<span data-ttu-id="b878a-107">`objectId` [入力] 参照を列挙する対象のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b878a-107">`objectId` [in] The object to enumerate references on.</span></span>

<span data-ttu-id="b878a-108">`callback` [入力] オブジェクトの参照によって呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="b878a-108">`callback` [in] The function that will be called with the references for the object.</span></span>

<span data-ttu-id="b878a-109">`clientData` [入力] `callback` 関数に渡す、プロファイラーによって提供されたデータ。</span><span class="sxs-lookup"><span data-stu-id="b878a-109">`clientData` [in] Profiler-provided data to pass to the `callback` function.</span></span>

## <a name="remarks"></a><span data-ttu-id="b878a-110">解説</span><span class="sxs-lookup"><span data-stu-id="b878a-110">Remarks</span></span>

<span data-ttu-id="b878a-111">`EnumerateObjectReferences` メソッドは [ObjectReferences](icorprofilercallback-objectreferences-method.md) に似ていますが、参照を格納するための配列を事前に割り当てるのではなく、プロファイラーからの要求に応じて参照を走査する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="b878a-111">The `EnumerateObjectReferences` method is similar to [ObjectReferences](icorprofilercallback-objectreferences-method.md), except that it walks the references on demand for the profiler instead of pre-allocating an array to store the references.</span></span>

## <a name="requirements"></a><span data-ttu-id="b878a-112">要件</span><span class="sxs-lookup"><span data-stu-id="b878a-112">Requirements</span></span>

<span data-ttu-id="b878a-113">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b878a-113">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="b878a-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b878a-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b878a-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b878a-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b878a-116">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b878a-116">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b878a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b878a-117">See also</span></span>

- [<span data-ttu-id="b878a-118">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b878a-118">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
