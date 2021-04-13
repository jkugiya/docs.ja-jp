---
title: EndMethodEnumeration 関数 (アンマネージド API リファレンス)
description: EndMethodEnumeration 関数では、メソッドの列挙シーケンスが終了します。
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 82f50530967699427d8a00b1c9f518b639273626
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708063"
---
# <a name="endmethodenumeration-function"></a>EndMethodEnumeration 関数

[BeginMethodEnumeration 関数](beginmethodenumeration.md)を呼び出すことで開始された列挙シーケンスが終了します。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | 0x8004101d | 内部エラーが発生しました。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) メソッドの呼び出しがラップされます。

呼び出し元では、[BeginMethodEnumeration 関数](beginmethodenumeration.md)を使用して列挙シーケンスが開始され、メソッドから `WBEM_S_NO_MORE_DATA` が返されるまで [NextMethod 関数](nextmethod.md )が呼び出されます。 呼び出し元は、`EndMethodEnumeration` を呼び出すことによってシーケンスを終了することもできます。 呼び出し元は、いつでも `EndMethodEnumeration` を呼び出すことによって列挙を早期に終了できます。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
