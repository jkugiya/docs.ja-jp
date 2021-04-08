---
description: '詳細情報: ICorProfilerInfo10::ResumeRuntime メソッド'
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6e40270377fab07e110bbd1ea0f94e4e10c3d033
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103583"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a><span data-ttu-id="3c2c1-103">ICorProfilerInfo10::ResumeRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="3c2c1-103">ICorProfilerInfo10::ResumeRuntime Method</span></span>

<span data-ttu-id="3c2c1-104">GC を実行せずにランタイムを再開します。</span><span class="sxs-lookup"><span data-stu-id="3c2c1-104">Resumes the runtime without performing a GC.</span></span>

## <a name="syntax"></a><span data-ttu-id="3c2c1-105">構文</span><span class="sxs-lookup"><span data-stu-id="3c2c1-105">Syntax</span></span>

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a><span data-ttu-id="3c2c1-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="3c2c1-106">Requirements</span></span>

<span data-ttu-id="3c2c1-107">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c2c1-107">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="3c2c1-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3c2c1-108">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="3c2c1-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c2c1-109">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3c2c1-110">**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c2c1-110">**.NET Versions:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3c2c1-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c2c1-111">See also</span></span>

- [<span data-ttu-id="3c2c1-112">ICorProfilerInfo10 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c2c1-112">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
