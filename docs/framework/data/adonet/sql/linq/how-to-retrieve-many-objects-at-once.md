---
description: '詳細情報: 方法:多くのオブジェクトを一度に取得する'
title: '方法: 多くのオブジェクトを一度に取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 18aff4d8-bde8-461b-9960-ccabb24e9d22
ms.openlocfilehash: 2bc202e09c64f2a1956b8688be30cfd87fb655c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802009"
---
# <a name="how-to-retrieve-many-objects-at-once"></a><span data-ttu-id="cdf21-103">方法: 多くのオブジェクトを一度に取得する</span><span class="sxs-lookup"><span data-stu-id="cdf21-103">How to: Retrieve Many Objects At Once</span></span>

<span data-ttu-id="cdf21-104">多くのオブジェクトを 1 つのクエリで取得するには、<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> を使用します。</span><span class="sxs-lookup"><span data-stu-id="cdf21-104">You can retrieve many objects in one query by using <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdf21-105">例</span><span class="sxs-lookup"><span data-stu-id="cdf21-105">Example</span></span>  

 <span data-ttu-id="cdf21-106"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> メソッドを使用して、`Customer` と `Order` の両方を取得するコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cdf21-106">The following code uses the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to retrieve both `Customer` and `Order` objects.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#9)]
 [!code-vb[DLinqQueryConcepts#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="cdf21-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="cdf21-107">See also</span></span>

- [<span data-ttu-id="cdf21-108">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="cdf21-108">Query Concepts</span></span>](query-concepts.md)
