---
description: '詳細について: ICorDebugEval2:: による Deabort メソッド'
title: ICorDebugEval2::RudeAbort メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
ms.openlocfilehash: 2835fd635da007b5ee3f0e642b77f3954945f168
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693513"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="2e9bc-103">ICorDebugEval2::RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="2e9bc-103">ICorDebugEval2::RudeAbort Method</span></span>

<span data-ttu-id="2e9bc-104">このが現在実行している計算を中止し `ICorDebugEval2` ます。</span><span class="sxs-lookup"><span data-stu-id="2e9bc-104">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e9bc-105">構文</span><span class="sxs-lookup"><span data-stu-id="2e9bc-105">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2e9bc-106">解説</span><span class="sxs-lookup"><span data-stu-id="2e9bc-106">Remarks</span></span>  

 <span data-ttu-id="2e9bc-107">`RudeAbort` は、エバリュエーターによって保持されているロックを解放しないため、デバッグセッションは安全ではない状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="2e9bc-107">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="2e9bc-108">このメソッドは細心の注意を払って呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="2e9bc-108">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e9bc-109">要件</span><span class="sxs-lookup"><span data-stu-id="2e9bc-109">Requirements</span></span>  

 <span data-ttu-id="2e9bc-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e9bc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e9bc-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e9bc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e9bc-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e9bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e9bc-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e9bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
