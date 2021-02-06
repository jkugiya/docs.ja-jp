---
description: '詳細について: ICorProfilerCallback:: ThreadAssignedToOSThread メソッド'
title: ICorProfilerCallback::ThreadAssignedToOSThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
ms.openlocfilehash: 04fba4cabb0ac58b3afeaae1fd579865335a9e14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647987"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="f9d1b-103">ICorProfilerCallback::ThreadAssignedToOSThread メソッド</span><span class="sxs-lookup"><span data-stu-id="f9d1b-103">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>

<span data-ttu-id="f9d1b-104">特定のオペレーティングシステムスレッドを使用してマネージスレッドが実装されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f9d1b-104">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9d1b-105">構文</span><span class="sxs-lookup"><span data-stu-id="f9d1b-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9d1b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9d1b-106">Parameters</span></span>  

 `managedThreadId`  
 <span data-ttu-id="f9d1b-107">からマネージスレッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="f9d1b-107">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="f9d1b-108">からオペレーティングシステムスレッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="f9d1b-108">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9d1b-109">解説</span><span class="sxs-lookup"><span data-stu-id="f9d1b-109">Remarks</span></span>  

 <span data-ttu-id="f9d1b-110">コールバックが存在するので、 `ThreadAssignedToOSThread` プロファイラーは、オペレーティングシステムスレッドのファイバー全体でマネージスレッドに対して正確なマッピングを維持できます。</span><span class="sxs-lookup"><span data-stu-id="f9d1b-110">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9d1b-111">要件</span><span class="sxs-lookup"><span data-stu-id="f9d1b-111">Requirements</span></span>  

 <span data-ttu-id="f9d1b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9d1b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9d1b-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9d1b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9d1b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9d1b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9d1b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9d1b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d1b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9d1b-116">See also</span></span>

- [<span data-ttu-id="f9d1b-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9d1b-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
