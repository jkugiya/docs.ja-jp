---
description: '詳細について: ICorProfilerCallback2:: GarbageCollectionFinished メソッド'
title: ICorProfilerCallback2::GarbageCollectionFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
ms.openlocfilehash: 9e41c5ced76af40866269fdff74fd302b937b70e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657113"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="154b9-103">ICorProfilerCallback2::GarbageCollectionFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="154b9-103">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>

<span data-ttu-id="154b9-104">ガベージコレクションが完了し、すべてのガベージコレクションコールバックが発行されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="154b9-104">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="154b9-105">構文</span><span class="sxs-lookup"><span data-stu-id="154b9-105">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="154b9-106">解説</span><span class="sxs-lookup"><span data-stu-id="154b9-106">Remarks</span></span>  

 <span data-ttu-id="154b9-107">メソッドが呼び出されたときに、プロファイラーが最終的な場所のオブジェクトを検査するのは安全です `GarbageCollectionFinished` 。</span><span class="sxs-lookup"><span data-stu-id="154b9-107">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="154b9-108">要件</span><span class="sxs-lookup"><span data-stu-id="154b9-108">Requirements</span></span>  

 <span data-ttu-id="154b9-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="154b9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="154b9-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="154b9-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="154b9-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="154b9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="154b9-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="154b9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="154b9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="154b9-113">See also</span></span>

- [<span data-ttu-id="154b9-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="154b9-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="154b9-115">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="154b9-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
