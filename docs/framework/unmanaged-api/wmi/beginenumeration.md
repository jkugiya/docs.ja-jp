---
title: BeginEnumeration 関数 (アンマネージド API リファレンス)
description: BeginEnumeration 関数では、列挙子が列挙の先頭にリセットされます
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6057526ddbe2efed65f8569e829c35524829e43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708219"
---
# <a name="beginenumeration-function"></a>BeginEnumeration 関数

列挙子を列挙の先頭にリセットします。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`\
[in] このパラメーターは使用されません。

`ptr`\
[in] [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。

`lEnumFlags`\
[in] 列挙に含まれるプロパティを制御する、「[解説](#remarks)」セクションで説明されているフラグまたは値のビットごとの組み合わせ。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnumFlags` のフラグの組み合わせが無効であるか、無効な引数が指定されました。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | `BeginEnumeration` への 2 回目の呼び出しは、[`EndEnumeration`](endenumeration.md) への中間呼び出しなしで行われました。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 新しい列挙を開始するのに十分なメモリがありません。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |
  
## <a name="remarks"></a>解説

この関数では、[IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) メソッドの呼び出しがラップされます。

`lEnumFlags` 引数として渡すことができるフラグは、*WbemCli.h* ヘッダー ファイル内で定義されているか、コード内で定数として定義することができます。  各グループのフラグを他のグループの任意のフラグと組み合わせることができます。 ただし、同じグループのフラグは相互に排他的です。

**グループ 1**

|定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | キーを構成するプロパティだけを含めます。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | オブジェクト参照であるプロパティだけを含めます。 |

**グループ 2**

定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 列挙をシステム プロパティのみに制限します。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | ローカルおよび伝播されたプロパティを含めますが、システム プロパティは列挙から除外します。 |

クラスの場合:

定数  |[値]  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | 列挙を、クラス定義でオーバーライドされたプロパティに限定します。 |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | 列挙を、現在のクラス定義でオーバーライドされたプロパティと、クラス内で定義されている新しいプロパティに限定します。 |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | `WBEM_FLAG_CLASS_OVERRIDES_ONLY` または `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` が設定されているかどうかを確認するために、`lEnumFlags` 値に対して適用するマスク (フラグではない)。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 列挙を、クラス自体で定義または変更されたプロパティに限定します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 列挙を、基底クラスから継承されたプロパティに限定します。 |

インスタンスの場合:

定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 列挙を、クラス自体で定義または変更されたプロパティに限定します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 列挙を、基底クラスから継承されたプロパティに限定します。 |

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
