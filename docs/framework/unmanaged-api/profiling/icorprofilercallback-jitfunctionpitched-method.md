---
description: '詳細について: ICorProfilerCallback:: JITFunctionPitched メソッド'
title: ICorProfilerCallback::JITFunctionPitched メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 11729de2188fe2f2cec7ec16ff7a5d1928cbd75d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705721"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="24390-103">ICorProfilerCallback::JITFunctionPitched メソッド</span><span class="sxs-lookup"><span data-stu-id="24390-103">ICorProfilerCallback::JITFunctionPitched Method</span></span>

<span data-ttu-id="24390-104">Just-in-time (JIT) でコンパイルされた関数がメモリから削除されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="24390-104">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24390-105">構文</span><span class="sxs-lookup"><span data-stu-id="24390-105">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24390-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24390-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="24390-107">から削除された関数の ID。</span><span class="sxs-lookup"><span data-stu-id="24390-107">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24390-108">解説</span><span class="sxs-lookup"><span data-stu-id="24390-108">Remarks</span></span>  

 <span data-ttu-id="24390-109">削除された関数が呼び出されると、関数が再コンパイルされると、プロファイラーは新しい JIT コンパイルイベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="24390-109">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="24390-110">現在、共通言語ランタイム (CLR) の JIT コンパイラでは、メモリから関数が削除されないため、このコールバックは現在使用されていないため、プロファイラーによって受信されません。</span><span class="sxs-lookup"><span data-stu-id="24390-110">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="24390-111">の値 `functionId` は、関数が再コンパイルされるまで有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="24390-111">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="24390-112">関数を再コンパイルすると、同じ `functionId` 値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="24390-112">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24390-113">要件</span><span class="sxs-lookup"><span data-stu-id="24390-113">Requirements</span></span>  

 <span data-ttu-id="24390-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24390-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24390-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24390-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24390-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24390-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24390-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24390-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24390-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="24390-118">See also</span></span>

- [<span data-ttu-id="24390-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24390-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
