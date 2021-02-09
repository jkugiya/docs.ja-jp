---
description: '詳細情報: メソッド ベースのクエリ構文例:集合演算子 (LINQ to DataSet)'
title: メソッド ベースのクエリ構文例:集合演算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa93af15-28af-4b5e-846b-897308410edb
ms.openlocfilehash: 3a50c9793e3af6fdab08227b4789c4042dd64931
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723752"
---
# <a name="method-based-query-syntax-examples-set-operators-linq-to-dataset"></a><span data-ttu-id="8690e-103">メソッド ベースのクエリ構文例:集合演算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8690e-103">Method-Based Query Syntax Examples: Set Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="8690e-104">このトピックの例では、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Except%2A>、<xref:System.Linq.Enumerable.Intersect%2A>、<xref:System.Linq.Enumerable.Union%2A> の各演算子を使用して、データ行の集合に対して値ベースの比較操作を実行する方法を示します。[DataSet へのデータの読み込み](loading-data-into-a-dataset.md)。<xref:System.Data.DataRowComparer> について詳しくは、「[DataRow の比較](comparing-datarows-linq-to-dataset.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8690e-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.[Loading Data Into a DataSet](loading-data-into-a-dataset.md) See [Comparing DataRows](comparing-datarows-linq-to-dataset.md) for more information on <xref:System.Data.DataRowComparer>.</span></span>  
  
 <span data-ttu-id="8690e-105">これらの例で使用されている `FillDataSet` メソッドは、「[DataSet へのデータの読み込み](loading-data-into-a-dataset.md)」で指定されています。</span><span class="sxs-lookup"><span data-stu-id="8690e-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="8690e-106">このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="8690e-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8690e-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="8690e-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="8690e-108">詳細については、[Visual Studio で LINQ to DataSet プロジェクトを作成する](how-to-create-a-linq-to-dataset-project-in-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8690e-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="distinct"></a><span data-ttu-id="8690e-109">Distinct</span><span class="sxs-lookup"><span data-stu-id="8690e-109">Distinct</span></span>  
  
### <a name="example"></a><span data-ttu-id="8690e-110">例</span><span class="sxs-lookup"><span data-stu-id="8690e-110">Example</span></span>  

 <span data-ttu-id="8690e-111">この例では、<xref:System.Linq.Enumerable.Distinct%2A> メソッドを使用してシーケンス内の重複する要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="8690e-111">This example uses the <xref:System.Linq.Enumerable.Distinct%2A> method to remove duplicate elements in a sequence.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#distinctrows)]
 [!code-vb[DP LINQ to DataSet Examples#DistinctRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#distinctrows)]  
  
## <a name="except"></a><span data-ttu-id="8690e-112">除く</span><span class="sxs-lookup"><span data-stu-id="8690e-112">Except</span></span>  
  
### <a name="example"></a><span data-ttu-id="8690e-113">例</span><span class="sxs-lookup"><span data-stu-id="8690e-113">Example</span></span>  

 <span data-ttu-id="8690e-114">この例では、最初のテーブルにのみ存在し、かつ 2 つ目のテーブルには存在しない連絡先だけを、<xref:System.Linq.Enumerable.Except%2A> メソッドを使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="8690e-114">This example uses the <xref:System.Linq.Enumerable.Except%2A> method to return contacts that appear in the first table but not in the second.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#except2)]
 [!code-vb[DP LINQ to DataSet Examples#Except2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#except2)]  
  
## <a name="intersect"></a><span data-ttu-id="8690e-115">交差</span><span class="sxs-lookup"><span data-stu-id="8690e-115">Intersect</span></span>  
  
### <a name="example"></a><span data-ttu-id="8690e-116">例</span><span class="sxs-lookup"><span data-stu-id="8690e-116">Example</span></span>  

 <span data-ttu-id="8690e-117">この例では、両方のテーブルに存在する連絡先を <xref:System.Linq.Enumerable.Intersect%2A> メソッドを使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="8690e-117">This example uses the <xref:System.Linq.Enumerable.Intersect%2A> method to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
## <a name="union"></a><span data-ttu-id="8690e-118">和集合</span><span class="sxs-lookup"><span data-stu-id="8690e-118">Union</span></span>  
  
### <a name="example"></a><span data-ttu-id="8690e-119">例</span><span class="sxs-lookup"><span data-stu-id="8690e-119">Example</span></span>  

 <span data-ttu-id="8690e-120">この例では、<xref:System.Linq.Enumerable.Union%2A> メソッドを使用して、2 つのテーブルのいずれかから一意の連絡先を取得します。</span><span class="sxs-lookup"><span data-stu-id="8690e-120">This example uses the <xref:System.Linq.Enumerable.Union%2A> method to return unique contacts from either of the two tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#union2)]
 [!code-vb[DP LINQ to DataSet Examples#Union2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#union2)]  
  
## <a name="see-also"></a><span data-ttu-id="8690e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8690e-121">See also</span></span>

- [<span data-ttu-id="8690e-122">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="8690e-122">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="8690e-123">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="8690e-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="8690e-124">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="8690e-124">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8690e-125">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8690e-125">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
