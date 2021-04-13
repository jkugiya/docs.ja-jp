---
title: VerifyClientKey 関数 (アンマネージド API リファレンス)
description: VerifyClientKey 関数によって、クライアント キーのセキュリティが適切であることが確認されます。
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 26cffe9936f2e01078b6f54e8499b58519f1018e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729422"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey 関数

クライアント キーに適切なセキュリティが確実に含められます。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a>戻り値

関数が成功した場合の戻り値は `ERROR_SUCCESS` (0) です。

関数が失敗した場合、戻り値は *WinError.h* で定義されている 0 以外のエラー コードです。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.def  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
