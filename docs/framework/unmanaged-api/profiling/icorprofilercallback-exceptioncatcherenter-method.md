---
description: '詳細について: ICorProfilerCallback:: ExceptionCatcherEnter メソッド'
title: ICorProfilerCallback::ExceptionCatcherEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 3a813936a7d1f3a5041e192c85d02b37976e3388
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657633"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="b4961-103">ICorProfilerCallback::ExceptionCatcherEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="b4961-103">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>

<span data-ttu-id="b4961-104">適切なブロックに制御が渡されていることをプロファイラーに通知し `catch` ます。</span><span class="sxs-lookup"><span data-stu-id="b4961-104">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4961-105">構文</span><span class="sxs-lookup"><span data-stu-id="b4961-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4961-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b4961-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b4961-107">\[in] ブロックを含む関数の識別子 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="b4961-107">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="b4961-108">\[in] 処理されている例外の識別子。</span><span class="sxs-lookup"><span data-stu-id="b4961-108">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4961-109">解説</span><span class="sxs-lookup"><span data-stu-id="b4961-109">Remarks</span></span>  

 <span data-ttu-id="b4961-110">メソッドは、 `ExceptionCatcherEnter` catch ポイントが just-in-time (JIT) コンパイラを使用してコンパイルされたコード内にある場合にのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b4961-110">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="b4961-111">アンマネージコードまたはランタイムの内部コードでキャッチされた例外は、この通知を呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="b4961-111">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="b4961-112">`objectId`通知後にガベージコレクションがオブジェクトを移動した可能性があるため、値は再度渡され `ExceptionThrown` ます。</span><span class="sxs-lookup"><span data-stu-id="b4961-112">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="b4961-113">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b4961-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b4961-114">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="b4961-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b4961-115">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="b4961-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4961-116">要件</span><span class="sxs-lookup"><span data-stu-id="b4961-116">Requirements</span></span>  

 <span data-ttu-id="b4961-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4961-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4961-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4961-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4961-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4961-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4961-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4961-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4961-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4961-121">See also</span></span>

- [<span data-ttu-id="b4961-122">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b4961-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b4961-123">ExceptionCatcherLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="b4961-123">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
