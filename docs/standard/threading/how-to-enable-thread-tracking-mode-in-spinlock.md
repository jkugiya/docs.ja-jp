---
description: '詳細情報: SpinLock のスレッド追跡モードを有効にする方法'
title: '方法: SpinLock のスレッド追跡モードを有効にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: 376582c7ccde999bd010753819159f6f8da92bf3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666902"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="35df8-103">方法: SpinLock のスレッド追跡モードを有効にする</span><span class="sxs-lookup"><span data-stu-id="35df8-103">How to: Enable Thread-Tracking Mode in SpinLock</span></span>

<span data-ttu-id="35df8-104"><xref:System.Threading.SpinLock?displayProperty=nameWithType> は低レベルの相互排他ロックであり、待機時間が非常に短いシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="35df8-104"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="35df8-105"><xref:System.Threading.SpinLock> は再入可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="35df8-105"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="35df8-106">スレッドはロックを取得した後、ロックを正しく解放してから再度取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35df8-106">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="35df8-107">通常、ロックを再取得しようとすると、デッドロックが発生し、デッドロックのデバッグが非常に困難になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="35df8-107">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="35df8-108">開発の支援手段として、<xref:System.Threading.SpinLock?displayProperty=nameWithType> ではスレッド追跡モードがサポートされ、スレッドが既に保持しているロックを再取得しようとしたときに例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35df8-108">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="35df8-109">これにより、ロックが正しく解放されたなかった位置を見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="35df8-109">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="35df8-110">スレッド追跡モードを有効にするには、ブール入力パラメーターを受け取る <xref:System.Threading.SpinLock> コンストラクターを使用して、`true` の引数を渡します。</span><span class="sxs-lookup"><span data-stu-id="35df8-110">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="35df8-111">開発およびテスト フェーズの完了後は、パフォーマンスを向上させるため、スレッド追跡モードを無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="35df8-111">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35df8-112">例</span><span class="sxs-lookup"><span data-stu-id="35df8-112">Example</span></span>  

 <span data-ttu-id="35df8-113">次の例はスレッド追跡モードを示しています。</span><span class="sxs-lookup"><span data-stu-id="35df8-113">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="35df8-114">以下のいずれかの結果の原因となるコード エラーをシミュレートするために、ロックを正しく解放する行がコメントアウトされています。</span><span class="sxs-lookup"><span data-stu-id="35df8-114">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
- <span data-ttu-id="35df8-115">`true` (Visual Basic では `True`) の引数を使用して <xref:System.Threading.SpinLock> が作成された場合、例外がスローされる。</span><span class="sxs-lookup"><span data-stu-id="35df8-115">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
- <span data-ttu-id="35df8-116">`false` (Visual Basic では `False`) の引数を使用して <xref:System.Threading.SpinLock> が作成された場合、デッドロックが発生する。</span><span class="sxs-lookup"><span data-stu-id="35df8-116">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="35df8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="35df8-117">See also</span></span>

- [<span data-ttu-id="35df8-118">SpinLock</span><span class="sxs-lookup"><span data-stu-id="35df8-118">SpinLock</span></span>](spinlock.md)
