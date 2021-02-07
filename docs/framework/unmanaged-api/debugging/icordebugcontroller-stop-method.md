---
description: '詳細については、次のページを参照してください: いいね:: Stop メソッド'
title: ICorDebugController::Stop メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
ms.openlocfilehash: 613fd81a03114580ae3d826a94d855023895b694
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764607"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="9252b-103">ICorDebugController::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="9252b-103">ICorDebugController::Stop Method</span></span>

<span data-ttu-id="9252b-104">プロセスでマネージコードを実行しているすべてのスレッドで協調停止を実行します。</span><span class="sxs-lookup"><span data-stu-id="9252b-104">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9252b-105">構文</span><span class="sxs-lookup"><span data-stu-id="9252b-105">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9252b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9252b-106">Parameters</span></span>  

 `dwTimeoutIgnored`  
 <span data-ttu-id="9252b-107">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="9252b-107">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9252b-108">解説</span><span class="sxs-lookup"><span data-stu-id="9252b-108">Remarks</span></span>  

 <span data-ttu-id="9252b-109">`Stop` プロセスでマネージコードを実行しているすべてのスレッドで協調停止を実行します。</span><span class="sxs-lookup"><span data-stu-id="9252b-109">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="9252b-110">マネージ専用のデバッグセッションでは、アンマネージスレッドは引き続き実行できます (ただし、マネージコードを呼び出そうとするとブロックされます)。</span><span class="sxs-lookup"><span data-stu-id="9252b-110">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="9252b-111">相互運用機能デバッグセッションでは、アンマネージスレッドも停止します。</span><span class="sxs-lookup"><span data-stu-id="9252b-111">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="9252b-112">現在、この `dwTimeoutIgnored` 値は無視され、無限 (-1) として扱われます。</span><span class="sxs-lookup"><span data-stu-id="9252b-112">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="9252b-113">デッドロックが原因で協調停止が失敗した場合、すべてのスレッドが中断され、E_TIMEOUT が返されます。</span><span class="sxs-lookup"><span data-stu-id="9252b-113">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9252b-114">`Stop` は、デバッグ API の唯一の同期メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9252b-114">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="9252b-115">`Stop`が S_OK を返した場合、プロセスは停止されます。</span><span class="sxs-lookup"><span data-stu-id="9252b-115">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="9252b-116">リスナーに停止を通知するためのコールバックが付与されていません。</span><span class="sxs-lookup"><span data-stu-id="9252b-116">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="9252b-117">デバッガーは、このプロセスを再開できるようにするために、を [実行](icordebugcontroller-continue-method.md) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9252b-117">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="9252b-118">デバッガーは停止カウンターを保持します。</span><span class="sxs-lookup"><span data-stu-id="9252b-118">The debugger maintains a stop counter.</span></span> <span data-ttu-id="9252b-119">カウンターが0になると、コントローラーが再開されます。</span><span class="sxs-lookup"><span data-stu-id="9252b-119">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="9252b-120">`Stop`またはディスパッチされた各コールバックの各呼び出しは、カウンターをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="9252b-120">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="9252b-121">を呼び出すたびに `ICorDebugController::Continue` カウンターがデクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="9252b-121">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9252b-122">要件</span><span class="sxs-lookup"><span data-stu-id="9252b-122">Requirements</span></span>  

 <span data-ttu-id="9252b-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9252b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9252b-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9252b-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9252b-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9252b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9252b-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9252b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9252b-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="9252b-127">See also</span></span>
