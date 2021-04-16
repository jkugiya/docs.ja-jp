---
description: '詳細情報: ICLRMetaHost インターフェイス'
title: ICLRMetaHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 5dc50af85c067bcb525414e47cddd34070b83a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637509"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost インターフェイス

バージョン番号に基づいて特定のバージョンの共通言語ランタイム (CLR) を返し、インストールされているすべての CLR を一覧表示し、指定されたプロセスに読み込まれているすべてのランタイムを一覧表示し、アセンブリをコンパイルするために使用された CLR バージョンを検出し、クリーン ランタイム シャットダウンを使用してプロセスを終了し、レガシ API バインディングを照会するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes メソッド](iclrmetahost-enumerateinstalledruntimes-method.md)|コンピューターにインストールされている各 CLR バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイス ポインターを含む列挙を返します。|  
|[EnumerateLoadedRuntimes メソッド](iclrmetahost-enumerateloadedruntimes-method.md)|指定したプロセスに読み込まれる CLR ごとに、有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイス ポインターを格納した列挙型を返します。 このメソッドは、[GetVersionFromProcess](getversionfromprocess-function.md) よりも優先されます。|  
|[ExitProcess メソッド](iclrmetahost-exitprocess-method.md)|読み込まれたすべてのランタイムを正常にシャットダウンしてから、プロセスを終了しようとします。 [CorExitProcess](corexitprocess-function.md) 関数よりも優先されます。|  
|[GetRuntime メソッド](iclrmetahost-getruntime-method.md)|特定の CLR バージョンに対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを取得します。 このメソッドは、[STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md)フラグと共に使用される [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 関数よりも優先されます。|  
|[GetVersionFromFile メソッド](iclrmetahost-getversionfromfile-method.md)|ファイルパスを指定して、アセンブリの元の .NET Framework コンパイルバージョン (メタデータに格納されている) を取得します。 このメソッドは、[GetFileVersion](getfileversion-function.md) よりも優先されます。|  
|[QueryLegacyV2RuntimeBinding メソッド](iclrmetahost-querylegacyv2runtimebinding-method.md)|[\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) 構成ファイル エントリの `useLegacyV2RuntimeActivationPolicy` 属性を使用するか、レガシ アクティブ化 API を直接使用するか、[ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) メソッドを呼び出して、レガシ アクティブ化ポリシーがバインドされているランタイムを表わすインターフェイスを返します。|  
|[RequestRuntimeLoadedNotification メソッド](iclrmetahost-requestruntimeloadednotification-method.md)|CLR バージョンが最初に読み込まれたものの、まだ起動されていない場合に、指定された関数ポインターへのコールバックを保証します。 このメソッドは、[LockClrVersion](lockclrversion-function.md) よりも優先されます|  
  
## <a name="remarks"></a>解説  

 このインターフェイスのインスタンスを取得する唯一の方法は、次のように [CLRCreateInstance](clrcreateinstance-function.md) 関数を呼び出すことです。  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](hosting-interfaces.md)
- [ホスティング](index.md)
