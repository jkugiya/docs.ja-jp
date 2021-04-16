---
description: '詳細情報: ICorConfiguration インターフェイス'
title: ICorConfiguration インターフェイス
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
ms.openlocfilehash: f75e9e445c7fe4615abcae27756bcc420b5255b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636678"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration インターフェイス

共通言語ランタイム (CLR) を構成するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AddDebuggerSpecialThread メソッド](icorconfiguration-adddebuggerspecialthread-method.md)|マネージまたはアンマネージのデバッグ シナリオ時にデバッガーによってアプリケーションが停止されている間に、特定のスレッドの実行を継続できるようにする必要があることを、デバッグ サービスに対して示します。|  
|[SetDebuggerThreadControl メソッド](icorconfiguration-setdebuggerthreadcontrol-method.md)|CLR スレッドがデバッグのためにブロックおよびブロック解除される際にデバッグ サービスによって呼び出されるコールバック インターフェイスを設定します。|  
|[SetGCHostControl メソッド](icorconfiguration-setgchostcontrol-method.md)|仮想メモリの制限を変更するようにホストに要求するために、ガベージ コレクターによって使用されるコールバック インターフェイスを設定します。|  
|[SetGCThreadControl メソッド](icorconfiguration-setgcthreadcontrol-method.md)|本来ならガベージ コレクションのためにブロックされる非ランタイム タスク用のスレッドをスケジュールするための、コールバック インターフェイスを設定します。|  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](hosting-interfaces.md)
- [CorRuntimeHost コクラス](corruntimehost-coclass.md)
