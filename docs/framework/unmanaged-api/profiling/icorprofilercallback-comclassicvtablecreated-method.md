---
description: '詳細について: ICorProfilerCallback:: COMClassicVTableCreated メソッド'
title: ICorProfilerCallback::COMClassicVTableCreated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
ms.openlocfilehash: 134ca44cbcd7a275e3ad61a3dd4decaa92668b5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657711"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="cc18d-103">ICorProfilerCallback::COMClassicVTableCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="cc18d-103">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>

<span data-ttu-id="cc18d-104">指定した IID およびクラスの COM 相互運用機能の vtable が作成されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cc18d-104">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc18d-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc18d-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc18d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc18d-106">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="cc18d-107">\[in] vtable が作成されたクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="cc18d-107">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="cc18d-108">\[in] クラスによって実装されるインターフェイスの ID。</span><span class="sxs-lookup"><span data-stu-id="cc18d-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="cc18d-109">この値は、インターフェイスが内部でのみ使用されている場合は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="cc18d-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="cc18d-110">\[) vtable の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cc18d-110">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="cc18d-111">\[in] vtable 内のスロットの数。</span><span class="sxs-lookup"><span data-stu-id="cc18d-111">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="cc18d-112">解説</span><span class="sxs-lookup"><span data-stu-id="cc18d-112">Remarks</span></span>  

 <span data-ttu-id="cc18d-113">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cc18d-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="cc18d-114">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="cc18d-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="cc18d-115">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="cc18d-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc18d-116">要件</span><span class="sxs-lookup"><span data-stu-id="cc18d-116">Requirements</span></span>  

 <span data-ttu-id="cc18d-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc18d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc18d-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc18d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc18d-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc18d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc18d-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc18d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc18d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc18d-121">See also</span></span>

- [<span data-ttu-id="cc18d-122">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc18d-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cc18d-123">COMClassicVTableDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="cc18d-123">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
