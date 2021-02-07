---
description: '詳細について: ICorProfilerCallback:: JITInlining メソッド'
title: ICorProfilerCallback::JITInlining メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 2bd6c48180b9484ef90b6afb505c8171aff57aa4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705643"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="2192a-103">ICorProfilerCallback::JITInlining メソッド</span><span class="sxs-lookup"><span data-stu-id="2192a-103">ICorProfilerCallback::JITInlining Method</span></span>

<span data-ttu-id="2192a-104">Just-in-time (JIT) コンパイラが、別の関数と共に関数を挿入しようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2192a-104">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2192a-105">構文</span><span class="sxs-lookup"><span data-stu-id="2192a-105">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2192a-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2192a-106">Parameters</span></span>  

 `callerId`  
 <span data-ttu-id="2192a-107">から関数が挿入される関数の ID `calleeId` 。</span><span class="sxs-lookup"><span data-stu-id="2192a-107">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="2192a-108">から挿入する関数の ID。</span><span class="sxs-lookup"><span data-stu-id="2192a-108">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="2192a-109">[出力] `true` 挿入の実行を許可する場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="2192a-109">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2192a-110">解説</span><span class="sxs-lookup"><span data-stu-id="2192a-110">Remarks</span></span>  

 <span data-ttu-id="2192a-111">プロファイラーでをに設定すると、関数が `pfShouldInline` `false` `calleeId` 関数に挿入されないようにすることができ `callerId` ます。</span><span class="sxs-lookup"><span data-stu-id="2192a-111">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="2192a-112">また、プロファイラーは、 [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) 列挙体の COR_PRF_DISABLE_INLINING 値を使用して、インライン挿入をグローバルに無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="2192a-112">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="2192a-113">インラインで挿入された関数は、入力または終了するためのイベントを発生させません。</span><span class="sxs-lookup"><span data-stu-id="2192a-113">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="2192a-114">したがって、 `pfShouldInline` 正確なコールグラフを生成するためには、プロファイラーをに設定する必要があり `false` ます。</span><span class="sxs-lookup"><span data-stu-id="2192a-114">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="2192a-115">`pfShouldInline`をに設定する `false` と、パフォーマンスに影響します。インライン挿入では通常、速度が向上し、挿入されたメソッドの個別の JIT コンパイルイベントの数が減少するためです。</span><span class="sxs-lookup"><span data-stu-id="2192a-115">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2192a-116">要件</span><span class="sxs-lookup"><span data-stu-id="2192a-116">Requirements</span></span>  

 <span data-ttu-id="2192a-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2192a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2192a-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2192a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2192a-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2192a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2192a-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2192a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2192a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="2192a-121">See also</span></span>

- [<span data-ttu-id="2192a-122">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2192a-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
