---
description: '詳細については、次を参照してください: ICorProfilerCallback:: RuntimeResumeStarted メソッド'
title: ICorProfilerCallback::RuntimeResumeStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
ms.openlocfilehash: 74e87906b4c429d795aa3074b25f4ac7a9edfa37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788840"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="3f36a-103">ICorProfilerCallback::RuntimeResumeStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="3f36a-103">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>

<span data-ttu-id="3f36a-104">ランタイムがすべてのランタイムスレッドを再開していることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="3f36a-104">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f36a-105">構文</span><span class="sxs-lookup"><span data-stu-id="3f36a-105">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3f36a-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="3f36a-106">Requirements</span></span>  

 <span data-ttu-id="3f36a-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f36a-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f36a-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f36a-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f36a-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f36a-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f36a-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f36a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f36a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f36a-111">See also</span></span>

- [<span data-ttu-id="3f36a-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f36a-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3f36a-113">RuntimeResumeFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="3f36a-113">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
