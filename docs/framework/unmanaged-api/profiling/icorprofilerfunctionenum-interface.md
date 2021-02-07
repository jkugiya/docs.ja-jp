---
description: 詳細については、「ICorProfilerFunctionEnum インターフェイス」を参照してください。
title: ICorProfilerFunctionEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: 0a9437ee1f5c481c2c2d1fd46361da6e938dd179
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737598"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="97cf3-103">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97cf3-103">ICorProfilerFunctionEnum Interface</span></span>

<span data-ttu-id="97cf3-104">共通言語ランタイムの関数のコレクションを順番に反復処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="97cf3-104">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97cf3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="97cf3-105">Methods</span></span>  
  
|<span data-ttu-id="97cf3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="97cf3-106">Method</span></span>|<span data-ttu-id="97cf3-107">説明</span><span class="sxs-lookup"><span data-stu-id="97cf3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97cf3-108">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="97cf3-108">Clone Method</span></span>](icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="97cf3-109">この `ICorProfilerFunctionEnum` インターフェイスのコピーへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="97cf3-109">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="97cf3-110">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="97cf3-110">GetCount Method</span></span>](icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="97cf3-111">アプリケーションによって読み込まれたか、またはプロファイラーによって強制的に読み込まれた関数の数を取得します。</span><span class="sxs-lookup"><span data-stu-id="97cf3-111">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="97cf3-112">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="97cf3-112">Next Method</span></span>](icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="97cf3-113">関数のシーケンシャル コレクションから、列挙子の現在の位置以降にある、指定した数の隣接する関数を取得します。</span><span class="sxs-lookup"><span data-stu-id="97cf3-113">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="97cf3-114">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="97cf3-114">Reset Method</span></span>](icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="97cf3-115">列挙子のカーソルをシーケンスの開始位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="97cf3-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="97cf3-116">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="97cf3-116">Skip Method</span></span>](icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="97cf3-117">指定した数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="97cf3-117">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97cf3-118">解説</span><span class="sxs-lookup"><span data-stu-id="97cf3-118">Remarks</span></span>  

 <span data-ttu-id="97cf3-119">`ICorProfilerFunctionEnum` インターフェイスは列挙子です。</span><span class="sxs-lookup"><span data-stu-id="97cf3-119">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="97cf3-120">このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。</span><span class="sxs-lookup"><span data-stu-id="97cf3-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="97cf3-121">つまり、受信側は配列要素のフローを明示的に制御できるため、大きな配列をメソッド パラメーターとして渡す場合に関連する問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="97cf3-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="97cf3-122">`ICorProfilerFunctionEnum` は、既に JIT コンパイルされた関数を列挙しますが、この中に Ngen.exe で生成されたネイティブ イメージから読み込まれた関数は含まれません。</span><span class="sxs-lookup"><span data-stu-id="97cf3-122">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97cf3-123">要件</span><span class="sxs-lookup"><span data-stu-id="97cf3-123">Requirements</span></span>  

 <span data-ttu-id="97cf3-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97cf3-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97cf3-125">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97cf3-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97cf3-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97cf3-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97cf3-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97cf3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97cf3-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="97cf3-128">See also</span></span>

- [<span data-ttu-id="97cf3-129">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97cf3-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="97cf3-130">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="97cf3-130">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="97cf3-131">EnumJITedFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="97cf3-131">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
