---
description: '詳細情報: ICorProfilerCallback:: ThreadDestroyed メソッド'
title: ICorProfilerCallback::ThreadDestroyed メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
ms.openlocfilehash: 63c8c4c523cb398bd7c766fc41bc669a2d74045e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657178"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="a8bf8-103">ICorProfilerCallback::ThreadDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="a8bf8-103">ICorProfilerCallback::ThreadDestroyed Method</span></span>

<span data-ttu-id="a8bf8-104">スレッドが破棄されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a8bf8-104">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8bf8-105">構文</span><span class="sxs-lookup"><span data-stu-id="a8bf8-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8bf8-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8bf8-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="a8bf8-107">から破棄されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="a8bf8-107">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8bf8-108">解説</span><span class="sxs-lookup"><span data-stu-id="a8bf8-108">Remarks</span></span>  

 <span data-ttu-id="a8bf8-109">`threadId`この呼び出しの時点では、この値は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a8bf8-109">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8bf8-110">要件</span><span class="sxs-lookup"><span data-stu-id="a8bf8-110">Requirements</span></span>  

 <span data-ttu-id="a8bf8-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8bf8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8bf8-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a8bf8-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a8bf8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8bf8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8bf8-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8bf8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8bf8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8bf8-115">See also</span></span>

- [<span data-ttu-id="a8bf8-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8bf8-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a8bf8-117">ThreadCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="a8bf8-117">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
