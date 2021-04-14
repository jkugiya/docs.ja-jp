---
title: GetQualifierSet 関数 (アンマネージド API リファレンス)
description: GetQualifierSet 関数では、クラスまたはインスタンスに対して設定された修飾子が取得されます。
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f9bb882a0f62499167b79bf3e6691d05e394720f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671344"
---
# <a name="getqualifierset-function"></a>GetQualifierSet 関数

クラス インスタンスまたはクラス定義で設定された修飾子が取得されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`ppQualSet`  
[out] クラス オブジェクトの修飾子にアクセスするためのインターフェイス ポインターを受け取ります。 `ppQualSet` として `null` を使用することはできません。 エラーが発生した場合、新しいオブジェクトは返されず、ポインターは変更されません。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定されたメソッドは存在しません。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | メモリ不足のため、操作を完了できません。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが `null` です。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) メソッドの呼び出しがラップされます。

[IWbemQualifierSet ポインター](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)を使用すると、呼び出し元はこれらの修飾子を追加、編集、削除できます。 そのように追加、編集、削除された修飾子は、インスタンスまたはクラス定義全体に適用されます。

## <a name="requirements"></a>必要条件  

**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
