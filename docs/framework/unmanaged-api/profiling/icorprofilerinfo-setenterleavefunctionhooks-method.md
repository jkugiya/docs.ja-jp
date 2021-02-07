---
description: '詳細について: ICorProfilerInfo:: SetEnterLeaveFunctionHooks メソッド'
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 45c161a76f3ae568da6a83a2c45acb214a327ff1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687208"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="be194-103">ICorProfilerInfo::SetEnterLeaveFunctionHooks メソッド</span><span class="sxs-lookup"><span data-stu-id="be194-103">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>

<span data-ttu-id="be194-104">マネージ関数の "enter"、"leave"、および "tailcall" フックで呼び出されるプロファイラー実装関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="be194-104">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be194-105">構文</span><span class="sxs-lookup"><span data-stu-id="be194-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be194-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be194-106">Parameters</span></span>  

 `pFuncEnter`  
 <span data-ttu-id="be194-107">から [Functionenter](functionenter-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="be194-107">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="be194-108">から [Functionleave](functionleave-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="be194-108">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="be194-109">から [FunctionTailcall](functiontailcall-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="be194-109">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be194-110">解説</span><span class="sxs-lookup"><span data-stu-id="be194-110">Remarks</span></span>  

 <span data-ttu-id="be194-111">.NET Framework バージョン1.0 では、対応するコールバックを無効にするために、各関数ポインターを null にすることができます。</span><span class="sxs-lookup"><span data-stu-id="be194-111">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="be194-112">一度にアクティブにできるコールバックのセットは1つだけです。</span><span class="sxs-lookup"><span data-stu-id="be194-112">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="be194-113">したがって、プロファイラーが `SetEnterLeaveFunctionHooks` と [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)の両方を呼び出すと、が `SetEnterLeaveFunctionHooks2` 優先されます。</span><span class="sxs-lookup"><span data-stu-id="be194-113">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="be194-114">`SetEnterLeaveFunctionHooks`メソッドを呼び出すことができるのは、プロファイラーの[ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)コールバックからだけです。</span><span class="sxs-lookup"><span data-stu-id="be194-114">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be194-115">要件</span><span class="sxs-lookup"><span data-stu-id="be194-115">Requirements</span></span>  

 <span data-ttu-id="be194-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be194-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be194-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="be194-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="be194-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be194-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be194-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be194-119">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be194-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="be194-120">See also</span></span>

- [<span data-ttu-id="be194-121">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be194-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
