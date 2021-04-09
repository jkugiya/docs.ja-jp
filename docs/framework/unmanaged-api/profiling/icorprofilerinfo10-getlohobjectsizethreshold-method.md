---
description: '詳細情報: ICorProfilerInfo10::GetLOHObjectSizeThreshold メソッド'
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
ms.openlocfilehash: 7dca887f6d0ff5f9360b0edaa1568bc4b1bb42ac
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759769"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a><span data-ttu-id="bbde0-103">ICorProfilerInfo10::GetLOHObjectSizeThreshold メソッド</span><span class="sxs-lookup"><span data-stu-id="bbde0-103">ICorProfilerInfo10::GetLOHObjectSizeThreshold Method</span></span>

<span data-ttu-id="bbde0-104">構成されているラージ オブジェクト ヒープ (LOH) のしきい値の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="bbde0-104">Gets the value of the configured large object heap (LOH) threshold.</span></span>

## <a name="syntax"></a><span data-ttu-id="bbde0-105">構文</span><span class="sxs-lookup"><span data-stu-id="bbde0-105">Syntax</span></span>

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a><span data-ttu-id="bbde0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbde0-106">Parameters</span></span>

<span data-ttu-id="bbde0-107">`pThreshold` [出力] ラージ オブジェクト ヒープのしきい値 (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="bbde0-107">`pThreshold` [out] The large object heap threshold in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbde0-108">解説</span><span class="sxs-lookup"><span data-stu-id="bbde0-108">Remarks</span></span>

<span data-ttu-id="bbde0-109">ラージ オブジェクト ヒープのしきい値より大きいオブジェクトは、ラージ オブジェクト ヒープ上に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="bbde0-109">Objects larger than the large object heap threshold will be allocated on the large object heap.</span></span> <span data-ttu-id="bbde0-110">.NET Core 3.0 以降では、ラージ オブジェクト ヒープのしきい値は構成可能であり、`pThreshold` にはアクティブなラージ オブジェクト ヒープのしきい値のサイズ (バイト単位) が格納されます。</span><span class="sxs-lookup"><span data-stu-id="bbde0-110">Starting with .NET Core 3.0 the large object heap threshold is configurable, `pThreshold` will contain the active large object heap threshold size in bytes.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbde0-111">要件</span><span class="sxs-lookup"><span data-stu-id="bbde0-111">Requirements</span></span>

<span data-ttu-id="bbde0-112">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbde0-112">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="bbde0-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bbde0-113">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="bbde0-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbde0-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="bbde0-115">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbde0-115">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bbde0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbde0-116">See also</span></span>

- [<span data-ttu-id="bbde0-117">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bbde0-117">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
