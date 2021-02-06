---
description: '詳細情報: FunctionIDMapper2 関数'
title: FunctionIDMapper2 関数
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: 1fd6680ffaa7b28e679dc3eaeb9840981ead5c45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648572"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="21a38-103">FunctionIDMapper2 関数</span><span class="sxs-lookup"><span data-stu-id="21a38-103">FunctionIDMapper2 Function</span></span>

<span data-ttu-id="21a38-104">指定された関数の識別子が、その関数の [FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、 [FunctionTailcall3](functiontailcall3-function.md)、または[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)、および [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) コールバックで使用される代替 ID に再マップされる可能性があることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="21a38-104">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="21a38-105">また `FunctionIDMapper2` により、プロファイラーはその関数のコールバックを受信するかどうかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="21a38-105">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a38-106">構文</span><span class="sxs-lookup"><span data-stu-id="21a38-106">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21a38-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="21a38-107">Parameters</span></span>

- `funcId`

  <span data-ttu-id="21a38-108">\[in) 再マップする関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="21a38-108">\[in] The function identifier to be remapped.</span></span>

- `clientData`

  <span data-ttu-id="21a38-109">\[では、ランタイム間を明確に区別するために使用されるデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="21a38-109">\[in] A pointer to data that is used to disambiguate among runtimes.</span></span>

- `pbHookFunction`

  <span data-ttu-id="21a38-110">\[out] プロファイラーが、、、、、、、の各コールバックを受信する場合は、に設定する値へのポインター `true` `FunctionEnter3` `FunctionLeave3` `FunctionTailcall3` `FunctionEnter3WithInfo` `FunctionLeave3WithInfo` `FunctionTailcall3WithInfo` 。それ以外の場合は、この値をに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="21a38-110">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="21a38-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="21a38-111">Return Value</span></span>  

 <span data-ttu-id="21a38-112">プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。</span><span class="sxs-lookup"><span data-stu-id="21a38-112">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="21a38-113">`false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="21a38-113">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="21a38-114">これ以外の状況で戻り値を null にすると、プロセスの中止など、予測できない結果が発生します。</span><span class="sxs-lookup"><span data-stu-id="21a38-114">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21a38-115">解説</span><span class="sxs-lookup"><span data-stu-id="21a38-115">Remarks</span></span>  

 <span data-ttu-id="21a38-116">このメソッドは、クライアントデータを渡すために使用される追加のパラメーターを使用して [Functionidmapper](functionidmapper-function.md) 関数を拡張します。</span><span class="sxs-lookup"><span data-stu-id="21a38-116">This method extends the [FunctionIDMapper](functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="21a38-117">クライアント データを使用すると、ランタイム間のあいまいさが解消されます。</span><span class="sxs-lookup"><span data-stu-id="21a38-117">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a38-118">要件</span><span class="sxs-lookup"><span data-stu-id="21a38-118">Requirements</span></span>  

 <span data-ttu-id="21a38-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21a38-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a38-120">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="21a38-120">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="21a38-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21a38-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21a38-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21a38-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a38-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="21a38-123">See also</span></span>

- [<span data-ttu-id="21a38-124">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="21a38-124">ICorProfilerInfo::SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="21a38-125">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="21a38-125">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="21a38-126">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="21a38-126">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="21a38-127">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="21a38-127">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="21a38-128">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="21a38-128">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="21a38-129">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="21a38-129">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="21a38-130">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="21a38-130">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="21a38-131">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="21a38-131">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="21a38-132">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="21a38-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
