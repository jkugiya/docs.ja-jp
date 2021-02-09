---
description: '詳細情報: クエリ式の構文例:要素演算子 (LINQ to DataSet)'
title: クエリ式の構文例:要素演算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca392dda-16e3-45c7-8d87-12d8d4ee0578
ms.openlocfilehash: 0bef18eb78a03c8b41220dd51cdccea34e3c64b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663626"
---
# <a name="query-expression-syntax-examples-element-operators-linq-to-dataset"></a><span data-ttu-id="b9433-103">クエリ式の構文例:要素演算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="b9433-103">Query Expression Syntax Examples: Element Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="b9433-104">このトピックでは、<xref:System.Linq.Enumerable.First%2A> メソッドおよび <xref:System.Linq.Enumerable.ElementAt%2A> メソッドを使用し、クエリ式の構文を使って <xref:System.Data.DataRow> から <xref:System.Data.DataSet> 要素を取得する例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="b9433-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="b9433-105">これらの例で使用されている `FillDataSet` メソッドの指定については、「[DataSet へのデータの読み込み](loading-data-into-a-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9433-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="b9433-106">このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="b9433-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b9433-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="b9433-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="b9433-108">詳細については、[Visual Studio で LINQ to DataSet プロジェクトを作成する](how-to-create-a-linq-to-dataset-project-in-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9433-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="elementat"></a><span data-ttu-id="b9433-109">ElementAt</span><span class="sxs-lookup"><span data-stu-id="b9433-109">ElementAt</span></span>  
  
### <a name="example"></a><span data-ttu-id="b9433-110">例</span><span class="sxs-lookup"><span data-stu-id="b9433-110">Example</span></span>  

 <span data-ttu-id="b9433-111">この例では、<xref:System.Linq.Enumerable.ElementAt%2A> メソッドを使用し、`PostalCode` == "M4B 1V7" の条件に該当する 5 番目の住所を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9433-111">This example uses the <xref:System.Linq.Enumerable.ElementAt%2A> method to retrieve the fifth address where `PostalCode` == "M4B 1V7".</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#elementat)]
 [!code-vb[DP LINQ to DataSet Examples#ElementAt](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#elementat)]  
  
## <a name="first"></a><span data-ttu-id="b9433-112">First</span><span class="sxs-lookup"><span data-stu-id="b9433-112">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="b9433-113">例</span><span class="sxs-lookup"><span data-stu-id="b9433-113">Example</span></span>  

 <span data-ttu-id="b9433-114">この例では、<xref:System.Linq.Enumerable.First%2A> メソッドを使用して、名が 'Brooke' である最初の連絡先を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9433-114">This example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is 'Brooke'.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP LINQ to DataSet Examples#FirstSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="b9433-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9433-115">See also</span></span>

- [<span data-ttu-id="b9433-116">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="b9433-116">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="b9433-117">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="b9433-117">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="b9433-118">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="b9433-118">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b9433-119">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9433-119">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
