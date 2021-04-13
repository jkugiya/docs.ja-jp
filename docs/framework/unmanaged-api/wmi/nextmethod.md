---
title: NextMethod 関数 (アンマネージド API リファレンス)
description: NextMethod 関数では、列挙内の次のメソッドが取得されます。
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a0466aee47b0a6142870640c78b43f49e221ac2b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726770"
---
# <a name="nextmethod-function"></a>NextMethod 関数

[BeginMethodEnumeration](beginmethodenumeration.md) の呼び出しによって開始された列挙内の次のメソッドが取得されます。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`lFlags`  
[in] 予約されています。 このパラメーターは、0 にする必要があります。

`pName`  
[out] 呼び出しの前の `null` を指すポインター。 関数から制御が戻るときに、メソッド名を含む新しい `BSTR` のアドレスが返されます。

`ppSignatureIn`  
[out] メソッドの `in` パラメーターを格納している [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) へのポインターを受け取るポインター。

`ppSignatureOut`  
[out] メソッドの `out` パラメーターを格納している [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) へのポインターを受け取るポインター。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | [`BeginEnumeration`](beginenumeration.md) 関数の呼び出しがありませんでした。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列挙にはこれ以上プロパティがありません。 |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) メソッドの呼び出しがラップされます。

呼び出し元では、[BeginMethodEnumeration 関数](beginmethodenumeration.md)を呼び出すことで列挙シーケンスが開始され、関数から `WBEM_S_NO_MORE_DATA` が返されるまで [NextMethod] 関数が呼び出されます。 必要に応じて、呼び出し元では [EndMethodEnumeration](endmethodenumeration.md) を呼び出すことによってシーケンスを終了します。 呼び出し元は、いつでも [EndMethodEnumeration](endmethodenumeration.md) を呼び出すことによって列挙を早期に終了できます。

## <a name="example"></a>例

C++ の例については、「[IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) メソッド」を参照してください。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
