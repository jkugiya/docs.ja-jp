---
description: '詳細情報: ICorProfilerCallback2:: FinalizeableObjectQueued メソッド'
title: ICorProfilerCallback2::FinalizeableObjectQueued メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: 62424ea60f72cee2328a143e4e50acd7af33e221
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647909"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="382b0-103">ICorProfilerCallback2::FinalizeableObjectQueued メソッド</span><span class="sxs-lookup"><span data-stu-id="382b0-103">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>

<span data-ttu-id="382b0-104">ファイナライザーを持つオブジェクトが、そのメソッドを実行するためにファイナライザースレッドに対してキューに登録されていることをコードプロファイラーに通知し `Finalize` ます。</span><span class="sxs-lookup"><span data-stu-id="382b0-104">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="382b0-105">構文</span><span class="sxs-lookup"><span data-stu-id="382b0-105">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="382b0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="382b0-106">Parameters</span></span>  

 `finalizerFlags`  
 <span data-ttu-id="382b0-107">からファイナライザーの側面を説明する [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="382b0-107">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="382b0-108">からキューに登録されたオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="382b0-108">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="382b0-109">要件</span><span class="sxs-lookup"><span data-stu-id="382b0-109">Requirements</span></span>  

 <span data-ttu-id="382b0-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="382b0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="382b0-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="382b0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="382b0-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="382b0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="382b0-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="382b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382b0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="382b0-114">See also</span></span>

- [<span data-ttu-id="382b0-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="382b0-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="382b0-116">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="382b0-116">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
