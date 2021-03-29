---
description: '詳細情報: ICorProfilerCallback10::EventPipeEventDelivered メソッド'
title: ICorProfilerCallback10::EventPipeEventDelivered メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerCallback10.EventPipeEventDelivered
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7b2ca813d610c2b41d97d8cd76dac22ca38802d7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805637"
---
# <a name="icorprofilercallback10eventpipeeventdelivered-method"></a>ICorProfilerCallback10::EventPipeEventDelivered メソッド

EventPipe イベントがそのプロファイラーの現在アクティブなセッションに配信されるたびにプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
    HRESULT EventPipeEventDelivered(
        [in] EVENTPIPE_PROVIDER provider,
        [in] DWORD eventId,
        [in] DWORD eventVersion,
        [in] ULONG cbMetadataBlob,
        [in, size_is(cbMetadataBlob)] LPCBYTE metadataBlob,
        [in] ULONG cbEventData,
        [in, size_is(cbEventData)] LPCBYTE eventData,
        [in] LPCGUID pActivityId,
        [in] LPCGUID pRelatedActivityId,
        [in] ThreadID eventThread,
        [in] ULONG numStackFrames,
        [in, length_is(numStackFrames)] UINT_PTR stackFrames[]); 
```  
  
## <a name="parameters"></a>パラメーター

`provider` [入力] このイベントの発信元のプロバイダー。

`eventId` [入力] 配信されるイベントの ID。

`eventVersion` [入力] 配信されるイベントのバージョン。

`cbMetadataBlob` [入力] `metadataBlob` の長さ (バイト数)。

`metadataBlob` [入力] イベントのメタデータ BLOB へのポインター。

`cbEventData` [入力] `eventData` の長さ (バイト数)。

`eventData` [入力] イベントのペイロード。

`pActivityId` [入力] イベントのアクティビティ ID を表す GUID へのポインター、または NULL。

`pRelatedActivityId` [入力] イベントの関連アクティビティ ID を表す GUID へのポインター、または NULL。

`eventThread` [入力] イベントが発生したスレッドの ID。

`numStackFrames` [入力] `stackFrames` 配列内の要素の数。

`stackFrames` [入力] イベントのマネージド呼び出し履歴を表すコード アドレスの配列。

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback10 インターフェイス](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 インターフェイス](icorprofilerinfo12-interface.md)
- [ICorProfilerInfo12.EventPipeStartSession メソッド](icorprofilerinfo12-eventpipestartsession-method.md)
