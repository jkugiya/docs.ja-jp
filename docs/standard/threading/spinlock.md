---
description: '詳細情報: SpinLock'
title: SpinLock
ms.date: 03/30/2017
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: 44285f27b387d411b1cdd511b7d191aa2a2166b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792350"
---
# <a name="spinlock"></a><span data-ttu-id="28edd-103">SpinLock</span><span class="sxs-lookup"><span data-stu-id="28edd-103">SpinLock</span></span>

<span data-ttu-id="28edd-104"><xref:System.Threading.SpinLock> 構造体は低レベルで相互排他的な同期プリミティブであり、ロックの取得を待機する間にスピンします。</span><span class="sxs-lookup"><span data-stu-id="28edd-104">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="28edd-105">マルチコア コンピューターでは、待機時間が短いことが予測され、競合を最小限に抑えられる場合、パフォーマンスは他の種類のロックよりも <xref:System.Threading.SpinLock> の方が優れています。</span><span class="sxs-lookup"><span data-stu-id="28edd-105">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="28edd-106">ただし、プロファイルにより、<xref:System.Threading.Monitor?displayProperty=nameWithType> メソッドまたは <xref:System.Threading.Interlocked> メソッドがプログラムのパフォーマンスを大幅に低下させていることがわかった場合にのみ、<xref:System.Threading.SpinLock> を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="28edd-106">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="28edd-107"><xref:System.Threading.SpinLock> では、ロックをまだ取得していない場合でも、スレッドのタイム スライスが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28edd-107"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="28edd-108">スレッドの優先順位の逆転を避ける場合と、ガベージ コレクターを進める場合にこのようになります。</span><span class="sxs-lookup"><span data-stu-id="28edd-108">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="28edd-109"><xref:System.Threading.SpinLock> を使用する場合は、スレッドが一定時間ロックを保持できないことと、スレッドがロックを保持している間はブロックできないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="28edd-109">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="28edd-110">SpinLock は値の型であるため、2 つのコピーで同じロックを参照する場合は、参照渡しで明示的に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="28edd-110">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="28edd-111">この型の使用方法の詳細については、「<xref:System.Threading.SpinLock?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28edd-111">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="28edd-112">例については、「[方法: 下位レベルの同期に SpinLock を使用する](how-to-use-spinlock-for-low-level-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28edd-112">For an example, see [How to: Use SpinLock for Low-Level Synchronization](how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="28edd-113"><xref:System.Threading.SpinLock> では *スレッド*-*追跡* モードがサポートされ、開発フェーズ中に使用することができ、特定の時間にロックを保持しているスレッドの追跡に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="28edd-113"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="28edd-114">スレッド追跡モードはデバッグに非常に役立ちますが、パフォーマンスが低下する可能性があるため、リリース バージョンのプログラムでは無効にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="28edd-114">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="28edd-115">詳細については、「[方法: SpinLock のスレッド追跡モードを有効にする](how-to-enable-thread-tracking-mode-in-spinlock.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28edd-115">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28edd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="28edd-116">See also</span></span>

- [<span data-ttu-id="28edd-117">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="28edd-117">Threading Objects and Features</span></span>](threading-objects-and-features.md)
