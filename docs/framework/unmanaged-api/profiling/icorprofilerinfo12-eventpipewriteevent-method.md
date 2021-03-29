---
description: '詳細情報: ICorProfilerInfo12::EventPipeWriteEvent メソッド'
title: ICorProfilerInfo12::EventPipeWriteEvent メソッドド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeWriteEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: a0a06ff0fa1c936518586834f4dfc73810ef0e44
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805741"
---
# <a name="icorprofilerinfo12eventpipewriteevent-method"></a>ICorProfilerInfo12::EventPipeWriteEvent メソッドド

このイベントを有効にしているすべてのリスナーに EventPipe イベントを書き込みます。
  
## <a name="syntax"></a>構文  
  
```cpp  
    HRESULT EventPipeWriteEvent(
                [in] EVENTPIPE_EVENT    event,
                [in] UINT32             cData,
                [in, size_is(cData)]
                     COR_PRF_EVENT_DATA data[],
                [in] LPCGUID            pActivityId,
                [in] LPCGUID            pRelatedActivityId);
```  
  
## <a name="parameters"></a>パラメーター

`event` [入力] 書き込まれるイベントの ID。

`cData` [入力] `data` 内の要素の数。

`data` [入力] イベント引数が含まれている `COR_PRF_EVENT_DATA` の配列。

`pActivityId` [入力] イベントのアクティビティ ID を指定する GUID へのポインター。

`pRelatedActivityId` [入力] イベントの関連アクティビティ ID を指定する GUID へのポインター。

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback10 インターフェイス](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 インターフェイス](icorprofilerinfo12-interface.md)
- [COR_PRF_EVENT_DATA 構造体](cor-prf-event-data-structure.md)
