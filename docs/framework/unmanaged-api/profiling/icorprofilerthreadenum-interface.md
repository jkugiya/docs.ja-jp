---
description: 詳細については、「ICorProfilerThreadEnum インターフェイス」を参照してください。
title: ICorProfilerThreadEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: 035296412aabf20503588a558c8e8ccc1338210e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636391"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="dd7a5-103">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd7a5-103">ICorProfilerThreadEnum Interface</span></span>

<span data-ttu-id="dd7a5-104">共通言語ランタイムのスレッドのコレクションを順番に反復処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-104">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd7a5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7a5-105">Methods</span></span>  
  
|<span data-ttu-id="dd7a5-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7a5-106">Method</span></span>|<span data-ttu-id="dd7a5-107">説明</span><span class="sxs-lookup"><span data-stu-id="dd7a5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd7a5-108">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7a5-108">Clone Method</span></span>](icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="dd7a5-109">この `ICorProfilerThreadEnum` インターフェイスのコピーへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-109">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="dd7a5-110">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7a5-110">GetCount Method</span></span>](icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="dd7a5-111">アプリケーションで使用されるスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-111">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="dd7a5-112">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="dd7a5-112">Next Method</span></span>](icorprofilerthreadenum-next-method.md)|<span data-ttu-id="dd7a5-113">スレッドのシーケンシャル コレクションから、列挙子の現在の位置以降にある指定した数の隣接するスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-113">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="dd7a5-114">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7a5-114">Reset Method</span></span>](icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="dd7a5-115">列挙子のカーソルをシーケンスの開始位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="dd7a5-116">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="dd7a5-116">Skip Method</span></span>](icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="dd7a5-117">指定した数の要素をスキップするため、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-117">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd7a5-118">解説</span><span class="sxs-lookup"><span data-stu-id="dd7a5-118">Remarks</span></span>  

 <span data-ttu-id="dd7a5-119">`ICorProfilerThreadEnum` インターフェイスは列挙子です。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-119">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="dd7a5-120">このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="dd7a5-121">つまり、受信側は配列要素のフローを明示的に制御できるため、大きな配列をメソッド パラメーターとして渡す場合に関連する問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd7a5-122">要件</span><span class="sxs-lookup"><span data-stu-id="dd7a5-122">Requirements</span></span>  

 <span data-ttu-id="dd7a5-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd7a5-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd7a5-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd7a5-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd7a5-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd7a5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd7a5-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd7a5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd7a5-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd7a5-127">See also</span></span>

- [<span data-ttu-id="dd7a5-128">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd7a5-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="dd7a5-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd7a5-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
