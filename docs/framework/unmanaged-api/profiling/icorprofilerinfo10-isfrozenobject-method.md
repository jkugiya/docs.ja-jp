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
ms.openlocfilehash: b07e456f7fa9c328217b8779733d45dfe2793fe2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753277"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="5f81b-103">ICorProfilerInfo10:: IsFrozenObject メソッド</span><span class="sxs-lookup"><span data-stu-id="5f81b-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="5f81b-104">ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="5f81b-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f81b-105">構文</span><span class="sxs-lookup"><span data-stu-id="5f81b-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="5f81b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f81b-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="5f81b-107">\[in) 調べるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5f81b-107">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="5f81b-108">\[out] `BOOL` オブジェクトが読み取り専用セグメント内にあるかどうかを示すです。</span><span class="sxs-lookup"><span data-stu-id="5f81b-108">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="5f81b-109">要件</span><span class="sxs-lookup"><span data-stu-id="5f81b-109">Requirements</span></span>

<span data-ttu-id="5f81b-110">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f81b-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="5f81b-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f81b-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5f81b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f81b-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5f81b-113">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f81b-113">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5f81b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f81b-114">See also</span></span>

- [<span data-ttu-id="5f81b-115">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f81b-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
