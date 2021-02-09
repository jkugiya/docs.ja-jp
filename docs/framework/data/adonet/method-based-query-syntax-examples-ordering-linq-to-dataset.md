---
description: '詳細情報: メソッド ベースのクエリ構文例:順序付け (LINQ to DataSet)'
title: メソッド ベースのクエリ構文例:順序付け (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f9ce4fd-e84f-48c0-bb64-89e217236d3e
ms.openlocfilehash: d655ff52fe30a9af15245a4c9989062107bb6842
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672661"
---
# <a name="method-based-query-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="13872-103">メソッド ベースのクエリ構文例:順序付け (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="13872-103">Method-Based Query Syntax Examples: Ordering (LINQ to DataSet)</span></span>

<span data-ttu-id="13872-104">このトピックでは、<xref:System.Linq.Enumerable.OrderBy%2A> に対し、<xref:System.Linq.Enumerable.Reverse%2A>、<xref:System.Linq.Enumerable.ThenBy%2A>、<xref:System.Data.DataSet> の各メソッドを使ってクエリを実行し、その結果をメソッドのクエリ構文を使って並べ替える例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="13872-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>,  <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenBy%2A> methods to query a <xref:System.Data.DataSet> and order the results using the method query syntax.</span></span>  
  
 <span data-ttu-id="13872-105">これらの例で使用されている `FillDataSet` メソッドの指定については、「[DataSet へのデータの読み込み](loading-data-into-a-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13872-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="13872-106">このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="13872-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="13872-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="13872-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="13872-108">詳細については、[Visual Studio で LINQ to DataSet プロジェクトを作成する](how-to-create-a-linq-to-dataset-project-in-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13872-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="13872-109">OrderBy</span><span class="sxs-lookup"><span data-stu-id="13872-109">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="13872-110">例</span><span class="sxs-lookup"><span data-stu-id="13872-110">Example</span></span>  

 <span data-ttu-id="13872-111">この例では、<xref:System.Linq.Enumerable.OrderBy%2A> メソッドおよびカスタム Comparer を使用し、大文字と小文字を区別せずに姓の並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="13872-111">This example uses the <xref:System.Linq.Enumerable.OrderBy%2A> method with a custom comparer to do a case-insensitive sort of last names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbycomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbycomparer_mq)]  
  
## <a name="reverse"></a><span data-ttu-id="13872-112">Reverse</span><span class="sxs-lookup"><span data-stu-id="13872-112">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="13872-113">例</span><span class="sxs-lookup"><span data-stu-id="13872-113">Example</span></span>  

 <span data-ttu-id="13872-114">この例では、<xref:System.Linq.Enumerable.Reverse%2A> メソッドを使用し、`OrderDate` が 2002 年 2 月 20 日よりも前の日付である注文のリストを作成します。</span><span class="sxs-lookup"><span data-stu-id="13872-114">This example uses the <xref:System.Linq.Enumerable.Reverse%2A> method to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenby"></a><span data-ttu-id="13872-115">ThenBy</span><span class="sxs-lookup"><span data-stu-id="13872-115">ThenBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="13872-116">例</span><span class="sxs-lookup"><span data-stu-id="13872-116">Example</span></span>  

 <span data-ttu-id="13872-117">この例では、<xref:System.Linq.Enumerable.OrderBy%2A> メソッドと <xref:System.Linq.Enumerable.ThenBy%2A> メソッド、およびカスタム Comparer を使用して最初に表示価格で並べ替えた後、製品名の降順で大文字と小文字を区別せずに並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="13872-117">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> and <xref:System.Linq.Enumerable.ThenBy%2A> methods with a custom comparer to first sort by list price, and then perform a case-insensitive descending sort of the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingcomparer_mq)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingComparer_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingcomparer_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="13872-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="13872-118">See also</span></span>

- [<span data-ttu-id="13872-119">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="13872-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="13872-120">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="13872-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="13872-121">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="13872-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="13872-122">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13872-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
