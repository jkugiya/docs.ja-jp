---
description: '詳細について: ICorProfilerCallback:: ClassUnloadFinished メソッド'
title: ICorProfilerCallback::ClassUnloadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: ae1ef56a1eb3b9b45c2165ecceb0af826cc7a2ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657737"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="6c399-103">ICorProfilerCallback::ClassUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="6c399-103">ICorProfilerCallback::ClassUnloadFinished Method</span></span>

<span data-ttu-id="6c399-104">クラスのアンロードが終了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6c399-104">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c399-105">構文</span><span class="sxs-lookup"><span data-stu-id="6c399-105">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c399-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6c399-106">Parameters</span></span>

- `classId`

  <span data-ttu-id="6c399-107">\[in] は、アンロードされたクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="6c399-107">\[in] Identifies the class that was unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="6c399-108">\[in] クラスが正常にアンロードされたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="6c399-108">\[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="6c399-109">解説</span><span class="sxs-lookup"><span data-stu-id="6c399-109">Remarks</span></span>  

 <span data-ttu-id="6c399-110">クラスのアンロードの一部は、コールバック後に続行される場合があり `ClassUnloadFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="6c399-110">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="6c399-111">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="6c399-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6c399-112">ただし、の成功 HRESULT は、 `hrStatus` クラスのアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="6c399-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c399-113">要件</span><span class="sxs-lookup"><span data-stu-id="6c399-113">Requirements</span></span>  

 <span data-ttu-id="6c399-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c399-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c399-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c399-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c399-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c399-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c399-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c399-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c399-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c399-118">See also</span></span>

- [<span data-ttu-id="6c399-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c399-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6c399-120">ClassUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="6c399-120">ClassUnloadStarted Method</span></span>](icorprofilercallback-classunloadstarted-method.md)
