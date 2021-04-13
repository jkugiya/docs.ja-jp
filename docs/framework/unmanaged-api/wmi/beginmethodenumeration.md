---
title: BeginMethodEnumeration 関数 (アンマネージド API リファレンス)
description: BeginMethodEnumeration 関数では、オブジェクトのメソッドの列挙が開始されます
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a72d61a572a0582ed8c03e56a8a9933c5f2775f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719763"
---
# <a name="beginmethodenumeration-function"></a>BeginMethodEnumeration 関数

オブジェクトで使用可能なメソッドの列挙が開始されます。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`lEnumFlags`  
[in] すべてのメソッドを表すゼロ (0)、または列挙のスコープを指定するフラグ。 次のフラグは、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 列挙を、クラス自体で定義されているメソッドに限定します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 列挙を、基底クラスから継承されたプロパティに限定します。 |

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags` は 0 以外であり、指定されたフラグの 1 つではありません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) メソッドの呼び出しがラップされます。

このメソッド呼び出しは、現在のオブジェクトがクラス定義の場合にのみサポートされます。 インスタンスを指す [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) ポインターからは、メソッド操作を使用できません。 メソッドが列挙される順序は、[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) の特定のインスタンスに対して不変であることが保証されます。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
