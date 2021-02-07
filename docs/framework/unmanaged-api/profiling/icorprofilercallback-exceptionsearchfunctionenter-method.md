---
description: '詳細について: ICorProfilerCallback:: ExceptionSearchFunctionEnter メソッド'
title: ICorProfilerCallback::ExceptionSearchFunctionEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
ms.openlocfilehash: 6e77ab5dc8c15a1d0785fb83310183c0a4693225
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706189"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="00670-103">ICorProfilerCallback::ExceptionSearchFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="00670-103">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>

<span data-ttu-id="00670-104">現在の例外のハンドラーを検索するために、例外処理の検索フェーズで関数の検索が開始されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="00670-104">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00670-105">構文</span><span class="sxs-lookup"><span data-stu-id="00670-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00670-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00670-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="00670-107">\[in] 入力された関数の ID。</span><span class="sxs-lookup"><span data-stu-id="00670-107">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="00670-108">要件</span><span class="sxs-lookup"><span data-stu-id="00670-108">Requirements</span></span>  

 <span data-ttu-id="00670-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00670-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00670-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00670-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00670-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00670-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00670-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00670-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00670-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="00670-113">See also</span></span>

- [<span data-ttu-id="00670-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00670-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="00670-115">ExceptionSearchFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="00670-115">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
