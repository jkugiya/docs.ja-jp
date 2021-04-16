---
description: '詳細情報: ICLRMetaHost::GetRuntime メソッド'
title: ICLRMetaHost::GetRuntime メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetRuntime
helpviewer_keywords:
- GetRuntime method [.NET Framework hosting]
- ICLRMetaHost::GetRuntime method [.NET Framework hosting]
ms.assetid: a10749f1-ab91-47cf-982f-d8ccd2e81bd2
topic_type:
- apiref
ms.openlocfilehash: 8a2ada652dbb139337150cb8ed20986ebf8ae7f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637522"
---
# <a name="iclrmetahostgetruntime-method"></a>ICLRMetaHost::GetRuntime メソッド

特定のバージョンの共通言語ランタイム (CLR) に対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを取得します。 このメソッドは、[STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)フラグと共に使用される [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 関数よりも優先されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRuntime (  
    [in] LPCWSTR pwzVersion,  
    [in] REFIID riid,  
    [out,iid_is(riid), retval] LPVOID *ppRuntime  
);  
```  
  
## <a name="parameters"></a>パラメーター  

 `pwzVersion`  
 [in] "v *A*.*B*[.*X*]" という形式でメタデータに格納された .NET Framework のコンパイル バージョン。 *A*、 *B*、および *X* は、メジャー バージョン、マイナー バージョン、およびビルド番号に対応する 10 進数です。  
  
> [!NOTE]
> このパラメーターは、C:\Windows\Microsoft.NET\Framework または C:\Windows\Microsoft.NET\Framework64 の下に表示される .NET Framework バージョンのディレクトリ名と一致する必要があります。  
  
 値の例としては、"v1.0.3705"、"v1.1.4322"、"v2.0.50727"、および "v4.0.*X*" があります。ここで *X* は、インストールされているビルド番号に依存します。 "v" プレフィックスが必要です。  
  
 `riid`  
 [in] 目的のインターフェイスの識別子。 現在、このパラメーターの有効な値は IID_ICLRRuntimeInfo だけです。  
  
 `ppRuntime`  
 [out] 要求されたランタイムに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスへのポインター。  
  
## <a name="return-value"></a>戻り値  

 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
|E_POINTER|`pwzVersion` または `ppRuntime` が null です。|  
  
## <a name="remarks"></a>解説  

 このメソッドは、[ICorRuntimeHost](icorruntimehost-interface.md) インターフェイスなどのレガシ インターフェイスや、非推奨の `CorBindTo*` 関数などのレガシ関数と整合性を保って相互作用します (.NET Framework 2.0 ホスティング API の「[非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)」を参照してください)。 つまり、レガシ API を使って読み込まれたランタイムは新しい API から参照でき、新しい API を使って読み込まれたランタイムはレガシ API から参照できます。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRMetaHost インターフェイス](iclrmetahost-interface.md)
- [非推奨の CLR のホスト インターフェイスおよびコクラス](deprecated-clr-hosting-interfaces-and-coclasses.md)
- [CLR ホスト インターフェイス](clr-hosting-interfaces.md)
- [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md)
- [ホスティング](index.md)
