---
description: '詳細情報: ICorProfilerInfo12::EventPipeGetProviderInfo メソッド'
title: ICorProfilerInfo12::EventPipeGetProviderInfo メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeGetProviderInfo
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 7bc7ffe1c31e88dc1c65f1670f9bd179e732abfe
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805702"
---
# <a name="icorprofilerinfo12eventpipegetproviderinfo-method"></a>ICorProfilerInfo12::EventPipeGetProviderInfo メソッド

他の EventPipe リスナーが受信するイベントを書き込むためにプロファイラーで使用できる EventPipe プロバイダーを作成します。
  
## <a name="syntax"></a>構文  
  
```cpp  
    HRESULT EventPipeGetProviderInfo(
                [in] EVENTPIPE_PROVIDER provider,
                [in]  ULONG      cchName,
                [out] ULONG      *pcchName,
                [out, annotation("_Out_writes_to_(cchName, *pcchName)")]
                      WCHAR      providerName[]);
```  
  
## <a name="parameters"></a>パラメーター

`provider` [入力] 名前を指定するプロバイダーの ID。

`cchName` [入力] `providerName` のサイズ (文字数)。

`pcchName` [出力] `providerName` の合計の文字の長さへのポインター。

`providerName` [出力] 呼び出し元によって提供されたワイド文字バッファー。 関数が戻るとき、このバッファーにプロバイダーの名前が格納されます。

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [EventPipe の概要](../../../core/diagnostics/eventpipe.md)
- [既知のイベント プロバイダー](../../../core/diagnostics/well-known-event-providers.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback10 インターフェイス](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 インターフェイス](icorprofilerinfo12-interface.md)
