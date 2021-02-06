---
description: '詳細について: ICorProfilerInfo:: GetHandleFromThread メソッド'
title: ICorProfilerInfo::GetHandleFromThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: 541a2872bc3cbbe8233e09283b9773957b0a7daf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647543"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="9bbaf-103">ICorProfilerInfo::GetHandleFromThread メソッド</span><span class="sxs-lookup"><span data-stu-id="9bbaf-103">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="9bbaf-104">スレッドの ID を Win32 スレッドハンドルにマップします。</span><span class="sxs-lookup"><span data-stu-id="9bbaf-104">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bbaf-105">構文</span><span class="sxs-lookup"><span data-stu-id="9bbaf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9bbaf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9bbaf-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="9bbaf-107">から割り当てられるスレッド ID。</span><span class="sxs-lookup"><span data-stu-id="9bbaf-107">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="9bbaf-108">入出力Win32 スレッドハンドルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9bbaf-108">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bbaf-109">解説</span><span class="sxs-lookup"><span data-stu-id="9bbaf-109">Remarks</span></span>  

 <span data-ttu-id="9bbaf-110">プロファイラーは、 `DuplicateHandle` 使用する前にハンドルで Win32 関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bbaf-110">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  

 <span data-ttu-id="9bbaf-111">このメソッドから返されたハンドルはランタイムによって所有されており、プロファイラーはそれを閉じることはできません。</span><span class="sxs-lookup"><span data-stu-id="9bbaf-111">The handle returned from this method is owned by the runtime and the profiler should never close it.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="9bbaf-112">要件</span><span class="sxs-lookup"><span data-stu-id="9bbaf-112">Requirements</span></span>  

 <span data-ttu-id="9bbaf-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bbaf-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bbaf-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9bbaf-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9bbaf-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9bbaf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bbaf-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bbaf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bbaf-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bbaf-117">See also</span></span>

- [<span data-ttu-id="9bbaf-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9bbaf-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
