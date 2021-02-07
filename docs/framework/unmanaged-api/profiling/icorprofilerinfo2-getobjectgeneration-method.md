---
description: '詳細について: ICorProfilerInfo2:: GetObjectGeneration メソッド'
title: ICorProfilerInfo2::GetObjectGeneration メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: f4927c081393a11f7dad7d59cce311b82072659c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716420"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="4e801-103">ICorProfilerInfo2::GetObjectGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="4e801-103">ICorProfilerInfo2::GetObjectGeneration Method</span></span>

<span data-ttu-id="4e801-104">指定されたオブジェクトを格納しているヒープのセグメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="4e801-104">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e801-105">構文</span><span class="sxs-lookup"><span data-stu-id="4e801-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e801-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e801-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="4e801-107">からオブジェクトの ID です。</span><span class="sxs-lookup"><span data-stu-id="4e801-107">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="4e801-108">入出力ガベージコレクション中のジェネレーション内のメモリの範囲 (つまり、ブロック) を記述する [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="4e801-108">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="4e801-109">この範囲には、指定されたオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4e801-109">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e801-110">解説</span><span class="sxs-lookup"><span data-stu-id="4e801-110">Remarks</span></span>  

 <span data-ttu-id="4e801-111">`GetObjectGeneration`ガベージコレクションが実行されていない場合は、任意のプロファイラーコールバックからメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4e801-111">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="4e801-112">つまり、 [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) と [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)の間で発生するものを除き、任意のコールバックから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4e801-112">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e801-113">要件</span><span class="sxs-lookup"><span data-stu-id="4e801-113">Requirements</span></span>  

 <span data-ttu-id="4e801-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e801-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e801-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e801-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e801-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e801-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e801-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e801-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e801-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e801-118">See also</span></span>

- [<span data-ttu-id="4e801-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e801-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="4e801-120">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e801-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
