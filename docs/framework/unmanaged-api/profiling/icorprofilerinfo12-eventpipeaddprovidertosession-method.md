---
description: '詳細情報: ICorProfilerInfo12::EventPipeAddProviderToSession メソッド'
title: ICorProfilerInfo12::EventPipeAddProviderToSession メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo12.EventPipeAddProviderToSession
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 70654660c496211c20459ef9ba37dfbd96b829b3
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805689"
---
# <a name="icorprofilerinfo12eventpipeaddprovidertosession-method"></a>ICorProfilerInfo12::EventPipeAddProviderToSession メソッド

既存の EventPipe セッションにプロバイダーを追加します。
  
## <a name="syntax"></a>構文  
  
```cpp  
    HRESULT EventPipeAddProviderToSession(
        [in] EVENTPIPE_SESSION                 session,
        [in] COR_PRF_EVENTPIPE_PROVIDER_CONFIG providerConfig);
```  
  
## <a name="parameters"></a>パラメーター

`session` [入力] プロバイダーの追加先のセッションの ID。

`providerConfig` [入力] セッションに追加するプロバイダーを記述した `COR_PRF_EVENTPIPE_PROVIDER_CONFIG`。

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。
**ヘッダー:** CorProf.idl、CorProf.h **.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]
  
## <a name="see-also"></a>関連項目

- [EventPipe の概要](../../../core/diagnostics/eventpipe.md)
- [既知のイベント プロバイダー](../../../core/diagnostics/well-known-event-providers.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerCallback10 インターフェイス](icorprofilercallback10-interface.md)
- [ICorProfilerInfo12 インターフェイス](icorprofilerinfo12-interface.md)
- [COR_PRF_EVENTPIPE_PROVIDER_CONFIG 構造体](cor-prf-eventpipe-provider-config-structure.md)
