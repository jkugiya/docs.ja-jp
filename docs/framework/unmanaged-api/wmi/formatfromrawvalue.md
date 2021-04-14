---
title: FormatFromRawValue 関数 (アンマネージド API リファレンス)
description: FormatFromRawValue 関数では、生のパフォーマンス データが指定した形式に変換されます。
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e678aca5baf82c07ec9fc5c85cef22630af5ab0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672332"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue 関数

1 つの生のパフォーマンス データ値が指定した形式に変換されます。この形式変換が時間ベースである場合は、2 つの生のパフォーマンス データ値が変換されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a>パラメーター

`dwCounterType`\
[in] カウンターの種類。 カウンターの種類の一覧については、「[WMI パフォーマンス カウンターの種類](/windows/desktop/WmiSdk/wmi-performance-counter-types)」を参照してください。 `dwCounterType` には、`PERF_LARGE_RAW_FRACTION` および `PERF_LARGE_RAW_BASE` を除く任意のカウンターの種類を指定できます。

`dwFormat`\
[in] 生のパフォーマンス データの変換後の形式。 次のいずれかの値を指定できます。

|定数  |[値]  |説明 |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | 計算された値を倍精度浮動小数点値として返します。 |
| `PDH_FMT_LARGE` | 0x00000400 | 計算された値を 64 ビット整数として返します。 |
| `PDH_FMT_LONG` | 0x00000100 | 計算された値を 32 ビット整数として返します。 |

上の値のいずれかを、次のいずれかのスケール フラグと OR 演算できます。

|定数  |[値]  |説明 |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | カウンターのスケール ファクターを適用しません。 |
| `PDH_FMT_1000` | 0x00002000 | 最終的な値を 1,000 で乗算します。 |

`pTimeBase`\
[in] 時間基準 (形式変換に必要な場合) へのポインター。 形式変換に時間基準の情報が不要な場合、このパラメーターの値は無視されます。

`pRawValue1`\
[in] 生のパフォーマンス値を表す [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) 構造体へのポインター。

`pRawValue2`\
[in] 2 番目の生のパフォーマンス値を表す [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) 構造体へのポインター。 2 番目の生のパフォーマンス値が不要な場合、このパラメーターは `null` にする必要があります。

`pFmtValue`\
[out] 書式設定されたパフォーマンス値を受け取る [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) 構造体へのポインター。

## <a name="return-value"></a>戻り値

この関数により、次の値が返されます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | 関数呼び出しは成功しました。 |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | 必須の引数が指定されていないか、正しくありません。 |
| `PDH_INVALID_HANDLE` | 0xC0000BBC | このハンドルは有効な PDH オブジェクトではありません。 |

## <a name="remarks"></a>解説

この関数では、[FormatFromRawValue](/previous-versions/ms231047(v=vs.85)) 関数の呼び出しがラップされます。

## <a name="requirements"></a>必要条件

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

 **ライブラリ:** PerfCounter.dll

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
