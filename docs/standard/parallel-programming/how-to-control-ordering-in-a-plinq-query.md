---
description: '詳細情報: PLINQ クエリの順序を制御する方法'
title: 方法:PLINQ クエリの順序を制御する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: 9c181a9dc7697b1a838d04caaeadb892f9ec4796
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702133"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="07c80-103">方法:PLINQ クエリの順序を制御する</span><span class="sxs-lookup"><span data-stu-id="07c80-103">How to: Control Ordering in a PLINQ Query</span></span>

<span data-ttu-id="07c80-104">以下の例では、<xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 拡張メソッドを使用して PLINQ クエリの順序を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="07c80-104">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="07c80-105">これらの例は使用法を示すことを主な目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が速い場合もあれば遅い場合もあります。</span><span class="sxs-lookup"><span data-stu-id="07c80-105">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07c80-106">例</span><span class="sxs-lookup"><span data-stu-id="07c80-106">Example</span></span>  

 <span data-ttu-id="07c80-107">次の例では、ソース シーケンスの順序を維持します。</span><span class="sxs-lookup"><span data-stu-id="07c80-107">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="07c80-108">この操作が必要になるのは、たとえば、正確な結果を生成するためにクエリ演算子で順序ありのソース シーケンスが求められる場合です。</span><span class="sxs-lookup"><span data-stu-id="07c80-108">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="07c80-109">例</span><span class="sxs-lookup"><span data-stu-id="07c80-109">Example</span></span>  

 <span data-ttu-id="07c80-110">次の例は、ソース シーケンスで順序付けが求められるクエリ演算子を示しています。</span><span class="sxs-lookup"><span data-stu-id="07c80-110">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="07c80-111">これらの演算子は、順序なしのシーケンスで動作しますが、予測できない結果を生成する場合があります。</span><span class="sxs-lookup"><span data-stu-id="07c80-111">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="07c80-112">このメソッドを実行するには、[PLINQ Data Sample](plinq-data-sample.md) プロジェクトの PLINQDataSample クラスに貼り付け、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="07c80-112">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07c80-113">例</span><span class="sxs-lookup"><span data-stu-id="07c80-113">Example</span></span>  

 <span data-ttu-id="07c80-114">次の例は、クエリの最初の部分で順序を維持した後に、join 句のパフォーマンスを向上させるために順序を削除し、最終的な結果に順序を再適用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="07c80-114">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="07c80-115">このメソッドを実行するには、[PLINQ Data Sample](plinq-data-sample.md) プロジェクトの PLINQDataSample クラスに貼り付け、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="07c80-115">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c80-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="07c80-116">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="07c80-117">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="07c80-117">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
