---
description: '詳細について: ICorProfilerInfo8:: GetFunctionFromIP3 メソッド'
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3ce0a0964e26254ab09e515826b6bceb657e07bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783834"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="91b70-103">ICorProfilerInfo8:: GetFunctionFromIP3 メソッド</span><span class="sxs-lookup"><span data-stu-id="91b70-103">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="91b70-104">マネージコード命令ポインターを FunctionID にマップします。</span><span class="sxs-lookup"><span data-stu-id="91b70-104">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="91b70-105">このメソッドは、動的メソッドと非動的メソッドの両方に対して機能します。</span><span class="sxs-lookup"><span data-stu-id="91b70-105">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="91b70-106">構文</span><span class="sxs-lookup"><span data-stu-id="91b70-106">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="91b70-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91b70-107">Parameters</span></span>

- `ip`

  <span data-ttu-id="91b70-108">\[in) マネージコード内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="91b70-108">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="91b70-109">\[out] 関数 ID。</span><span class="sxs-lookup"><span data-stu-id="91b70-109">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="91b70-110">\[out] 関数の JIT 再コンパイルバージョンの id。</span><span class="sxs-lookup"><span data-stu-id="91b70-110">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="91b70-111">解説</span><span class="sxs-lookup"><span data-stu-id="91b70-111">Remarks</span></span>

<span data-ttu-id="91b70-112">このメソッドは、動的メソッドと非動的メソッドの両方に対して機能します。</span><span class="sxs-lookup"><span data-stu-id="91b70-112">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="91b70-113">これは [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)のスーパーセットであり、メタデータを持つ関数に対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="91b70-113">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="91b70-114">要件</span><span class="sxs-lookup"><span data-stu-id="91b70-114">Requirements</span></span>

<span data-ttu-id="91b70-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91b70-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="91b70-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="91b70-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="91b70-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91b70-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="91b70-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="91b70-118">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="91b70-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="91b70-119">See also</span></span>

- [<span data-ttu-id="91b70-120">ICorProfilerInfo8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="91b70-120">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
