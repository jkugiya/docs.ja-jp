---
description: '詳細情報: 並列および順次の LINQ クエリを連結する方法'
title: '方法: 並列および順次の LINQ クエリを連結する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: b3ff966b944516bed6cfb4cacd32cb550455fea9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702068"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="a8deb-103">方法: 並列および順次の LINQ クエリを連結する</span><span class="sxs-lookup"><span data-stu-id="a8deb-103">How to: Combine Parallel and Sequential LINQ Queries</span></span>

<span data-ttu-id="a8deb-104">この例では、PLINQ にクエリ内の後続のすべての演算子を順次処理するように指示する <xref:System.Linq.ParallelEnumerable.AsSequential%2A> メソッドの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a8deb-104">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="a8deb-105">順次処理はしばしば並列処理よりも遅いですが、正しい結果を出すためにこれが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a8deb-105">Although sequential processing is often slower than parallel, sometimes it's necessary to produce correct results.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8deb-106">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8deb-106">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="a8deb-107">高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8deb-107">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8deb-108">例</span><span class="sxs-lookup"><span data-stu-id="a8deb-108">Example</span></span>  

 <span data-ttu-id="a8deb-109">次の例は、クエリの前の句で確立された順序を保持する <xref:System.Linq.ParallelEnumerable.AsSequential%2A> が必要な 1 つのシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="a8deb-109">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8deb-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a8deb-110">Compiling the Code</span></span>  

 <span data-ttu-id="a8deb-111">このコードをコンパイルして実行するには、これを [PLINQ データのサンプル](plinq-data-sample.md) プロジェクトに貼り付けて、`Main` からメソッドを呼び出す行を追加し、**F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a8deb-111">To compile and run this code, paste it into the [PLINQ Data Sample](plinq-data-sample.md) project, add a line to call the method from `Main`, and press **F5**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8deb-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8deb-112">See also</span></span>

- [<span data-ttu-id="a8deb-113">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a8deb-113">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
