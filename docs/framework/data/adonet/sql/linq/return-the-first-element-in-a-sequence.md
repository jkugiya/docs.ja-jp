---
description: '詳細情報: シーケンスの最初の要素の取得'
title: シーケンスの最初の要素の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 004e9a1f03677f6ba49916404b1c44408df40dfa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663015"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="750e8-103">シーケンスの最初の要素の取得</span><span class="sxs-lookup"><span data-stu-id="750e8-103">Return the First Element in a Sequence</span></span>

<span data-ttu-id="750e8-104"><xref:System.Linq.Enumerable.First%2A> 演算子を使用すると、シーケンスの内最初の要素を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="750e8-104">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="750e8-105"><xref:System.Linq.Enumerable.First%2A> を使用するクエリは直ちに実行されます。</span><span class="sxs-lookup"><span data-stu-id="750e8-105">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="750e8-106">は <xref:System.Linq.Enumerable.Last%2A> 演算子をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="750e8-106">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="750e8-107">例</span><span class="sxs-lookup"><span data-stu-id="750e8-107">Example</span></span>  

 <span data-ttu-id="750e8-108">次のコードは、テーブル内の最初の `Shipper` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="750e8-108">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="750e8-109">Northwind サンプル データベースに対してこのクエリを実行すると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="750e8-109">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="750e8-110">`ID = 1, Company = Speedy Express`.</span><span class="sxs-lookup"><span data-stu-id="750e8-110">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="750e8-111">例</span><span class="sxs-lookup"><span data-stu-id="750e8-111">Example</span></span>  

 <span data-ttu-id="750e8-112">次のコードは、`Customer` が BONAP の単一の `CustomerID` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="750e8-112">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="750e8-113">Northwind サンプル データベースに対してこのクエリを実行すると、結果は `ID = BONAP, Contact = Laurence Lebihan` になります。</span><span class="sxs-lookup"><span data-stu-id="750e8-113">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="750e8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="750e8-114">See also</span></span>

- [<span data-ttu-id="750e8-115">クエリの例</span><span class="sxs-lookup"><span data-stu-id="750e8-115">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="750e8-116">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="750e8-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
