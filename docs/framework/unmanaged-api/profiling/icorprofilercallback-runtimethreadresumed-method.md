---
description: '詳細については、次を参照してください: ICorProfilerCallback:: RuntimeThreadResumed メソッド'
title: ICorProfilerCallback::RuntimeThreadResumed メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: a01be057bb442c69890d3b1cb4ebe1f861d2518c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657347"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="28418-103">ICorProfilerCallback::RuntimeThreadResumed メソッド</span><span class="sxs-lookup"><span data-stu-id="28418-103">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>

<span data-ttu-id="28418-104">指定したスレッドが中断された後に再開されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="28418-104">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28418-105">構文</span><span class="sxs-lookup"><span data-stu-id="28418-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28418-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28418-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="28418-107">から再開されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="28418-107">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28418-108">要件</span><span class="sxs-lookup"><span data-stu-id="28418-108">Requirements</span></span>  

 <span data-ttu-id="28418-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28418-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28418-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28418-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28418-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28418-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28418-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28418-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28418-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="28418-113">See also</span></span>

- [<span data-ttu-id="28418-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28418-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="28418-115">RuntimeThreadSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="28418-115">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
