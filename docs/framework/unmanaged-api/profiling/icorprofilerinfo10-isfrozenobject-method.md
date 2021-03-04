---
description: '詳細について: ICorProfilerInfo10:: IsFrozenObject メソッド'
title: ICorProfilerInfo10::IsFrozenObject
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3b47204630056e2797b5cf126bd7c291830cea05
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103453"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>ICorProfilerInfo10:: IsFrozenObject メソッド

ObjectID が指定された場合、オブジェクトが読み取り専用セグメント内にあるかどうかを判断します。

## <a name="syntax"></a>構文

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

## <a name="parameters"></a>パラメーター

- `objectId`

  \[in) 調べるオブジェクト。

- `pbFrozen`

  \[out] `BOOL` オブジェクトが読み取り専用セグメント内にあるかどうかを示すです。

## <a name="requirements"></a>必要条件

**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.Net のバージョン:**[!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](icorprofilerinfo10-interface.md)
