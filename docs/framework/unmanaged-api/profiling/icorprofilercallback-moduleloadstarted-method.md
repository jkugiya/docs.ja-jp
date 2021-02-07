---
description: '詳細について: ICorProfilerCallback:: ModuleLoadStarted メソッド'
title: ICorProfilerCallback::ModuleLoadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
ms.openlocfilehash: e8d15bece7baf82f69162663da00d331c7904837
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745269"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="4dfe9-103">ICorProfilerCallback::ModuleLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="4dfe9-103">ICorProfilerCallback::ModuleLoadStarted Method</span></span>

<span data-ttu-id="4dfe9-104">モジュールが読み込まれていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4dfe9-104">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dfe9-105">構文</span><span class="sxs-lookup"><span data-stu-id="4dfe9-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dfe9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4dfe9-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="4dfe9-107">から読み込まれているモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="4dfe9-107">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dfe9-108">解説</span><span class="sxs-lookup"><span data-stu-id="4dfe9-108">Remarks</span></span>  

 <span data-ttu-id="4dfe9-109">の値は、 `moduleId` [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) メソッドが呼び出されるまで、情報要求に対して無効です。</span><span class="sxs-lookup"><span data-stu-id="4dfe9-109">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dfe9-110">要件</span><span class="sxs-lookup"><span data-stu-id="4dfe9-110">Requirements</span></span>  

 <span data-ttu-id="4dfe9-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4dfe9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dfe9-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4dfe9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4dfe9-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4dfe9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dfe9-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dfe9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfe9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4dfe9-115">See also</span></span>

- [<span data-ttu-id="4dfe9-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4dfe9-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
