---
description: '詳細について: ICorProfilerInfo10:: SuspendRuntime メソッド'
title: ICorProfilerInfo10::SuspendRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.SuspendRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d019b163c8c71331b2d9a77fc0384d42a04c1fbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794560"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="9b591-103">ICorProfilerInfo10:: SuspendRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="9b591-103">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="9b591-104">GC を実行せずにランタイムを中断します。</span><span class="sxs-lookup"><span data-stu-id="9b591-104">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="9b591-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b591-105">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="9b591-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="9b591-106">Requirements</span></span>

<span data-ttu-id="9b591-107">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b591-107">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="9b591-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b591-108">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="9b591-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b591-109">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9b591-110">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b591-110">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9b591-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b591-111">See also</span></span>

- [<span data-ttu-id="9b591-112">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b591-112">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
