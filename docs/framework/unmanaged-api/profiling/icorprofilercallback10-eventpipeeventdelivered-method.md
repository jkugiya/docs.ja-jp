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
ms.openlocfilehash: 73f3eb64671b22b1ec16b5a5b1b24115f7f65f6d
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231337"
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
