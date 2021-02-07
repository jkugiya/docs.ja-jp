---
description: '詳細については、次の情報を参照してください:: HasQueuedCallbacks メソッド'
title: ICorDebugController::HasQueuedCallbacks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: bdc22831b912d3bad565b6abf5c73591d07ffe11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764649"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="453be-103">ICorDebugController::HasQueuedCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="453be-103">ICorDebugController::HasQueuedCallbacks Method</span></span>

<span data-ttu-id="453be-104">マネージコールバックが、指定されたスレッドに対して現在キューに登録されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="453be-104">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="453be-105">構文</span><span class="sxs-lookup"><span data-stu-id="453be-105">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="453be-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="453be-106">Parameters</span></span>  

 `pThread`  
 <span data-ttu-id="453be-107">からスレッドを表す "ツールスレッド" オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="453be-107">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="453be-108">入出力 `true` マネージコールバックが、指定されたスレッドに対して現在キューに格納されている場合は、その値を指すポインター。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="453be-108">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="453be-109">パラメーターに null が指定されている場合 `pThread` 、 `HasQueuedCallbacks` は、 `true` 現在マネージコールバックが任意のスレッドに対してキューに置かれている場合、を返します。</span><span class="sxs-lookup"><span data-stu-id="453be-109">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="453be-110">解説</span><span class="sxs-lookup"><span data-stu-id="453be-110">Remarks</span></span>  

 <span data-ttu-id="453be-111">コールバックは [、次の](icordebugcontroller-continue-method.md) ように表示されるたびに1つずつディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="453be-111">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="453be-112">デバッガーでは、同時に発生する複数のデバッグイベントを報告する場合に、このフラグをチェックできます。</span><span class="sxs-lookup"><span data-stu-id="453be-112">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="453be-113">デバッグイベントがキューに登録されている場合は、既に発生しているため、デバッガーはキュー全体をドレインして、デバッグ対象の状態を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="453be-113">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="453be-114">( `ICorDebugController::Continue` を呼び出してキューをドレインします)。たとえば、キューにスレッド *x* の2つのデバッグイベントが含まれており、デバッガーが最初のデバッグイベントの後にスレッド *x* を中断した後にを呼び出すと、スレッド `ICorDebugController::Continue` が中断されていても、スレッド *x* の2番目のデバッグイベントがディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="453be-114">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="453be-115">要件</span><span class="sxs-lookup"><span data-stu-id="453be-115">Requirements</span></span>  

 <span data-ttu-id="453be-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="453be-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="453be-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="453be-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="453be-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="453be-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="453be-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="453be-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="453be-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="453be-120">See also</span></span>
