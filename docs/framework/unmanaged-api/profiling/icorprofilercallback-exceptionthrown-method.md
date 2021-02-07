---
description: '詳細情報: ICorProfilerCallback:: ExceptionThrown されたメソッド'
title: ICorProfilerCallback::ExceptionThrown メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: 77ebca8fbc52ed0c46a4f76fb5cdf6cb2923edaf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706137"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="34714-103">ICorProfilerCallback::ExceptionThrown メソッド</span><span class="sxs-lookup"><span data-stu-id="34714-103">ICorProfilerCallback::ExceptionThrown Method</span></span>

<span data-ttu-id="34714-104">例外がスローされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="34714-104">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34714-105">この関数は、例外がマネージコードに到達した場合にのみ呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="34714-105">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34714-106">構文</span><span class="sxs-lookup"><span data-stu-id="34714-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34714-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34714-107">Parameters</span></span>

- `thrownObjectId`

  <span data-ttu-id="34714-108">\[in] 例外がスローされる原因となったオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="34714-108">\[in] The ID of the object that caused the exception to be thrown.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="34714-109">解説</span><span class="sxs-lookup"><span data-stu-id="34714-109">Remarks</span></span>  

 <span data-ttu-id="34714-110">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="34714-110">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="34714-111">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="34714-111">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="34714-112">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="34714-112">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34714-113">要件</span><span class="sxs-lookup"><span data-stu-id="34714-113">Requirements</span></span>  

 <span data-ttu-id="34714-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34714-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34714-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34714-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34714-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34714-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34714-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34714-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34714-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="34714-118">See also</span></span>

- [<span data-ttu-id="34714-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="34714-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
