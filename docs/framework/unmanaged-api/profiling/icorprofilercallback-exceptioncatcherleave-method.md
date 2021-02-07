---
description: '詳細について: ICorProfilerCallback:: ExceptionCatcherLeave メソッド'
title: ICorProfilerCallback::ExceptionCatcherLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: 402a622dc949ef6f93c0ca5916a0690c6e734bd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706358"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="536de-103">ICorProfilerCallback::ExceptionCatcherLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="536de-103">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>

<span data-ttu-id="536de-104">適切なブロックから制御が渡されていることをプロファイラーに通知し `catch` ます。</span><span class="sxs-lookup"><span data-stu-id="536de-104">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="536de-105">構文</span><span class="sxs-lookup"><span data-stu-id="536de-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="536de-106">解説</span><span class="sxs-lookup"><span data-stu-id="536de-106">Remarks</span></span>  

 <span data-ttu-id="536de-107">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="536de-107">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="536de-108">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="536de-108">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="536de-109">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="536de-109">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="536de-110">要件</span><span class="sxs-lookup"><span data-stu-id="536de-110">Requirements</span></span>  

 <span data-ttu-id="536de-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="536de-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="536de-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="536de-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="536de-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="536de-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="536de-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="536de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="536de-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="536de-115">See also</span></span>

- [<span data-ttu-id="536de-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="536de-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="536de-117">ExceptionCatcherEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="536de-117">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
