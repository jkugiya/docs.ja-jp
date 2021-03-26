---
description: '詳細情報: ICorProfilerInfo9::GetNativeCodeStartAddresses メソッド'
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
ms.openlocfilehash: 062aebf6d5bed208ea71b215bd9f857b82483673
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759048"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="0c3f0-103">ICorProfilerInfo9::GetNativeCodeStartAddresses メソッド</span><span class="sxs-lookup"><span data-stu-id="0c3f0-103">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="0c3f0-104">functionId と rejitId を指定すると、現在存在するこのコードのすべての just-in-time バージョンのネイティブ コード開始アドレスが列挙されます。</span><span class="sxs-lookup"><span data-stu-id="0c3f0-104">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c3f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="0c3f0-105">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="0c3f0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c3f0-106">Parameters</span></span>

<span data-ttu-id="0c3f0-107">`functionId` [in] ネイティブコード開始アドレスを返す必要がある関数の ID。</span><span class="sxs-lookup"><span data-stu-id="0c3f0-107">`functionId` [in] The ID of the function whose native code start addresses should be returned.</span></span>

<span data-ttu-id="0c3f0-108">`reJitId` [in] JIT 再コンパイルされた関数のID。</span><span class="sxs-lookup"><span data-stu-id="0c3f0-108">`reJitId` [in] The identity of the JIT-recompiled function.</span></span>

<span data-ttu-id="0c3f0-109">`cCodeStartAddresses` [in] `codeStartAddresses` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="0c3f0-109">`cCodeStartAddresses` [in] The maximum size of the `codeStartAddresses` array.</span></span>

<span data-ttu-id="0c3f0-110">`pcCodeStartAddresses` [out] 使用可能なアドレスの数。</span><span class="sxs-lookup"><span data-stu-id="0c3f0-110">`pcCodeStartAddresses` [out] The number of available addresses.</span></span>

<span data-ttu-id="0c3f0-111">`codeStartAddresses` [out] `UINT_PTR` の配列。それぞれが指定された関数のネイティブ本体の開始アドレスです。</span><span class="sxs-lookup"><span data-stu-id="0c3f0-111">`codeStartAddresses` [out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c3f0-112">解説</span><span class="sxs-lookup"><span data-stu-id="0c3f0-112">Remarks</span></span>

<span data-ttu-id="0c3f0-113">階層化コンパイルが有効にされている場合、関数には複数のネイティブ コード本体を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0c3f0-113">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c3f0-114">要件</span><span class="sxs-lookup"><span data-stu-id="0c3f0-114">Requirements</span></span>

<span data-ttu-id="0c3f0-115">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c3f0-115">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="0c3f0-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c3f0-116">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0c3f0-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c3f0-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0c3f0-118">**.NET のバージョン:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c3f0-118">**.NET Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0c3f0-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c3f0-119">See also</span></span>

- [<span data-ttu-id="0c3f0-120">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c3f0-120">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
