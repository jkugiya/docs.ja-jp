---
description: '詳細情報: 動的パーティションを実装する方法'
title: 方法:動的パーティションを実装する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 3f0b383b9f4f7a47acb21d3ec3451b1761a3368c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701964"
---
# <a name="how-to-implement-dynamic-partitions"></a><span data-ttu-id="3f4f0-103">方法:動的パーティションを実装する</span><span class="sxs-lookup"><span data-stu-id="3f4f0-103">How to: Implement Dynamic Partitions</span></span>

<span data-ttu-id="3f4f0-104">次の例は、特定のオーバーロード <xref:System.Threading.Tasks.Parallel.ForEach%2A> と PLINQ から動的なパーティション分割を実装するカスタム <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> を実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3f4f0-104">The following example shows how to implement a custom <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> that implements dynamic partitioning and can be used from certain overloads <xref:System.Threading.Tasks.Parallel.ForEach%2A> and from PLINQ.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f4f0-105">例</span><span class="sxs-lookup"><span data-stu-id="3f4f0-105">Example</span></span>

<span data-ttu-id="3f4f0-106">列挙子でパーティションが <xref:System.Collections.IEnumerator.MoveNext%2A> を呼び出すたびに、列挙子はパーティションに 1 つのリスト要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="3f4f0-106">Each time a partition calls <xref:System.Collections.IEnumerator.MoveNext%2A> on the enumerator, the enumerator provides the partition with one list element.</span></span> <span data-ttu-id="3f4f0-107">PLINQ と <xref:System.Threading.Tasks.Parallel.ForEach%2A> では、パーティションは <xref:System.Threading.Tasks.Task> インスタンスです。</span><span class="sxs-lookup"><span data-stu-id="3f4f0-107">In the case of PLINQ and <xref:System.Threading.Tasks.Parallel.ForEach%2A>, the partition is a <xref:System.Threading.Tasks.Task> instance.</span></span> <span data-ttu-id="3f4f0-108">要求は、複数のスレッドで同時に発生しているため、現在のインデックスへのアクセスは同期されます。</span><span class="sxs-lookup"><span data-stu-id="3f4f0-108">Because requests are happening concurrently on multiple threads, access to the current index is synchronized.</span></span>  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

<span data-ttu-id="3f4f0-109">これは、各チャンクが 1 つの要素で構成されるチャンク パーティション分割の例です。</span><span class="sxs-lookup"><span data-stu-id="3f4f0-109">This is an example of chunk partitioning, with each chunk consisting of one element.</span></span> <span data-ttu-id="3f4f0-110">一度に複数の要素を提供することにより、ロックの競合を減らし、理論的により高速なパフォーマンスを実現することができます。</span><span class="sxs-lookup"><span data-stu-id="3f4f0-110">By providing more elements at a time, you could reduce the contention over the lock and theoretically achieve faster performance.</span></span> <span data-ttu-id="3f4f0-111">ただし、チャンクが大きい場合、すべての作業が完了するまで、すべてのスレッドをビジーにするために、ある時点で追加の負荷分散ロジックが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3f4f0-111">However, at some point, larger chunks might require additional load-balancing logic in order to keep all threads busy until all the work is done.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4f0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f4f0-112">See also</span></span>

* [<span data-ttu-id="3f4f0-113">PLINQ および TPL 用のカスタム パーティショナー</span><span class="sxs-lookup"><span data-stu-id="3f4f0-113">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
* [<span data-ttu-id="3f4f0-114">方法:静的パーティション分割用にパーティショナーを実装する</span><span class="sxs-lookup"><span data-stu-id="3f4f0-114">How to: Implement a Partitioner for Static Partitioning</span></span>](how-to-implement-a-partitioner-for-static-partitioning.md)
