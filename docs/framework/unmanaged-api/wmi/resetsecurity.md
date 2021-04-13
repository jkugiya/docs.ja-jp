---
title: ResetSecurity 関数 (アンマネージド API リファレンス)
description: ResetSecurity 関数では、現在のスレッドに偽装トークンが割り当てられます。
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 259bef74356f16221f1453dd4086e2fbb26faa83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721115"
---
# <a name="resetsecurity-function"></a>ResetSecurity 関数

指定した偽装トークンが現在のスレッドに割り当てられます。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a>パラメーター

`token`  
[in] 現在のスレッドに関連付ける偽装トークン。 この値は `null` の場合もあります。

## <a name="return-value"></a>戻り値

関数が成功した場合の戻り値は `S_OK` (0) です。

関数が失敗した場合の戻り値はゼロ以外のエラー コードです。 拡張されたエラー情報を取得するには、[GetErrorInfo](geterrorinfo.md) 関数を呼び出します。
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
