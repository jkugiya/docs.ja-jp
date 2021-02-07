---
description: '詳細について: ICorProfilerInfo2:: GetGenerationBounds メソッド'
title: ICorProfilerInfo2::GetGenerationBounds メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
ms.openlocfilehash: 2f6fb9037be2722166653cceb4081a5ddcb81327
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753225"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="51dde-103">ICorProfilerInfo2::GetGenerationBounds メソッド</span><span class="sxs-lookup"><span data-stu-id="51dde-103">ICorProfilerInfo2::GetGenerationBounds Method</span></span>

<span data-ttu-id="51dde-104">各種ガベージ コレクション ジェネレーションを構成するメモリ領域 (ヒープのセグメント) を取得します。</span><span class="sxs-lookup"><span data-stu-id="51dde-104">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51dde-105">構文</span><span class="sxs-lookup"><span data-stu-id="51dde-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51dde-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="51dde-106">Parameters</span></span>  

 `cObjectRanges`  
 <span data-ttu-id="51dde-107">[in] `ranges` 配列の呼び出し元によって割り当てられた要素の数。</span><span class="sxs-lookup"><span data-stu-id="51dde-107">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="51dde-108">[out] その一部または全部が `ranges` 配列で返される範囲の総数を指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="51dde-108">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="51dde-109">入出力 [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) 構造体の配列。それぞれがガベージコレクションを行っているジェネレーション内のメモリの範囲 (つまり、ブロック) を記述します。</span><span class="sxs-lookup"><span data-stu-id="51dde-109">[out] An array of [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51dde-110">解説</span><span class="sxs-lookup"><span data-stu-id="51dde-110">Remarks</span></span>  

 <span data-ttu-id="51dde-111">ガベージ コレクションを処理中でない場合、`GetGenerationBounds` メソッドは任意のプロファイラー コールバックから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="51dde-111">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span>

 <span data-ttu-id="51dde-112">通常、ジェネレーションの移動はガベージ コレクション中に行われます。</span><span class="sxs-lookup"><span data-stu-id="51dde-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="51dde-113">コレクションの間にジェネレーションが増大する可能性はありますが、一般的に移動はありません。</span><span class="sxs-lookup"><span data-stu-id="51dde-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="51dde-114">したがって、`GetGenerationBounds` を呼び出す上で最も注目すべき地点は `ICorProfilerCallback2::GarbageCollectionStarted` と `ICorProfilerCallback2::GarbageCollectionFinished` の間です。</span><span class="sxs-lookup"><span data-stu-id="51dde-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="51dde-115">プログラムの起動中に、いくつかのオブジェクトが共通言語ランタイム (CLR) 自体によって割り当てられます。これは、一般的にはジェネレーションの 3 と 0 で行われます。</span><span class="sxs-lookup"><span data-stu-id="51dde-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="51dde-116">したがって、マネージド コードが実行を開始するまでに、これらのジェネレーションには既にオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="51dde-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="51dde-117">通常、ジェネレーションの 1 と 2 は、ガベージ コレクターによって生成されたダミー オブジェクトを除き、空です。</span><span class="sxs-lookup"><span data-stu-id="51dde-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="51dde-118">(ダミーオブジェクトのサイズは、CLR の32ビット実装では12バイトです。64ビットの実装では、サイズは大きくなります)。また、ネイティブイメージジェネレーター (NGen.exe) によって生成されたモジュール内にあるジェネレーション2の範囲が表示される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="51dde-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="51dde-119">この場合、ジェネレーション2のオブジェクトは固定された *オブジェクト* であり、ガベージコレクターではなく NGen.exe 実行されるときに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="51dde-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="51dde-120">この関数は、呼び出し元が割り当てたバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="51dde-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51dde-121">要件</span><span class="sxs-lookup"><span data-stu-id="51dde-121">Requirements</span></span>  

 <span data-ttu-id="51dde-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51dde-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51dde-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51dde-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51dde-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51dde-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51dde-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51dde-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51dde-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="51dde-126">See also</span></span>

- [<span data-ttu-id="51dde-127">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51dde-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="51dde-128">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51dde-128">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="51dde-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="51dde-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="51dde-130">プロファイル</span><span class="sxs-lookup"><span data-stu-id="51dde-130">Profiling</span></span>](index.md)
