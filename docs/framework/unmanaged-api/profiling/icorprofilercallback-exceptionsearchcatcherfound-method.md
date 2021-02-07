---
description: '詳細について: ICorProfilerCallback:: ExceptionSearchCatcherFound メソッド'
title: ICorProfilerCallback::ExceptionSearchCatcherFound メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: b222e629cbfce2fde27c2d266b3a343466a1419c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706319"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="0527a-103">ICorProfilerCallback::ExceptionSearchCatcherFound メソッド</span><span class="sxs-lookup"><span data-stu-id="0527a-103">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>

<span data-ttu-id="0527a-104">例外処理の検索フェーズによってスローされた例外のハンドラーが見つかったことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0527a-104">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0527a-105">構文</span><span class="sxs-lookup"><span data-stu-id="0527a-105">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0527a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0527a-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="0527a-107">\[in] 例外ハンドラーを含む関数の ID。</span><span class="sxs-lookup"><span data-stu-id="0527a-107">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="0527a-108">要件</span><span class="sxs-lookup"><span data-stu-id="0527a-108">Requirements</span></span>  

 <span data-ttu-id="0527a-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0527a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0527a-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0527a-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0527a-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0527a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0527a-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0527a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0527a-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0527a-113">See also</span></span>

- [<span data-ttu-id="0527a-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0527a-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
