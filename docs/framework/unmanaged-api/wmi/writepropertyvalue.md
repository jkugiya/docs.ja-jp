---
title: WritePropertyValue 関数 (アンマネージド API リファレンス)
description: WritePropertyValue 関数では、プロパティにバイトが書き込まれます。
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e225516b06c477dc1a24cf721bc3e1ade9076b75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729409"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue 関数

指定したバイト数が、プロパティ ハンドルによって識別されるプロパティに書き込まれます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WritePropertyValue (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) インスタンスへのポインター。

`lHandle`  
[in] このプロパティを識別するハンドルを格納している整数。 ハンドルは、[GetPropertyHandle](getpropertyhandle.md) 関数を呼び出すことによって取得できます。

`lNumBytes`  
[in] プロパティに書き込まれるバイト数。 詳細については、「[解説](#remarks)」セクションを参照してください。

`pHandle` [out] データが格納されているバイト配列へのポインター。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | 型の不一致が発生しました。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) メソッドの呼び出しがラップされます。

この関数を使用して、文字列と、`DWORD` または `QWORD` 以外のその他すべてのデータを設定できます。

文字列以外のプロパティ値の場合、`lNumBytes` は、指定されたプロパティ型の正しいデータ サイズである必要があります。 文字列プロパティ値の場合、`lNumBytes` は、指定された文字列の長さ (バイト単位) である必要があり、文字列自体は偶数バイト単位の長さで、その後に null 終端文字が続く必要があります。

## <a name="requirements"></a>必要条件  

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
