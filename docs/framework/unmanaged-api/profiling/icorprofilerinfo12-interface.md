---
description: '詳細情報: ICorProfilerInfo12 インターフェイス'
title: ICorProfilerInfo12 インターフェイス
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a8b91eba686478c3e825ae15d6ae95bd0ffad944
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805728"
---
# <a name="icorprofilerinfo12-interface"></a>ICorProfilerInfo12 インターフェイス

 EventPipe セッション、イベント、プロバイダーを作成するためのメソッドを提供する、[ICorProfilerInfo11](icorprofilerinfo11-interface.md) のサブクラス。
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EventPipeStartSession メソッド](icorprofilerinfo12-eventpipestartsession-method.md)|プロファイラーの EventPipe セッションを開始します。|
|[EventPipeAddProviderToSession メソッド](icorprofilerinfo12-eventpipeaddprovidertosession-method.md)|既存の EventPipe セッションにプロバイダーを追加します。|
|[EventPipeStopSession メソッド](icorprofilerinfo12-eventpipestopsession-method.md)|EventPipe セッションを停止します。|
|[EventPipeCreateProvider メソッド](icorprofilerinfo12-eventpipecreateprovider-method.md)|EventPipe プロバイダーを作成します。|  
|[EventPipeGetProviderInfo メソッド](icorprofilerinfo12-eventpipegetproviderinfo-method.md)|EventPipe プロバイダーの名前をその ID から取得します。|
|[EventPipeDefineEvent メソッド](icorprofilerinfo12-eventpipedefineevent-method.md)|既存の EventPipe プロバイダーでイベントを定義します。|  
|[EventPipeWriteEvent メソッド](icorprofilerinfo12-eventpipewriteevent-method.md)|EventPipe イベントを書き込みます。|
  
## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  

## <a name="see-also"></a>関連項目

- [EventPipe の概要](../../../core/diagnostics/eventpipe.md)
- [既知のイベント プロバイダー](../../../core/diagnostics/well-known-event-providers.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback10 インターフェイス](icorprofilercallback10-interface.md)
