---
title: CloneEnumWbemClassObject 関数 (アンマネージド API リファレンス)
description: CloneEnumWbemClassObject 関数では、列挙子の論理コピーが作成されます。
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fa8a7f436c018e3e083be452d300eb21e17f93f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708128"
---
# <a name="cloneenumwbemclassobject-function"></a>CloneEnumWbemClassObject 関数

列挙型内での位置を維持して、列挙子の論理コピーが作成されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum,
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject,
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority
);
```

## <a name="parameters"></a>パラメーター

`ppEnum`\
[out] 新しい [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) へのポインターを受け取ります。

`authLevel`\
[in] 承認レベル。

`impLevel`\
[in] 偽装レベル。

`pCurrentEnumWbemClassObject`\
[out] 複製する [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) インスタンスへのポインター。

`strUser`\
[in] ユーザー名。 詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。

`strPassword`\
[in] パスワード。 詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。

`strAuthority`\
[in] ユーザーのドメイン名。 詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WbemCli.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般エラーが発生しました。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | メモリ不足のため、操作を完了できません。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 現在のプロセスと WMI の間のリモート プロシージャ コール (RPC) リンクが失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しは成功しました。  |

## <a name="remarks"></a>解説

この関数では、[IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) メソッドの呼び出しがラップされます。

このメソッドでは、"ベスト エフォート" コピーだけが行われます。 多くの CIM オブジェクトは動的な性質を持つため、新しい列挙子ではソース列挙子と同じオブジェクトのセットが列挙されない可能性があります。

関数呼び出しが失敗した場合は、[GetErrorInfo](geterrorinfo.md) 関数を呼び出して追加のエラー情報を取得できます。

## <a name="example"></a>例

例については、「[IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) メソッド」を参照してください。

## <a name="requirements"></a>必要条件

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

 **ヘッダー:** WMINet_Utils.idl

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
