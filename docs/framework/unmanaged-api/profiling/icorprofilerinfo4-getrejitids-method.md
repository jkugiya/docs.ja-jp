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
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="58e9e-103">ICorProfilerInfo4::GetReJITIDs メソッド</span><span class="sxs-lookup"><span data-stu-id="58e9e-103">ICorProfilerInfo4::GetReJITIDs Method</span></span>

<span data-ttu-id="58e9e-104">指定された関数のすべての JIT 再コンパイル バージョンのうち、まだ割り当てられているものを識別する ID の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="58e9e-104">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="58e9e-105">これには、後で元に戻されたものの、まだ解放されていない関数の JIT 再コンパイル バージョンが含まれます (たとえば、元に戻された関数を含んでいるアプリケーション ドメインがまだ使用されている場合など)。</span><span class="sxs-lookup"><span data-stu-id="58e9e-105">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e9e-106">構文</span><span class="sxs-lookup"><span data-stu-id="58e9e-106">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58e9e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58e9e-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="58e9e-108">[in] バージョンを列挙する関数インスタンスの `FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="58e9e-108">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="58e9e-109">[in] `reJitIds` 配列に割り当てられた JIT 再コンパイル済み ID の数。</span><span class="sxs-lookup"><span data-stu-id="58e9e-109">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="58e9e-110">[out] JIT 再コンパイル済み ID の実際の数。</span><span class="sxs-lookup"><span data-stu-id="58e9e-110">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="58e9e-111">[out] 指定した関数の JIT 再コンパイル済み ID を格納する、呼び出し元割り当て済み配列。</span><span class="sxs-lookup"><span data-stu-id="58e9e-111">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58e9e-112">解説</span><span class="sxs-lookup"><span data-stu-id="58e9e-112">Remarks</span></span>  

 <span data-ttu-id="58e9e-113">`GetReJITIDs` では、指定された関数インスタンスのアクティブな JIT 再コンパイル済み ID が列挙されます。</span><span class="sxs-lookup"><span data-stu-id="58e9e-113">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="58e9e-114">これは、呼び出し元割り当て済みバッファーを受け入れる他の `ICorProfilerInfo` 関数と同じ使用パターンに従います。</span><span class="sxs-lookup"><span data-stu-id="58e9e-114">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58e9e-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="58e9e-115">Requirements</span></span>  

 <span data-ttu-id="58e9e-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58e9e-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58e9e-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58e9e-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58e9e-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58e9e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58e9e-119">**.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58e9e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e9e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="58e9e-120">See also</span></span>

- [<span data-ttu-id="58e9e-121">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58e9e-121">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="58e9e-122">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="58e9e-122">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="58e9e-123">プロファイル</span><span class="sxs-lookup"><span data-stu-id="58e9e-123">Profiling</span></span>](index.md)
