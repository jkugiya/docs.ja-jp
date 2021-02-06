---
description: '詳細について: ICorProfilerInfo9:: GetNativeCodeStartAddresses メソッド'
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 1ca686cef4a45ebb9e05190fa790ed5300c0d816
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646492"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="556de-103">ICorProfilerInfo9:: GetNativeCodeStartAddresses メソッド</span><span class="sxs-lookup"><span data-stu-id="556de-103">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="556de-104">指定された functionId と rejitId は、現在存在する、このコードのすべての just-in-time バージョンのネイティブコードの開始アドレスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="556de-104">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="556de-105">構文</span><span class="sxs-lookup"><span data-stu-id="556de-105">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="556de-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="556de-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="556de-107">\[in] ネイティブコードの開始アドレスを返す関数の ID。</span><span class="sxs-lookup"><span data-stu-id="556de-107">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="556de-108">\[in) JIT 再コンパイルされた関数の id。</span><span class="sxs-lookup"><span data-stu-id="556de-108">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="556de-109">\[in] 配列の最大サイズ `codeStartAddresses` 。</span><span class="sxs-lookup"><span data-stu-id="556de-109">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="556de-110">\[out] 使用可能なアドレスの数。</span><span class="sxs-lookup"><span data-stu-id="556de-110">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="556de-111">\[out] の配列 `UINT_PTR` 。各は、指定された関数のネイティブ本体の開始アドレスです。</span><span class="sxs-lookup"><span data-stu-id="556de-111">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="556de-112">解説</span><span class="sxs-lookup"><span data-stu-id="556de-112">Remarks</span></span>

<span data-ttu-id="556de-113">階層化コンパイルが有効になっている場合、関数は複数のネイティブコード本体を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="556de-113">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="556de-114">要件</span><span class="sxs-lookup"><span data-stu-id="556de-114">Requirements</span></span>

<span data-ttu-id="556de-115">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="556de-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="556de-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="556de-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="556de-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="556de-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="556de-118">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="556de-118">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="556de-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="556de-119">See also</span></span>

- [<span data-ttu-id="556de-120">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="556de-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
