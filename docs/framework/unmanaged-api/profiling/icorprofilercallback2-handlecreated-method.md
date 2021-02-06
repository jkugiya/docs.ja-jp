---
description: '詳細について: ICorProfilerCallback2:: HandleCreated メソッド'
title: ICorProfilerCallback2::HandleCreated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 17f4ed83646907a229dcc6a30dcce1b52fa608d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657087"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="49d1b-103">ICorProfilerCallback2::HandleCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="49d1b-103">ICorProfilerCallback2::HandleCreated Method</span></span>

<span data-ttu-id="49d1b-104">ガベージコレクションハンドルが作成されたことをコードプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="49d1b-104">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d1b-105">構文</span><span class="sxs-lookup"><span data-stu-id="49d1b-105">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49d1b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49d1b-106">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="49d1b-107">からガベージコレクションのハンドルの ID。</span><span class="sxs-lookup"><span data-stu-id="49d1b-107">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="49d1b-108">からガベージコレクションハンドルが作成されたオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="49d1b-108">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d1b-109">要件</span><span class="sxs-lookup"><span data-stu-id="49d1b-109">Requirements</span></span>  

 <span data-ttu-id="49d1b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49d1b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49d1b-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49d1b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49d1b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49d1b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49d1b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49d1b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d1b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="49d1b-114">See also</span></span>

- [<span data-ttu-id="49d1b-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49d1b-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="49d1b-116">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49d1b-116">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
