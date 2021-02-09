---
description: '詳細情報: 2 つのシーケンスの差集合の取得'
title: 2 つのシーケンスの差集合の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 6836195ac4e1ee678fd3e8089e7c341f7dd247e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662984"
---
# <a name="return-the-set-difference-between-two-sequences"></a><span data-ttu-id="8737e-103">2 つのシーケンスの差集合の取得</span><span class="sxs-lookup"><span data-stu-id="8737e-103">Return the Set Difference Between Two Sequences</span></span>

<span data-ttu-id="8737e-104">2 つのシーケンスの差集合を返すには、<xref:System.Linq.Queryable.Except%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="8737e-104">Use the <xref:System.Linq.Queryable.Except%2A> operator to return the set difference between two sequences.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8737e-105">例</span><span class="sxs-lookup"><span data-stu-id="8737e-105">Example</span></span>  

 <span data-ttu-id="8737e-106">この例では、<xref:System.Linq.Queryable.Except%2A> を使用して、`Customers` は居住しているが `Employees` は居住していないすべての国/リージョンのシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="8737e-106">This example uses <xref:System.Linq.Queryable.Except%2A> to return a sequence of all countries/regions in which `Customers` live but in which no `Employees` live.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 <span data-ttu-id="8737e-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Linq.Queryable.Except%2A> 演算は集合でのみ適切に定義されます。</span><span class="sxs-lookup"><span data-stu-id="8737e-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Linq.Queryable.Except%2A> operation is well defined only on sets.</span></span> <span data-ttu-id="8737e-108">マルチセットのセマンティクスは未定義です。</span><span class="sxs-lookup"><span data-stu-id="8737e-108">The semantics for multisets is undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8737e-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8737e-109">See also</span></span>

- [<span data-ttu-id="8737e-110">クエリの例</span><span class="sxs-lookup"><span data-stu-id="8737e-110">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="8737e-111">標準クエリ演算子の変換</span><span class="sxs-lookup"><span data-stu-id="8737e-111">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
