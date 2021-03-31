---
description: '詳細情報: カスタムの PLINQ 集約関数を記述する方法'
title: 方法:カスタムの PLINQ 集約関数を記述する
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: a16b211ee735b51ed56dd7af3a8602e0f8cd3f28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701613"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="646be-103">方法:カスタムの PLINQ 集約関数を記述する</span><span class="sxs-lookup"><span data-stu-id="646be-103">How to: Write a Custom PLINQ Aggregate Function</span></span>

<span data-ttu-id="646be-104">この例は、<xref:System.Linq.ParallelEnumerable.Aggregate%2A> メソッドを使用して、カスタム集計関数をソース シーケンスに適用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="646be-104">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="646be-105">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="646be-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="646be-106">高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="646be-106">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="646be-107">例</span><span class="sxs-lookup"><span data-stu-id="646be-107">Example</span></span>  

 <span data-ttu-id="646be-108">次の例では、整数シーケンスの標準偏差を計算します。</span><span class="sxs-lookup"><span data-stu-id="646be-108">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="646be-109">この例では、PLINQ に固有の Aggregate 標準クエリ演算子のオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="646be-109">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="646be-110">このオーバーロードでは、3 番目の入力パラメーターとして、追加の <xref:System.Func%603?displayProperty=nameWithType> を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="646be-110">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="646be-111">このデリゲートは、集計結果で最終計算を実行する前に、すべてのスレッドからの結果を結合します。</span><span class="sxs-lookup"><span data-stu-id="646be-111">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="646be-112">この例では、すべてのスレッドからの合計をまとめます。</span><span class="sxs-lookup"><span data-stu-id="646be-112">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="646be-113">ラムダ式の本体が単一の式で構成されている場合、<xref:System.Func%602?displayProperty=nameWithType> デリゲートの戻り値は式の値になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="646be-113">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646be-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="646be-114">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="646be-115">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="646be-115">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
