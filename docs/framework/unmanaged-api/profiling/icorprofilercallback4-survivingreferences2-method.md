---
description: '詳細について: ICorProfilerCallback4:: SurvivingReferences2 メソッド'
title: ICorProfilerCallback4::SurvivingReferences2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
ms.openlocfilehash: d092729c77b0c4feb253bb2f54968f7ff8bdbb2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788684"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a><span data-ttu-id="1599c-103">ICorProfilerCallback4::SurvivingReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="1599c-103">ICorProfilerCallback4::SurvivingReferences2 Method</span></span>

<span data-ttu-id="1599c-104">非圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトのレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="1599c-104">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span> <span data-ttu-id="1599c-105">このメソッドは、プロファイラーが [ICorProfilerCallback4](icorprofilercallback4-interface.md) インターフェイスを実装した場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1599c-105">This method is called if the profiler has implemented the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="1599c-106">このコールバックでは、 [ICorProfilerCallback2:: SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) メソッドが置き換えられます。これは、長さが ULONG で表現できる値を超えるオブジェクトの範囲を超える可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="1599c-106">This callback replaces the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1599c-107">構文</span><span class="sxs-lookup"><span data-stu-id="1599c-107">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="1599c-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1599c-108">Parameters</span></span>  

 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="1599c-109">[in] 非圧縮ガベージ コレクションを実行した後に存続する、隣接したオブジェクトのブロック数。</span><span class="sxs-lookup"><span data-stu-id="1599c-109">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="1599c-110">つまり、`cSurvivingObjectIDRanges` の値は、`objectIDRangeStart` 配列と `cObjectIDRangeLength` 配列のサイズを表します。これらの配列にはそれぞれ、オブジェクトの各ブロックの `ObjectID` と長さが格納されます。</span><span class="sxs-lookup"><span data-stu-id="1599c-110">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="1599c-111">`SurvivingReferences2` の次の2個の引数は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="1599c-111">The next two arguments of `SurvivingReferences2` are parallel arrays.</span></span> <span data-ttu-id="1599c-112">つまり、`objectIDRangeStart` と `cObjectIDRangeLength` は隣接するオブジェクトの同じブロックを対象としています。</span><span class="sxs-lookup"><span data-stu-id="1599c-112">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="1599c-113">[in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの開始アドレスを表す、`ObjectID` 値の配列。</span><span class="sxs-lookup"><span data-stu-id="1599c-113">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="1599c-114">[in] それぞれがメモリ内に存続する隣接オブジェクト ブロックのサイズを表す、整数の配列。</span><span class="sxs-lookup"><span data-stu-id="1599c-114">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="1599c-115">サイズは、`objectIDRangeStart` 配列内の参照される各ブロックに対して指定します。</span><span class="sxs-lookup"><span data-stu-id="1599c-115">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1599c-116">解説</span><span class="sxs-lookup"><span data-stu-id="1599c-116">Remarks</span></span>  

 <span data-ttu-id="1599c-117">`objectIDRangeStart` 配列と `cObjectIDRangeLength` 配列の要素は、次のように解釈されて、ガベージ コレクションでオブジェクトが存続したかどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1599c-117">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="1599c-118">`ObjectID` 値 (`ObjectID`) が次の範囲内にあるとします。</span><span class="sxs-lookup"><span data-stu-id="1599c-118">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="1599c-119">次の範囲内にある `i` のすべての値について、オブジェクトはガベージ コレクションの実行後に存続しています。</span><span class="sxs-lookup"><span data-stu-id="1599c-119">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="1599c-120">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="1599c-120">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="1599c-121">非圧縮ガベージ コレクションは、"無効な" オブジェクトによって占有されているメモリをクリアしますが、解放された領域は圧縮しません。</span><span class="sxs-lookup"><span data-stu-id="1599c-121">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="1599c-122">そのため、メモリはヒープに返されますが、"有効な" オブジェクトは移動されません。</span><span class="sxs-lookup"><span data-stu-id="1599c-122">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="1599c-123">共通言語ランタイム (CLR: Common Language Runtime) は、非圧縮ガベージ コレクションに対して `SurvivingReferences2` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1599c-123">The common language runtime (CLR) calls `SurvivingReferences2` for non-compacting garbage collections.</span></span> <span data-ttu-id="1599c-124">ガベージコレクションを圧縮する場合は、代わりに [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="1599c-124">For compacting garbage collections, [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) is called instead.</span></span> <span data-ttu-id="1599c-125">単一のガベージ コレクションで 1 つのジェネレーションを圧縮できますが、その他のジェネレーションは非圧縮になります。</span><span class="sxs-lookup"><span data-stu-id="1599c-125">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="1599c-126">特定のジェネレーションのガベージコレクションの場合、プロファイラーは `SurvivingReferences2` コールバックまたは [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) コールバックのいずれかを受け取りますが、両方を受け取ることはありません。</span><span class="sxs-lookup"><span data-stu-id="1599c-126">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences2` callback or a [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) callback, but not both.</span></span>  
  
 <span data-ttu-id="1599c-127">特定のガベージ コレクションで複数の `SurvivingReferences2` コールバックを受け取ることがあります。この原因としては、内部バッファリングの制限、サーバーのガベージ コレクション中の複数のコールバックなどが考えられます。</span><span class="sxs-lookup"><span data-stu-id="1599c-127">Multiple `SurvivingReferences2` callbacks might be received during a particular garbage collection, because of limited internal buffering, multiple callbacks during server garbage collection, and other reasons.</span></span> <span data-ttu-id="1599c-128">あるガベージ コレクションで複数のコールバックが生じる場合、情報が累積されます。つまり、`SurvivingReferences2` コールバックで報告されるすべての参照は対象のガベージ コレクション後も存続します。</span><span class="sxs-lookup"><span data-stu-id="1599c-128">In the case of multiple callbacks during a garbage collection, the information is cumulative; all references that are reported in any `SurvivingReferences2` callback survive the garbage collection.</span></span>  
  
 <span data-ttu-id="1599c-129">プロファイラーが [ICorProfilerCallback](icorprofilercallback-interface.md) インターフェイスと [ICorProfilerCallback4](icorprofilercallback4-interface.md) インターフェイスの両方を実装している場合、 `SurvivingReferences2` メソッドは [ICorProfilerCallback2:: SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) メソッドの前に呼び出されますが、が正常に返された場合にのみ呼び出され `SurvivingReferences2` ます。</span><span class="sxs-lookup"><span data-stu-id="1599c-129">If the profiler implements both the [ICorProfilerCallback](icorprofilercallback-interface.md) and the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interfaces, the `SurvivingReferences2` method is called before the [ICorProfilerCallback2::SurvivingReferences](icorprofilercallback2-survivingreferences-method.md) method, but only if `SurvivingReferences2` returns successfully.</span></span> <span data-ttu-id="1599c-130">プロファイラーは HRESULT を返すことがあり、これは `SurvivingReferences2` メソッドの失敗を示し、2 番目のメソッドが呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="1599c-130">Profilers can return an HRESULT that indicates failure from the `SurvivingReferences2` method to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1599c-131">要件</span><span class="sxs-lookup"><span data-stu-id="1599c-131">Requirements</span></span>  

 <span data-ttu-id="1599c-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1599c-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1599c-133">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1599c-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1599c-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1599c-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1599c-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1599c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1599c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="1599c-136">See also</span></span>

- [<span data-ttu-id="1599c-137">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1599c-137">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1599c-138">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1599c-138">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="1599c-139">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1599c-139">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
