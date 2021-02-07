---
description: '詳細について: ICorProfilerInfo:: GetThreadInfo メソッド'
title: ICorProfilerInfo::GetThreadInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
ms.openlocfilehash: 5514b1c4860067a07bf922e9d9a8bfab8c05e218
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760551"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="c75c7-103">ICorProfilerInfo::GetThreadInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="c75c7-103">ICorProfilerInfo::GetThreadInfo Method</span></span>

<span data-ttu-id="c75c7-104">指定したスレッドの現在の Win32 スレッド id を取得します。</span><span class="sxs-lookup"><span data-stu-id="c75c7-104">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c75c7-105">構文</span><span class="sxs-lookup"><span data-stu-id="c75c7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c75c7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c75c7-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="c75c7-107">から現在の Win32 ID を取得するスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="c75c7-107">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="c75c7-108">入出力指定したスレッドの現在の Win32 スレッド ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c75c7-108">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c75c7-109">要件</span><span class="sxs-lookup"><span data-stu-id="c75c7-109">Requirements</span></span>  

 <span data-ttu-id="c75c7-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c75c7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c75c7-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c75c7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c75c7-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c75c7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c75c7-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c75c7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75c7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c75c7-114">See also</span></span>

- [<span data-ttu-id="c75c7-115">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c75c7-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
