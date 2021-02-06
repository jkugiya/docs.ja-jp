---
description: '詳細について: ICorProfilerInfo:: SetFunctionIDMapper メソッド'
title: ICorProfilerInfo::SetFunctionIDMapper メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: c03c225db3b4126c3ac46ef6e5d36a5f72e529f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647207"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="545eb-103">ICorProfilerInfo::SetFunctionIDMapper メソッド</span><span class="sxs-lookup"><span data-stu-id="545eb-103">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>

<span data-ttu-id="545eb-104">`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。</span><span class="sxs-lookup"><span data-stu-id="545eb-104">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545eb-105">構文</span><span class="sxs-lookup"><span data-stu-id="545eb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="545eb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="545eb-106">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="545eb-107">から値を代替値にマップするために呼び出される [Functionidmapper](functionidmapper-function.md) 実装へのポインター `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="545eb-107">[in] A pointer to the [FunctionIDMapper](functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="545eb-108">解説</span><span class="sxs-lookup"><span data-stu-id="545eb-108">Remarks</span></span>  

 <span data-ttu-id="545eb-109">値の代替手段は、 `FunctionID` [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)メソッドによって指定されたプロファイラーの関数の開始/終了フック ([FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)、および[FunctionTailcall2](functiontailcall2-function.md)) に渡されます。</span><span class="sxs-lookup"><span data-stu-id="545eb-109">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="545eb-110">は `FunctionIDMapper` 一度だけ設定でき、 [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) コールバックで設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="545eb-110">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="545eb-111">要件</span><span class="sxs-lookup"><span data-stu-id="545eb-111">Requirements</span></span>  

 <span data-ttu-id="545eb-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="545eb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="545eb-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="545eb-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="545eb-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="545eb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="545eb-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="545eb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="545eb-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="545eb-116">See also</span></span>

- [<span data-ttu-id="545eb-117">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="545eb-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
