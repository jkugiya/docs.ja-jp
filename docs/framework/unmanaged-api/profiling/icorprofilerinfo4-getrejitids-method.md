---
description: '詳細情報: ICorProfilerInfo4::GetReJITIDs メソッド'
title: ICorProfilerInfo4::GetReJITIDs メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: 60df4cb6023bbee68d2909e1cc0e9de5595ac0b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636404"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs メソッド

指定された関数のすべての JIT 再コンパイル バージョンのうち、まだ割り当てられているものを識別する ID の配列を返します。 これには、後で元に戻されたものの、まだ解放されていない関数の JIT 再コンパイル バージョンが含まれます (たとえば、元に戻された関数を含んでいるアプリケーション ドメインがまだ使用されている場合など)。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>パラメーター  

 `functionId`  
 [in] バージョンを列挙する関数インスタンスの `FunctionID`。  
  
 `cReJitIds`  
 [in] `reJitIds` 配列に割り当てられた JIT 再コンパイル済み ID の数。  
  
 `pcReJitIds`  
 [out] JIT 再コンパイル済み ID の実際の数。  
  
 `reJitIds`  
 [out] 指定した関数の JIT 再コンパイル済み ID を格納する、呼び出し元割り当て済み配列。  
  
## <a name="remarks"></a>解説  

 `GetReJITIDs` では、指定された関数インスタンスのアクティブな JIT 再コンパイル済み ID が列挙されます。 これは、呼び出し元割り当て済みバッファーを受け入れる他の `ICorProfilerInfo` 関数と同じ使用パターンに従います。  
  
## <a name="requirements"></a>必要条件  

 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo4 インターフェイス](icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](profiling-interfaces.md)
- [プロファイル](index.md)
