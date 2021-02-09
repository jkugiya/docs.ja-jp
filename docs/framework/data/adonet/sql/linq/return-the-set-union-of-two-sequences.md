---
description: '詳細情報: 2 つのシーケンスの和集合の取得'
title: 2 つのシーケンスの和集合の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 5541316560c05712e22c54f706b02d868fadb381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662963"
---
# <a name="return-the-set-union-of-two-sequences"></a><span data-ttu-id="9132e-103">2 つのシーケンスの和集合の取得</span><span class="sxs-lookup"><span data-stu-id="9132e-103">Return the Set Union of Two Sequences</span></span>

<span data-ttu-id="9132e-104">2 つのシーケンスの和集合を返すには、<xref:System.Linq.Queryable.Union%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="9132e-104">Use the <xref:System.Linq.Queryable.Union%2A> operator to return the set union of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9132e-105">例</span><span class="sxs-lookup"><span data-stu-id="9132e-105">Example</span></span>  

 <span data-ttu-id="9132e-106">この例では、<xref:System.Linq.Queryable.Union%2A> を使用して、`Customers` と `Employees` のいずれかが居住しているすべての国と地域のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="9132e-106">This example uses <xref:System.Linq.Queryable.Union%2A> to return a sequence of all countries/regions in which there are either `Customers` or `Employees`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 <span data-ttu-id="9132e-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Linq.Queryable.Union%2A> 演算子は、マルチセットの順序なし連結演算子として、マルチセットに対して定義されます (事実上、SQL の [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) 句の結果)。</span><span class="sxs-lookup"><span data-stu-id="9132e-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Union%2A> operator is defined for multisets as the unordered concatenation of the multisets (effectively the result of the [`UNION ALL`](/sql/t-sql/language-elements/set-operators-union-transact-sql) clause in SQL).</span></span>

<span data-ttu-id="9132e-108">詳細な情報と例については、「<xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9132e-108">For more info and examples, see <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9132e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="9132e-109">See also</span></span>

- [<span data-ttu-id="9132e-110">クエリの例</span><span class="sxs-lookup"><span data-stu-id="9132e-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="9132e-111">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="9132e-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
