---
description: '詳細情報: 数値のシーケンスの合計の計算'
title: 数値のシーケンスの合計の計算
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: c4eb066b9286335111d96d32437291da9ea2d49a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712546"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a><span data-ttu-id="497b8-103">数値のシーケンスの合計の計算</span><span class="sxs-lookup"><span data-stu-id="497b8-103">Compute the Sum of Values in a Numeric Sequence</span></span>

<span data-ttu-id="497b8-104"><xref:System.Linq.Enumerable.Sum%2A> 演算子を使用すると、シーケンス内の数値の合計を計算できます。</span><span class="sxs-lookup"><span data-stu-id="497b8-104">Use the <xref:System.Linq.Enumerable.Sum%2A> operator to compute the sum of numeric values in a sequence.</span></span>  
  
 <span data-ttu-id="497b8-105">`Sum` の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 演算子には、次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="497b8-105">Note the following characteristics of the `Sum` operator in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:</span></span>  
  
- <span data-ttu-id="497b8-106">標準クエリ演算子の集計演算子 `Sum` では、空のシーケンスや null のみを含むシーケンスはゼロに評価されます。</span><span class="sxs-lookup"><span data-stu-id="497b8-106">The Standard Query Operator aggregate operator `Sum` evaluates to zero for an empty sequence or a sequence that contains only nulls.</span></span> <span data-ttu-id="497b8-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、SQL のセマンティクスは維持されます。</span><span class="sxs-lookup"><span data-stu-id="497b8-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged.</span></span> <span data-ttu-id="497b8-108">したがって、空のシーケンスまたは null のみを含むシーケンスについては、`Sum` 演算子は 0 ではなく null に評価します。</span><span class="sxs-lookup"><span data-stu-id="497b8-108">For this reason, `Sum` evaluates to null instead of to zero for an empty sequence or for a sequence that contains only nulls.</span></span>  
  
- <span data-ttu-id="497b8-109">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での集計には、中間結果に対する SQL の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="497b8-109">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="497b8-110">64 ビットの結果を使って 32 ビット整数の合計値を計算することはできません。[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] による `Sum` の変換で、オーバーフローが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="497b8-110">Sum of 32-bit integer quantities is not computed by using 64-bit results, and overflow can occur for the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Sum`.</span></span> <span data-ttu-id="497b8-111">これは、標準クエリ演算子の実装で、対応するメモリ内シーケンスでオーバーフローが発生しない場合でも起こる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="497b8-111">This possibility exists even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="497b8-112">例</span><span class="sxs-lookup"><span data-stu-id="497b8-112">Example</span></span>  

 <span data-ttu-id="497b8-113">`Order` テーブルに含まれるすべての注文の運賃の合計を求める例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="497b8-113">The following example finds the total freight of all orders in the `Order` table.</span></span>  
  
 <span data-ttu-id="497b8-114">Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`64942.6900` です。</span><span class="sxs-lookup"><span data-stu-id="497b8-114">If you run this query against the Northwind sample database, the output is: `64942.6900`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="497b8-115">例</span><span class="sxs-lookup"><span data-stu-id="497b8-115">Example</span></span>  

 <span data-ttu-id="497b8-116">すべての製品の受注単位の合計を求める例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="497b8-116">The following example finds the total number of units on order for all products.</span></span>  
  
 <span data-ttu-id="497b8-117">Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`780` です。</span><span class="sxs-lookup"><span data-stu-id="497b8-117">If you run this query against the Northwind sample database, the output is: `780`.</span></span>  
  
 <span data-ttu-id="497b8-118">`short` には `UnitsOnOrder` 型のオーバーロードがないため、short 型 (`Sum` など) をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="497b8-118">Note that you must cast `short` types (for example, `UnitsOnOrder`) because `Sum` has no overload for short types.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="497b8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="497b8-119">See also</span></span>

- [<span data-ttu-id="497b8-120">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="497b8-120">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="497b8-121">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="497b8-121">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
