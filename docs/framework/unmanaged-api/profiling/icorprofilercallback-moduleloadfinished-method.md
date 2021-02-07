---
description: '詳細について: ICorProfilerCallback:: ModuleLoadFinished メソッド'
title: ICorProfilerCallback::ModuleLoadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 960eb9edd036055069ef3f9ab3a93602ce4ef9bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745347"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="9b8af-103">ICorProfilerCallback::ModuleLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="9b8af-103">ICorProfilerCallback::ModuleLoadFinished Method</span></span>

<span data-ttu-id="9b8af-104">モジュールが読み込みを終了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9b8af-104">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8af-105">構文</span><span class="sxs-lookup"><span data-stu-id="9b8af-105">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b8af-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b8af-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="9b8af-107">から読み込みを終了したモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="9b8af-107">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="9b8af-108">からモジュールが正常に読み込まれたかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="9b8af-108">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b8af-109">解説</span><span class="sxs-lookup"><span data-stu-id="9b8af-109">Remarks</span></span>  

 <span data-ttu-id="9b8af-110">の値 `moduleId` は、 `ModuleLoadFinished` メソッドが呼び出されるまで、情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="9b8af-110">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="9b8af-111">モジュールの読み込みの一部は、コールバック後に続行される場合があり `ModuleLoadFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="9b8af-111">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="9b8af-112">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="9b8af-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="9b8af-113">ただし、の成功 HRESULT は、 `hrStatus` モジュールの読み込みの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9b8af-113">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b8af-114">要件</span><span class="sxs-lookup"><span data-stu-id="9b8af-114">Requirements</span></span>  

 <span data-ttu-id="9b8af-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b8af-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b8af-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b8af-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b8af-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b8af-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b8af-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b8af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b8af-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b8af-119">See also</span></span>

- [<span data-ttu-id="9b8af-120">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b8af-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9b8af-121">ModuleLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="9b8af-121">ModuleLoadStarted Method</span></span>](icorprofilercallback-moduleloadstarted-method.md)
