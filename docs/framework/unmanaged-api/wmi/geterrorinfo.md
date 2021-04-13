---
title: GetErrorInfo 関数 (アンマネージド API リファレンス)
description: GetErrorInfo 関数では、前の関数呼び出しからのエラー情報が取得されます。
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5da4eaa459c515689b822e4cb537380245e800e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722766"
---
# <a name="geterrorinfo-function"></a>GetErrorInfo 関数

前の関数呼び出しからエラー情報が取得されます。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a>戻り値

関数呼び出しが成功した場合は、[IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) オブジェクトへのポインター。失敗した場合は `null`。
  
## <a name="remarks"></a>解説

この関数では、[IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) メソッドの呼び出しがラップされます。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.def  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
