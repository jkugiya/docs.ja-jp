---
description: '詳細について: ICorProfilerCallback:: ThreadCreated メソッド'
title: ICorProfilerCallback::ThreadCreated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 8b6208856b78298f643161cd6bb78773ac86bc3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657204"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="35383-103">ICorProfilerCallback::ThreadCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="35383-103">ICorProfilerCallback::ThreadCreated Method</span></span>

<span data-ttu-id="35383-104">スレッドが作成されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="35383-104">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35383-105">構文</span><span class="sxs-lookup"><span data-stu-id="35383-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="35383-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="35383-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="35383-107">から作成されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="35383-107">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35383-108">解説</span><span class="sxs-lookup"><span data-stu-id="35383-108">Remarks</span></span>  

 <span data-ttu-id="35383-109">この `threadId` 値はすぐに有効です。</span><span class="sxs-lookup"><span data-stu-id="35383-109">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35383-110">要件</span><span class="sxs-lookup"><span data-stu-id="35383-110">Requirements</span></span>  

 <span data-ttu-id="35383-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35383-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35383-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="35383-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35383-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35383-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35383-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35383-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35383-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="35383-115">See also</span></span>

- [<span data-ttu-id="35383-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="35383-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="35383-117">ThreadDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="35383-117">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
