---
title: SpawnDerivedClass 関数 (アンマネージド API リファレンス)
description: SpawnDerivedClass 関数では、オブジェクトから派生する新しいオブジェクトが作成されます。
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8020dd851b6773e6c76c53892c4b2bc21e4261bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716513"
---
# <a name="spawnderivedclass-function"></a>SpawnDerivedClass 関数

指定したオブジェクトから新たに派生するクラス オブジェクトが作成されます。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`lFlags`  
[in] 予約されています。 このパラメーターは、0 にする必要があります。

`ppNewClass`  
[out] 新しいクラス定義オブジェクトへのポインターを受け取ります。 エラーが発生した場合、新しいオブジェクトは返されず、`ppNewClass` は未変更のままになります。 この値を `null` にすることはできません。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般エラーが発生しました。 |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | 無効な操作 (例: インスタンスからクラスを生成する) が要求されました。 |
| `WBEM_E_INCOMPLETE_CLASS` | ソース クラスが完全に定義されていないか、Windows 管理に登録されていないため、新しい派生クラスは許可されません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | メモリ不足のため、操作を完了できません。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` が `null`です。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) メソッドの呼び出しがラップされます。

`ptr` は、生成されたオブジェクトの親クラスになるクラス定義である必要があります。 返されたオブジェクトは、現在のオブジェクトのサブクラスになります。

`ppNewClass` で返された新しいオブジェクトは、自動的に現在のオブジェクトのサブクラスになります。 この動作はオーバーライドできません。 サブクラス (派生クラス) を作成する方法は他にありません。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
