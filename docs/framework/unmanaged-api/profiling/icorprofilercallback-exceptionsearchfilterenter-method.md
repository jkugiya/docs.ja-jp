---
description: '詳細について: ICorProfilerCallback:: ExceptionSearchFilterEnter メソッド'
title: ICorProfilerCallback::ExceptionSearchFilterEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
ms.openlocfilehash: ca0eb80f57d7c00d0abfab1bb602650c951a30e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745365"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="c0c8e-103">ICorProfilerCallback::ExceptionSearchFilterEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="c0c8e-103">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>

<span data-ttu-id="c0c8e-104">例外処理の検索フェーズがユーザー定義の例外フィルターの実行を開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c0c8e-104">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0c8e-105">構文</span><span class="sxs-lookup"><span data-stu-id="c0c8e-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0c8e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c0c8e-106">Parameters</span></span>

- `functionId`

  <span data-ttu-id="c0c8e-107">\[in] フィルターを含む関数の ID。</span><span class="sxs-lookup"><span data-stu-id="c0c8e-107">\[in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="c0c8e-108">要件</span><span class="sxs-lookup"><span data-stu-id="c0c8e-108">Requirements</span></span>  

 <span data-ttu-id="c0c8e-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0c8e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0c8e-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0c8e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0c8e-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0c8e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0c8e-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0c8e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0c8e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0c8e-113">See also</span></span>

- [<span data-ttu-id="c0c8e-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0c8e-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c0c8e-115">ExceptionSearchFilterLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="c0c8e-115">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
