---
description: '詳細について: ICorDebugFunction3:: GetActiveReJitRequestILCode メソッド'
title: ICorDebugFunction3::GetActiveReJitRequestILCode メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 9225c5cdf97395b7e1b11c61d653cab8d52031c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692122"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="0377e-103">ICorDebugFunction3::GetActiveReJitRequestILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="0377e-103">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>

<span data-ttu-id="0377e-104">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="0377e-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0377e-105">アクティブな ReJIT 要求から IL を含む、 [コード](icordebugilcode-interface.md) へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0377e-105">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0377e-106">構文</span><span class="sxs-lookup"><span data-stu-id="0377e-106">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0377e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0377e-107">Parameters</span></span>  

 `ppReJitedILCode`  
 <span data-ttu-id="0377e-108">アクティブな ReJIT 要求からの、IL へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0377e-108">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0377e-109">解説</span><span class="sxs-lookup"><span data-stu-id="0377e-109">Remarks</span></span>  

 <span data-ttu-id="0377e-110">この `ICorDebugFunction3` オブジェクトによって表示されるメソッドがアクティブな ReJIT 要求を持っている場合、`ppReJitedILCode` は IL へのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="0377e-110">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="0377e-111">一般的なケースであるアクティブな要求がない場合、 `ppReJitedILCode` は **null** になります。</span><span class="sxs-lookup"><span data-stu-id="0377e-111">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="0377e-112">ReJIT 要求は、 [ICorProfilerCallback4:: GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) メソッドの呼び出しから実行が戻った直後にアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="0377e-112">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="0377e-113">これは、まだ JIT コンパイルされていない可能性があり、スレッドはコードの元のバージョンで実行中の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0377e-113">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="0377e-114">ReJIT 要求は、 [ICorProfilerInfo4:: RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) メソッドへのプロファイラーの呼び出し中に非アクティブになります。</span><span class="sxs-lookup"><span data-stu-id="0377e-114">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="0377e-115">LI が戻された後であっても、スレッドは JIT 再コンパイル (ReJIT) されたコードで実行中の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0377e-115">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0377e-116">要件</span><span class="sxs-lookup"><span data-stu-id="0377e-116">Requirements</span></span>  

 <span data-ttu-id="0377e-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0377e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0377e-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0377e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0377e-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0377e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0377e-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0377e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0377e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0377e-121">See also</span></span>

- [<span data-ttu-id="0377e-122">ICorDebugFunction3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0377e-122">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="0377e-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0377e-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0377e-124">ReJIT: How-To ガイド</span><span class="sxs-lookup"><span data-stu-id="0377e-124">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
