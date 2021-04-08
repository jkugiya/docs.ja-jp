---
description: '詳細情報: ICorProfilerInfo10 インターフェイス'
title: ICorProfilerInfo10 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2fa0115f6894ac737696b63c1f0f00a0cb028ec
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106905"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 インターフェイス

関数 IL の変更、ランタイムからの情報のクエリ、およびランタイムの一時停止と再開のためのメソッドを提供する [ICorProfilerInfo9](icorprofilerinfo9-interface.md) のサブクラス。

## <a name="methods"></a>メソッド  

| メソッド|説明|  
| ------------|-----------------|  
|[EnumerateObjectReferences メソッド](icorprofilerinfo10-enumerateobjectreferences-method.md)|ObjectID、callback、clientData が指定されると、各オブジェクト参照 (存在する場合) を列挙します。 |
|[IsFrozenObject メソッド](icorprofilerinfo10-isfrozenobject-method.md)|ObjectID が指定されると、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。 |
|[GetLOHObjectSizeThreshold メソッド](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|構成されている LOH しきい値の値を取得します。 |
|[RequestReJITWithInliners メソッド](icorprofilerinfo10-requestrejitwithinliners-method.md)| 要求されたメソッドに加えて、要求されたメソッドのすべてのインライナも ReJIT します。  |
|[SuspendRuntime メソッド](icorprofilerinfo10-suspendruntime-method.md)| GC を実行せずにランタイムを一時停止します。 |
|[ResumeRuntime メソッド](icorprofilerinfo10-resumeruntime-method.md)| GC を実行せずにランタイムを再開します。 |

## <a name="requirements"></a>必要条件  

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。  
**ヘッダー** : CorProf.idl、CorProf.h  
**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](profiling-interfaces.md)
