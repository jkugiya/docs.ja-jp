---
title: PutMethod 関数 (アンマネージド API リファレンス)
description: PutMethod 関数ではメソッドが作成されます。
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 8edbb8074573b98c017f98197d370c2ad37db80c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726757"
---
# <a name="putmethod-function"></a>PutMethod 関数

メソッドが作成されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`wszName`  
[in] 作成するメソッドの名前。

`lFlags`  
[in] 予約されています。 このパラメーターは、0 にする必要があります。

`pSignatureIn`  
[in] メソッドの `in` パラメーターを格納している [__Parameters システム クラス](/windows/desktop/WmiSdk/--parameters)のコピーへのポインター。 `null` に設定されている場合、このパラメーターは無視されます。  

`pSignatureOut`  
[in] メソッドの `out` パラメーターを格納している [__Parameters システム クラス](/windows/desktop/WmiSdk/--parameters)のコピーへのポインター。 `null` に設定されている場合、このパラメーターは無視されます。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つ以上のパラメーターが無効です。 |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | 0x80041043 | *pInSignature* と *pOutSignature* の両方のオブジェクトで指定された `[in, out]` メソッド パラメーターの修飾子が異なります。
| `WBEM_E_MISSING_PARAMETER_ID` | 0x80041036 | メソッド パラメーターに **ID** 修飾子の指定がありません。 |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | 0x80041038 | メソッドのパラメーターに割り当てられている ID 系列が連続していないか、0 から始まっていません。 |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | 0x80041039 | メソッドの戻り値に **ID** 修飾子があります。 |
| `WBEM_E_PROPAGATED_METHOD` | 0x80041034 | 親クラスから既存のメソッド名を再使用しようとしました。また、シグネチャは一致しませんでした。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。 |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) メソッドの呼び出しがラップされます。

このメソッド呼び出しは、`ptr` が CIM クラス定義の場合にのみサポートされます。 CIM インスタンスを指す [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ポインターからは、メソッド操作を使用できません。

ユーザーは、アンダースコアで開始または終了する名前を持つメソッドを作成することはできません。 これは、システム クラスおよびプロパティ用に予約されています。

メソッドの場合、`in` および `out` パラメーターは [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) オブジェクトのプロパティとして記述されます。

`[in/out]` パラメーターを定義するには、`pInSignature` および `pOutSignature` パラメーターが指す両方のオブジェクトに同じプロパティを追加します。 この場合、プロパティは同じ **ID** 修飾子値を共有します。

`ReturnValue` 以外の [__Parameters](/windows/desktop/WmiSdk/--parameters) クラス オブジェクトの各プロパティには **ID** 修飾子が必要です。これは、パラメーターが表示される順序を示す 0 から始まる数値です。 2 つのパラメーターの **ID** 値を同じにすることはできません。また、**ID** 値をスキップすることもできません。 どちらかの条件が発生した場合は、`PutMethod` 関数から `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` が返されます。

## <a name="example"></a>例

例については、「[IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) メソッド」を参照してください。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
