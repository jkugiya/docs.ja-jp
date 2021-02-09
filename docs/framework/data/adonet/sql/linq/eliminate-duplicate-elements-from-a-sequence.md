---
description: '詳細情報: シーケンスからの重複する要素の削除'
title: シーケンスからの重複する要素の削除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: f371fc27794361e3ea92d342f845996d9291d30c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786096"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a><span data-ttu-id="074b1-103">シーケンスからの重複する要素の削除</span><span class="sxs-lookup"><span data-stu-id="074b1-103">Eliminate Duplicate Elements from a Sequence</span></span>

<span data-ttu-id="074b1-104">重複する要素をシーケンスから削除するには、<xref:System.Linq.Queryable.Distinct%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="074b1-104">Use the <xref:System.Linq.Queryable.Distinct%2A> operator to eliminate duplicate elements from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="074b1-105">例</span><span class="sxs-lookup"><span data-stu-id="074b1-105">Example</span></span>  

 <span data-ttu-id="074b1-106">次の例では、<xref:System.Linq.Queryable.Distinct%2A> を使用して、顧客の住所がある市のシーケンスを選択します。それぞれの市はシーケンス内で重複しません。</span><span class="sxs-lookup"><span data-stu-id="074b1-106">The following example uses <xref:System.Linq.Queryable.Distinct%2A> to select a sequence of the unique cities that have customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a><span data-ttu-id="074b1-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="074b1-107">See also</span></span>

- [<span data-ttu-id="074b1-108">クエリの例</span><span class="sxs-lookup"><span data-stu-id="074b1-108">Query Examples</span></span>](query-examples.md)
