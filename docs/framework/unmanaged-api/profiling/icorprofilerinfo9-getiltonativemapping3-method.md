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
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9::GetILToNativeMapping3 メソッド

ネイティブ コードの開始アドレスを指定すると、この just-in-time バージョンのコードのネイティブから IL へのマッピング情報が返されます。

## <a name="syntax"></a>構文

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a>パラメーター

`pNativeCodeStartAddress` [in] ネイティブ関数の開始へのポインター。

`cMap` [in] `map` 配列の最大サイズ。

`pcMap` [out] 使用できる COR_DEBUG_IL_TO_NATIVE_MAP 構造体の総数。

`map` [out] [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) 構造体の配列。各構造体はオフセットを指定します。 `GetILToNativeMapping3` メソッドから制御が戻ると、`COR_DEBUG_IL_TO_NATIVE_MAP` 構造体の一部または全部が `map` に格納されます。

## <a name="remarks"></a>解説

階層化コンパイルが有効にされている場合、メソッドには複数のネイティブ コード本体を指定できます。 [ICorProfilerInfo9:: GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) によって、すべてのネイティブ コード本体の開始アドレスが返されます。

## <a name="requirements"></a>要件

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo9 インターフェイス](icorprofilerinfo9-interface.md)
