---
description: '詳細情報: 2 つのシーケンスの連結'
title: 2 つのシーケンスの連結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 5e48f3e2900bf53d042eb9c2aad6535bad9ec7e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773174"
---
# <a name="concatenate-two-sequences"></a><span data-ttu-id="0793e-103">2 つのシーケンスの連結</span><span class="sxs-lookup"><span data-stu-id="0793e-103">Concatenate Two Sequences</span></span>

<span data-ttu-id="0793e-104">2 つのシーケンスを連結するには、<xref:System.Linq.Queryable.Concat%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="0793e-104">Use the <xref:System.Linq.Queryable.Concat%2A> operator to concatenate two sequences.</span></span>  
  
 <span data-ttu-id="0793e-105"><xref:System.Linq.Queryable.Concat%2A> 演算子は、受信側と引数の順序が同じである、順序付けされたマルチセットに対して定義されます。</span><span class="sxs-lookup"><span data-stu-id="0793e-105">The <xref:System.Linq.Queryable.Concat%2A> operator is defined for ordered multisets where the orders of the receiver and the argument are the same.</span></span>  
  
 <span data-ttu-id="0793e-106">SQL での順序付けは、結果が作成される前の最終段階です。</span><span class="sxs-lookup"><span data-stu-id="0793e-106">Ordering in SQL is the final step before results are produced.</span></span> <span data-ttu-id="0793e-107">このため、<xref:System.Linq.Queryable.Concat%2A> 演算子は `UNION ALL` を使用して実装され、その引数の順序を保持しません。</span><span class="sxs-lookup"><span data-stu-id="0793e-107">For this reason, the <xref:System.Linq.Queryable.Concat%2A> operator is implemented by using `UNION ALL` and does not preserve the order of its arguments.</span></span> <span data-ttu-id="0793e-108">結果内での順序付けを正しく行うには、結果の順序を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0793e-108">To make sure ordering is correct in the results, make sure to explicitly order the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0793e-109">例</span><span class="sxs-lookup"><span data-stu-id="0793e-109">Example</span></span>  

 <span data-ttu-id="0793e-110">この例では、<xref:System.Linq.Queryable.Concat%2A> を使用して、すべての `Customer` と `Employee` の電話番号と FAX 番号のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="0793e-110">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` telephone and fax numbers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a><span data-ttu-id="0793e-111">例</span><span class="sxs-lookup"><span data-stu-id="0793e-111">Example</span></span>  

 <span data-ttu-id="0793e-112">この例では、<xref:System.Linq.Queryable.Concat%2A> を使用して、すべての `Customer` と `Employee` の名前と電話番号のマッピングのシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="0793e-112">This example uses <xref:System.Linq.Queryable.Concat%2A> to return a sequence of all `Customer` and `Employee` name and telephone number mappings.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a><span data-ttu-id="0793e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0793e-113">See also</span></span>

- [<span data-ttu-id="0793e-114">クエリの例</span><span class="sxs-lookup"><span data-stu-id="0793e-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="0793e-115">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="0793e-115">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
