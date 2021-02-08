---
description: 詳細については、「ICorDebug インターフェイス」を参照してください。
title: ICorDebug インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: b989013f7eb54e163feeb965e10448a3a1756e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772524"
---
# <a name="icordebug-interface"></a><span data-ttu-id="a7486-103">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7486-103">ICorDebug Interface</span></span>

<span data-ttu-id="a7486-104">開発者が共通言語ランタイム (CLR) 環境でアプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a7486-104">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7486-105">混合モード (マネージコードとネイティブコード) のデバッグは、Windows 95、Windows 98、または Windows ME ではサポートされておらず、x86 以外のプラットフォーム (IA64 や AMD64 など) ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a7486-105">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7486-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-106">Methods</span></span>  
  
|<span data-ttu-id="a7486-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-107">Method</span></span>|<span data-ttu-id="a7486-108">説明</span><span class="sxs-lookup"><span data-stu-id="a7486-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7486-109">CanLaunchOrAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-109">CanLaunchOrAttach Method</span></span>](icordebug-canlaunchorattach-method.md)|<span data-ttu-id="a7486-110">現在のコンピューターおよびランタイム構成のコンテキスト内で、新しいプロセスを起動するか、指定したプロセスにアタッチするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="a7486-110">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="a7486-111">CreateProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-111">CreateProcess Method</span></span>](icordebug-createprocess-method.md)|<span data-ttu-id="a7486-112">デバッガーの制御下でプロセスとそのプライマリスレッドを起動します。</span><span class="sxs-lookup"><span data-stu-id="a7486-112">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="a7486-113">DebugActiveProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-113">DebugActiveProcess Method</span></span>](icordebug-debugactiveprocess-method.md)|<span data-ttu-id="a7486-114">デバッガーを既存のプロセスにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="a7486-114">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="a7486-115">EnumerateProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-115">EnumerateProcesses Method</span></span>](icordebug-enumerateprocesses-method.md)|<span data-ttu-id="a7486-116">デバッグ中のプロセスの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a7486-116">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="a7486-117">GetProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-117">GetProcess Method</span></span>](icordebug-getprocess-method.md)|<span data-ttu-id="a7486-118">指定されたプロセス ID を持つ "いいプロセス" オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="a7486-118">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="a7486-119">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-119">Initialize Method</span></span>](icordebug-initialize-method.md)|<span data-ttu-id="a7486-120">`ICorDebug` オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="a7486-120">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="a7486-121">SetManagedHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-121">SetManagedHandler Method</span></span>](icordebug-setmanagedhandler-method.md)|<span data-ttu-id="a7486-122">マネージイベントのイベントハンドラーオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7486-122">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="a7486-123">SetUnmanagedHandler メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-123">SetUnmanagedHandler Method</span></span>](icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="a7486-124">アンマネージイベントのイベントハンドラーオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="a7486-124">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="a7486-125">Terminate メソッド</span><span class="sxs-lookup"><span data-stu-id="a7486-125">Terminate Method</span></span>](icordebug-terminate-method.md)|<span data-ttu-id="a7486-126">オブジェクトを終了 `ICorDebug` します。</span><span class="sxs-lookup"><span data-stu-id="a7486-126">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7486-127">解説</span><span class="sxs-lookup"><span data-stu-id="a7486-127">Remarks</span></span>  

 <span data-ttu-id="a7486-128">`ICorDebug` デバッガープロセスのイベント処理ループを表します。</span><span class="sxs-lookup"><span data-stu-id="a7486-128">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="a7486-129">デバッガーは、このインターフェイスを解放する前に、デバッグされているすべてのプロセスからの "ExitProcess" コール [バック](icordebugmanagedcallback-exitprocess-method.md) を待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7486-129">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="a7486-130">オブジェクトは、 `ICorDebug` さらに管理されているすべてのデバッグを制御するための初期オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a7486-130">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="a7486-131">.NET Framework バージョン1.0 および1.1 では、このオブジェクトは `CoClass` COM から作成されたオブジェクトでした。</span><span class="sxs-lookup"><span data-stu-id="a7486-131">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="a7486-132">.NET Framework バージョン2.0 では、このオブジェクトはオブジェクトではなくなりました `CoClass` 。</span><span class="sxs-lookup"><span data-stu-id="a7486-132">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="a7486-133">これは、バージョンを認識する [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) 関数によって作成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7486-133">It must be created by the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="a7486-134">この新しい作成関数を使用すると、クライアントは特定の `ICorDebug` バージョンのデバッグ API もエミュレートするの特定の実装を取得できます。</span><span class="sxs-lookup"><span data-stu-id="a7486-134">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7486-135">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a7486-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7486-136">要件</span><span class="sxs-lookup"><span data-stu-id="a7486-136">Requirements</span></span>  

 <span data-ttu-id="a7486-137">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7486-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7486-138">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7486-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7486-139">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7486-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7486-140">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7486-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7486-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7486-141">See also</span></span>

- [<span data-ttu-id="a7486-142">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a7486-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
