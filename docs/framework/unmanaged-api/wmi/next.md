---
title: Next 関数 (アンマネージド API リファレンス)
description: Next 関数では、列挙内の次のプロパティが取得されます。
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c2a7fae32e82caae40a95bfdad10fa78082988ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726787"
---
# <a name="next-function"></a>Next 関数

[BeginEnumeration](beginenumeration.md) の呼び出しによって開始された列挙内の次のプロパティが取得されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a>パラメーター

`vFunc`\
[in] このパラメーターは使用されません。

`ptr`\
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`lFlags`\
[in] 予約されています。 このパラメーターは、0 にする必要があります。

`pstrName`\
[out] プロパティ名を格納している新しい `BSTR`。 名前が不要な場合は、このパラメーターを `null` に設定できます。

`pVal`\
[out] プロパティの値が格納された `VARIANT`。 値が不要な場合は、このパラメーターを `null` に設定できます。 関数からエラー コードが返される場合、`pVal` に渡された `VARIANT` は変更されずに残ります。

`pvtType`\
[out] `CIMTYPE` 変数 (プロパティの型が配置される `LONG`) へのポインター。 このプロパティの値には、`VT_NULL_VARIANT` を指定できます。この場合、プロパティの実際の型を特定する必要があります。 このパラメーターは、`null` にすることもできます。

`plFlavor`\
[out] `null`、またはプロパティの発生元に関する情報を受け取る値。 考えられる値については、「解説」を参照してください。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般エラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | [`BeginEnumeration`](beginenumeration.md) 関数の呼び出しがありませんでした。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するのに十分なメモリがありません。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 現在のプロセスと Windows 管理間のリモート プロシージャ コールが失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙にはこれ以上プロパティがありません。 |

## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) メソッドの呼び出しがラップされます。

このメソッドからは、システム プロパティも返されます。

プロパティの基になる型がオブジェクト パス、日付か時刻、または別の特殊な型である場合、戻り値の型には十分な情報が含まれていません。 呼び出し元では、プロパティがオブジェクト参照、日付か時刻、または別の特殊な型であるかどうかを判断するために、指定されたプロパティの `CIMTYPE` を調べる必要があります。

`plFlavor` が `null` でない場合、`LONG` の値は、次のように、プロパティの発生元に関する情報を受け取ります。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | プロパティは、標準のシステム プロパティです。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | クラスの場合: プロパティは親クラスから継承されます。 <br> インスタンスの場合: プロパティは親クラスから継承されましたが、インスタンスによって変更されていません。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | クラスの場合: プロパティは派生クラスに属します。 <br> インスタンスの場合: プロパティは、インスタンスによって変更されています。つまり、値が指定されたか、修飾子が追加または変更されました。 |

## <a name="requirements"></a>必要条件

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
