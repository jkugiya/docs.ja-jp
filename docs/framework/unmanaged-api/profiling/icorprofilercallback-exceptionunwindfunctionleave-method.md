---
description: '詳細について: ICorProfilerCallback:: ExceptionUnwindFunctionLeave メソッド'
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: f428230b017841e931463057144ef72cc1ead45f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705965"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="82342-103">ICorProfilerCallback::ExceptionUnwindFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="82342-103">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>

<span data-ttu-id="82342-104">例外処理のアンワインドフェーズが関数のアンワインドを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="82342-104">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82342-105">構文</span><span class="sxs-lookup"><span data-stu-id="82342-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="82342-106">解説</span><span class="sxs-lookup"><span data-stu-id="82342-106">Remarks</span></span>  

 <span data-ttu-id="82342-107">`ExceptionUnwindFunctionLeave`メソッドが呼び出されると、関数インスタンスとそのスタックデータがスタックから削除されます。</span><span class="sxs-lookup"><span data-stu-id="82342-107">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="82342-108">スタックがガベージコレクションを許可する状態ではなく、したがって、プリエンプティブガベージコレクションを有効にできないため、この呼び出し中にプロファイラーはブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="82342-108">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="82342-109">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="82342-109">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="82342-110">また、この呼び出しでは、プロファイラーはマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="82342-110">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82342-111">要件</span><span class="sxs-lookup"><span data-stu-id="82342-111">Requirements</span></span>  

 <span data-ttu-id="82342-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82342-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82342-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="82342-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82342-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82342-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82342-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82342-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82342-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="82342-116">See also</span></span>

- [<span data-ttu-id="82342-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82342-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="82342-118">ExceptionUnwindFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="82342-118">ExceptionUnwindFunctionEnter Method</span></span>](icorprofilercallback-exceptionunwindfunctionenter-method.md)
