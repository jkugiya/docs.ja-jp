---
description: '詳細については、次を参照してください: ICorProfilerCallback:: RuntimeResumeFinished メソッド'
title: ICorProfilerCallback::RuntimeResumeFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
ms.openlocfilehash: a8a38ff8372df9890239966c90175d72bda4b09d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788853"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="3ab81-103">ICorProfilerCallback::RuntimeResumeFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="3ab81-103">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>

<span data-ttu-id="3ab81-104">ランタイムがすべてのランタイムスレッドを再開し、通常の動作に戻ったことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="3ab81-104">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ab81-105">構文</span><span class="sxs-lookup"><span data-stu-id="3ab81-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="3ab81-106">解説</span><span class="sxs-lookup"><span data-stu-id="3ab81-106">Remarks</span></span>  

 <span data-ttu-id="3ab81-107">`RuntimeResumeFinished`コールバックは、 [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)コールバックと同じスレッドで実行されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="3ab81-107">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="3ab81-108">ただし、 [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) コールバックと同じスレッドで発生することは保証されています。</span><span class="sxs-lookup"><span data-stu-id="3ab81-108">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ab81-109">要件</span><span class="sxs-lookup"><span data-stu-id="3ab81-109">Requirements</span></span>  

 <span data-ttu-id="3ab81-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ab81-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ab81-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ab81-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ab81-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ab81-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ab81-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ab81-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ab81-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ab81-114">See also</span></span>

- [<span data-ttu-id="3ab81-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ab81-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
