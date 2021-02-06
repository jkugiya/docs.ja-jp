---
description: '詳細について: ICorProfilerCallback:: ExceptionOSHandlerLeave メソッド'
title: ICorProfilerCallback::ExceptionOSHandlerLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: 809f9440510bc0b55c9cae9827757eb61e61b257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657568"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="a1069-103">ICorProfilerCallback::ExceptionOSHandlerLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="a1069-103">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>

<span data-ttu-id="a1069-104">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="a1069-104">Not implemented.</span></span> <span data-ttu-id="a1069-105">アンマネージ例外情報を必要とするプロファイラーは、他の方法でこの情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1069-105">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1069-106">構文</span><span class="sxs-lookup"><span data-stu-id="a1069-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a1069-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="a1069-107">Requirements</span></span>  

 <span data-ttu-id="a1069-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1069-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1069-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1069-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1069-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1069-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1069-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1069-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1069-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1069-112">See also</span></span>

- [<span data-ttu-id="a1069-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1069-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
