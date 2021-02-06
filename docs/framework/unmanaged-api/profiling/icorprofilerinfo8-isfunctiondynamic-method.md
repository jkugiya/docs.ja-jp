---
description: '詳細について: ICorProfilerInfo8:: IsFunctionDynamic メソッド'
title: 'ICorProfilerInfo8:: IsFunctionDynamic'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8ab942e6919f8029ef0d1c20336917622a1d22ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646531"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="9f8c6-103">ICorProfilerInfo8:: IsFunctionDynamic メソッド</span><span class="sxs-lookup"><span data-stu-id="9f8c6-103">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="9f8c6-104">関数にメタデータが関連付けられていないかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="9f8c6-104">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="9f8c6-105">構文</span><span class="sxs-lookup"><span data-stu-id="9f8c6-105">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="9f8c6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f8c6-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="9f8c6-107">\[in] `FunctionID` 対象の関数を識別する。</span><span class="sxs-lookup"><span data-stu-id="9f8c6-107">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="9f8c6-108">\[out] `BOOL` 関数にメタデータが含まれていないかどうかを示す値を格納するへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9f8c6-108">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="9f8c6-109">解説</span><span class="sxs-lookup"><span data-stu-id="9f8c6-109">Remarks</span></span>

<span data-ttu-id="9f8c6-110">関数は、メタデータがない場合は動的と見なされます。</span><span class="sxs-lookup"><span data-stu-id="9f8c6-110">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="9f8c6-111">IL スタブや LCG メソッドなどの特定のメソッドには、IMetaDataImport Api を使用して取得できるメタデータが関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="9f8c6-111">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="9f8c6-112">これらのメソッドは、命令ポインターを通じて、または [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)をリッスンすることによって、プロファイラーによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="9f8c6-112">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9f8c6-113">要件</span><span class="sxs-lookup"><span data-stu-id="9f8c6-113">Requirements</span></span>

<span data-ttu-id="9f8c6-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f8c6-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="9f8c6-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9f8c6-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="9f8c6-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f8c6-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9f8c6-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9f8c6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9f8c6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f8c6-118">See also</span></span>

- [<span data-ttu-id="9f8c6-119">ICorProfilerInfo8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9f8c6-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
