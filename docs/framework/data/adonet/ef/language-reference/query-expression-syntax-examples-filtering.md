---
description: '詳細情報: クエリ式の構文例:フィルター処理'
title: クエリ式の構文例:フィルター処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: f8bc2d08f7a8916ccbd2884ff9a9af616b2118f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696231"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="a8d0c-103">クエリ式の構文例:フィルター処理</span><span class="sxs-lookup"><span data-stu-id="a8d0c-103">Query Expression Syntax Examples: Filtering</span></span>

<span data-ttu-id="a8d0c-104">このトピックでは、クエリ式構文で、`Where` メソッドおよび `Where…Contains` メソッドを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-104">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="a8d0c-105">Where…`Contains`</span><span class="sxs-lookup"><span data-stu-id="a8d0c-105">Note, Where…`Contains`</span></span> <span data-ttu-id="a8d0c-106">を[コンパイル済みクエリ](compiled-queries-linq-to-entities.md)の一部として使用することはできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-106">cannot be used as a part of a [compiled query](compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="a8d0c-107">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-107">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="a8d0c-108">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="a8d0c-109">Where</span><span class="sxs-lookup"><span data-stu-id="a8d0c-109">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="a8d0c-110">例</span><span class="sxs-lookup"><span data-stu-id="a8d0c-110">Example</span></span>  

 <span data-ttu-id="a8d0c-111">次の例では、すべてのオンライン注文が返されます。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-111">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="a8d0c-112">例</span><span class="sxs-lookup"><span data-stu-id="a8d0c-112">Example</span></span>  

 <span data-ttu-id="a8d0c-113">次の例では、注文数量が 3 個以上で 5 個以下の注文が返されます。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-113">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="a8d0c-114">例</span><span class="sxs-lookup"><span data-stu-id="a8d0c-114">Example</span></span>  

 <span data-ttu-id="a8d0c-115">次の例では、色が赤の製品がすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-115">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="a8d0c-116">例</span><span class="sxs-lookup"><span data-stu-id="a8d0c-116">Example</span></span>  

 <span data-ttu-id="a8d0c-117">次の例では、`Where` メソッドを使用して、2003 年 12 月 1 日以降に受けた注文を検索します。次に、`order.SalesOrderDetail` ナビゲーション プロパティを使用して、各注文の詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-117">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="a8d0c-118">Where…Contains</span><span class="sxs-lookup"><span data-stu-id="a8d0c-118">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="a8d0c-119">例</span><span class="sxs-lookup"><span data-stu-id="a8d0c-119">Example</span></span>  

 <span data-ttu-id="a8d0c-120">次の例では、配列を `Where…Contains` 句の一部として使用し、その配列内の値と一致する `ProductModelID` を持つすべての製品を検出します。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-120">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="a8d0c-121">`Where…Contains` 句の述語として、<xref:System.Array>、<xref:System.Collections.Generic.List%601>、または <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装する任意の型のコレクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-121">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="a8d0c-122">さらに、LINQ to Entities クエリ内でコレクションを宣言および初期化できます。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-122">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="a8d0c-123">詳細については、次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-123">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a8d0c-124">例</span><span class="sxs-lookup"><span data-stu-id="a8d0c-124">Example</span></span>  

 <span data-ttu-id="a8d0c-125">次の例では、`Where…Contains` 句で配列を宣言および初期化し、その配列内の値と一致する `ProductModelID` または `Size` を持つすべての製品を検出します。</span><span class="sxs-lookup"><span data-stu-id="a8d0c-125">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a8d0c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8d0c-126">See also</span></span>

- [<span data-ttu-id="a8d0c-127">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="a8d0c-127">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
