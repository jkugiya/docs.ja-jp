---
description: '詳細情報: ICorProfilerInfo9 インターフェイス'
title: ICorProfilerInfo9 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 44e3d694b426f87ee4e4bc12181f46322b0d246f
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805676"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9 インターフェイス

複数のネイティブ コード バージョンを持つ関数に関する情報を照会するためのメソッドを提供する、[ICorProfilerInfo8](icorprofilerinfo8-interface.md) のサブクラス。  

## <a name="methods"></a>メソッド  

| メソッド|説明|  
| ------------|-----------------|  
|[GetNativeCodeStartAddresses メソッド](icorprofilerinfo9-getnativecodestartaddresses-method.md)| functionId と rejitId を指定すると、現在存在するこのコードのすべての just-in-time バージョンのネイティブ コードの開始アドレスが列挙されます。 |
|[GetILToNativeMapping3 メソッド](icorprofilerinfo9-getiltonativemapping3-method.md)| ネイティブ コードの開始アドレスを指定すると、この just-in-time バージョンのコードのネイティブから IL へのマッピング情報が返されます。 |
|[GetCodeInfo4 メソッド](icorprofilerinfo9-getcodeinfo4-method.md)| ネイティブ コードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。 |

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.NET のバージョン:** [!INCLUDE[net_core](../../../../includes/net-core-21-md.md)]  

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
