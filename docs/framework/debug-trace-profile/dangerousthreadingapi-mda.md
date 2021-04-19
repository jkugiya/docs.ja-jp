---
title: dangerousThreadingAPI MDA
description: dangerousThreadingAPI マネージド デバッグ アシスタント (MDA) について確認します。これは、現在のスレッド以外のスレッドで Thread.Suspend が呼び出されたときにアクティブになります。
ms.date: 03/30/2017
helpviewer_keywords:
- suspending threads
- DangerousThreadingAPI MDA
- managed debugging assistants (MDAs), dangerous threading operations
- threading [.NET Framework], suspending
- MDAs (managed debugging assistants), dangerous threading operations
- Suspend method
- threading [.NET Framework], managed debugging assistants
ms.assetid: 3e5efbc5-92e4-4229-b31f-ce368a1adb96
ms.openlocfilehash: 707e3e339cb8a692f862afc15328eef53f0547e5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286085"
---
# <a name="dangerousthreadingapi-mda"></a><span data-ttu-id="75ae7-103">dangerousThreadingAPI MDA</span><span class="sxs-lookup"><span data-stu-id="75ae7-103">dangerousThreadingAPI MDA</span></span>

<span data-ttu-id="75ae7-104">`dangerousThreadingAPI` マネージド デバッグ アシスタント (MDA) は、現在のスレッド以外のスレッドで <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> メソッドが呼び出されるとアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="75ae7-104">The `dangerousThreadingAPI` managed debugging assistant (MDA) is activated when the <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> method is called on a thread other than the current thread.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="75ae7-105">現象</span><span class="sxs-lookup"><span data-stu-id="75ae7-105">Symptoms</span></span>  

 <span data-ttu-id="75ae7-106">アプリケーションがいつまでも応答しないかハングアップしています。</span><span class="sxs-lookup"><span data-stu-id="75ae7-106">An application is unresponsive or hangs indefinitely.</span></span> <span data-ttu-id="75ae7-107">システムまたはアプリケーションのデータが一時的に、またはアプリケーションのシャットダウン後も、予期しない状態のままになっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75ae7-107">System or application data might be left in an unpredictable state temporarily or even after an application has been shut down.</span></span> <span data-ttu-id="75ae7-108">一部の操作が予期したとおりに完了していません。</span><span class="sxs-lookup"><span data-stu-id="75ae7-108">Some operations are not completing as expected.</span></span>  
  
 <span data-ttu-id="75ae7-109">問題に伴うランダム性により、症状は大きく異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="75ae7-109">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="75ae7-110">原因</span><span class="sxs-lookup"><span data-stu-id="75ae7-110">Cause</span></span>  

 <span data-ttu-id="75ae7-111">スレッドは、<xref:System.Threading.Thread.Suspend%2A> メソッドを使用する別のスレッドによって非同期に中断されています。</span><span class="sxs-lookup"><span data-stu-id="75ae7-111">A thread is asynchronously suspended by another thread using the <xref:System.Threading.Thread.Suspend%2A> method.</span></span> <span data-ttu-id="75ae7-112">操作途中である可能性がある別のスレッドを安全に中断できるタイミングを判断する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="75ae7-112">There is no way to determine when it is safe to suspend another thread which might be in the middle of an operation.</span></span> <span data-ttu-id="75ae7-113">スレッドを中断すると、データの破損やインバリアントの中断が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="75ae7-113">Suspending the thread can result in the corruption of data or the breaking of invariants.</span></span> <span data-ttu-id="75ae7-114">スレッドが中断状態になっていて、<xref:System.Threading.Thread.Resume%2A> メソッドを使用して再開されないと、アプリケーションのハングアップ状態がいつまでも続き、アプリケーション データが損害を受けることがあります。</span><span class="sxs-lookup"><span data-stu-id="75ae7-114">Should a thread be placed into a suspended state and never resumed using the <xref:System.Threading.Thread.Resume%2A> method, the application can hang indefinitely and possibly damage application data.</span></span> <span data-ttu-id="75ae7-115">これらのメソッドは不使用とマークされています。</span><span class="sxs-lookup"><span data-stu-id="75ae7-115">These methods have been marked as obsolete.</span></span>  
  
 <span data-ttu-id="75ae7-116">同期プリミティブがターゲット スレッドによって保持されている場合は、中断の間も保持されたままになります。</span><span class="sxs-lookup"><span data-stu-id="75ae7-116">If synchronization primitives are held by the target thread, they remain held during suspension.</span></span> <span data-ttu-id="75ae7-117">これにより、<xref:System.Threading.Thread.Suspend%2A> を実行するスレッドなど、別のスレッドがプリミティブのロックを取得しようとすると、デッドロックが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="75ae7-117">This can lead to deadlocks should another thread, for example the thread performing the <xref:System.Threading.Thread.Suspend%2A>, attempt to acquire a lock on the primitive.</span></span> <span data-ttu-id="75ae7-118">この場合、問題自体がデッドロックとして現れます。</span><span class="sxs-lookup"><span data-stu-id="75ae7-118">In this situation, the problem manifests itself as a deadlock.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="75ae7-119">解決方法</span><span class="sxs-lookup"><span data-stu-id="75ae7-119">Resolution</span></span>  

 <span data-ttu-id="75ae7-120"><xref:System.Threading.Thread.Suspend%2A> および <xref:System.Threading.Thread.Resume%2A> を使用する必要のある設計を避けます。</span><span class="sxs-lookup"><span data-stu-id="75ae7-120">Avoid designs that require the use of <xref:System.Threading.Thread.Suspend%2A> and <xref:System.Threading.Thread.Resume%2A>.</span></span> <span data-ttu-id="75ae7-121">スレッド間の協調では、<xref:System.Threading.Monitor>、<xref:System.Threading.ReaderWriterLock>、<xref:System.Threading.Mutex> などの同期プリミティブや、C# の `lock` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="75ae7-121">For cooperation between threads, use synchronization primitives such as <xref:System.Threading.Monitor>, <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Mutex>, or the C# `lock` statement.</span></span> <span data-ttu-id="75ae7-122">これらのメソッドを使用する必要がある場合は、時間を短くし、スレッドが中断状態にある間に実行されるコードの量を最小限に留めます。</span><span class="sxs-lookup"><span data-stu-id="75ae7-122">If you must use these methods, reduce the window of time and minimize the amount of code that executes while the thread is in a suspended state.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="75ae7-123">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="75ae7-123">Effect on the Runtime</span></span>  

 <span data-ttu-id="75ae7-124">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="75ae7-124">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="75ae7-125">危険なスレッド処理操作に関するデータを報告するだけです。</span><span class="sxs-lookup"><span data-stu-id="75ae7-125">It only reports data about dangerous threading operations.</span></span>  
  
## <a name="output"></a><span data-ttu-id="75ae7-126">出力</span><span class="sxs-lookup"><span data-stu-id="75ae7-126">Output</span></span>  

 <span data-ttu-id="75ae7-127">MDA は、アクティブになった原因である危険なスレッド処理メソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="75ae7-127">The MDA identifies the dangerous threading method that caused it to be activated.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="75ae7-128">構成</span><span class="sxs-lookup"><span data-stu-id="75ae7-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dangerousThreadingAPI />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="75ae7-129">例</span><span class="sxs-lookup"><span data-stu-id="75ae7-129">Example</span></span>  

 <span data-ttu-id="75ae7-130">`dangerousThreadingAPI` のアクティブ化の原因となる <xref:System.Threading.Thread.Suspend%2A> メソッド呼び出しのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="75ae7-130">The following code example demonstrates a call to the <xref:System.Threading.Thread.Suspend%2A> method that causes the activation of the `dangerousThreadingAPI`.</span></span>  
  
```csharp
using System.Threading;  
void FireMda()  
{  
Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Suspend();
    t.Resume();  
    t.Join();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="75ae7-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="75ae7-131">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="75ae7-132">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="75ae7-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="75ae7-133">lock ステートメント</span><span class="sxs-lookup"><span data-stu-id="75ae7-133">lock Statement</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
