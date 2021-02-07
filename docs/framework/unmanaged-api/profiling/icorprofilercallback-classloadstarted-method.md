---
description: '詳細について: ICorProfilerCallback:: ClassLoadStarted メソッド'
title: ICorProfilerCallback::ClassLoadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 2474f8041b0858cbcb81d3f4042f1748cb99df3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706475"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="ec40b-103">ICorProfilerCallback::ClassLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="ec40b-103">ICorProfilerCallback::ClassLoadStarted Method</span></span>

<span data-ttu-id="ec40b-104">クラスが読み込まれていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ec40b-104">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec40b-105">構文</span><span class="sxs-lookup"><span data-stu-id="ec40b-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec40b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ec40b-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="ec40b-107">\[in] は、読み込むクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="ec40b-107">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="ec40b-108">解説</span><span class="sxs-lookup"><span data-stu-id="ec40b-108">Remarks</span></span>  

 <span data-ttu-id="ec40b-109">の値 `classId` は、 [ICorProfilerCallback:: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) メソッドが呼び出されるまで、情報要求に対して無効です。</span><span class="sxs-lookup"><span data-stu-id="ec40b-109">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec40b-110">要件</span><span class="sxs-lookup"><span data-stu-id="ec40b-110">Requirements</span></span>  

 <span data-ttu-id="ec40b-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec40b-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec40b-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ec40b-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ec40b-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec40b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec40b-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec40b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec40b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec40b-115">See also</span></span>

- [<span data-ttu-id="ec40b-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ec40b-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
