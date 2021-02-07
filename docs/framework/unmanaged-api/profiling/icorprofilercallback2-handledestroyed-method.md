---
description: '詳細について: ICorProfilerCallback2:: HandleDestroyed メソッド'
title: ICorProfilerCallback2::HandleDestroyed メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleDestroyed
helpviewer_keywords:
- ICorProfilerCallback2::HandleDestroyed method [.NET Framework profiling]
- HandleDestroyed method [.NET Framework profiling]
ms.assetid: ab4f4bbd-40c7-4667-bfde-60cd73803110
topic_type:
- apiref
ms.openlocfilehash: d583a2170efbb4ebe72d7eacdd60af1a089a518f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705581"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="f22ee-103">ICorProfilerCallback2::HandleDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="f22ee-103">ICorProfilerCallback2::HandleDestroyed Method</span></span>

<span data-ttu-id="f22ee-104">ガベージコレクションハンドルが破棄されたことをコードプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f22ee-104">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f22ee-105">構文</span><span class="sxs-lookup"><span data-stu-id="f22ee-105">Syntax</span></span>  
  
```cpp  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f22ee-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f22ee-106">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="f22ee-107">からガベージコレクションのハンドルの ID。</span><span class="sxs-lookup"><span data-stu-id="f22ee-107">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f22ee-108">要件</span><span class="sxs-lookup"><span data-stu-id="f22ee-108">Requirements</span></span>  

 <span data-ttu-id="f22ee-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f22ee-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f22ee-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f22ee-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f22ee-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f22ee-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f22ee-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f22ee-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f22ee-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f22ee-113">See also</span></span>

- [<span data-ttu-id="f22ee-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f22ee-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f22ee-115">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f22ee-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
