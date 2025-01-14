---
description: '詳細情報: ICorProfilerInfo10::RequestReJITWithInliners メソッド'
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3d85537030e042d53bb4ff859eb1d2c3a24a45a5
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760783"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10::RequestReJITWithInliners メソッド

要求されたメソッドに加えて、要求されたメソッドのすべてのインライナも ReJIT します。

## <a name="syntax"></a>構文

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a>パラメーター

`dwRejitFlags` [入力] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md) のビットマスク。

`cFunctions` [入力] 再コンパイルする関数の数。

`moduleIds` [入力] 再コンパイルする関数を識別する (`module`、`methodDef`) ペアの `moduleId` の部分を指定します。

`methodIds`[入力] 再コンパイルする関数を識別する (`module`、`methodDef`) ペアの `methodId` の部分を指定します。

## <a name="remarks"></a>解説

[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) では、インライン化されたメソッドの追跡は行われません。 プロファイラーは、インライン化をブロックするか、または、インライン化を追跡し、すべてのインライナに対して `RequestReJIT` を呼び出すことで、インライン化されたメソッドの各インスタンスが確実に ReJIT されるようにする必要がありました。 インライン化を監視するためのプロファイラーは存在しないため、これにより、アタッチ時に ReJIT に関する問題が発生します。 このメソッドを呼び出すと、インライナの完全なセットも ReJIT されることが保証されます。

## <a name="requirements"></a>要件

**プラットフォーム:** [.NET Core がサポートされているオペレーティング システム](../../../core/install/windows.md?pivots=os-windows)に関するページを参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET のバージョン:** [!INCLUDE[net_core_30](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](icorprofilerinfo10-interface.md)
