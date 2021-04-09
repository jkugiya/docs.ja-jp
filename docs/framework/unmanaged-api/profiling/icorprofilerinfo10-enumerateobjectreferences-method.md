---
description: '詳細情報: ICorProfilerInfo10::EnumerateObjectReferences メソッド'
title: ICorProfilerInfo10::EnumerateObjectReferences
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: bcd374aec2944977a0745177995ba8adf0cce9b7
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104759418"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10::EnumerateObjectReferences メソッド

ObjectID、callback、clientData が指定されると、各オブジェクト参照 (存在する場合) を列挙します。

## <a name="syntax"></a>構文

```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```

## <a name="parameters"></a>パラメーター

`objectId` [入力] 参照を列挙する対象のオブジェクト。

`callback` [入力] オブジェクトの参照によって呼び出される関数。

`clientData` [入力] `callback` 関数に渡す、プロファイラーによって提供されたデータ。

## <a name="remarks"></a>解説

`EnumerateObjectReferences` メソッドは [ObjectReferences](icorprofilercallback-objectreferences-method.md) に似ていますが、参照を格納するための配列を事前に割り当てるのではなく、プロファイラーからの要求に応じて参照を走査する点が異なります。

## <a name="requirements"></a>要件

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](icorprofilerinfo10-interface.md)
