---
description: '詳細情報: ICLRMetaHostPolicy インターフェイス'
title: ICLRMetaHostPolicy インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: b14ad417617c32242f8a59844f7c1f1a8d05c78d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637418"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy インターフェイス

ポリシー条件、マネージド アセンブリ、バージョン、および構成ファイルに基づいて、共通言語ランタイム (CLR) インターフェイスへのポインターを返す [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) メソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetRequestedRuntime メソッド](iclrmetahostpolicy-getrequestedruntime-method.md)|ポリシー条件、マネージド アセンブリ、バージョン、および構成ファイルに基づいて、優先される CLR インターフェイスを提供します。|  
  
## <a name="remarks"></a>解説  

 このインターフェイスへの参照を取得するには、次のコードに示すように [CLRCreateInstance](clrcreateinstance-function.md) 関数を呼び出します。  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> このインターフェイスでは、実際には CLR の読み込みもアクティブ化も行われず、インストールまたは読み込まれている使用可能なバージョンに基づいて、優先される CLR バージョンが返されます。  
  
 .NET Framework 4 のホスティング API では、特定のニーズを持つホストが意図しないペナルティを伴うことなく基本的な機能を使用できるようにするために、ポリシーが統合されています。 たとえば、MSCorEE.dll エクスポートの多くは特定の CLR にバインドされますが、メソッドでは論理的に要求されない場合もあります。 [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) 列挙体では、ほとんどのホストに共通するバインド ポリシーが提供されています。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [ホスト インターフェイス](hosting-interfaces.md)
- [ホスティング](index.md)
