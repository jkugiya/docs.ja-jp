---
description: '詳細について: ICorProfilerCallback:: ExceptionUnwindFunctionEnter メソッド'
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
ms.openlocfilehash: 3f0376e01263290596aa722b37f6a796ab919139
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706020"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="8aff5-103">ICorProfilerCallback::ExceptionUnwindFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="8aff5-103">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>

<span data-ttu-id="8aff5-104">例外処理のアンワインドフェーズが関数のアンワインドを開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8aff5-104">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aff5-105">構文</span><span class="sxs-lookup"><span data-stu-id="8aff5-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aff5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8aff5-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="8aff5-107">\[in] アンワインドされている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="8aff5-107">\[in] The ID of the function that is being unwound.</span></span>

## <a name="remarks"></a><span data-ttu-id="8aff5-108">解説</span><span class="sxs-lookup"><span data-stu-id="8aff5-108">Remarks</span></span>  

 <span data-ttu-id="8aff5-109">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="8aff5-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="8aff5-110">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="8aff5-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="8aff5-111">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="8aff5-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aff5-112">要件</span><span class="sxs-lookup"><span data-stu-id="8aff5-112">Requirements</span></span>  

 <span data-ttu-id="8aff5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8aff5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aff5-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8aff5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8aff5-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aff5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aff5-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aff5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aff5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8aff5-117">See also</span></span>

- [<span data-ttu-id="8aff5-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8aff5-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8aff5-119">ExceptionUnwindFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="8aff5-119">ExceptionUnwindFunctionLeave Method</span></span>](icorprofilercallback-exceptionunwindfunctionleave-method.md)
