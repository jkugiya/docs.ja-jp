---
description: '詳細について: ICorDebugUnmanagedCallback::D Eバグイベントメソッド'
title: ICorDebugUnmanagedCallback::DebugEvent メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
ms.openlocfilehash: fcd7bc3b380add7465473cb01585eb1656d00aad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690575"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="11875-103">ICorDebugUnmanagedCallback::DebugEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="11875-103">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>

<span data-ttu-id="11875-104">ネイティブイベントが発生したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="11875-104">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11875-105">構文</span><span class="sxs-lookup"><span data-stu-id="11875-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11875-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11875-106">Parameters</span></span>  

 `pDebugEvent`  
 <span data-ttu-id="11875-107">からネイティブイベントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="11875-107">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="11875-108">[in] `true` 、アンマネージイベントが発生した後にマネージプロセス状態との相互作用が不可能な場合は、デバッガーが "を実行しています [:: Continue](icordebugcontroller-continue-method.md)" を呼び出す場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="11875-108">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11875-109">解説</span><span class="sxs-lookup"><span data-stu-id="11875-109">Remarks</span></span>  

 <span data-ttu-id="11875-110">デバッグ中のスレッドが Win32 スレッドである場合は、Win32 デバッグインターフェイスのメンバーを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="11875-110">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="11875-111">を呼び出すことができるのは、 `ICorDebugController::Continue` Win32 スレッドだけで、帯域外のイベントを継続している場合のみです。</span><span class="sxs-lookup"><span data-stu-id="11875-111">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="11875-112">コールバックは、コールバック `DebugEvent` の標準規則に従っていません。</span><span class="sxs-lookup"><span data-stu-id="11875-112">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="11875-113">を呼び出すと、プロセスは、" `DebugEvent` 生の OS-デバッグが停止しました" 状態になります。</span><span class="sxs-lookup"><span data-stu-id="11875-113">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="11875-114">プロセスは同期されません。</span><span class="sxs-lookup"><span data-stu-id="11875-114">The process will not be synchronized.</span></span> <span data-ttu-id="11875-115">マネージコードに関する情報の要求を満たすために、必要に応じて自動的に同期された状態になります。これにより、他の入れ子になったコールバックが発生する可能性があり `DebugEvent` ます。</span><span class="sxs-lookup"><span data-stu-id="11875-115">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="11875-116">プロセス [を続行](icordebugprocess-clearcurrentexception-method.md) する前に例外イベントを無視するには、プロセスでを実行します。</span><span class="sxs-lookup"><span data-stu-id="11875-116">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="11875-117">このメソッドを呼び出すと、CONTINUE 要求で DBG_EXCEPTION_NOT_HANDLED ではなく DBG_CONTINUE が送信され、帯域外のブレークポイントとシングルステップの例外が自動的にクリアされます。</span><span class="sxs-lookup"><span data-stu-id="11875-117">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="11875-118">帯域外イベントは、デバッグ中のアプリケーションが停止した場合や、未処理の帯域内イベントが既に存在する場合でも、いつでも発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11875-118">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="11875-119">.NET Framework バージョン2.0 では、デバッガーはすぐに帯域外のブレークポイントイベントを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11875-119">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="11875-120">デバッガーでは、 [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) メソッドと [ICorDebugProcess2:: ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) メソッドを使用して、ブレークポイントの追加と削除を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="11875-120">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="11875-121">これらのメソッドは、帯域外のブレークポイントを自動的にスキップします。</span><span class="sxs-lookup"><span data-stu-id="11875-121">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="11875-122">したがって、ディスパッチされるアウトオブバンドブレークポイントは、Win32 関数の呼び出しなど、命令ストリームに既に存在する未加工のブレークポイントである必要があり `DebugBreak` ます。</span><span class="sxs-lookup"><span data-stu-id="11875-122">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="11875-123">を使用しないでください `ICorDebugProcess::ClearCurrentException` 。これは、[デバッグ API](index.md)の他のメンバーである、テキスト[処理:: getthreadcontext](icordebugprocess-getthreadcontext-method.md)、テキスト[処理:: setthreadcontext](icordebugprocess-setthreadcontext-method.md)、またはその他のメンバーを使用します。</span><span class="sxs-lookup"><span data-stu-id="11875-123">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11875-124">要件</span><span class="sxs-lookup"><span data-stu-id="11875-124">Requirements</span></span>  

 <span data-ttu-id="11875-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11875-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11875-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11875-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11875-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11875-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11875-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11875-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11875-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="11875-129">See also</span></span>

- [<span data-ttu-id="11875-130">ICorDebugUnmanagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11875-130">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
