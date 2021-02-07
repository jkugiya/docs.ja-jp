---
description: '詳細について: ICorProfilerCallback:: ModuleUnloadFinished メソッド'
title: ICorProfilerCallback::ModuleUnloadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
ms.openlocfilehash: 32182beb879813a4e60f69494bd93799c0f66e1d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745256"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="ebbd3-103">ICorProfilerCallback::ModuleUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="ebbd3-103">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>

<span data-ttu-id="ebbd3-104">モジュールがアンロードを終了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ebbd3-104">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebbd3-105">構文</span><span class="sxs-lookup"><span data-stu-id="ebbd3-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebbd3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebbd3-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="ebbd3-107">からアンロードされたモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="ebbd3-107">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="ebbd3-108">からモジュールが正常にアンロードされたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="ebbd3-108">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebbd3-109">解説</span><span class="sxs-lookup"><span data-stu-id="ebbd3-109">Remarks</span></span>  

 <span data-ttu-id="ebbd3-110">`moduleId` [ICorProfilerCallback:: ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md)メソッドがを返すと、の値は情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="ebbd3-110">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="ebbd3-111">クラスのアンロードの一部は、コールバック後に続行される場合があり `ModuleUnloadFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="ebbd3-111">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="ebbd3-112">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="ebbd3-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="ebbd3-113">ただし、の成功 HRESULT は、 `hrStatus` モジュールのアンロードの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ebbd3-113">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebbd3-114">要件</span><span class="sxs-lookup"><span data-stu-id="ebbd3-114">Requirements</span></span>  

 <span data-ttu-id="ebbd3-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebbd3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebbd3-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ebbd3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ebbd3-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ebbd3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebbd3-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebbd3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbd3-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="ebbd3-119">See also</span></span>

- [<span data-ttu-id="ebbd3-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ebbd3-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
