---
description: 詳細については、「ModuleBindInfo 構造体」を参照してください。
title: ModuleBindInfo 構造体
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
ms.openlocfilehash: 0969c0ecc459414336800e8e7da5817ac0c1a8ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679624"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo 構造体

参照されるモジュールとそれを含むアセンブリに関する詳細情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dwAppDomainId`|参照先の `IStream` モジュールの読み込み元である [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md) メソッドへの呼び出しによって返されるの一意の識別子。|  
|`lpAssemblyIdentity`|参照されたモジュールを含むアセンブリの一意の識別子。|  
|`lpModuleName`|参照されているモジュールの名前。|  
  
## <a name="remarks"></a>解説  

 `ModuleBindInfo` は、にパラメーターとして渡され `IHostAssemblyStore::ProvideModule` ます。 ホストは、一意の識別子 `dwAppDomainId` を共通言語ランタイム (CLR) に提供します。 [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md)メソッドの呼び出しが返されると、ランタイムは識別子を使用して、の内容が `IStream` マップされているかどうかを判断します。 その場合、ランタイムはストリームを再マップするのではなく、既存のコピーを読み込みます。 ランタイムは、メソッドへの呼び出しから返されるストリームの参照キーとしても、この識別子を使用し `IHostAssemblyStore::ProvideAssembly` ます。 このため、識別子は、モジュール要求とアセンブリ要求に対して一意である必要があります。  
  
## <a name="requirements"></a>要件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](hosting-structures.md)
- [AssemblyBindInfo 構造体](assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager インターフェイス](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList インターフェイス](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager インターフェイス](ihostassemblymanager-interface.md)
