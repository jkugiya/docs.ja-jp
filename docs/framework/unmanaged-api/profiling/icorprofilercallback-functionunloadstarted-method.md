---
description: '詳細について: ICorProfilerCallback:: FunctionUnloadStarted メソッド'
title: ICorProfilerCallback::FunctionUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: 3dd5d46a224c0c51dfee251cf5d0c6ae9320b630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705960"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="cdf1e-103">ICorProfilerCallback::FunctionUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="cdf1e-103">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>

<span data-ttu-id="cdf1e-104">ランタイムが関数のアンロードを開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="cdf1e-104">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf1e-105">構文</span><span class="sxs-lookup"><span data-stu-id="cdf1e-105">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="cdf1e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cdf1e-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="cdf1e-107">\[in] アンロードされる関数の ID。</span><span class="sxs-lookup"><span data-stu-id="cdf1e-107">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdf1e-108">解説</span><span class="sxs-lookup"><span data-stu-id="cdf1e-108">Remarks</span></span>  

 <span data-ttu-id="cdf1e-109">パラメーターの値 `functionId` は、このメソッドが呼び出し元に戻った後に有効ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="cdf1e-109">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdf1e-110">要件</span><span class="sxs-lookup"><span data-stu-id="cdf1e-110">Requirements</span></span>  

 <span data-ttu-id="cdf1e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cdf1e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdf1e-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cdf1e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cdf1e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdf1e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdf1e-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdf1e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf1e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdf1e-115">See also</span></span>

- [<span data-ttu-id="cdf1e-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cdf1e-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
