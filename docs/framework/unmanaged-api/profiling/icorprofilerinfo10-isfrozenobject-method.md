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
ms.openlocfilehash: c4d31c96fd7470a153437ffb0125e81ca8ea77bd
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759756"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a><span data-ttu-id="11232-103">ICorProfilerInfo10::IsFrozenObject メソッド</span><span class="sxs-lookup"><span data-stu-id="11232-103">ICorProfilerInfo10::IsFrozenObject Method</span></span>

<span data-ttu-id="11232-104">ObjectID が指定されると、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="11232-104">Given an ObjectID, determines whether the object is in a read-only segment.</span></span>

## <a name="syntax"></a><span data-ttu-id="11232-105">構文</span><span class="sxs-lookup"><span data-stu-id="11232-105">Syntax</span></span>

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a><span data-ttu-id="11232-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11232-106">Parameters</span></span>

<span data-ttu-id="11232-107">`objectId` [入力] 調べる対象のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="11232-107">`objectId` [in] The object to examine.</span></span>

<span data-ttu-id="11232-108">`pbFrozen` [出力] オブジェクトが読み取り専用セグメント内にあるかどうかを示す `BOOL`。</span><span class="sxs-lookup"><span data-stu-id="11232-108">`pbFrozen` [out] A `BOOL` indicating if the object is in a read-only segment.</span></span>

## <a name="requirements"></a><span data-ttu-id="11232-109">要件</span><span class="sxs-lookup"><span data-stu-id="11232-109">Requirements</span></span>

<span data-ttu-id="11232-110">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="11232-110">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="11232-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11232-111">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="11232-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11232-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="11232-113">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11232-113">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="11232-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="11232-114">See also</span></span>

- [<span data-ttu-id="11232-115">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11232-115">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
