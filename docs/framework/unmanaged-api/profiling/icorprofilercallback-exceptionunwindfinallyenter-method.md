---
description: '詳細について: ICorProfilerCallback:: ExceptionUnwindFinallyEnter メソッド'
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
ms.openlocfilehash: e4a701597b318a387405a152f2c3b4758d616eb0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706085"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a><span data-ttu-id="4879a-103">ICorProfilerCallback::ExceptionUnwindFinallyEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="4879a-103">ICorProfilerCallback::ExceptionUnwindFinallyEnter Method</span></span>

<span data-ttu-id="4879a-104">例外処理のアンワインドフェーズが、指定された `finally` 関数に含まれる句を入力していることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4879a-104">Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4879a-105">構文</span><span class="sxs-lookup"><span data-stu-id="4879a-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4879a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4879a-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="4879a-107">\[in] 句を含む関数の ID `finally` 。</span><span class="sxs-lookup"><span data-stu-id="4879a-107">\[in] The ID of the function that contains the `finally` clause.</span></span>

## <a name="remarks"></a><span data-ttu-id="4879a-108">解説</span><span class="sxs-lookup"><span data-stu-id="4879a-108">Remarks</span></span>  

 <span data-ttu-id="4879a-109">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4879a-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="4879a-110">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="4879a-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="4879a-111">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="4879a-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4879a-112">要件</span><span class="sxs-lookup"><span data-stu-id="4879a-112">Requirements</span></span>  

 <span data-ttu-id="4879a-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4879a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4879a-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4879a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4879a-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4879a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4879a-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4879a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4879a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="4879a-117">See also</span></span>

- [<span data-ttu-id="4879a-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4879a-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4879a-119">GetNotifiedExceptionClauseInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="4879a-119">GetNotifiedExceptionClauseInfo Method</span></span>](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [<span data-ttu-id="4879a-120">ExceptionUnwindFinallyLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="4879a-120">ExceptionUnwindFinallyLeave Method</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)
