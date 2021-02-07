---
description: '詳細情報: の説明'
title: ICorDebugManagedCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
ms.openlocfilehash: 0dd33e4295caa8f5ae41c65d9bd10152737156ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722816"
---
# <a name="icordebugmanagedcallback-interface"></a><span data-ttu-id="e8223-103">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8223-103">ICorDebugManagedCallback Interface</span></span>

<span data-ttu-id="e8223-104">デバッガーのコールバックを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e8223-104">Provides methods to process debugger callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8223-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-105">Methods</span></span>  
  
|<span data-ttu-id="e8223-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-106">Method</span></span>|<span data-ttu-id="e8223-107">説明</span><span class="sxs-lookup"><span data-stu-id="e8223-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8223-108">Break メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-108">Break Method</span></span>](icordebugmanagedcallback-break-method.md)|<span data-ttu-id="e8223-109"><xref:System.Reflection.Emit.OpCodes.Break>コードストリーム内の命令が実行されたときに、デバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-109">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>|  
|[<span data-ttu-id="e8223-110">Breakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-110">Breakpoint Method</span></span>](icordebugmanagedcallback-breakpoint-method.md)|<span data-ttu-id="e8223-111">ブレークポイントが検出されたときにデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-111">Notifies the debugger when a breakpoint is encountered.</span></span>|  
|[<span data-ttu-id="e8223-112">BreakpointSetError メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-112">BreakpointSetError Method</span></span>](icordebugmanagedcallback-breakpointseterror-method.md)|<span data-ttu-id="e8223-113">関数が just-in-time (JIT) コンパイルされる前に設定されたブレークポイントを共通言語ランタイム (CLR) が正しくバインドできなかったことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-113">Notifies the debugger that the common language runtime (CLR) was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>|  
|[<span data-ttu-id="e8223-114">ControlCTrap メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-114">ControlCTrap Method</span></span>](icordebugmanagedcallback-controlctrap-method.md)|<span data-ttu-id="e8223-115">デバッグ中のプロセスで CTRL + C がトラップされることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-115">Notifies the debugger that a CTRL+C is trapped in the process being debugged.</span></span>|  
|[<span data-ttu-id="e8223-116">CreateAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-116">CreateAppDomain Method</span></span>](icordebugmanagedcallback-createappdomain-method.md)|<span data-ttu-id="e8223-117">アプリケーションドメインが作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-117">Notifies the debugger that an application domain has been created.</span></span>|  
|[<span data-ttu-id="e8223-118">CreateProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-118">CreateProcess Method</span></span>](icordebugmanagedcallback-createprocess-method.md)|<span data-ttu-id="e8223-119">プロセスが初めてアタッチまたは開始されたときにデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-119">Notifies the debugger when a process has been attached or started for the first time.</span></span>|  
|[<span data-ttu-id="e8223-120">CreateThread メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-120">CreateThread Method</span></span>](icordebugmanagedcallback-createthread-method.md)|<span data-ttu-id="e8223-121">スレッドがマネージコードの実行を開始したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-121">Notifies the debugger that a thread has started executing managed code.</span></span>|  
|[<span data-ttu-id="e8223-122">DebuggerError メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-122">DebuggerError Method</span></span>](icordebugmanagedcallback-debuggererror-method.md)|<span data-ttu-id="e8223-123">CLR からのイベントを処理しようとしたときにエラーが発生したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-123">Notifies the debugger that an error has occurred while attempting to handle an event from the CLR.</span></span>|  
|[<span data-ttu-id="e8223-124">EditAndContinueRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-124">EditAndContinueRemap Method</span></span>](icordebugmanagedcallback-editandcontinueremap-method.md)|<span data-ttu-id="e8223-125">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="e8223-125">Deprecated.</span></span> <span data-ttu-id="e8223-126">リマップイベントが IDE に送信されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-126">Notifies the debugger that a remap event has been sent to the IDE.</span></span>|  
|[<span data-ttu-id="e8223-127">EvalComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-127">EvalComplete Method</span></span>](icordebugmanagedcallback-evalcomplete-method.md)|<span data-ttu-id="e8223-128">評価が完了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-128">Notifies the debugger that an evaluation has been completed.</span></span>|  
|[<span data-ttu-id="e8223-129">EvalException メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-129">EvalException Method</span></span>](icordebugmanagedcallback-evalexception-method.md)|<span data-ttu-id="e8223-130">ハンドルされない例外で評価が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-130">Notifies the debugger that an evaluation has been terminated with an unhandled exception.</span></span>|  
|[<span data-ttu-id="e8223-131">Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-131">Exception Method</span></span>](icordebugmanagedcallback-exception-method.md)|<span data-ttu-id="e8223-132">マネージコードから例外がスローされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-132">Notifies the debugger that an exception has been thrown from managed code.</span></span>|  
|[<span data-ttu-id="e8223-133">ExitAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-133">ExitAppDomain Method</span></span>](icordebugmanagedcallback-exitappdomain-method.md)|<span data-ttu-id="e8223-134">アプリケーションドメインが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-134">Notifies the debugger that an application domain has exited.</span></span>|  
|[<span data-ttu-id="e8223-135">ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-135">ExitProcess Method</span></span>](icordebugmanagedcallback-exitprocess-method.md)|<span data-ttu-id="e8223-136">プロセスが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-136">Notifies the debugger that a process has exited.</span></span>|  
|[<span data-ttu-id="e8223-137">ExitThread メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-137">ExitThread Method</span></span>](icordebugmanagedcallback-exitthread-method.md)|<span data-ttu-id="e8223-138">マネージコードを実行していたスレッドが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-138">Notifies the debugger that a thread that was executing managed code has exited.</span></span>|  
|[<span data-ttu-id="e8223-139">LoadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-139">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)|<span data-ttu-id="e8223-140">CLR アセンブリが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-140">Notifies the debugger that a CLR assembly has been successfully loaded.</span></span>|  
|[<span data-ttu-id="e8223-141">LoadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-141">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)|<span data-ttu-id="e8223-142">クラスが読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-142">Notifies the debugger that a class has been loaded.</span></span>|  
|[<span data-ttu-id="e8223-143">LoadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-143">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)|<span data-ttu-id="e8223-144">CLR モジュールが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-144">Notifies the debugger that a CLR module has been successfully loaded.</span></span>|  
|[<span data-ttu-id="e8223-145">LogMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-145">LogMessage Method</span></span>](icordebugmanagedcallback-logmessage-method.md)|<span data-ttu-id="e8223-146">CLR マネージスレッドが <xref:System.Diagnostics.EventLog> イベントをログに記録するためにクラスのメソッドを呼び出したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-146">Notifies the debugger that a CLR managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>|  
|[<span data-ttu-id="e8223-147">LogSwitch メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-147">LogSwitch Method</span></span>](icordebugmanagedcallback-logswitch-method.md)|<span data-ttu-id="e8223-148">CLR マネージスレッドが、 <xref:System.Diagnostics.Switch> デバッグ/トレーススイッチを作成、変更、または削除するために、クラスのメソッドを呼び出したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-148">Notifies the debugger that a CLR managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>|  
|[<span data-ttu-id="e8223-149">NameChange メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-149">NameChange Method</span></span>](icordebugmanagedcallback-namechange-method.md)|<span data-ttu-id="e8223-150">アプリケーションドメインまたはスレッドの名前が変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-150">Notifies the debugger that the name of either an application domain or thread has changed.</span></span>|  
|[<span data-ttu-id="e8223-151">StepComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-151">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)|<span data-ttu-id="e8223-152">ステップが完了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-152">Notifies the debugger that a step has completed.</span></span>|  
|[<span data-ttu-id="e8223-153">UnloadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-153">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)|<span data-ttu-id="e8223-154">CLR アセンブリがアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-154">Notifies the debugger that a CLR assembly has been unloaded.</span></span>|  
|[<span data-ttu-id="e8223-155">UnloadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-155">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)|<span data-ttu-id="e8223-156">クラスがアンロードされていることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-156">Notifies the debugger that a class is being unloaded.</span></span>|  
|[<span data-ttu-id="e8223-157">UnloadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-157">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)|<span data-ttu-id="e8223-158">CLR モジュール (DLL) がアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-158">Notifies the debugger that a CLR module (DLL) has been unloaded.</span></span>|  
|[<span data-ttu-id="e8223-159">UpdateModuleSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="e8223-159">UpdateModuleSymbols Method</span></span>](icordebugmanagedcallback-updatemodulesymbols-method.md)|<span data-ttu-id="e8223-160">CLR モジュールのシンボルが変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e8223-160">Notifies the debugger that the symbols for a CLR module have changed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8223-161">解説</span><span class="sxs-lookup"><span data-stu-id="e8223-161">Remarks</span></span>  

 <span data-ttu-id="e8223-162">すべてのコールバックがシリアル化され、同じスレッドで呼び出され、プロセスと同期された状態で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-162">All callbacks are serialized, called in the same thread, and called with the process in the synchronized state.</span></span>  
  
 <span data-ttu-id="e8223-163">各コールバックの実装では、実行を再開するために、「いいね! [:: Continue](icordebugcontroller-continue-method.md) 」を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e8223-163">Each callback implementation must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to resume execution.</span></span> <span data-ttu-id="e8223-164">`ICorDebugController::Continue`コールバックが戻る前にが呼び出されなかった場合、プロセスは停止したままになり、が呼び出されるまで、これ以上イベントコールバックは実行されません `ICorDebugController::Continue` 。</span><span class="sxs-lookup"><span data-stu-id="e8223-164">If `ICorDebugController::Continue` is not called before the callback returns, the process will remain stopped and no more event callbacks will occur until `ICorDebugController::Continue` is called.</span></span>  
  
 <span data-ttu-id="e8223-165">デバッガーが .NET Framework バージョン2.0 のアプリケーションをデバッグしている場合は、 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8223-165">A debugger must implement [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) if it is debugging .NET Framework version 2.0 applications.</span></span> <span data-ttu-id="e8223-166">またはのインスタンスは、 `ICorDebugManagedCallback` `ICorDebugManagedCallback2` コールバックオブジェクトとして [ICorDebug:: setmanagedhandler](icordebug-setmanagedhandler-method.md)に渡されます。</span><span class="sxs-lookup"><span data-stu-id="e8223-166">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8223-167">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e8223-167">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8223-168">要件</span><span class="sxs-lookup"><span data-stu-id="e8223-168">Requirements</span></span>  

 <span data-ttu-id="e8223-169">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8223-169">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8223-170">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8223-170">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8223-171">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8223-171">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8223-172">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8223-172">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8223-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8223-173">See also</span></span>

- [<span data-ttu-id="e8223-174">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8223-174">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="e8223-175">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8223-175">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="e8223-176">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8223-176">Debugging Interfaces</span></span>](debugging-interfaces.md)
