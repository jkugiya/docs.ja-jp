---
description: '詳細情報: ICorProfilerCallback10 インターフェイス'
title: ICorProfilerCallback10 インターフェイス
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d9091dc81307e2dcb83e74154a8217dffaa1e7a2
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805650"
---
# <a name="icorprofilercallback10-interface"></a>ICorProfilerCallback10 インターフェイス

 プロファイラーに、EventPipe イベントがそのプロファイラーの現在アクティブなセッションに配信されたことを通知するためのコールバック メソッドを提供する、[ICorProfilerCallback9](icorprofilercallback9-interface.md) のサブクラス。
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EventPipeEventDelivered メソッド](icorprofilercallback10-eventpipeeventdelivered-method.md)|プロファイラーに、EventPipe イベントがそのプロファイラーが開いているセッションに配信されたことを通知します。|
|[EventPipeProviderCreated メソッド](icorprofilercallback10-eventpipeprovidercreated-method.md)|プロファイラーに、EventPipe プロバイダーが作成され、そのプロバイダーを自身のセッションに追加できるようになったことを通知します。|  
  
## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  

## <a name="see-also"></a>関連項目

- [EventPipe の概要](../../../core/diagnostics/eventpipe.md)
- [既知のイベント プロバイダー](../../../core/diagnostics/well-known-event-providers.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerInfo12 インターフェイス](ICorProfilerInfo12-interface.md)
- [ICorProfilerInfo12.EventPipeStartSession メソッド](ICorProfilerInfo12-eventpipestartsession-method.md)
- [ICorProfilerInfo12.EventPipeStopSession メソッド](ICorProfilerInfo12-eventpipestopsession-method.md)
