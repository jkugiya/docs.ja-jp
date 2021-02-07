---
description: '詳細について: ICorProfilerCallback:: ExceptionSearchFunctionLeave メソッド'
title: ICorProfilerCallback::ExceptionSearchFunctionLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
ms.openlocfilehash: 1a30d7ef979f751596cdd723b76eefee3cc1db5a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706150"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="22298-103">ICorProfilerCallback::ExceptionSearchFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="22298-103">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>

<span data-ttu-id="22298-104">例外処理の検索フェーズで関数の検索が終了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="22298-104">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22298-105">構文</span><span class="sxs-lookup"><span data-stu-id="22298-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="22298-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="22298-106">Requirements</span></span>  

 <span data-ttu-id="22298-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22298-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22298-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22298-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22298-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22298-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22298-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22298-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22298-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="22298-111">See also</span></span>

- [<span data-ttu-id="22298-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="22298-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="22298-113">ExceptionSearchFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="22298-113">ExceptionSearchFunctionEnter Method</span></span>](icorprofilercallback-exceptionsearchfunctionenter-method.md)
