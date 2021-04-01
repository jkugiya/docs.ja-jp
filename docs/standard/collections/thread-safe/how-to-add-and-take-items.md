---
description: '詳細情報: BlockingCollection の項目を個別に追加および取得する方法'
title: '方法: BlockingCollection の項目を個別に追加および取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, blocking dictionary
ms.assetid: 38f2f3d8-15e5-4bf4-9c83-2b5b6f22bad1
ms.openlocfilehash: c601cf35633838a81271a6296b9e1fcb6e389fbb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99676080"
---
# <a name="how-to-add-and-take-items-individually-from-a-blockingcollection"></a><span data-ttu-id="4ea6b-103">方法: BlockingCollection の項目を個別に追加および取得する</span><span class="sxs-lookup"><span data-stu-id="4ea6b-103">How to: Add and Take Items Individually from a BlockingCollection</span></span>

<span data-ttu-id="4ea6b-104">この例では、ブロッキングと非ブロッキングの 2 つの方法で <xref:System.Collections.Concurrent.BlockingCollection%601> の項目を追加、削除する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-104">This example shows how to add and remove items from a <xref:System.Collections.Concurrent.BlockingCollection%601> in both a blocking and a non-blocking manner.</span></span> <span data-ttu-id="4ea6b-105"><xref:System.Collections.Concurrent.BlockingCollection%601> の詳細については、「[BlockingCollection の概要](blockingcollection-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-105">For more information on <xref:System.Collections.Concurrent.BlockingCollection%601>, see [BlockingCollection Overview](blockingcollection-overview.md).</span></span>  
  
 <span data-ttu-id="4ea6b-106">空になって追加する要素がなくなるまで <xref:System.Collections.Concurrent.BlockingCollection%601> を列挙する方法の例については、「[方法: ForEach を使用して BlockingCollection 内の項目を削除する](how-to-use-foreach-to-remove.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-106">For an example of how to enumerate a <xref:System.Collections.Concurrent.BlockingCollection%601> until it is empty and no more elements will be added, see [How to: Use ForEach to Remove Items in a BlockingCollection](how-to-use-foreach-to-remove.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="4ea6b-107">例</span><span class="sxs-lookup"><span data-stu-id="4ea6b-107">Example</span></span>  

 <span data-ttu-id="4ea6b-108">この最初の例では、コレクションが一時的に空 (取得時) または最大容量 (追加時) になるか、指定されたタイムアウト期間が経過したときに、操作をブロックするように、項目を追加および取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-108">This first example shows how to add and take items so that the operations will block if the collection is either temporarily empty (when taking) or at maximum capacity (when adding), or if a specified timeout period has elapsed.</span></span> <span data-ttu-id="4ea6b-109">最大容量のブロックは、BlockingCollection が、コンストラクターで指定された最大容量で作成された場合にのみ有効になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-109">Note that blocking on maximum capacity is only enabled when the BlockingCollection has been created with a maximum capacity specified in the constructor.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#01](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example01.cs#01)]
 [!code-vb[CDS_BlockingCollection#01](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/simpleblocking.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="4ea6b-110">例</span><span class="sxs-lookup"><span data-stu-id="4ea6b-110">Example</span></span>  

 <span data-ttu-id="4ea6b-111">この 2 番目の例では、操作をブロックしないように、項目を追加および取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-111">This second example shows how to add and take items so that the operations will not block.</span></span> <span data-ttu-id="4ea6b-112">項目が存在しない場合、サイズ制限のあるコレクションの最大容量に達した場合、またはタイムアウト期間が経過した場合、<xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> または <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 操作は false を返します。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-112">If no item is present, maximum capacity on a bounded collection has been reached, or the timeout period has elapsed, then the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operation returns false.</span></span> <span data-ttu-id="4ea6b-113">これによりスレッドはしばらくの間、他の何らかの有益な処理を行い、後からもう一度新しいアイテムを取得するか、以前に追加できなかった項目を追加しようとします。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-113">This allows the thread to do some other useful work for a while and then try again later to either retrieve a new item, or try to add the same item that could not be added previously.</span></span> <span data-ttu-id="4ea6b-114">このプログラムはまた、<xref:System.Collections.Concurrent.BlockingCollection%601> へのアクセス時にキャンセルを実装する方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="4ea6b-114">The program also demonstrates how to implement cancellation when accessing a <xref:System.Collections.Concurrent.BlockingCollection%601>.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#02](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example02.cs#02)]
 [!code-vb[CDS_BlockingCollection#02](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/nonblockingbc.vb#02)]  
  
## <a name="see-also"></a><span data-ttu-id="4ea6b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ea6b-115">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="4ea6b-116">BlockingCollection の概要</span><span class="sxs-lookup"><span data-stu-id="4ea6b-116">BlockingCollection Overview</span></span>](blockingcollection-overview.md)
