---
description: '詳細情報: ICLRPolicyManager インターフェイス'
title: ICLRPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 8823f1db8b15b327306ff3c592b46c94537f4331
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637379"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager インターフェイス

エラーやタイムアウトが発生した場合に実行されるポリシー アクションをホストで指定できるようにするメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[SetActionOnFailure メソッド](iclrpolicymanager-setactiononfailure-method.md)|指定した失敗の発生時に共通言語ランタイム (CLR) により実行されるポリシー アクションを指定します。|  
|[SetActionOnTimeout メソッド](iclrpolicymanager-setactionontimeout-method.md)|指定された操作がタイムアウトしたときに CLR により実行されるポリシー アクションを指定します。|  
|[SetDefaultAction メソッド](iclrpolicymanager-setdefaultaction-method.md)|指定された操作が発生したときに CLR により実行されるポリシー アクションを指定します。|  
|[SetTimeout メソッド](iclrpolicymanager-settimeout-method.md)|指定された操作のタイムアウト値を設定します。|  
|[SetTimeoutAndAction メソッド](iclrpolicymanager-settimeoutandaction-method.md)|指定された操作のタイムアウト値を設定し、その操作が行われたとき、CLR で行うポリシー アクションを指定します。|  
|[SetUnhandledExceptionPolicy メソッド](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|未処理の例外が発生した場合の CLR の動作を指定します。|  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** リソースとして MSCorEE.dll に含まれている  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EClrFailure 列挙型](eclrfailure-enumeration.md)
- [EClrOperation 列挙型](eclroperation-enumeration.md)
- [EPolicyAction 列挙型](epolicyaction-enumeration.md)
- [ICLRControl インターフェイス](iclrcontrol-interface.md)
