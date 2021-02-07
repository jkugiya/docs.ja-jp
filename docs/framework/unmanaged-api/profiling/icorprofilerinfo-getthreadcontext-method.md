---
description: '詳細について: ICorProfilerInfo:: GetThreadContext メソッド'
title: ICorProfilerInfo::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: b2970da90250819cc68eee55b70188d4830113a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687273"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="3733f-103">ICorProfilerInfo::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="3733f-103">ICorProfilerInfo::GetThreadContext Method</span></span>

<span data-ttu-id="3733f-104">指定したスレッドに現在関連付けられているコンテキスト id を取得します。</span><span class="sxs-lookup"><span data-stu-id="3733f-104">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3733f-105">構文</span><span class="sxs-lookup"><span data-stu-id="3733f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3733f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3733f-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="3733f-107">からスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="3733f-107">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="3733f-108">入出力指定されたスレッドに現在関連付けられているコンテキスト ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3733f-108">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="3733f-109">スレッドに現在関連付けられているコンテキストがない場合、この関数は CORPROF_E_DATAINCOMPLETE を返します。</span><span class="sxs-lookup"><span data-stu-id="3733f-109">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3733f-110">要件</span><span class="sxs-lookup"><span data-stu-id="3733f-110">Requirements</span></span>  

 <span data-ttu-id="3733f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3733f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3733f-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3733f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3733f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3733f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3733f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3733f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3733f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3733f-115">See also</span></span>

- [<span data-ttu-id="3733f-116">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3733f-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
