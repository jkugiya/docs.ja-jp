---
description: '詳細情報: ICorProfilerInfo10::GetLOHObjectSizeThreshold メソッド'
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 7dca887f6d0ff5f9360b0edaa1568bc4b1bb42ac
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759769"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10::GetLOHObjectSizeThreshold メソッド

構成されているラージ オブジェクト ヒープ (LOH) のしきい値の値を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>パラメーター

`pThreshold` [出力] ラージ オブジェクト ヒープのしきい値 (バイト単位)。

## <a name="remarks"></a>解説

ラージ オブジェクト ヒープのしきい値より大きいオブジェクトは、ラージ オブジェクト ヒープ上に割り当てられます。 .NET Core 3.0 以降では、ラージ オブジェクト ヒープのしきい値は構成可能であり、`pThreshold` にはアクティブなラージ オブジェクト ヒープのしきい値のサイズ (バイト単位) が格納されます。

## <a name="requirements"></a>要件

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](icorprofilerinfo10-interface.md)
