---
description: '詳細情報: クエリ式の構文例:グループ化'
title: クエリ式の構文例:グループ化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: 1d8bd51a783cbd53716daebfa9b547f5e4fffc1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696218"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="23709-103">クエリ式の構文例:グループ化</span><span class="sxs-lookup"><span data-stu-id="23709-103">Query Expression Syntax Examples: Grouping</span></span>

<span data-ttu-id="23709-104">このトピックでは、クエリ式構文で、`GroupBy` メソッドを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="23709-104">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="23709-105">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="23709-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="23709-106">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="23709-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="23709-107">例</span><span class="sxs-lookup"><span data-stu-id="23709-107">Example</span></span>  

 <span data-ttu-id="23709-108">次の例では、郵便番号でグループ化された `Address` オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="23709-108">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="23709-109">結果は匿名型に射影されます。</span><span class="sxs-lookup"><span data-stu-id="23709-109">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="23709-110">例</span><span class="sxs-lookup"><span data-stu-id="23709-110">Example</span></span>  

 <span data-ttu-id="23709-111">次の例では、`Contact` オブジェクトを、連絡先の姓の先頭文字でグループ化して返します。</span><span class="sxs-lookup"><span data-stu-id="23709-111">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="23709-112">結果は姓の先頭文字で並べ替えられ、匿名型に射影されます。</span><span class="sxs-lookup"><span data-stu-id="23709-112">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="23709-113">例</span><span class="sxs-lookup"><span data-stu-id="23709-113">Example</span></span>  

 <span data-ttu-id="23709-114">次の例では、顧客 ID でグループ化された `SalesOrderHeader` オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="23709-114">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="23709-115">顧客ごとの販売数も返されます。</span><span class="sxs-lookup"><span data-stu-id="23709-115">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="23709-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="23709-116">See also</span></span>

- [<span data-ttu-id="23709-117">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="23709-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
