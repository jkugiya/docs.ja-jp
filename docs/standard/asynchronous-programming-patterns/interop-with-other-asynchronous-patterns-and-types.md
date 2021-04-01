---
description: '詳細情報: 他の非同期パターンと型との相互運用'
title: 他の非同期パターンと型との相互運用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: f120a5d9-933b-4d1d-acb6-f034a57c3749
ms.openlocfilehash: 52b3628f3a6371ef1a4a132723e81b8c83d7fa3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702926"
---
# <a name="interop-with-other-asynchronous-patterns-and-types"></a><span data-ttu-id="7e903-103">他の非同期パターンと型との相互運用</span><span class="sxs-lookup"><span data-stu-id="7e903-103">Interop with Other Asynchronous Patterns and Types</span></span>

<span data-ttu-id="7e903-104">.NET での非同期パターンの簡単な歴史は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7e903-104">A brief history of asynchronous patterns in .NET:</span></span>

- <span data-ttu-id="7e903-105">.NET Framework 1.0 で、[非同期プログラミング モデル (APM)](asynchronous-programming-model-apm.md) とも、`Begin/End` パターンとも呼ばれる <xref:System.IAsyncResult> パターンが導入されました。</span><span class="sxs-lookup"><span data-stu-id="7e903-105">.NET Framework 1.0 introduced the <xref:System.IAsyncResult> pattern, otherwise known as the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md), or the `Begin/End` pattern.</span></span>
- <span data-ttu-id="7e903-106">.NET Framework 2.0 で、[イベント ベースの非同期パターン (EAP)](event-based-asynchronous-pattern-eap.md) が追加されました。</span><span class="sxs-lookup"><span data-stu-id="7e903-106">.NET Framework 2.0 added the [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>
- <span data-ttu-id="7e903-107">.NET Framework 4 以降で、以前のパターンから簡単に移行ルーチンをビルドできる、APM および EAP よりも優先される、[タスク ベースの非同期パターン (TAP)](task-based-asynchronous-pattern-tap.md) が導入されました。</span><span class="sxs-lookup"><span data-stu-id="7e903-107">.NET Framework 4 introduced the [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md), which supersedes both APM and EAP and provides the ability to easily build migration routines from the earlier patterns.</span></span>
  
## <a name="tasks-and-the-asynchronous-programming-model-apm"></a><span data-ttu-id="7e903-108">タスクおよび非同期プログラミング モデル (APM)</span><span class="sxs-lookup"><span data-stu-id="7e903-108">Tasks and the Asynchronous Programming Model (APM)</span></span>

### <a name="from-apm-to-tap"></a><span data-ttu-id="7e903-109">APM から TAP へ</span><span class="sxs-lookup"><span data-stu-id="7e903-109">From APM to TAP</span></span>  

 <span data-ttu-id="7e903-110">[非同期プログラミング モデル (APM)](asynchronous-programming-model-apm.md) パターンは構造化されているため、APM 実装を TAP 実装として公開するラッパーをとても簡単にビルドできます。</span><span class="sxs-lookup"><span data-stu-id="7e903-110">Because the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md) pattern is structured, it is quite easy to build a wrapper to expose an APM implementation as a TAP implementation.</span></span> <span data-ttu-id="7e903-111">.NET Framework 4 以降のバージョンには、この変換を行う <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> メソッドのオーバーロードという形のヘルパー ルーチンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7e903-111">.NET Framework 4 and later versions include helper routines in the form of <xref:System.Threading.Tasks.TaskFactory.FromAsync%2A> method overloads to provide this translation.</span></span>  
  
 <span data-ttu-id="7e903-112"><xref:System.IO.Stream> クラスと、そのクラスの <xref:System.IO.Stream.BeginRead%2A> および <xref:System.IO.Stream.EndRead%2A> メソッドについて考えてみましょう。これらのメソッドは、同期 <xref:System.IO.Stream.Read%2A> メソッドに対応する APM 側のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="7e903-112">Consider the <xref:System.IO.Stream> class and its <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> methods, which represent the APM counterpart to the synchronous <xref:System.IO.Stream.Read%2A> method:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#1)]
 [!code-vb[Conceptual.AsyncInterop#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#1)]  
[!code-csharp[Conceptual.AsyncInterop#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#2)]
[!code-vb[Conceptual.AsyncInterop#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#2)]  
[!code-csharp[Conceptual.AsyncInterop#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Stream1.cs#3)]
[!code-vb[Conceptual.AsyncInterop#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/stream1.vb#3)]  
  
 <span data-ttu-id="7e903-113"><xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> メソッドを次のように使用すると、この操作に対する TAP ラッパーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="7e903-113">You can use the <xref:System.Threading.Tasks.TaskFactory%601.FromAsync%2A?displayProperty=nameWithType> method to implement a TAP wrapper for this operation as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap1.cs#4)]
 [!code-vb[Conceptual.AsyncInterop#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap1.vb#4)]  
  
 <span data-ttu-id="7e903-114">この実装は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7e903-114">This implementation is similar to the following:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wrap2.cs#5)]
 [!code-vb[Conceptual.AsyncInterop#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wrap2.vb#5)]  
  
### <a name="from-tap-to-apm"></a><span data-ttu-id="7e903-115">TAP から APM へ</span><span class="sxs-lookup"><span data-stu-id="7e903-115">From TAP to APM</span></span>  

 <span data-ttu-id="7e903-116">既存のインフラストラクチャで APM パターンを使用することを想定している場合は、TAP の実装を用意し、APM の実装を想定している場所でその TAP の実装を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e903-116">If your existing infrastructure expects the APM pattern, you'll also want to take a TAP implementation and use it where an APM implementation is expected.</span></span>  <span data-ttu-id="7e903-117">タスクは合成することができ、 <xref:System.Threading.Tasks.Task> クラスが <xref:System.IAsyncResult>を実装するため、これは単純なヘルパー関数を使用して実現することができます。</span><span class="sxs-lookup"><span data-stu-id="7e903-117">Because tasks can be composed and  the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, you can use a straightforward helper function to do this.</span></span> <span data-ttu-id="7e903-118">次のコードでは、 <xref:System.Threading.Tasks.Task%601> クラスの拡張を使用しますが、ほぼ同じ関数を非ジェネリック タスクに使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e903-118">The following code uses an extension of the <xref:System.Threading.Tasks.Task%601> class, but you can use an almost identical function for non-generic tasks.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM1.cs#6)]
 [!code-vb[Conceptual.AsyncInterop#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM1.vb#6)]  
  
 <span data-ttu-id="7e903-119">ここで、TAP 実装がある次のような例を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="7e903-119">Now, consider a case where you have the following TAP implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#7)]
 [!code-vb[Conceptual.AsyncInterop#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#7)]  
  
 <span data-ttu-id="7e903-120">そして、次の APM 実装を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e903-120">and you want to provide this APM implementation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#8)]
 [!code-vb[Conceptual.AsyncInterop#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#8)]  
[!code-csharp[Conceptual.AsyncInterop#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#9)]
[!code-vb[Conceptual.AsyncInterop#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#9)]  
  
 <span data-ttu-id="7e903-121">次のコードは、APM への移行の一例です。</span><span class="sxs-lookup"><span data-stu-id="7e903-121">The following example demonstrates one migration to APM:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/APM2.cs#10)]
 [!code-vb[Conceptual.AsyncInterop#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/APM2.vb#10)]  
  
## <a name="tasks-and-the-event-based-asynchronous-pattern-eap"></a><span data-ttu-id="7e903-122">タスクとイベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="7e903-122">Tasks and the Event-based Asynchronous Pattern (EAP)</span></span>  

 <span data-ttu-id="7e903-123">[イベント ベースの非同期パターン (EAP)](event-based-asynchronous-pattern-eap.md) 実装をラップする手順は、APM パターンをラップするより複雑です。EAP パターンのほうが APM パターンよりもバリエーションが多く、構造化の程度が低いためです。</span><span class="sxs-lookup"><span data-stu-id="7e903-123">Wrapping an [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md) implementation is more involved than wrapping an APM pattern, because the EAP pattern has more variation and less structure than the APM pattern.</span></span>  <span data-ttu-id="7e903-124">例を示すために、次のコードでは `DownloadStringAsync` メソッドをラップしています。</span><span class="sxs-lookup"><span data-stu-id="7e903-124">To demonstrate, the following code wraps the `DownloadStringAsync` method.</span></span>  <span data-ttu-id="7e903-125">`DownloadStringAsync` は、URI を受け付け、進行状況として複数の統計情報をレポートするためにダウンロード中に `DownloadProgressChanged` イベントを発生させ、完了時に `DownloadStringCompleted` イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="7e903-125">`DownloadStringAsync` accepts a URI, raises the `DownloadProgressChanged` event while downloading in order to report multiple statistics on progress, and raises the `DownloadStringCompleted` event when it's done.</span></span>  <span data-ttu-id="7e903-126">最終結果は、指定された URI にあるページのコンテンツを含む文字列です。</span><span class="sxs-lookup"><span data-stu-id="7e903-126">The final result is a string that contains the contents of the page at the specified URI.</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/EAP1.cs#11)]
 [!code-vb[Conceptual.AsyncInterop#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/EAP1.vb#11)]  
  
## <a name="tasks-and-wait-handles"></a><span data-ttu-id="7e903-127">タスクおよび待機ハンドル</span><span class="sxs-lookup"><span data-stu-id="7e903-127">Tasks and Wait Handles</span></span>  
  
### <a name="from-wait-handles-to-tap"></a><span data-ttu-id="7e903-128">待機ハンドルから TAP へ</span><span class="sxs-lookup"><span data-stu-id="7e903-128">From Wait Handles to TAP</span></span>  

 <span data-ttu-id="7e903-129">待機ハンドルは非同期パターンを実装しませんが、上級開発者は、待機ハンドルが設定されるときに非同期の通知を行うため、 <xref:System.Threading.WaitHandle> クラスおよび <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e903-129">Although wait handles don't implement an asynchronous pattern, advanced developers may use the <xref:System.Threading.WaitHandle> class and the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> method for asynchronous notifications when a wait handle is set.</span></span>  <span data-ttu-id="7e903-130"><xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> メソッドをラップすると、待機ハンドルのすべての同期待機をタスク ベースの待機にできます。</span><span class="sxs-lookup"><span data-stu-id="7e903-130">You can wrap the <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> method to enable a task-based alternative to any synchronous wait on a wait handle:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#12)]
 [!code-vb[Conceptual.AsyncInterop#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#12)]  
  
 <span data-ttu-id="7e903-131">このメソッドにより、非同期メソッドで既存の <xref:System.Threading.WaitHandle> 実装を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e903-131">With this method, you can use existing <xref:System.Threading.WaitHandle> implementations in asynchronous methods.</span></span>  <span data-ttu-id="7e903-132">たとえば、特定の時点に実行する非同期操作の数を絞り込む場合は、セマフォ ( <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> オブジェクト) を利用できます。</span><span class="sxs-lookup"><span data-stu-id="7e903-132">For example, if you want to throttle the number of asynchronous operations that are executing at any particular time, you can utilize a semaphore (a <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> object).</span></span>  <span data-ttu-id="7e903-133">セマフォのカウントを *N* に初期化し、操作を実行するときには常にセマフォを待機し、操作完了時にセマフォを解放することで、同時実行される操作の数を *N* に絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7e903-133">You can throttle to *N* the number of operations that run concurrently by initializing the semaphore's count to *N*, waiting on the semaphore any time you want to perform an operation, and releasing the semaphore when you're done with an operation:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#13](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Semaphore1.cs#13)]
 [!code-vb[Conceptual.AsyncInterop#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Semaphore1.vb#13)]  
  
 <span data-ttu-id="7e903-134">また、待機ハンドルに依存せず、代わりにタスクで完全に動作する非同期セマフォもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="7e903-134">You can also build an asynchronous semaphore that does not rely on wait handles and instead works completely with tasks.</span></span> <span data-ttu-id="7e903-135">これを行うには、 [T:System.Threading.Tasks.Task](consuming-the-task-based-asynchronous-pattern.md) の上位にデータ構造をビルドするという「 <xref:System.Threading.Tasks.Task>が追加されました。</span><span class="sxs-lookup"><span data-stu-id="7e903-135">To do this, you can use techniques such as those discussed in [Consuming the Task-based Asynchronous Pattern](consuming-the-task-based-asynchronous-pattern.md) for building data structures on top of <xref:System.Threading.Tasks.Task>.</span></span>  
  
### <a name="from-tap-to-wait-handles"></a><span data-ttu-id="7e903-136">TAP から待機ハンドルへ</span><span class="sxs-lookup"><span data-stu-id="7e903-136">From TAP to Wait Handles</span></span>  

 <span data-ttu-id="7e903-137">前述のとおり、 <xref:System.Threading.Tasks.Task> クラスは、 <xref:System.IAsyncResult>を実装し、その実装は <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> プロパティを公開します。このプロパティは、 <xref:System.Threading.Tasks.Task> が完了したときに設定される待機ハンドルを返します。</span><span class="sxs-lookup"><span data-stu-id="7e903-137">As previously mentioned, the <xref:System.Threading.Tasks.Task> class implements <xref:System.IAsyncResult>, and that implementation exposes an <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle%2A> property that returns a wait handle that will be set when the <xref:System.Threading.Tasks.Task> completes.</span></span>  <span data-ttu-id="7e903-138"><xref:System.Threading.WaitHandle> の <xref:System.Threading.Tasks.Task> は次のように取得できます。</span><span class="sxs-lookup"><span data-stu-id="7e903-138">You can get a <xref:System.Threading.WaitHandle> for a <xref:System.Threading.Tasks.Task> as follows:</span></span>  
  
 [!code-csharp[Conceptual.AsyncInterop#14](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.AsyncInterop/cs/Wait1.cs#14)]
 [!code-vb[Conceptual.AsyncInterop#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.AsyncInterop/vb/Wait1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="7e903-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e903-139">See also</span></span>

- [<span data-ttu-id="7e903-140">タスク ベースの非同期パターン (TAP)</span><span class="sxs-lookup"><span data-stu-id="7e903-140">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="7e903-141">タスク ベースの非同期パターンの実装</span><span class="sxs-lookup"><span data-stu-id="7e903-141">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="7e903-142">T:System.Threading.Tasks.Task</span><span class="sxs-lookup"><span data-stu-id="7e903-142">Consuming the Task-based Asynchronous Pattern</span></span>](consuming-the-task-based-asynchronous-pattern.md)
