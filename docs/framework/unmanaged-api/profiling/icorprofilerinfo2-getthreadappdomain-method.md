---
description: '詳細について: ICorProfilerInfo2:: GetThreadAppDomain メソッド'
title: ICorProfilerInfo2::GetThreadAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: b480388254a6ee84db9f6c3e8d44b7358246502a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647064"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="f6e83-103">ICorProfilerInfo2::GetThreadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="f6e83-103">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>

<span data-ttu-id="f6e83-104">指定したスレッドが現在コードを実行しているアプリケーションドメインの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="f6e83-104">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e83-105">構文</span><span class="sxs-lookup"><span data-stu-id="f6e83-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6e83-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f6e83-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="f6e83-107">からスレッドを指定する ID。</span><span class="sxs-lookup"><span data-stu-id="f6e83-107">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="f6e83-108">入出力アプリケーションドメインの ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f6e83-108">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6e83-109">要件</span><span class="sxs-lookup"><span data-stu-id="f6e83-109">Requirements</span></span>  

 <span data-ttu-id="f6e83-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6e83-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6e83-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f6e83-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6e83-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6e83-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6e83-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6e83-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6e83-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6e83-114">See also</span></span>

- [<span data-ttu-id="f6e83-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6e83-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f6e83-116">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f6e83-116">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
