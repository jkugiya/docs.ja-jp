---
description: '詳細情報: 下位レベルの同期に SpinLock を使用する方法'
title: '方法: 下位レベルの同期に SpinLock を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: 854d34b94d04ea4817b7818193324b8dc4d0a44a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666746"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="0a890-103">方法: 下位レベルの同期に SpinLock を使用する</span><span class="sxs-lookup"><span data-stu-id="0a890-103">How to: use SpinLock for low-level synchronization</span></span>

<span data-ttu-id="0a890-104"><xref:System.Threading.SpinLock> の使用例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="0a890-104">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="0a890-105">この例では、クリティカル セクションが実行する作業量は最小限であるため、<xref:System.Threading.SpinLock> に適しています。</span><span class="sxs-lookup"><span data-stu-id="0a890-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="0a890-106">作業量を少し増やすと、標準ロックと比較して <xref:System.Threading.SpinLock> のパフォーマンスは高まります。</span><span class="sxs-lookup"><span data-stu-id="0a890-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="0a890-107">ただし、SpinLock が標準ロックよりも高負荷になるポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="0a890-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="0a890-108">プロファイリング ツールでコンカレンシープロファイリング機能を使用して、どのタイプのロックを使用すればプログラムのパフォーマンスが高まるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="0a890-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="0a890-109">詳細については、「[コンカレンシー ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a890-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="0a890-110"><xref:System.Threading.SpinLock> は、共有リソースのロックが非常に長い期間使用されない場合に有用なことがあります。</span><span class="sxs-lookup"><span data-stu-id="0a890-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="0a890-111">そのような場合、マルチコア コンピューターでは、ロックが解除されるまで数回のサイクルの間、ブロックされたスレッドをスピンさせると効率が高まることがあります。</span><span class="sxs-lookup"><span data-stu-id="0a890-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="0a890-112">スピンするとスレッドはブロックされなくなりますが、これは CPU 負荷の高いプロセスです。</span><span class="sxs-lookup"><span data-stu-id="0a890-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="0a890-113">ハイパースレッディングを使用するシステムでは、<xref:System.Threading.SpinLock> は特定の状況でスピンを停止して、論理プロセッサの不足や優先順位の逆転が発生するのを回避します。</span><span class="sxs-lookup"><span data-stu-id="0a890-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="0a890-114">この例では、<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> クラスを使用するため、マルチスレッド アクセスにはユーザーによる同期が必要になります。</span><span class="sxs-lookup"><span data-stu-id="0a890-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="0a890-115">別の選択肢としては <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> を使用します。その場合、ユーザー ロックは不要です。</span><span class="sxs-lookup"><span data-stu-id="0a890-115">Another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="0a890-116"><xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType> の呼び出しに `false` が使用されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="0a890-116">Note the use of `false` in the call to <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0a890-117">これにより、最適なパフォーマンスを得られます。</span><span class="sxs-lookup"><span data-stu-id="0a890-117">This provides the best performance.</span></span> <span data-ttu-id="0a890-118">メモリ フェンスを使用するには、IA64 アーキテクチャで `true` を指定します。これにより、書き込みバッファーがフラッシュされるので、ロックを使用して他のスレッドを確実に入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a890-118">Specify `true` on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to enter.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0a890-119">参照</span><span class="sxs-lookup"><span data-stu-id="0a890-119">See also</span></span>

- [<span data-ttu-id="0a890-120">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="0a890-120">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="0a890-121">lock ステートメント (C#)</span><span class="sxs-lookup"><span data-stu-id="0a890-121">lock statement (C#)</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
- [<span data-ttu-id="0a890-122">SyncLock ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a890-122">SyncLock statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/synclock-statement.md)
