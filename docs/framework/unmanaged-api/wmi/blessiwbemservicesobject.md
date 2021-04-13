---
title: BlessIWbemServicesObject 関数 (アンマネージド API リファレンス)
description: BlessIWbemServicesObject 関数では、ユーザー資格情報によって IWbemServices オブジェクトへのアクセスが許可されるかどうかが示されます
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1aab2076f57f938715a3e65481a3540dc52279c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719750"
---
# <a name="blessiwbemservicesobject-function"></a>BlessIWbemServicesObject 関数

指定した [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) オブジェクトへのアクセスがユーザーの資格情報によって許可されるかどうかが示されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a>パラメーター

`pIWbemServices`\
[in] WMI サービス オブジェクトへのポインター。

`strUser`\
[in] ユーザー名。

`strPassword`\
[in] `strUser` に関連付けられているパスワード。

`strAuthority`\
[in] ユーザーのドメイン名。 詳細については、「[ConnectServerWmi](connectserverwmi.md) 関数」を参照してください。

`impLevel`\
[in] 偽装レベル。

`authnLevel`\
[in] 承認レベル。

## <a name="return-value"></a>戻り値

この関数によって返される次の値は、*WinError.h* ヘッダー ファイル内で定義されています。または、コード内で定数として定義することもできます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `E_INVALIDARG` | 0x80070057 | 1 つ以上の引数が無効です。 |
| `E_POINTER` | 0x80004003 | `pIWbemServices` が `null`です。 |
| `E_FAIL` | 0x80000008 | 特定できないエラーが発生しました。 |
| `E_OUTOFMEMORY` | 0x80000002 | 操作を実行するのに十分なメモリがありません。 |
| `S_OK` | 0 | 関数呼び出しは成功しました。 |

## <a name="requirements"></a>必要条件

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。

 **ヘッダー:** WMINet_Utils.idl

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
