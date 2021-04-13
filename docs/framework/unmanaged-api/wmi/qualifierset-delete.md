---
title: QualifierSet_Delete 関数 (アンマネージド API リファレンス)
description: QualifierSet_Delete 関数では、名前で指定した修飾子が削除されます。
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2000de77903c3dabb43116fa1700b4ed393aeb5a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721154"
---
# <a name="qualifierset_delete-function"></a>QualifierSet_Delete 関数

名前によって指定した修飾子が削除されます。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr` [in] [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) インスタンスへのポインター。

`wszName` [in] 削除する修飾子の名前。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName` パラメーターが有効ではありません。 |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | この修飾子の削除は無効です。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 指定した修飾子が見つかりませんでした。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | ローカル オーバーライドが削除され、親オブジェクトからの元の修飾子のスコープが再開されました。 |

## <a name="remarks"></a>解説

この関数では、[IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) メソッドの呼び出しがラップされます。

修飾子の伝達規則により、特定の修飾子が別のオブジェクトから継承され、現在のクラスまたはインスタンス内で単にオーバーライドされている可能性があります。 この場合、`QualifierSet_Delete` メソッドによって、修飾子が元の継承された値にリセットされます。 この場合、関数では状態コード `WBEM_S_RESET_TO_DEFAULT` が返されます。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
