---
title: QualifierSet_Next 関数 (アンマネージド API リファレンス)
description: QualifierSet_Next 関数では、列挙型内の次の修飾子が取得されます。
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 54d79a3dc081e9cdcb42153b6f7aa457557e3399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721128"
---
# <a name="qualifierset_next-function"></a>QualifierSet_Next 関数

[QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) 関数の呼び出しによって開始された列挙型内の次の修飾子が返されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor
);
```  

## <a name="parameters"></a>パラメーター

`vFunc` [in] このパラメーターは使用されません。

`ptr` [in] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) インスタンスへのポインター。

`lFlags` [in] 予約されています。 このパラメーターは、0 にする必要があります。

`pstrName` [out] 修飾子の名前。 `null` の場合、このパラメーターは無視されます。それ以外の場合、`pstrName` は有効な `BSTR` を指していないか、メモリ リークが発生しています。 null 値以外の場合、関数では、`WBEM_S_NO_ERROR` を返すときに常に新しい `BSTR` が割り当てられます。

`pVal` [out] 成功した場合は、修飾子の値。 関数が失敗した場合、`pVal` が指す `VARIANT` を変更することはできません。 このパラメーターが `null` の場合、このパラメーターは無視されます。

`plFlavor` [out] 修飾子の種類を受け取る LONG へのポインター。 種類の情報が必要でない場合は、このパラメーターを `null` にすることができます。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 呼び出し元によって [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) が呼び出されませんでした。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するのに十分なメモリがありません。 |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙内にはそれ以上修飾子が残されていません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) メソッドの呼び出しがラップされます。

`QualifierSet_Next` 関数を繰り返し呼び出して、関数から `WBEM_S_NO_MORE_DATA` が返されるまですべての修飾子を列挙します。 列挙を早期に終了するには、[QualifierSet_EndEnumeration](qualifierset-endenumeration.md) 関数を呼び出します。

列挙中に返される修飾子の順序は定義されていません。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
