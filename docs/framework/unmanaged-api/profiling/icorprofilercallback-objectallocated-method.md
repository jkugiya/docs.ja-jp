---
description: '詳細について: ICorProfilerCallback:: ObjectAllocated メソッド'
title: ICorProfilerCallback::ObjectAllocated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: 58b58aeb4bb88d0df32cebc32440317a4d23632d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745165"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="31b85-103">ICorProfilerCallback::ObjectAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="31b85-103">ICorProfilerCallback::ObjectAllocated Method</span></span>

<span data-ttu-id="31b85-104">ヒープ内のメモリがオブジェクトに割り当てられたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="31b85-104">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31b85-105">構文</span><span class="sxs-lookup"><span data-stu-id="31b85-105">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31b85-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31b85-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="31b85-107">からメモリが割り当てられたオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="31b85-107">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="31b85-108">からオブジェクトがインスタンスとして使用されているクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="31b85-108">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31b85-109">解説</span><span class="sxs-lookup"><span data-stu-id="31b85-109">Remarks</span></span>  

 <span data-ttu-id="31b85-110">メソッドは、 `ObjectedAllocated` スタックまたはアンマネージメモリからの割り当てのために呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="31b85-110">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="31b85-111">パラメーターは、 `classId` まだ読み込まれていないマネージコード内のクラスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="31b85-111">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="31b85-112">プロファイラーは、コールバックの直後に、そのクラスのクラス読み込みコールバックを受け取り `ObjectAllocated` ます。</span><span class="sxs-lookup"><span data-stu-id="31b85-112">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31b85-113">要件</span><span class="sxs-lookup"><span data-stu-id="31b85-113">Requirements</span></span>  

 <span data-ttu-id="31b85-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31b85-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31b85-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31b85-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31b85-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31b85-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31b85-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31b85-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b85-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="31b85-118">See also</span></span>

- [<span data-ttu-id="31b85-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31b85-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="31b85-120">ClassLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="31b85-120">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="31b85-121">ClassLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="31b85-121">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
