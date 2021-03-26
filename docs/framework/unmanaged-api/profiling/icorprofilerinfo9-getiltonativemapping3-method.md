---
description: '詳細情報: ICorProfilerInfo9::GetILToNativeMapping3 メソッド'
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 865545e2352209447b3942da3a62f3733c165b35
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759327"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a><span data-ttu-id="a82e7-103">ICorProfilerInfo9::GetILToNativeMapping3 メソッド</span><span class="sxs-lookup"><span data-stu-id="a82e7-103">ICorProfilerInfo9::GetILToNativeMapping3 Method</span></span>

<span data-ttu-id="a82e7-104">ネイティブ コードの開始アドレスを指定すると、この just-in-time バージョンのコードのネイティブから IL へのマッピング情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="a82e7-104">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span>

## <a name="syntax"></a><span data-ttu-id="a82e7-105">構文</span><span class="sxs-lookup"><span data-stu-id="a82e7-105">Syntax</span></span>

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a><span data-ttu-id="a82e7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a82e7-106">Parameters</span></span>

<span data-ttu-id="a82e7-107">`pNativeCodeStartAddress` [in] ネイティブ関数の開始へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a82e7-107">`pNativeCodeStartAddress` [in] A pointer to the start of a native function.</span></span>

<span data-ttu-id="a82e7-108">`cMap` [in] `map` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="a82e7-108">`cMap` [in] The maximum size of the `map` array.</span></span>

<span data-ttu-id="a82e7-109">`pcMap` [out] 使用できる COR_DEBUG_IL_TO_NATIVE_MAP 構造体の総数。</span><span class="sxs-lookup"><span data-stu-id="a82e7-109">`pcMap` [out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>

<span data-ttu-id="a82e7-110">`map` [out] [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) 構造体の配列。各構造体はオフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="a82e7-110">`map` [out] An array of [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) structures, each of which specifies the offsets.</span></span> <span data-ttu-id="a82e7-111">`GetILToNativeMapping3` メソッドから制御が戻ると、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の一部または全部が `map` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="a82e7-111">After the `GetILToNativeMapping3` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>

## <a name="remarks"></a><span data-ttu-id="a82e7-112">解説</span><span class="sxs-lookup"><span data-stu-id="a82e7-112">Remarks</span></span>

<span data-ttu-id="a82e7-113">階層化コンパイルが有効にされている場合、メソッドには複数のネイティブ コード本体を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a82e7-113">When tiered compilation is enabled, a method may have more than one native code body.</span></span> <span data-ttu-id="a82e7-114">[ICorProfilerInfo9:: GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) によって、すべてのネイティブ コード本体の開始アドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="a82e7-114">[ICorProfilerInfo9::GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) will return the start addresses for all of the native code bodies.</span></span>

## <a name="requirements"></a><span data-ttu-id="a82e7-115">要件</span><span class="sxs-lookup"><span data-stu-id="a82e7-115">Requirements</span></span>

<span data-ttu-id="a82e7-116">**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a82e7-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="a82e7-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a82e7-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a82e7-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a82e7-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a82e7-119">**.NET Framework のバージョン:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a82e7-119">**.NET Framework Versions:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a82e7-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a82e7-120">See also</span></span>

- [<span data-ttu-id="a82e7-121">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a82e7-121">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
