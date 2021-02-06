---
description: '詳細について: ICorProfilerCallback:: ExceptionOSHandlerEnter メソッド'
title: ICorProfilerCallback::ExceptionOSHandlerEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
ms.openlocfilehash: 88dfd062451c63265716e7cf4c04292aa15f91ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657620"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="44fda-103">ICorProfilerCallback::ExceptionOSHandlerEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="44fda-103">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>

<span data-ttu-id="44fda-104">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="44fda-104">Not implemented.</span></span> <span data-ttu-id="44fda-105">アンマネージ例外情報を必要とするプロファイラーは、他の方法でこの情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="44fda-105">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44fda-106">構文</span><span class="sxs-lookup"><span data-stu-id="44fda-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="44fda-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="44fda-107">Requirements</span></span>  

 <span data-ttu-id="44fda-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44fda-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44fda-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="44fda-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44fda-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44fda-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44fda-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44fda-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44fda-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="44fda-112">See also</span></span>

- [<span data-ttu-id="44fda-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44fda-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
