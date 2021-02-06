---
description: '詳細について: ICorProfilerInfo:: GetCurrentThreadID メソッド'
title: ICorProfilerInfo::GetCurrentThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: 562c6cb61f13e9ab568d18c7d179872cbc7cdb06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647643"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="5c17c-103">ICorProfilerInfo::GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="5c17c-103">ICorProfilerInfo::GetCurrentThreadID Method</span></span>

<span data-ttu-id="5c17c-104">マネージスレッドの場合、現在のスレッドの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="5c17c-104">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c17c-105">構文</span><span class="sxs-lookup"><span data-stu-id="5c17c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c17c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c17c-106">Parameters</span></span>  

 `pThreadId`  
 <span data-ttu-id="5c17c-107">入出力返されたマネージスレッドの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5c17c-107">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c17c-108">解説</span><span class="sxs-lookup"><span data-stu-id="5c17c-108">Remarks</span></span>  

 <span data-ttu-id="5c17c-109">現在のスレッドが内部ランタイムスレッドまたはその他のアンマネージスレッドである場合、は `GetCurrentThreadID` CORPROF_E_NOT_MANAGED_THREAD を HRESULT として返し、パラメーターの戻り値は null になり `pThreadId` ます。</span><span class="sxs-lookup"><span data-stu-id="5c17c-109">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c17c-110">要件</span><span class="sxs-lookup"><span data-stu-id="5c17c-110">Requirements</span></span>  

 <span data-ttu-id="5c17c-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5c17c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c17c-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c17c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c17c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c17c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c17c-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c17c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c17c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c17c-115">See also</span></span>

- [<span data-ttu-id="5c17c-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c17c-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
