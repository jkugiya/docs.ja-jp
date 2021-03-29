---
description: '詳細情報: ICorProfilerInfo11 インターフェイス'
title: ICorProfilerInfo11 インターフェイス
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 083714b67d83291f1faada3f673df13f16ef3856
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805624"
---
# <a name="icorprofilerinfo11-interface"></a>ICorProfilerInfo11 インターフェイス

 プロセスで環境変数を取得および設定するためのメソッドを提供する、[ICorProfilerInfo10](icorprofilerinfo10-interface.md) のサブクラス。
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetEnvironmentVariable メソッド](icorprofilerinfo11-getenvironmentvariable-method.md)|環境変数を取得します。|
|[SetEnvironmentVariable メソッド](icorprofilerinfo11-setenvironmentvariable-method.md)|環境変数を設定します。|  
  
## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-50-md.md)]  

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
