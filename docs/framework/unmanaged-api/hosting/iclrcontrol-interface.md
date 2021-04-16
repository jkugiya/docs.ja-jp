---
description: '詳細情報: ICLRControl インターフェイス'
title: ICLRControl インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: e108506d06b746d631f4c15c37d467399de30aba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637665"
---
# <a name="iclrcontrol-interface"></a>ICLRControl インターフェイス

共通言語ランタイム (CLR) への参照をホストで取得し、その側面を構成できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCLRManager メソッド](iclrcontrol-getclrmanager-method.md)|ホストで CLR を構成するために使用できる任意のマネージャー型のインスタンスへのインターフェイス ポインターを取得します。|  
|[SetAppDomainManagerType メソッド](iclrcontrol-setappdomainmanagertype-method.md)|アプリケーション ドメイン マネージャーの型として <xref:System.AppDomainManager> から派生した型を設定します。|  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRAssemblyIdentityManager インターフェイス](iclrassemblyidentitymanager-interface.md)
- [ICLRDebugManager インターフェイス](iclrdebugmanager-interface.md)
- [ICLRGCManager インターフェイス](iclrgcmanager-interface.md)
- [ICLRHostBindingPolicyManager インターフェイス](iclrhostbindingpolicymanager-interface.md)
- [ICLRHostProtectionManager インターフェイス](iclrhostprotectionmanager-interface.md)
- [ICLROnEventManager インターフェイス](iclroneventmanager-interface.md)
- [ICLRPolicyManager インターフェイス](iclrpolicymanager-interface.md)
- [IHostControl インターフェイス](ihostcontrol-interface.md)
- [ホスト インターフェイス](hosting-interfaces.md)
