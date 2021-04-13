---
title: GetDemultiplexedStub 関数 (アンマネージド API リファレンス)
description: GetDemultiplexedStub 関数では、Windows 管理から非同期呼び出しを受信する際にクライアントを支援するオブジェクト転送シンクが作成されます。
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f8f9b56268168bb16c476a9366facd17e8ac44e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730631"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub 関数

Windows 管理から非同期呼び出しを受信する際にクライアントを支援するオブジェクト転送シンクが作成されます。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a>パラメーター

`pObject`  
[in] [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink) のクライアントのインプロセス実装へのポインター。

`isLocal`  
[in] イベントがローカル (`true`) であるか、それ以外であるか (`false`) を示すフラグ。

`ppObject`  
[out] Windows 管理から非同期呼び出しを受信する際にクライアントを支援するオブジェクト転送シンク。

## <a name="return-value"></a>戻り値

関数が成功した場合の戻り値は `S_OK` (0) です。

関数が失敗した場合の戻り値はゼロ以外のエラー コードです。 拡張されたエラー情報を取得するには、[GetErrorInfo](geterrorinfo.md) 関数を呼び出します。

## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)](index.md)
