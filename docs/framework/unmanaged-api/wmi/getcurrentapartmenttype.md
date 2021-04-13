---
title: GetCurrentApartmentType 関数 (アンマネージド API リファレンス)
description: GetCurrentApartmentType 関数では、呼び出し元が実行されているアパートメントの種類が取得されます。
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0832867d86b7dda80e037846d9aa66c1d37f87be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726198"
---
# <a name="getcurrentapartmenttype-function"></a>GetCurrentApartmentType 関数

呼び出し元が実行されているアパートメントの種類が取得されます。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in] このパラメーターは使用されません。

`ptr`  
[in] [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) インスタンスへのポインター。

`aptType`  
[out] 呼び出し元のアパートメントを示す [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) 列挙値へのポインター。

## <a name="return-value"></a>戻り値

|定数  |[値]  |説明  |
|---------|---------|---------|
| `S_OK` | 0 | 関数は正常に終了しました。 |
| `E_FAIL` | 0x80000008 | 呼び出し元がアパートメント内で実行されていません。 |
  
## <a name="remarks"></a>解説

この関数では、[IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) メソッドの呼び出しがラップされます。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
