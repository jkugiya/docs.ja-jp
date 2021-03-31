---
description: '詳細情報: CountdownEvent'
title: CountdownEvent
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
ms.openlocfilehash: 8b16666c6419b0b63a45182ee9f383476d6858cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675456"
---
# <a name="countdownevent"></a><span data-ttu-id="acd4b-103">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="acd4b-103">CountdownEvent</span></span>

<span data-ttu-id="acd4b-104"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> は同期プリミティブであり、特定の回数シグナル状態になった後、待機スレッドのブロックを解除します。</span><span class="sxs-lookup"><span data-stu-id="acd4b-104"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> is a synchronization primitive that unblocks its waiting threads after it has been signaled a certain number of times.</span></span> <span data-ttu-id="acd4b-105"><xref:System.Threading.CountdownEvent> は、通常は <xref:System.Threading.ManualResetEvent> または <xref:System.Threading.ManualResetEventSlim> を使用して、イベントをシグナル化する前に変数を手動でデクリメントする必要があるシナリオ用に設計されています。</span><span class="sxs-lookup"><span data-stu-id="acd4b-105"><xref:System.Threading.CountdownEvent> is designed for scenarios in which you would otherwise have to use a <xref:System.Threading.ManualResetEvent> or <xref:System.Threading.ManualResetEventSlim> and manually decrement a variable before signaling the event.</span></span> <span data-ttu-id="acd4b-106">たとえば、fork/join シナリオでは、単にシグナル数 5 の <xref:System.Threading.CountdownEvent> を作成し、スレッド プールで 5 つの作業項目を開始し、完了時に各作業項目呼び出し <xref:System.Threading.CountdownEvent.Signal%2A> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="acd4b-106">For example, in a fork/join scenario, you can just create a <xref:System.Threading.CountdownEvent> that has a signal count of 5, and then start five work items on the thread pool and have each work item call <xref:System.Threading.CountdownEvent.Signal%2A> when it completes.</span></span> <span data-ttu-id="acd4b-107"><xref:System.Threading.CountdownEvent.Signal%2A> を呼び出すたびに、シグナル数が 1 だけデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="acd4b-107">Each call to <xref:System.Threading.CountdownEvent.Signal%2A> decrements the signal count by 1.</span></span> <span data-ttu-id="acd4b-108">メイン スレッドでは、シグナル数がゼロになるまで、<xref:System.Threading.CountdownEvent.Wait%2A> の呼び出しがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="acd4b-108">On the main thread, the call to <xref:System.Threading.CountdownEvent.Wait%2A> will block until the signal count is zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acd4b-109">レガシ .NET Framework の同期 API と対話する必要がないコードの場合は、fork と join の並列実行をさらに簡単に表すために <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトまたは <xref:System.Threading.Tasks.Parallel.Invoke%2A> メソッドの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="acd4b-109">For code that does not have to interact with legacy .NET Framework synchronization APIs, consider using <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or the <xref:System.Threading.Tasks.Parallel.Invoke%2A> method for an even easier approach to expressing fork-join parallelism.</span></span>  
  
 <span data-ttu-id="acd4b-110"><xref:System.Threading.CountdownEvent> には以下の追加機能があります。</span><span class="sxs-lookup"><span data-stu-id="acd4b-110"><xref:System.Threading.CountdownEvent> has these additional features:</span></span>  
  
- <span data-ttu-id="acd4b-111">取り消しトークンを使用して、待機操作を取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="acd4b-111">The wait operation can be canceled by using cancellation tokens.</span></span>  
  
- <span data-ttu-id="acd4b-112">インスタンスの作成後に、シグナル数をインクリメントできます。</span><span class="sxs-lookup"><span data-stu-id="acd4b-112">Its signal count can be incremented after the instance is created.</span></span>  
  
- <span data-ttu-id="acd4b-113"><xref:System.Threading.CountdownEvent.Reset%2A> メソッドを呼び出すことで <xref:System.Threading.CountdownEvent.Wait%2A> が返された後、インスタンスを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="acd4b-113">Instances can be reused after <xref:System.Threading.CountdownEvent.Wait%2A> has returned by calling the <xref:System.Threading.CountdownEvent.Reset%2A> method.</span></span>  
  
- <span data-ttu-id="acd4b-114">インスタンスは、<xref:System.Threading.WaitHandle.WaitAll%2A> などの他の .NET の同期 API との統合のために <xref:System.Threading.WaitHandle> を公開します。</span><span class="sxs-lookup"><span data-stu-id="acd4b-114">Instances expose a <xref:System.Threading.WaitHandle> for integration with other .NET synchronization APIs, such as <xref:System.Threading.WaitHandle.WaitAll%2A>.</span></span>  
  
## <a name="basic-usage"></a><span data-ttu-id="acd4b-115">基本的な使用方法</span><span class="sxs-lookup"><span data-stu-id="acd4b-115">Basic Usage</span></span>  

 <span data-ttu-id="acd4b-116"><xref:System.Threading.CountdownEvent> と <xref:System.Threading.ThreadPool> 作業項目を使用する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="acd4b-116">The following example demonstrates how to use a <xref:System.Threading.CountdownEvent> with <xref:System.Threading.ThreadPool> work items.</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a><span data-ttu-id="acd4b-117">CountdownEvent と Cancellation</span><span class="sxs-lookup"><span data-stu-id="acd4b-117">CountdownEvent With Cancellation</span></span>  

 <span data-ttu-id="acd4b-118">次の例は、取り消しトークンを使用して、<xref:System.Threading.CountdownEvent> での待機操作を取り消す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="acd4b-118">The following example shows how to cancel the wait operation on <xref:System.Threading.CountdownEvent> by using a cancellation token.</span></span> <span data-ttu-id="acd4b-119">基本的なパターンでは、.NET Framework 4 で導入された統合取り消しのモデルに従います。</span><span class="sxs-lookup"><span data-stu-id="acd4b-119">The basic pattern follows the model for unified cancellation, which was introduced in .NET Framework 4.</span></span> <span data-ttu-id="acd4b-120">詳細については、「[マネージド スレッドのキャンセル](cancellation-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="acd4b-120">For more information, see [Cancellation in Managed Threads](cancellation-in-managed-threads.md).</span></span>  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 <span data-ttu-id="acd4b-121">待機操作では、それをシグナル化するスレッドが取り消されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="acd4b-121">Note that the wait operation does not cancel the threads that are signaling it.</span></span> <span data-ttu-id="acd4b-122">通常、取り消しは論理操作に適用され、待機が同期中のすべての作業項目だけでなく、イベントでの待機を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="acd4b-122">Typically, cancellation is applied to a logical operation, and that can include waiting on the event as well as all the work items that the wait is synchronizing.</span></span> <span data-ttu-id="acd4b-123">この例では、各作業項目には同じ取り消しトークンのコピーが渡されるため、取り消し要求に応答することができます。</span><span class="sxs-lookup"><span data-stu-id="acd4b-123">In this example, each work item is passed a copy of the same cancellation token so that it can respond to the cancellation request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd4b-124">参照</span><span class="sxs-lookup"><span data-stu-id="acd4b-124">See also</span></span>

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
