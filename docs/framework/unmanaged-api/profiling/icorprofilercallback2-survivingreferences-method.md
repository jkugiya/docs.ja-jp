---
description: '詳細について: ICorProfilerCallback2:: SurvivingReferences メソッド'
title: ICorProfilerCallback2::SurvivingReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
ms.openlocfilehash: 64edaf5388aeb0bded3de8e8bbde0bf7a5159ed4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799058"
---
# <a name="icorprofilercallback2survivingreferences-method"></a><span data-ttu-id="3195f-103">ICorProfilerCallback2::SurvivingReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="3195f-103">ICorProfilerCallback2::SurvivingReferences Method</span></span>

<span data-ttu-id="3195f-104">非圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトのレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="3195f-104">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3195f-105">構文</span><span class="sxs-lookup"><span data-stu-id="3195f-105">Syntax</span></span>  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3195f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3195f-106">Parameters</span></span>  

 `cSurvivingObjectIDRanges`  
 <span data-ttu-id="3195f-107">[in] 非圧縮ガベージ コレクションを実行した後に存続する、隣接したオブジェクトのブロック数。</span><span class="sxs-lookup"><span data-stu-id="3195f-107">[in] The number of blocks of contiguous objects that survived as the result of the non-compacting garbage collection.</span></span> <span data-ttu-id="3195f-108">つまり、`cSurvivingObjectIDRanges` の値は、`objectIDRangeStart` 配列と `cObjectIDRangeLength` 配列のサイズを表します。これらの配列にはそれぞれ、オブジェクトの各ブロックの `ObjectID` と長さが格納されます。</span><span class="sxs-lookup"><span data-stu-id="3195f-108">That is, the value of `cSurvivingObjectIDRanges` is the size of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays, which store an `ObjectID` and a length, respectively, for each block of objects.</span></span>  
  
 <span data-ttu-id="3195f-109">`SurvivingReferences` の次の2個の引数は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="3195f-109">The next two arguments of `SurvivingReferences` are parallel arrays.</span></span> <span data-ttu-id="3195f-110">つまり、`objectIDRangeStart` と `cObjectIDRangeLength` は隣接するオブジェクトの同じブロックを対象としています。</span><span class="sxs-lookup"><span data-stu-id="3195f-110">In other words, `objectIDRangeStart` and `cObjectIDRangeLength` concern the same block of contiguous objects.</span></span>  
  
 `objectIDRangeStart`  
 <span data-ttu-id="3195f-111">[in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの開始アドレスを表す、`ObjectID` 値の配列。</span><span class="sxs-lookup"><span data-stu-id="3195f-111">[in] An array of `ObjectID` values, each of which is the starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="3195f-112">[in] それぞれがメモリ内に存続する隣接オブジェクト ブロックのサイズを表す、整数の配列。</span><span class="sxs-lookup"><span data-stu-id="3195f-112">[in] An array of integers, each of which is the size of a surviving block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="3195f-113">サイズは、`objectIDRangeStart` 配列内の参照される各ブロックに対して指定します。</span><span class="sxs-lookup"><span data-stu-id="3195f-113">A size is specified for each block that is referenced in the `objectIDRangeStart` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3195f-114">解説</span><span class="sxs-lookup"><span data-stu-id="3195f-114">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3195f-115">このメソッドは、64 ビット プラットフォームで 4 GB より大きいオブジェクトのサイズを `MAX_ULONG` として報告します。</span><span class="sxs-lookup"><span data-stu-id="3195f-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="3195f-116">4 GB を超えるオブジェクトの場合は、代わりに [ICorProfilerCallback4:: SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="3195f-116">For objects that are larger than 4 GB, use the [ICorProfilerCallback4::SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="3195f-117">`objectIDRangeStart` 配列と `cObjectIDRangeLength` 配列の要素は、次のように解釈されて、ガベージ コレクションでオブジェクトが存続したかどうかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3195f-117">The elements of the `objectIDRangeStart` and `cObjectIDRangeLength` arrays should be interpreted as follows to determine whether an object survived the garbage collection.</span></span> <span data-ttu-id="3195f-118">`ObjectID` 値 (`ObjectID`) が次の範囲内にあるとします。</span><span class="sxs-lookup"><span data-stu-id="3195f-118">Assume that an `ObjectID` value (`ObjectID`) lies within the following range:</span></span>  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="3195f-119">次の範囲内にある `i` のすべての値について、オブジェクトはガベージ コレクションの実行後に存続しています。</span><span class="sxs-lookup"><span data-stu-id="3195f-119">For any value of `i` that is in the following range, the object has survived the garbage collection:</span></span>  
  
 <span data-ttu-id="3195f-120">0 <= `i` < `cSurvivingObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="3195f-120">0 <= `i` < `cSurvivingObjectIDRanges`</span></span>  
  
 <span data-ttu-id="3195f-121">非圧縮ガベージ コレクションは、"無効な" オブジェクトによって占有されているメモリをクリアしますが、解放された領域は圧縮しません。</span><span class="sxs-lookup"><span data-stu-id="3195f-121">A non-compacting garbage collection reclaims the memory occupied by "dead" objects, but does not compact that freed space.</span></span> <span data-ttu-id="3195f-122">そのため、メモリはヒープに返されますが、"有効な" オブジェクトは移動されません。</span><span class="sxs-lookup"><span data-stu-id="3195f-122">As a result, memory is returned to the heap, but no "live" objects are moved.</span></span>  
  
 <span data-ttu-id="3195f-123">共通言語ランタイム (CLR: Common Language Runtime) は、非圧縮ガベージ コレクションに対して `SurvivingReferences` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3195f-123">The common language runtime (CLR) calls `SurvivingReferences` for non-compacting garbage collections.</span></span> <span data-ttu-id="3195f-124">ガベージコレクションを圧縮する場合は、代わりに [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3195f-124">For compacting garbage collections, [ICorProfilerCallback::MovedReferences](icorprofilercallback-movedreferences-method.md) is called instead.</span></span> <span data-ttu-id="3195f-125">単一のガベージ コレクションで 1 つのジェネレーションを圧縮できますが、その他のジェネレーションは非圧縮になります。</span><span class="sxs-lookup"><span data-stu-id="3195f-125">A single garbage collection can be compacting for one generation and non-compacting for another.</span></span> <span data-ttu-id="3195f-126">どの特定のジェネレーションのガベージ コレクションについても、プロファイラーは `SurvivingReferences` コールバックと `MovedReferences` コールバックのいずれかを受け取り、両方を受け取ることはありません。</span><span class="sxs-lookup"><span data-stu-id="3195f-126">For a garbage collection on any particular generation, the profiler will receive either a `SurvivingReferences` callback or a `MovedReferences` callback, but not both.</span></span>  
  
 <span data-ttu-id="3195f-127">特定のガベージ コレクションで複数の `SurvivingReferences` コールバックを受け取ることがあります。この原因としては、内部バッファリングの制限、サーバーのガベージ コレクション中の複数のコールバックなどが考えられます。</span><span class="sxs-lookup"><span data-stu-id="3195f-127">Multiple `SurvivingReferences` callbacks might be received during a particular garbage collection, due to limited internal buffering, multiple threads reporting in the case of server garbage collection, and other reasons.</span></span> <span data-ttu-id="3195f-128">あるガベージ コレクションで複数のコールバックが生じる場合、情報が累積されます。つまり、`SurvivingReferences` コールバックで報告されるすべての参照は対象のガベージ コレクション後も存続します。</span><span class="sxs-lookup"><span data-stu-id="3195f-128">In the case of multiple callbacks during a garbage collection, the information is cumulative — all references that are reported in any `SurvivingReferences` callback survive the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3195f-129">要件</span><span class="sxs-lookup"><span data-stu-id="3195f-129">Requirements</span></span>  

 <span data-ttu-id="3195f-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3195f-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3195f-131">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3195f-131">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3195f-132">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3195f-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3195f-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3195f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3195f-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="3195f-134">See also</span></span>

- [<span data-ttu-id="3195f-135">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3195f-135">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3195f-136">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3195f-136">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="3195f-137">SurvivingReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="3195f-137">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)
