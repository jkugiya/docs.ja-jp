---
description: '詳細情報: ICorProfilerInfo11::GetEnvironmentVariable メソッド'
title: ICorProfilerInfo11::GetEnvironmentVariable メソッド
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.GetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 635c5fb67b880c39f15fbc194a51a706d9ef7fe4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805832"
---
# <a name="icorprofilerinfo11getenvironmentvariable-method"></a>ICorProfilerInfo11::GetEnvironmentVariable メソッド

プロセスから環境変数を取得します。 Windows 以外のプラットフォームでは、スレッド セーフを確保するために、ランタイムに環境変数の内部キャッシュが保持されます。 つまり、`getenv` を呼び出しても、新しい環境変数や、起動後にプロセスで実行されているマネージド コードによって設定された更新された環境変数は読み取られません。
  
## <a name="syntax"></a>構文  
  
```cpp  
    HRESULT GetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in]         ULONG cchValue,
                [out]        ULONG *pcchValue,
                [out, annotation("_Out_writes_to_(cchValue, *pcchValue)")]
                             WCHAR szValue[]);
```  
  
## <a name="parameters"></a>パラメーター

`szName` [入力] 取得する環境変数の名前が含まれている null で終わるワイド文字列へのポインター。

`cchValue` [入力] `szValue` の長さ (文字数)。

`pcchValue` [出力] `szValue` の合計の文字の長さへのポインター。

`szValue` [出力] 呼び出し元によって提供されたワイド文字バッファー。 関数が戻るとき、このバッファーに環境変数の値が格納されます。

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [ICorProfilerInfo11 インターフェイス](icorprofilerinfo11-interface.md)
