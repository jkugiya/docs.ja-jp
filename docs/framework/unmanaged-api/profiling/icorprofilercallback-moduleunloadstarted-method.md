---
description: '詳細について: ICorProfilerCallback:: ModuleUnloadStarted メソッド'
title: ICorProfilerCallback::ModuleUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: 3d10654e23481fe6f8956129a0aef7ed4206bba9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745230"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="12ed5-103">ICorProfilerCallback::ModuleUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="12ed5-103">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>

<span data-ttu-id="12ed5-104">モジュールがアンロードされていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="12ed5-104">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ed5-105">構文</span><span class="sxs-lookup"><span data-stu-id="12ed5-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="12ed5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12ed5-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="12ed5-107">からアンロードされるモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="12ed5-107">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12ed5-108">解説</span><span class="sxs-lookup"><span data-stu-id="12ed5-108">Remarks</span></span>  

 <span data-ttu-id="12ed5-109">の値は、 `moduleId` メソッドから制御が戻った後の情報要求に対して有効ではありません `ModuleUnloadStarted` 。これは、このモジュールに関する情報を取得する最後の機会です。</span><span class="sxs-lookup"><span data-stu-id="12ed5-109">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12ed5-110">要件</span><span class="sxs-lookup"><span data-stu-id="12ed5-110">Requirements</span></span>  

 <span data-ttu-id="12ed5-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12ed5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ed5-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12ed5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12ed5-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12ed5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12ed5-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12ed5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ed5-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="12ed5-115">See also</span></span>

- [<span data-ttu-id="12ed5-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12ed5-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="12ed5-117">ModuleUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="12ed5-117">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
