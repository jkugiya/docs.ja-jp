---
description: '詳細情報: ICorProfilerInfo10::SuspendRuntime メソッド'
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
ms.openlocfilehash: 8cc098e4ae5f139f729ca0593b51c25eaf031704
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106879"
---
# <a name="icorprofilerinfo10suspendruntime-method"></a><span data-ttu-id="30f5b-103">ICorProfilerInfo10::SuspendRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="30f5b-103">ICorProfilerInfo10::SuspendRuntime Method</span></span>

<span data-ttu-id="30f5b-104">GC を実行せずにランタイムを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="30f5b-104">Suspends the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="30f5b-105">構文</span><span class="sxs-lookup"><span data-stu-id="30f5b-105">Syntax</span></span>

```cpp
HRESULT SuspendRuntime();
```

## <a name="requirements"></a><span data-ttu-id="30f5b-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="30f5b-106">Requirements</span></span>

<span data-ttu-id="30f5b-107">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="30f5b-107">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="30f5b-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30f5b-108">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="30f5b-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30f5b-109">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="30f5b-110">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30f5b-110">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="30f5b-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="30f5b-111">See also</span></span>

- [<span data-ttu-id="30f5b-112">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30f5b-112">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
