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
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9::GetNativeCodeStartAddresses メソッド

functionId と rejitId を指定すると、現在存在するこのコードのすべての just-in-time バージョンのネイティブ コード開始アドレスが列挙されます。

## <a name="syntax"></a>構文

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>パラメーター

`functionId` [in] ネイティブコード開始アドレスを返す必要がある関数の ID。

`reJitId` [in] JIT 再コンパイルされた関数のID。

`cCodeStartAddresses` [in] `codeStartAddresses` 配列の最大サイズ。

`pcCodeStartAddresses` [out] 使用可能なアドレスの数。

`codeStartAddresses` [out] `UINT_PTR` の配列。それぞれが指定された関数のネイティブ本体の開始アドレスです。

## <a name="remarks"></a>解説

階層化コンパイルが有効にされている場合、関数には複数のネイティブ コード本体を指定できます。

## <a name="requirements"></a>要件

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET のバージョン:** [!INCLUDE[net_core_21](../../../../includes/net-core-21-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo9 インターフェイス](icorprofilerinfo9-interface.md)
