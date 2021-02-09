---
description: '詳細情報: クエリ式の構文例:射影'
title: クエリ式の構文例:射影
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: e14a84272cef03dca24df5d0f889b8aaa77e94d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696010"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="c66a0-103">クエリ式の構文例:射影</span><span class="sxs-lookup"><span data-stu-id="c66a0-103">Query Expression Syntax Examples: Projection</span></span>

<span data-ttu-id="c66a0-104">このトピックでは、クエリ式の構文で、`Select` メソッドおよび `From … From …` キーワードを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="c66a0-104">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="c66a0-105">`From … From …` は、メソッドは、`SelectMany` メソッドのクエリ ベース版に相当します。</span><span class="sxs-lookup"><span data-stu-id="c66a0-105">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="c66a0-106">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="c66a0-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c66a0-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="c66a0-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="c66a0-108">選択</span><span class="sxs-lookup"><span data-stu-id="c66a0-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="c66a0-109">例</span><span class="sxs-lookup"><span data-stu-id="c66a0-109">Example</span></span>  

 <span data-ttu-id="c66a0-110">次の例では、<xref:System.Linq.Enumerable.Select%2A> メソッドを使用して `Product` テーブルからすべての行を取得し、製品名を表示しています。</span><span class="sxs-lookup"><span data-stu-id="c66a0-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="c66a0-111">例</span><span class="sxs-lookup"><span data-stu-id="c66a0-111">Example</span></span>  

 <span data-ttu-id="c66a0-112">次の例では、<xref:System.Linq.Enumerable.Select%2A> を使用して、一連の製品名だけを取得しています。</span><span class="sxs-lookup"><span data-stu-id="c66a0-112">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="c66a0-113">例</span><span class="sxs-lookup"><span data-stu-id="c66a0-113">Example</span></span>  

 <span data-ttu-id="c66a0-114">次の例では、<xref:System.Linq.Queryable.Select%2A> メソッドを使用して、`Product.Name` プロパティおよび `Product.ProductID` プロパティを一連の匿名型に射影します。</span><span class="sxs-lookup"><span data-stu-id="c66a0-114">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="c66a0-115">From …</span><span class="sxs-lookup"><span data-stu-id="c66a0-115">From …</span></span> <span data-ttu-id="c66a0-116">From …</span><span class="sxs-lookup"><span data-stu-id="c66a0-116">From …</span></span> <span data-ttu-id="c66a0-117">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="c66a0-117">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="c66a0-118">例</span><span class="sxs-lookup"><span data-stu-id="c66a0-118">Example</span></span>  

 <span data-ttu-id="c66a0-119">次の例では、`From … From …` (<xref:System.Linq.Enumerable.SelectMany%2A> メソッドと等価) を使用して、`TotalDue` が 500.00 に満たないすべての注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="c66a0-119">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="c66a0-120">例</span><span class="sxs-lookup"><span data-stu-id="c66a0-120">Example</span></span>  

 <span data-ttu-id="c66a0-121">次の例では、`From … From …` (<xref:System.Linq.Enumerable.SelectMany%2A> メソッドと等価) を使用して、2002 年 10 月 1 日以降に受けたすべての注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="c66a0-121">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="c66a0-122">例</span><span class="sxs-lookup"><span data-stu-id="c66a0-122">Example</span></span>  

 <span data-ttu-id="c66a0-123">次の例では、`From … From …` (<xref:System.Linq.Enumerable.SelectMany%2A> メソッドと等価) を使用して、注文の合計が 10000.00 を超えるすべての注文を選択します。このとき、`From` 割り当てを使用して、合計を 2 回要求しないようにしています。</span><span class="sxs-lookup"><span data-stu-id="c66a0-123">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="c66a0-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="c66a0-124">See also</span></span>

- [<span data-ttu-id="c66a0-125">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="c66a0-125">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
