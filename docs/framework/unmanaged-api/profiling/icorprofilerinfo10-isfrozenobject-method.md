---
description: '詳細について: ICorProfilerInfo10:: IsFrozenObject メソッド'
title: ICorProfilerInfo10::IsFrozenObject
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3b47204630056e2797b5cf126bd7c291830cea05
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103453"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="a1ee0-103">ICorProfilerInfo10:: IsFrozenObject メソッド</span><span class="sxs-lookup"><span data-stu-id="a1ee0-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="a1ee0-104">ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="a1ee0-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="a1ee0-105">構文</span><span class="sxs-lookup"><span data-stu-id="a1ee0-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="a1ee0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1ee0-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="a1ee0-107">\[in) 調べるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a1ee0-107">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="a1ee0-108">\[out] `BOOL` オブジェクトが読み取り専用セグメント内にあるかどうかを示すです。</span><span class="sxs-lookup"><span data-stu-id="a1ee0-108">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="a1ee0-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="a1ee0-109">Requirements</span></span>

<span data-ttu-id="a1ee0-110">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ee0-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="a1ee0-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1ee0-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a1ee0-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1ee0-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a1ee0-113">**.Net のバージョン:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ee0-113">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a1ee0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1ee0-114">See also</span></span>

- [<span data-ttu-id="a1ee0-115">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1ee0-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
