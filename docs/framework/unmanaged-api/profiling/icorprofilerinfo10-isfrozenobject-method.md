---
description: '詳細情報: ICorProfilerInfo10::IsFrozenObject メソッド'
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
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103453"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="a679a-103">ICorProfilerInfo10::IsFrozenObject メソッド</span><span class="sxs-lookup"><span data-stu-id="a679a-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="a679a-104">ObjectID が指定されると、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="a679a-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="a679a-105">構文</span><span class="sxs-lookup"><span data-stu-id="a679a-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="a679a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a679a-106">Parameters</span></span>

- `objectId`

  <span data-ttu-id="a679a-107">\[入力] 調べる対象のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="a679a-107">\[in] The object to examine.</span></span>

- `pbFrozen`

  <span data-ttu-id="a679a-108">\[出力] オブジェクトが読み取り専用セグメント内にあるかどうかを示す `BOOL`。</span><span class="sxs-lookup"><span data-stu-id="a679a-108">\[out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="a679a-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="a679a-109">Requirements</span></span>

<span data-ttu-id="a679a-110">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a679a-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="a679a-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a679a-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a679a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a679a-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a679a-113">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a679a-113">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a679a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a679a-114">See also</span></span>

- [<span data-ttu-id="a679a-115">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a679a-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
