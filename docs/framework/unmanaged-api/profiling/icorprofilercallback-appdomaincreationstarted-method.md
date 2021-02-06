---
description: '詳細について: ICorProfilerCallback:: AppDomainCreationStarted メソッド'
title: ICorProfilerCallback::AppDomainCreationStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: 00ebbe35f6f4446caeee5ebcd56b853d6e6dc80c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648257"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="234b6-103">ICorProfilerCallback::AppDomainCreationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="234b6-103">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>

<span data-ttu-id="234b6-104">アプリケーションドメインが作成中であることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="234b6-104">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="234b6-105">構文</span><span class="sxs-lookup"><span data-stu-id="234b6-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="234b6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="234b6-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="234b6-107">\[in] 作成されるドメインを識別します。</span><span class="sxs-lookup"><span data-stu-id="234b6-107">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="234b6-108">解説</span><span class="sxs-lookup"><span data-stu-id="234b6-108">Remarks</span></span>  

 <span data-ttu-id="234b6-109">ID は、 [ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) メソッドが呼び出されるまで、情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="234b6-109">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="234b6-110">要件</span><span class="sxs-lookup"><span data-stu-id="234b6-110">Requirements</span></span>  

 <span data-ttu-id="234b6-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="234b6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="234b6-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="234b6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="234b6-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="234b6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="234b6-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="234b6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="234b6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="234b6-115">See also</span></span>

- [<span data-ttu-id="234b6-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="234b6-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
