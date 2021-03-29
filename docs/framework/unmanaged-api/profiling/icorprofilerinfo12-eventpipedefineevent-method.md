---
description: '詳細情報: ICorProfilerInfo12::EventPipeDefineEvent メソッド'
title: ICorProfilerInfo12::EventPipeDefineEvent メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeDefineEvent
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 845f7f26dce7aa0f4b7d895b9f04cc89e7ac7192
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805754"
---
# <a name="icorprofilerinfo12eventpipedefineevent-method"></a>ICorProfilerInfo12::EventPipeDefineEvent メソッド

既存のプロバイダーで EventPipe イベントを定義します。 このプロバイダーを使用すると、他のリスナーが受信できる EventPipe イベントを書き込むことができます。
  
## <a name="syntax"></a>構文  
  
```cpp  
    HRESULT EventPipeDefineEvent(
                [in] EVENTPIPE_PROVIDER     provider,
                [in, string] const WCHAR   *eventName,
                [in] UINT32                 eventID,
                [in] UINT64                 keywords,
                [in] UINT32                 eventVersion,
                [in] UINT32                 level,
                [in] UINT8                  opcode,
                [in] BOOL                   needStack,
                [in] UINT32                 cParamDescs,
                [in, size_is(cParamDescs)]
                     COR_PRF_EVENTPIPE_PARAM_DESC pParamDescs[],
                [out] EVENTPIPE_EVENT      *pEvent);
```  
  
## <a name="parameters"></a>パラメーター

`provider` [入力] イベントを定義するプロバイダーの ID。

`eventName` [入力] イベント名が含まれている null で終わるワイド文字列へのポインター。

`eventID` [入力] 定義されるイベントの ID。

`keywords` [入力] 定義されるイベントのキーワード。

`eventVersion` [入力] 定義されるイベントのバージョン。

`level` [入力] 定義されるイベントのレベル。

`opcode` [入力] 定義されるイベントのオペコード。

`needStack` [入力] このイベントが起動されるたびにマネージド スタックを収集するかどうかを示す `BOOL`。

`cParamDescs` [入力] `pParamDescs` 内のパラメーターの数。

`pParamDescs` [入力] 定義されるイベントへのパラメーターの型を定義している `COR_PRF_EVENTPIPE_PARAM_DESC` の配列。

`pEvent` [出力] 関数が戻るときに定義されるイベントの ID が入力される、呼び出し元によって提供されたポインター。

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [EventPipe の概要](../../../core/diagnostics/eventpipe.md)
- [既知のイベント プロバイダー](../../../core/diagnostics/well-known-event-providers.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback10 インターフェイス](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 インターフェイス](icorprofilerinfo12-interface.md)
- [COR_PRF_EVENTPIPE_PARAM_DESC 構造体](cor-prf-eventpipe-param-desc-structure.md)
