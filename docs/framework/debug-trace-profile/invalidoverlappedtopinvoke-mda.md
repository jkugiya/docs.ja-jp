---
title: invalidOverlappedToPinvoke MDA
description: .NET の invalidOverlappedToPinvoke マネージド デバッグ アシスタント (MDA) について確認します。これは、クラッシュまたは説明のつかないヒープ破損時にアクティブになる可能性があります。
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
ms.openlocfilehash: 55b10af87130bd32410508cef2bc3e4e733549c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281326"
---
# <a name="invalidoverlappedtopinvoke-mda"></a><span data-ttu-id="2bb52-103">invalidOverlappedToPinvoke MDA</span><span class="sxs-lookup"><span data-stu-id="2bb52-103">invalidOverlappedToPinvoke MDA</span></span>

<span data-ttu-id="2bb52-104">`invalidOverlappedToPinvoke` マネージド デバッグ アシスタント (MDA: Managed Debugging Assistant) は、ガベージ コレクション ヒープで作成されていないオーバーラップ ポインターが特定の Win32 関数に渡されるとアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="2bb52-104">The `invalidOverlappedToPinvoke` managed debugging assistant (MDA) is activated when an overlapped pointer that was not created on the garbage collection heap is passed to specific Win32 functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bb52-105">既定では、この MDA は、プラットフォームの起動の呼び出しがコードで定義され、デバッガーが各メソッドの JustMyCode 状態をレポートする場合にのみアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="2bb52-105">By default, this MDA is activated only if the platform invoke call is defined in your code and the debugger reports the JustMyCode status of each method.</span></span> <span data-ttu-id="2bb52-106">JustMyCode を理解しないデバッガー (拡張機能なしの MDbg.exe など) は、この MDA をアクティブにしません。</span><span class="sxs-lookup"><span data-stu-id="2bb52-106">A debugger that does not understand JustMyCode (such as MDbg.exe with no extensions) will not activate this MDA.</span></span> <span data-ttu-id="2bb52-107">このようなデバッガーに対してこの MDA を有効にするには、構成ファイルを使用し、.mda.config ファイルで `justMyCode="false"` を明示的に設定します`(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`)。</span><span class="sxs-lookup"><span data-stu-id="2bb52-107">This MDA can be enabled for those debuggers by using a configuration file and explicitly settting `justMyCode="false"` in the .mda.config file `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2bb52-108">現象</span><span class="sxs-lookup"><span data-stu-id="2bb52-108">Symptoms</span></span>  

 <span data-ttu-id="2bb52-109">クラッシュまたは説明のつかないヒープ破損。</span><span class="sxs-lookup"><span data-stu-id="2bb52-109">Crashes or unexplainable heap corruptions.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2bb52-110">原因</span><span class="sxs-lookup"><span data-stu-id="2bb52-110">Cause</span></span>  

 <span data-ttu-id="2bb52-111">ガベージ コレクション ヒープで作成されていないオーバーラップ ポインターが特定のオペレーティング システム関数に渡されています。</span><span class="sxs-lookup"><span data-stu-id="2bb52-111">An overlapped pointer that was not created on the garbage collection heap is passed to specific operating system functions.</span></span>  
  
 <span data-ttu-id="2bb52-112">この MDA が追跡する関数を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="2bb52-112">The following table shows the functions that this MDA tracks.</span></span>  
  
|<span data-ttu-id="2bb52-113">Module</span><span class="sxs-lookup"><span data-stu-id="2bb52-113">Module</span></span>|<span data-ttu-id="2bb52-114">機能</span><span class="sxs-lookup"><span data-stu-id="2bb52-114">Function</span></span>|  
|------------|--------------|  
|<span data-ttu-id="2bb52-115">HttpApi.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-115">HttpApi.dll</span></span>|`HttpReceiveHttpRequest`|  
|<span data-ttu-id="2bb52-116">IpHlpApi.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-116">IpHlpApi.dll</span></span>|`NotifyAddrChange`|  
|<span data-ttu-id="2bb52-117">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-117">kernel32.dll</span></span>|`ReadFile`|  
|<span data-ttu-id="2bb52-118">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-118">kernel32.dll</span></span>|`ReadFileEx`|  
|<span data-ttu-id="2bb52-119">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-119">kernel32.dll</span></span>|`WriteFile`|  
|<span data-ttu-id="2bb52-120">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-120">kernel32.dll</span></span>|`WriteFileEx`|  
|<span data-ttu-id="2bb52-121">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-121">kernel32.dll</span></span>|`ReadDirectoryChangesW`|  
|<span data-ttu-id="2bb52-122">kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-122">kernel32.dll</span></span>|`PostQueuedCompletionStatus`|  
|<span data-ttu-id="2bb52-123">MSWSock.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-123">MSWSock.dll</span></span>|`ConnectEx`|  
|<span data-ttu-id="2bb52-124">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-124">WS2_32.dll</span></span>|`WSASend`|  
|<span data-ttu-id="2bb52-125">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-125">WS2_32.dll</span></span>|`WSASendTo`|  
|<span data-ttu-id="2bb52-126">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-126">WS2_32.dll</span></span>|`WSARecv`|  
|<span data-ttu-id="2bb52-127">WS2_32.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-127">WS2_32.dll</span></span>|`WSARecvFrom`|  
|<span data-ttu-id="2bb52-128">MQRT.dll</span><span class="sxs-lookup"><span data-stu-id="2bb52-128">MQRT.dll</span></span>|`MQReceiveMessage`|  
  
 <span data-ttu-id="2bb52-129">呼び出しを行う <xref:System.AppDomain> がアンロードされる可能性があるため、この条件ではヒープが破損する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="2bb52-129">The potential for heap corruption is high for this condition because the <xref:System.AppDomain> making the call might unload.</span></span> <span data-ttu-id="2bb52-130"><xref:System.AppDomain> がアンロードされると、アプリケーション コードがオーバーラップ ポインター用メモリを解放するため、操作終了時に破損が発生します。または、コードによってメモリ リークが発生し、後で問題となります。</span><span class="sxs-lookup"><span data-stu-id="2bb52-130">If the <xref:System.AppDomain> unloads, the application code will either free the memory for the overlapped pointer, causing corruption when the operation finishes, or the code will leak the memory, causing difficulties later.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2bb52-131">解決方法</span><span class="sxs-lookup"><span data-stu-id="2bb52-131">Resolution</span></span>  

 <span data-ttu-id="2bb52-132"><xref:System.Threading.Overlapped> オブジェクトを使用して <xref:System.Threading.Overlapped.Pack%2A> メソッドを呼び出し、関数に渡すことができる <xref:System.Threading.NativeOverlapped> 構造体を取得します。</span><span class="sxs-lookup"><span data-stu-id="2bb52-132">Use an <xref:System.Threading.Overlapped> object, calling the <xref:System.Threading.Overlapped.Pack%2A> method to get a <xref:System.Threading.NativeOverlapped> structure that can be passed to the function.</span></span> <span data-ttu-id="2bb52-133"><xref:System.AppDomain> がアンロードされると、CLR は非同期操作が完了するのを待ってからポインターを解放します。</span><span class="sxs-lookup"><span data-stu-id="2bb52-133">If the <xref:System.AppDomain> unloads, the CLR waits until the asynchronous operation completes before freeing the pointer.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2bb52-134">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="2bb52-134">Effect on the Runtime</span></span>  

 <span data-ttu-id="2bb52-135">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="2bb52-135">This MDA had no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2bb52-136">出力</span><span class="sxs-lookup"><span data-stu-id="2bb52-136">Output</span></span>  

 <span data-ttu-id="2bb52-137">この MDA からの出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2bb52-137">The following is an example of output from this MDA.</span></span>  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a><span data-ttu-id="2bb52-138">構成</span><span class="sxs-lookup"><span data-stu-id="2bb52-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bb52-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bb52-139">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="2bb52-140">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="2bb52-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="2bb52-141">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="2bb52-141">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
