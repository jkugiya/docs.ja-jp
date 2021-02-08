---
description: 詳細については、「ICorProfilerModuleEnum インターフェイス」を参照してください。
title: ICorProfilerModuleEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 195379e9ad6bce94fc93465fe5e1418c5d8c076d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783821"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="c664f-103">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c664f-103">ICorProfilerModuleEnum Interface</span></span>

<span data-ttu-id="c664f-104">アプリケーションまたはプロファイラーによってロードされたモジュールのコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c664f-104">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c664f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c664f-105">Methods</span></span>  
  
|<span data-ttu-id="c664f-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="c664f-106">Method</span></span>|<span data-ttu-id="c664f-107">説明</span><span class="sxs-lookup"><span data-stu-id="c664f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c664f-108">Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="c664f-108">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="c664f-109">この `ICorProfilerModuleEnum` インターフェイスのコピーへのインターフェイス ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c664f-109">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="c664f-110">GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="c664f-110">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="c664f-111">アプリケーションによって読み込まれたマネージド モジュールの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="c664f-111">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="c664f-112">次のメソッド</span><span class="sxs-lookup"><span data-stu-id="c664f-112">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="c664f-113">オブジェクトのシーケンシャル コレクションから、列挙子の現在の位置以降にある指定した数の隣接するモジュールを取得します。</span><span class="sxs-lookup"><span data-stu-id="c664f-113">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="c664f-114">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="c664f-114">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="c664f-115">列挙子のカーソルをシーケンスの開始位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="c664f-115">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="c664f-116">Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="c664f-116">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="c664f-117">指定した数の要素がスキップされるように、この列挙子のカーソルの位置を進めます。</span><span class="sxs-lookup"><span data-stu-id="c664f-117">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c664f-118">解説</span><span class="sxs-lookup"><span data-stu-id="c664f-118">Remarks</span></span>  

 <span data-ttu-id="c664f-119">`ICorProfilerModuleEnum` インターフェイスは列挙子です。</span><span class="sxs-lookup"><span data-stu-id="c664f-119">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="c664f-120">このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。</span><span class="sxs-lookup"><span data-stu-id="c664f-120">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="c664f-121">つまり、受信側は配列要素のフローを明示的に制御できるため、大きな配列をメソッド パラメーターとして渡す場合に関連する問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="c664f-121">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c664f-122">要件</span><span class="sxs-lookup"><span data-stu-id="c664f-122">Requirements</span></span>  

 <span data-ttu-id="c664f-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c664f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c664f-124">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c664f-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c664f-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c664f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c664f-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c664f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c664f-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c664f-127">See also</span></span>

- [<span data-ttu-id="c664f-128">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c664f-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c664f-129">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c664f-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c664f-130">EnumModules メソッド</span><span class="sxs-lookup"><span data-stu-id="c664f-130">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
