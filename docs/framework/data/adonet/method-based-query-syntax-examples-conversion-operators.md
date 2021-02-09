---
description: '詳細情報: メソッド ベースのクエリ構文例:変換演算子 (LINQ to DataSet)'
title: メソッド ベースのクエリ構文例:変換演算子 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a084c16b-9b55-4690-aefd-f8e0810a92c3
ms.openlocfilehash: 958e5c0ac1d1d8a98e6099ffcad055e78f07b23e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672739"
---
# <a name="method-based-query-syntax-examples-conversion-operators-linq-to-dataset"></a><span data-ttu-id="8d91f-103">メソッド ベースのクエリ構文例:変換演算子 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="8d91f-103">Method-Based Query Syntax Examples: Conversion Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="8d91f-104">このトピックでは、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A>、<xref:System.Linq.Enumerable.ToList%2A> の各メソッドを使ってクエリ式を即時実行する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="8d91f-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 <span data-ttu-id="8d91f-105">これらの例で使用されている `FillDataSet` メソッドは、「[DataSet へのデータの読み込み](loading-data-into-a-dataset.md)」で指定されています。</span><span class="sxs-lookup"><span data-stu-id="8d91f-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="8d91f-106">このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="8d91f-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8d91f-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="8d91f-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="8d91f-108">詳細については、[Visual Studio で LINQ to DataSet プロジェクトを作成する](how-to-create-a-linq-to-dataset-project-in-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d91f-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="toarray"></a><span data-ttu-id="8d91f-109">ToArray</span><span class="sxs-lookup"><span data-stu-id="8d91f-109">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="8d91f-110">例</span><span class="sxs-lookup"><span data-stu-id="8d91f-110">Example</span></span>  

 <span data-ttu-id="8d91f-111">この例では、<xref:System.Linq.Enumerable.ToArray%2A> メソッドを使用して、シーケンスを配列として即時評価します。</span><span class="sxs-lookup"><span data-stu-id="8d91f-111">This example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="8d91f-112">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="8d91f-112">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="8d91f-113">例</span><span class="sxs-lookup"><span data-stu-id="8d91f-113">Example</span></span>  

 <span data-ttu-id="8d91f-114">この例では、<xref:System.Linq.Enumerable.ToDictionary%2A> メソッドを使用して、シーケンスおよび関連するキー式をディクショナリとして即時評価します。</span><span class="sxs-lookup"><span data-stu-id="8d91f-114">This example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP LINQ to DataSet Examples#ToDictionary](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="8d91f-115">ToList</span><span class="sxs-lookup"><span data-stu-id="8d91f-115">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="8d91f-116">例</span><span class="sxs-lookup"><span data-stu-id="8d91f-116">Example</span></span>  

 <span data-ttu-id="8d91f-117">この例では、<xref:System.Linq.Enumerable.ToList%2A> メソッドを使用して、シーケンスを <xref:System.Collections.Generic.List%601> として即時評価します。ここで、`T` は <xref:System.Data.DataRow> 型を表します。</span><span class="sxs-lookup"><span data-stu-id="8d91f-117">This example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#tolist)]
 [!code-vb[DP LINQ to DataSet Examples#ToList](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="8d91f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d91f-118">See also</span></span>

- [<span data-ttu-id="8d91f-119">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="8d91f-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="8d91f-120">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="8d91f-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="8d91f-121">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="8d91f-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8d91f-122">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d91f-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
