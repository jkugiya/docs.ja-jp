---
description: '詳細情報: ICLRRuntimeHost::UnloadAppDomain メソッド'
title: ICLRRuntimeHost::UnloadAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
ms.openlocfilehash: 2a47c6250434c3ee4122f8eeae75f25ee4c08a34
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637288"
---
# <a name="iclrruntimehostunloadappdomain-method"></a>ICLRRuntimeHost::UnloadAppDomain メソッド

指定された数値識別子に対応するマネージド <xref:System.AppDomain> をアンロードします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `dwAppDomainId`  
 [in] アンロードするアプリケーション ドメインの数値識別子。  
  
 `fWaitUntilDone`  
 [in] アプリケーション ドメインのアンロードを試行する前に、アプリケーションの現在のスレッドの実行が完了するまで共通言語ランタイム (CLR) を待機させる必要がある場合は、`true` を指定します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`UnloadAppDomain` が正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていない、または CLR が、マネージド コードを実行したり呼び出しを正常に処理したりできない状態にあります。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元はロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバーが待機しているイベントがキャンセルされました。|  
|E_FAIL|不明な壊滅的なエラーが発生しました。 メソッドで E_FAIL が返される場合、CLR をプロセス内で使用することはできなくなります。 ホスト メソッドに対する後続の呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>解説  

 現在のスレッドが実行されているアプリケーション ドメインの数値識別子は、[GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md) を呼び出すことで取得できます。 この識別子は、マネージド <xref:System.AppDomain> 型の <xref:System.AppDomain.Id%2A> プロパティに対応します。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRRuntimeHost インターフェイス](iclrruntimehost-interface.md)
