---
description: '詳細情報: 2 つのシーケンスの積集合の取得'
title: 2 つのシーケンスの積集合の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 163e138761caadb73b6dc5d672c02353a88a2c22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662983"
---
# <a name="return-the-set-intersection-of-two-sequences"></a><span data-ttu-id="9b9a0-103">2 つのシーケンスの積集合の取得</span><span class="sxs-lookup"><span data-stu-id="9b9a0-103">Return the Set Intersection of Two Sequences</span></span>

<span data-ttu-id="9b9a0-104">2 つのシーケンスの積集合を返すには、<xref:System.Linq.Queryable.Intersect%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="9b9a0-104">Use the <xref:System.Linq.Queryable.Intersect%2A> operator to return the set intersection of two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b9a0-105">例</span><span class="sxs-lookup"><span data-stu-id="9b9a0-105">Example</span></span>  

 <span data-ttu-id="9b9a0-106">この例では、<xref:System.Linq.Queryable.Intersect%2A> を使用して、`Customers` と `Employees` の両方が居住しているすべての国や地域のシーケンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="9b9a0-106">This example uses <xref:System.Linq.Queryable.Intersect%2A> to return a sequence of all countries/regions in which both `Customers` and `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 <span data-ttu-id="9b9a0-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Linq.Queryable.Intersect%2A> 演算は集合でのみ適切に定義されます。</span><span class="sxs-lookup"><span data-stu-id="9b9a0-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Intersect%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="9b9a0-108">マルチセットのセマンティクスは未定義です。</span><span class="sxs-lookup"><span data-stu-id="9b9a0-108">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b9a0-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b9a0-109">See also</span></span>

- [<span data-ttu-id="9b9a0-110">クエリの例</span><span class="sxs-lookup"><span data-stu-id="9b9a0-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="9b9a0-111">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="9b9a0-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
