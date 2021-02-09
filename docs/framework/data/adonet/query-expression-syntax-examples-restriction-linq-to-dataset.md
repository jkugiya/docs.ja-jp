---
description: '詳細情報: クエリ式の構文例:制限 (LINQ to DataSet)'
title: クエリ式の構文例:制限 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1daf42c2-c9f4-4cda-b291-7641b9c6d3fe
ms.openlocfilehash: 06ffaa782a02191be4c9568587824ec1767f1249
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695984"
---
# <a name="query-expression-syntax-examples-restriction-linq-to-dataset"></a><span data-ttu-id="dcb80-103">クエリ式の構文例:制限 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="dcb80-103">Query Expression Syntax Examples: Restriction (LINQ to DataSet)</span></span>

<span data-ttu-id="dcb80-104">このトピックでは、<xref:System.Linq.Enumerable.Where%2A> メソッドで、クエリ式の構文を使って <xref:System.Data.DataSet> に対するクエリを実行する例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="dcb80-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="dcb80-105">これらの例で使用されている `FillDataSet` メソッドの指定については、「[DataSet へのデータの読み込み](loading-data-into-a-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcb80-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="dcb80-106">このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="dcb80-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="dcb80-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="dcb80-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
[!code-csharp[DP LINQ to DataSetExamples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
  
 <span data-ttu-id="dcb80-108">詳細については、[Visual Studio で LINQ to DataSet プロジェクトを作成する](how-to-create-a-linq-to-dataset-project-in-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dcb80-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="where"></a><span data-ttu-id="dcb80-109">Where</span><span class="sxs-lookup"><span data-stu-id="dcb80-109">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="dcb80-110">例</span><span class="sxs-lookup"><span data-stu-id="dcb80-110">Example</span></span>  

 <span data-ttu-id="dcb80-111">この例では、すべてのオンライン注文が返されます。</span><span class="sxs-lookup"><span data-stu-id="dcb80-111">This example returns all online orders.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)]
  
### <a name="example"></a><span data-ttu-id="dcb80-112">例</span><span class="sxs-lookup"><span data-stu-id="dcb80-112">Example</span></span>  

 <span data-ttu-id="dcb80-113">この例では、注文数量が 3 個以上で 5 個以下の注文が返されます。</span><span class="sxs-lookup"><span data-stu-id="dcb80-113">This example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where2)]  
 [!code-vb[DP LINQ to DataSet Examples#Where2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where2)]
  
### <a name="example"></a><span data-ttu-id="dcb80-114">例</span><span class="sxs-lookup"><span data-stu-id="dcb80-114">Example</span></span>  

 <span data-ttu-id="dcb80-115">この例では、色が赤の製品がすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="dcb80-115">This example returns all red colored products.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where3)]  
 [!code-vb[DP LINQ to DataSet Examples#Where3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where3)]
  
### <a name="example"></a><span data-ttu-id="dcb80-116">例</span><span class="sxs-lookup"><span data-stu-id="dcb80-116">Example</span></span>  

 <span data-ttu-id="dcb80-117">この例では、<xref:System.Linq.Enumerable.Where%2A> メソッドを使用して、2002 年 12 月 1 日以降に受けた注文を検索します。次に、<xref:System.Data.DataRow.GetChildRows%2A> メソッドを使用して、各注文の詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="dcb80-117">This example uses the <xref:System.Linq.Enumerable.Where%2A> method to find orders that were made after December 1, 2002 and then uses the <xref:System.Data.DataRow.GetChildRows%2A> method to get the details for each order.</span></span>  
  
 [!code-csharp[DP LINQ to DataSetExamples#WhereDrillDown](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#wheredrilldown)]
 [!code-vb[DP LINQ to DataSet Examples#WhereDrillDown](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#wheredrilldown)]  
  
## <a name="see-also"></a><span data-ttu-id="dcb80-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcb80-118">See also</span></span>

- [<span data-ttu-id="dcb80-119">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="dcb80-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="dcb80-120">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="dcb80-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="dcb80-121">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="dcb80-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="dcb80-122">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcb80-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
