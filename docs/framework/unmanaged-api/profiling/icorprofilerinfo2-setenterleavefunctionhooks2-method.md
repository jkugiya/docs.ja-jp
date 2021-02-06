---
description: '詳細について: ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 メソッド'
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 34f292d9bec4bcd334f824f7e3e1fd127331ba33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646973"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a><span data-ttu-id="f40bf-103">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="f40bf-103">ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 Method</span></span>

<span data-ttu-id="f40bf-104">マネージ関数の "enter"、"leave"、および "tailcall" の各フックの更新バージョンで呼び出されるプロファイラー実装関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="f40bf-104">Specifies profiler-implemented functions to be called on the updated versions of the "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f40bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="f40bf-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f40bf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f40bf-106">Parameters</span></span>  

 `pFuncEnter`  
 <span data-ttu-id="f40bf-107">から [FunctionEnter2](functionenter2-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f40bf-107">[in] A pointer to the implementation to be used as the [FunctionEnter2](functionenter2-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="f40bf-108">から [FunctionLeave2](functionleave2-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f40bf-108">[in] A pointer to the implementation to be used as the [FunctionLeave2](functionleave2-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="f40bf-109">から [FunctionTailcall2](functiontailcall2-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f40bf-109">[in] A pointer to the implementation to be used as the [FunctionTailcall2](functiontailcall2-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f40bf-110">解説</span><span class="sxs-lookup"><span data-stu-id="f40bf-110">Remarks</span></span>  

 <span data-ttu-id="f40bf-111">`SetEnterLeaveFunctionHooks2`メソッドは、 [ICorProfilerInfo:: SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md)メソッドに似ています。</span><span class="sxs-lookup"><span data-stu-id="f40bf-111">The `SetEnterLeaveFunctionHooks2` method is similar to the [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) method.</span></span> <span data-ttu-id="f40bf-112">前者を使用して、enter/leave/tailcall コールバックの新しいバージョンとして使用する関数を指定します。後者の場合は、以前のバージョンの enter/leave/tailcall コールバックとして使用する関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="f40bf-112">Use the former to specify functions to be used as the newer versions of the enter/leave/tailcall callbacks, and the latter to specify functions to be used as the older versions of the enter/leave/tailcall callbacks.</span></span>  
  
 <span data-ttu-id="f40bf-113">コールバックのセットは一度に1つしかアクティブにできません。</span><span class="sxs-lookup"><span data-stu-id="f40bf-113">Only one set of callbacks may be active at a time.</span></span> <span data-ttu-id="f40bf-114">したがって、プロファイラーがとの両方を呼び出す `ICorProfilerInfo::SetEnterLeaveFunctionHooks` と `SetEnterLeaveFunctionHooks2` 、 `SetEnterLeaveFunctionHooks2` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f40bf-114">Thus, if a profiler calls both `ICorProfilerInfo::SetEnterLeaveFunctionHooks` and `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` is used.</span></span>  
  
 <span data-ttu-id="f40bf-115">メソッドは、 `SetEnterLeaveFunctionHooks2` プロファイラーの [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) コールバックからのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f40bf-115">The `SetEnterLeaveFunctionHooks2` method may be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f40bf-116">要件</span><span class="sxs-lookup"><span data-stu-id="f40bf-116">Requirements</span></span>  

 <span data-ttu-id="f40bf-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f40bf-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f40bf-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f40bf-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f40bf-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f40bf-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f40bf-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f40bf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40bf-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f40bf-121">See also</span></span>

- [<span data-ttu-id="f40bf-122">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f40bf-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f40bf-123">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f40bf-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
