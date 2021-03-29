---
description: '詳細情報: ICorProfilerInfo11::SetEnvironmentVariable メソッド'
title: ICorProfilerInfo11::SetEnvironmentVariable メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.SetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 77dc3fc992dec037881573323822dc11481a56be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805606"
---
# <a name="icorprofilerinfo11setenvironmentvariable-method"></a>ICorProfilerInfo11::SetEnvironmentVariable メソッド

プロセスで環境変数を設定します。 Windows 以外のプラットフォームでは、スレッド セーフを確保するために、ランタイムに環境変数の内部キャッシュが保持されます。 つまり、プロファイラーで `setenv` を呼び出しても、新しい環境変数はプロセスで実行されているマネージド コードによって取得されません。
  
## <a name="syntax"></a>構文  
  
```cpp  
    HRESULT SetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in, string] const WCHAR *szValue);
```  
  
## <a name="parameters"></a>パラメーター

`szName` [入力] 設定する環境変数の名前が含まれている null で終わるワイド文字列へのポインター。

`szValue` [入力] 設定する環境変数の値が含まれている null で終わるワイド文字列へのポインター。

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerInfo11 インターフェイス](icorprofilerinfo11-interface.md)
