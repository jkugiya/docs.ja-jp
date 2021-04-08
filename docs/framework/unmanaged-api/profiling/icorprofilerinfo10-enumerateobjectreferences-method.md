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
ms.openlocfilehash: c18532450e420f38413028a18630dbf3e308fa61
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106723"
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

- `objectId`

  \[入力] 参照を列挙する対象のオブジェクト。

- `callback`

  \[入力] オブジェクトの参照によって呼び出される関数。

- `clientData`

  \[入力] `callback` 関数に渡す、プロファイラーによって提供されたデータ。

## <a name="remarks"></a>解説

`EnumerateObjectReferences` メソッドは [ObjectReferences](icorprofilercallback-objectreferences-method.md) に似ていますが、参照を格納するための配列を事前に割り当てるのではなく、プロファイラーからの要求に応じて参照を走査する点が異なります。

## <a name="requirements"></a>必要条件

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](icorprofilerinfo10-interface.md)
