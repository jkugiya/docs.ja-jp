---
description: '詳細情報: シーケンス内の要素数のカウント'
title: シーケンス内の要素数のカウント
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: 91030516098e900229a1e131ea0c9a7d8bef4034
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663080"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a><span data-ttu-id="5d8a6-103">シーケンス内の要素数のカウント</span><span class="sxs-lookup"><span data-stu-id="5d8a6-103">Count the Number of Elements in a Sequence</span></span>

<span data-ttu-id="5d8a6-104"><xref:System.Linq.Enumerable.Count%2A> 演算子を使用すると、シーケンス内の要素数をカウントできます。</span><span class="sxs-lookup"><span data-stu-id="5d8a6-104">Use the <xref:System.Linq.Enumerable.Count%2A> operator to count the number of elements in a sequence.</span></span>  
  
 <span data-ttu-id="5d8a6-105">Northwind サンプル データベースに対してこのクエリを実行すると、出力は `91` になります。</span><span class="sxs-lookup"><span data-stu-id="5d8a6-105">Running this query against the Northwind sample database produces an output of `91`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d8a6-106">例</span><span class="sxs-lookup"><span data-stu-id="5d8a6-106">Example</span></span>  

 <span data-ttu-id="5d8a6-107">データベース内の `Customers` の数をカウントする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5d8a6-107">The following example counts the number of `Customers` in the database.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="5d8a6-108">例</span><span class="sxs-lookup"><span data-stu-id="5d8a6-108">Example</span></span>  

 <span data-ttu-id="5d8a6-109">データベース内の製品のうち、生産中止になっていない製品の数をカウントする例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5d8a6-109">The following example counts the number of products in the database that have not been discontinued.</span></span>  
  
 <span data-ttu-id="5d8a6-110">Northwind サンプル データベースに対してこのクエリを実行すると、出力は `69` になります。</span><span class="sxs-lookup"><span data-stu-id="5d8a6-110">Running this example against the Northwind sample database produces an output of `69`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5d8a6-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d8a6-111">See also</span></span>

- [<span data-ttu-id="5d8a6-112">集計クエリ</span><span class="sxs-lookup"><span data-stu-id="5d8a6-112">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="5d8a6-113">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="5d8a6-113">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
