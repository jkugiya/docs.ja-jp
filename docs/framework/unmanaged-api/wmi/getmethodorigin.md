---
title: GetMethodOrigin 関数 (アンマネージド API リファレンス)
description: GetMethodOrigin 関数では、メソッドを宣言しているクラスが特定されます。
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 434392ffb4d9124e319bcd9c42fdd340d3fec5b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722779"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin 関数

メソッドを宣言しているクラスが特定されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`wszMethodName`  
[in] 所有クラスが要求されているオブジェクトのメソッドの名前。

`pstrClassName`  
[out] メソッドを所有するクラスの名前を受け取ります。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定したメソッドが見つかりませんでした。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つ以上のパラメーターが無効です。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) メソッドの呼び出しがラップされます。

クラスは 1 つまたは複数の基底クラスからメソッドを継承できるため、多くの場合、開発者は特定のメソッドが定義されているクラスを判別する必要があります。

`pstrClassName` パラメーターは `out` パラメーターであるため、この関数が呼び出される前は有効な `BSTR` を指していてはなりません。このポインターは、関数から制御が戻った後に割り当て解除されません。

## <a name="requirements"></a>必要条件  

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
