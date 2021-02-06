---
description: '詳細について: ICorProfilerInfo8:: GetDynamicFunctionInfo メソッド'
title: 'ICorProfilerInfo8:: GetDynamicFunctionInfo'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 48c8dbe20ccafb3fb23e9e289f728d5e3370613a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646583"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="090b4-103">ICorProfilerInfo8:: GetDynamicFunctionInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="090b4-103">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="090b4-104">動的メソッドに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="090b4-104">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="090b4-105">構文</span><span class="sxs-lookup"><span data-stu-id="090b4-105">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="090b4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="090b4-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="090b4-107">\[in] 情報を取得する関数の ID。</span><span class="sxs-lookup"><span data-stu-id="090b4-107">\[in] The ID of the function for which to retrieve information.</span></span>

- `moduleId`

  <span data-ttu-id="090b4-108">\[では、関数の親クラスが定義されているモジュールへのポインター。</span><span class="sxs-lookup"><span data-stu-id="090b4-108">\[in] A pointer to the module in which the function's parent class is defined.</span></span>

- `ppvSig`

  <span data-ttu-id="090b4-109">\[out] 関数のシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="090b4-109">\[out] A pointer to the signature for the function.</span></span>

- `pbSig`

  <span data-ttu-id="090b4-110">\[out] 関数シグネチャのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="090b4-110">\[out] A pointer to the count of bytes for the function signature.</span></span>

- `cchName`

  <span data-ttu-id="090b4-111">\[in] 配列の最大サイズ `wszName` 。</span><span class="sxs-lookup"><span data-stu-id="090b4-111">\[in] The maximum size of the `wszName` array.</span></span>

- `pcchName`

  <span data-ttu-id="090b4-112">\[out] 配列内の文字数 `wszName` 。</span><span class="sxs-lookup"><span data-stu-id="090b4-112">\[out] The number of characters in the `wszName` array.</span></span>

- `wszName`

  <span data-ttu-id="090b4-113">\[out] `WCHAR` 関数の名前 (存在する場合) の配列。</span><span class="sxs-lookup"><span data-stu-id="090b4-113">\[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="090b4-114">解説</span><span class="sxs-lookup"><span data-stu-id="090b4-114">Remarks</span></span>

<span data-ttu-id="090b4-115">IL スタブや LCG などの特定のメソッドには、 [IMetaDataImport](../metadata/imetadataimport-interface.md) Api と [IMetaDataImport2](../metadata/imetadataimport2-interface.md) api を使用して取得できるメタデータが関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="090b4-115">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="090b4-116">このようなメソッドは、命令ポインターを通じて、または [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)をリッスンすることによって、プロファイラーによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="090b4-116">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="090b4-117">この API を使用して、表示名などの動的メソッドに関する情報を取得できます (使用可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="090b4-117">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="090b4-118">要件</span><span class="sxs-lookup"><span data-stu-id="090b4-118">Requirements</span></span>

<span data-ttu-id="090b4-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="090b4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="090b4-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="090b4-120">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="090b4-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="090b4-121">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="090b4-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="090b4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="090b4-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="090b4-123">See also</span></span>

- [<span data-ttu-id="090b4-124">ICorProfilerInfo8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="090b4-124">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
