---
description: '詳細について: ICorProfilerInfo10:: GetLOHObjectSizeThreshold メソッド'
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 665a08ae226f04d5282b9584932078736751d5d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737310"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="0447a-103">ICorProfilerInfo10:: GetLOHObjectSizeThreshold メソッド</span><span class="sxs-lookup"><span data-stu-id="0447a-103">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="0447a-104">構成されたラージオブジェクトヒープ (LOH) のしきい値の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="0447a-104">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="0447a-105">構文</span><span class="sxs-lookup"><span data-stu-id="0447a-105">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="0447a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0447a-106">Parameters</span></span>

- `pThreshold`

  <span data-ttu-id="0447a-107">\[out: 大きなオブジェクトヒープのしきい値 (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="0447a-107">\[out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="0447a-108">解説</span><span class="sxs-lookup"><span data-stu-id="0447a-108">Remarks</span></span>

<span data-ttu-id="0447a-109">大きなオブジェクトヒープのしきい値より大きいオブジェクトは、大きなオブジェクトヒープに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="0447a-109">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="0447a-110">.NET Core 3.0 以降では、大きなオブジェクトヒープのしきい値は構成可能で、 `pThreshold` アクティブなラージオブジェクトヒープのしきい値のサイズはバイト単位で格納されます。</span><span class="sxs-lookup"><span data-stu-id="0447a-110">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="0447a-111">要件</span><span class="sxs-lookup"><span data-stu-id="0447a-111">Requirements</span></span>

<span data-ttu-id="0447a-112">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0447a-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="0447a-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0447a-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0447a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0447a-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0447a-115">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0447a-115">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0447a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0447a-116">See also</span></span>

- [<span data-ttu-id="0447a-117">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0447a-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
