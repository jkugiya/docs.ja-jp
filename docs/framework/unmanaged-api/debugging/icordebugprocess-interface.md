---
description: '詳細については、次を参照してください: のプロセスインターフェイス'
title: ICorDebugProcess インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
ms.openlocfilehash: 7172ee12bf450235db1c18601c8ff7de51435520
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746790"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="31849-103">ICorDebugProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31849-103">ICorDebugProcess Interface</span></span>

<span data-ttu-id="31849-104">マネージド コードを実行しているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="31849-104">Represents a process that is executing managed code.</span></span> <span data-ttu-id="31849-105">このインターフェイスは、というコントロールのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="31849-105">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="31849-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-106">Methods</span></span>  
  
|<span data-ttu-id="31849-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-107">Method</span></span>|<span data-ttu-id="31849-108">説明</span><span class="sxs-lookup"><span data-stu-id="31849-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="31849-109">ClearCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-109">ClearCurrentException Method</span></span>](icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="31849-110">指定されたスレッドで現在のアンマネージ例外をクリアします。</span><span class="sxs-lookup"><span data-stu-id="31849-110">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="31849-111">EnableLogMessages メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-111">EnableLogMessages Method</span></span>](icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="31849-112">デバッガーへのログメッセージの送信を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="31849-112">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="31849-113">EnumerateAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-113">EnumerateAppDomains Method</span></span>](icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="31849-114">プロセス内のすべてのアプリケーションドメインを列挙します。</span><span class="sxs-lookup"><span data-stu-id="31849-114">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="31849-115">EnumerateObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-115">EnumerateObjects Method</span></span>](icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="31849-116">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="31849-116">Not implemented.</span></span>|  
|[<span data-ttu-id="31849-117">GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-117">GetHandle Method</span></span>](icordebugprocess-gethandle-method.md)|<span data-ttu-id="31849-118">プロセスを処理するハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="31849-118">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="31849-119">GetHelperThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-119">GetHelperThreadID Method</span></span>](icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="31849-120">デバッガーの内部ヘルパースレッドのオペレーティングシステム (OS) スレッド ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="31849-120">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="31849-121">GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-121">GetID Method</span></span>](icordebugprocess-getid-method.md)|<span data-ttu-id="31849-122">プロセスのオペレーティングシステム (OS) ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="31849-122">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="31849-123">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-123">GetObject Method</span></span>](icordebugprocess-getobject-method.md)|<span data-ttu-id="31849-124">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="31849-124">Not implemented.</span></span>|  
|[<span data-ttu-id="31849-125">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-125">GetThread Method</span></span>](icordebugprocess-getthread-method.md)|<span data-ttu-id="31849-126">指定された OS スレッド ID を持つコードスレッドインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="31849-126">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="31849-127">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-127">GetThreadContext Method</span></span>](icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="31849-128">指定されたスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="31849-128">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="31849-129">IsOSSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-129">IsOSSuspended Method</span></span>](icordebugprocess-isossuspended-method.md)|<span data-ttu-id="31849-130">デバッガーがプロセスを停止した結果としてスレッドが中断されたかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="31849-130">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="31849-131">IsTransitionStub メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-131">IsTransitionStub Method</span></span>](icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="31849-132">マネージコードへの遷移を発生させるスタブ内にアドレスがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="31849-132">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="31849-133">ModifyLogSwitch メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-133">ModifyLogSwitch Method</span></span>](icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="31849-134">指定されたログスイッチの重大度レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="31849-134">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="31849-135">ReadMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-135">ReadMemory Method</span></span>](icordebugprocess-readmemory-method.md)|<span data-ttu-id="31849-136">プロセスからメモリを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="31849-136">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="31849-137">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-137">SetThreadContext Method</span></span>](icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="31849-138">指定されたスレッドのコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="31849-138">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="31849-139">ThreadForFiberCookie メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-139">ThreadForFiberCookie Method</span></span>](icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="31849-140">非推奨になりました。</span><span class="sxs-lookup"><span data-stu-id="31849-140">Deprecated.</span></span>|  
|[<span data-ttu-id="31849-141">WriteMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="31849-141">WriteMemory Method</span></span>](icordebugprocess-writememory-method.md)|<span data-ttu-id="31849-142">プロセスのメモリ領域にデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="31849-142">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="31849-143">解説</span><span class="sxs-lookup"><span data-stu-id="31849-143">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31849-144">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="31849-144">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31849-145">要件</span><span class="sxs-lookup"><span data-stu-id="31849-145">Requirements</span></span>  

 <span data-ttu-id="31849-146">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31849-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31849-147">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31849-147">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31849-148">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31849-148">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31849-149">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31849-149">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31849-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="31849-150">See also</span></span>

- [<span data-ttu-id="31849-151">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31849-151">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="31849-152">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="31849-152">Debugging Interfaces</span></span>](debugging-interfaces.md)
