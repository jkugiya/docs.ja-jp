---
description: '詳細情報: シーケンスのすべての要素が条件を満たしているかどうかの確認'
title: シーケンスのすべての要素が条件を満たしているかどうかの確認
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: a46cf7e4e213eba830dc203f9266a408103cee80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786109"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="eef23-103">シーケンスのすべての要素が条件を満たしているかどうかの確認</span><span class="sxs-lookup"><span data-stu-id="eef23-103">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>

<span data-ttu-id="eef23-104"><xref:System.Linq.Enumerable.All%2A> 演算子は、シーケンスのすべての要素が条件を満たす場合に `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="eef23-104">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="eef23-105"><xref:System.Linq.Queryable.Any%2A> 演算子は、シーケンスの要素が 1 つでも条件を満たす場合に `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="eef23-105">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eef23-106">例</span><span class="sxs-lookup"><span data-stu-id="eef23-106">Example</span></span>  

 <span data-ttu-id="eef23-107">次の例では、最低 1 件の注文がある顧客のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="eef23-107">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="eef23-108">`Where`/`where` 句は、指定した `Customer` に `Order` がある場合に `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="eef23-108">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="eef23-109">例</span><span class="sxs-lookup"><span data-stu-id="eef23-109">Example</span></span>  

 <span data-ttu-id="eef23-110">次の Visual Basic コードでは、注文がない顧客のリストを調べ、リストに記載されている顧客に連絡先名があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eef23-110">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="eef23-111">例</span><span class="sxs-lookup"><span data-stu-id="eef23-111">Example</span></span>  

 <span data-ttu-id="eef23-112">次の C# コードでは、注文の `ShipCity` が "C" で始まる顧客のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="eef23-112">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="eef23-113">注文のない顧客も結果に含まれます。</span><span class="sxs-lookup"><span data-stu-id="eef23-113">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="eef23-114">(<xref:System.Linq.Queryable.All%2A> 演算子はシーケンスが空の場合に `true` を返すように設計されています)。注文のない顧客を削除してコンソールに出力するには、`Count` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="eef23-114">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="eef23-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="eef23-115">See also</span></span>

- [<span data-ttu-id="eef23-116">クエリの例</span><span class="sxs-lookup"><span data-stu-id="eef23-116">Query Examples</span></span>](query-examples.md)
