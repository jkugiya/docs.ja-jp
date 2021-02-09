---
description: '詳細情報: 方法:DataContext レベルでフィルター処理する'
title: '方法: DataContext レベルでフィルター処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: ffb287ac1ef8cc19044ec3d519e745f905fe213d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785979"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="27a97-103">方法: DataContext レベルでフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="27a97-103">How to: Filter at the DataContext Level</span></span>

<span data-ttu-id="27a97-104">`EntitySets` を `DataContext` レベルでフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="27a97-104">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="27a97-105">このフィルター処理は、対象の <xref:System.Data.Linq.DataContext> インスタンスを使って実行されたすべてのクエリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="27a97-105">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27a97-106">例</span><span class="sxs-lookup"><span data-stu-id="27a97-106">Example</span></span>  

 <span data-ttu-id="27a97-107">次の例では、あらかじめ読み込まれた顧客からの注文を <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> に基づいてフィルター処理するために `ShippedDate` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="27a97-107">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="27a97-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="27a97-108">See also</span></span>

- [<span data-ttu-id="27a97-109">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="27a97-109">Query Concepts</span></span>](query-concepts.md)
