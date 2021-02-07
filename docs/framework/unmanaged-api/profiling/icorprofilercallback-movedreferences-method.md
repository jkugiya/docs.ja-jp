---
description: '詳細について: ICorProfilerCallback:: MovedReferences メソッド'
title: ICorProfilerCallback::MovedReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
ms.openlocfilehash: da77ace52e19540e30488d3304d2822500c90391
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745191"
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="562d4-103">ICorProfilerCallback::MovedReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="562d4-103">ICorProfilerCallback::MovedReferences Method</span></span>

<span data-ttu-id="562d4-104">圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトの新しいレイアウトを報告するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="562d4-104">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="562d4-105">構文</span><span class="sxs-lookup"><span data-stu-id="562d4-105">Syntax</span></span>  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="562d4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="562d4-106">Parameters</span></span>  

 `cMovedObjectIDRanges`  
 <span data-ttu-id="562d4-107">[in] 圧縮ガベージ コレクションを実行した後に移動される、隣接したオブジェクトのブロック数。</span><span class="sxs-lookup"><span data-stu-id="562d4-107">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="562d4-108">つまり、`cMovedObjectIDRanges` の値は `oldObjectIDRangeStart`、`newObjectIDRangeStart`、および `cObjectIDRangeLength` 配列の合計サイズです。</span><span class="sxs-lookup"><span data-stu-id="562d4-108">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="562d4-109">`MovedReferences` の次の 3 つの引数は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="562d4-109">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="562d4-110">つまり、`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]`、`cObjectIDRangeLength[i]` はすべて、隣接するオブジェクトの同じブロックを対象としています。</span><span class="sxs-lookup"><span data-stu-id="562d4-110">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="562d4-111">[in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの古い (ガベージ コレクション実行前の) 開始アドレスを表す、`ObjectID` 値の配列。</span><span class="sxs-lookup"><span data-stu-id="562d4-111">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="562d4-112">[in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの新しい (ガベージ コレクション実行後の) 開始アドレスを表す、`ObjectID` 値の配列。</span><span class="sxs-lookup"><span data-stu-id="562d4-112">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="562d4-113">[in] それぞれがメモリ内の隣接オブジェクト ブロックのサイズを表す、整数の配列。</span><span class="sxs-lookup"><span data-stu-id="562d4-113">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="562d4-114">サイズは、`oldObjectIDRangeStart` および `newObjectIDRangeStart` 配列内の参照される各ブロックに対して指定します。</span><span class="sxs-lookup"><span data-stu-id="562d4-114">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="562d4-115">解説</span><span class="sxs-lookup"><span data-stu-id="562d4-115">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="562d4-116">このメソッドは、64 ビット プラットフォームで 4 GB より大きいオブジェクトのサイズを `MAX_ULONG` として報告します。</span><span class="sxs-lookup"><span data-stu-id="562d4-116">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="562d4-117">4 GB より大きいオブジェクトのサイズを取得するには、代わりに [ICorProfilerCallback4:: MovedReferences2](icorprofilercallback4-movedreferences2-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="562d4-117">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="562d4-118">圧縮ガベージ コレクターは、無効なオブジェクトによって占有されているメモリを解放し、解放された領域を圧縮します。</span><span class="sxs-lookup"><span data-stu-id="562d4-118">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="562d4-119">その結果、ヒープ内で有効なオブジェクトが移動され、以前の通知で配布された `ObjectID` の値が変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="562d4-119">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="562d4-120">既存の `ObjectID` の値 (`oldObjectID`) が次の範囲内にあるとします。</span><span class="sxs-lookup"><span data-stu-id="562d4-120">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="562d4-121">この場合、範囲の開始からオブジェクトの開始までのオフセットは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="562d4-121">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="562d4-122">`i` の値が次の範囲内にあるとします。</span><span class="sxs-lookup"><span data-stu-id="562d4-122">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="562d4-123">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="562d4-123">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="562d4-124">この場合、新しい `ObjectID` は次のように計算できます。</span><span class="sxs-lookup"><span data-stu-id="562d4-124">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="562d4-125">`newObjectID` = `newObjectIDRangeStart[i]` + ( `oldObjectID` – `oldObjectIDRangeStart[i]` )</span><span class="sxs-lookup"><span data-stu-id="562d4-125">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="562d4-126">ガーベッジ コレクションでオブジェクトが古い場所から新しい場所へ移動中の可能性があるため、コールバックの間は `MovedReferences` によって渡される `ObjectID` 値はすべて無効です。</span><span class="sxs-lookup"><span data-stu-id="562d4-126">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="562d4-127">このため、`MovedReferences` 呼び出しの間、プロファイラーはオブジェクトを検査するべきではありません。</span><span class="sxs-lookup"><span data-stu-id="562d4-127">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="562d4-128">[ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)コールバックは、すべてのオブジェクトが新しい場所に移動され、検査を実行できることを示します。</span><span class="sxs-lookup"><span data-stu-id="562d4-128">A [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="562d4-129">要件</span><span class="sxs-lookup"><span data-stu-id="562d4-129">Requirements</span></span>  

 <span data-ttu-id="562d4-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="562d4-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="562d4-131">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="562d4-131">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="562d4-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="562d4-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="562d4-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="562d4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="562d4-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="562d4-134">See also</span></span>

- [<span data-ttu-id="562d4-135">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="562d4-135">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="562d4-136">MovedReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="562d4-136">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)
- [<span data-ttu-id="562d4-137">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="562d4-137">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="562d4-138">プロファイル</span><span class="sxs-lookup"><span data-stu-id="562d4-138">Profiling</span></span>](index.md)
