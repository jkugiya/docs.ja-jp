---
description: '詳細情報: メソッド ベースのクエリ構文例:変換'
title: メソッド ベースのクエリ構文例:変換
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 19f66872-d5ab-49f8-969f-e53f9632a13d
ms.openlocfilehash: 054ef9291a66216b14e2f03ecebd28fb24c6574d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696751"
---
# <a name="method-based-query-syntax-examples-conversion"></a><span data-ttu-id="fb20f-103">メソッド ベースのクエリ構文例:変換</span><span class="sxs-lookup"><span data-stu-id="fb20f-103">Method-Based Query Syntax Examples: Conversion</span></span>

<span data-ttu-id="fb20f-104">このトピックでは、メソッド ベースのクエリ構文で、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A>、<xref:System.Linq.Enumerable.ToList%2A> の各メソッドを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="fb20f-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A> and <xref:System.Linq.Enumerable.ToList%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="fb20f-105">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="fb20f-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="fb20f-106">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="fb20f-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="toarray"></a><span data-ttu-id="fb20f-107">ToArray</span><span class="sxs-lookup"><span data-stu-id="fb20f-107">ToArray</span></span>  
  
### <a name="example"></a><span data-ttu-id="fb20f-108">例</span><span class="sxs-lookup"><span data-stu-id="fb20f-108">Example</span></span>  

 <span data-ttu-id="fb20f-109">次の例では、<xref:System.Linq.Enumerable.ToArray%2A> メソッドを使用して、シーケンスを配列として即時評価します。</span><span class="sxs-lookup"><span data-stu-id="fb20f-109">The following example uses the <xref:System.Linq.Enumerable.ToArray%2A> method to immediately evaluate a sequence into an array.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToArray](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#toarray)]
 [!code-vb[DP L2E Examples#ToArray](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#toarray)]  
  
## <a name="todictionary"></a><span data-ttu-id="fb20f-110">ToDictionary</span><span class="sxs-lookup"><span data-stu-id="fb20f-110">ToDictionary</span></span>  
  
### <a name="example"></a><span data-ttu-id="fb20f-111">例</span><span class="sxs-lookup"><span data-stu-id="fb20f-111">Example</span></span>  

 <span data-ttu-id="fb20f-112">次の例では、<xref:System.Linq.Enumerable.ToDictionary%2A> メソッドを使用して、シーケンスおよび関連するキー式をディクショナリとして即時評価します。</span><span class="sxs-lookup"><span data-stu-id="fb20f-112">The following example uses the <xref:System.Linq.Enumerable.ToDictionary%2A> method to immediately evaluate a sequence and a related key expression into a dictionary.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#todictionary)]
 [!code-vb[DP L2E Examples#ToDictionary](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#todictionary)]  
  
## <a name="tolist"></a><span data-ttu-id="fb20f-113">ToList</span><span class="sxs-lookup"><span data-stu-id="fb20f-113">ToList</span></span>  
  
### <a name="example"></a><span data-ttu-id="fb20f-114">例</span><span class="sxs-lookup"><span data-stu-id="fb20f-114">Example</span></span>  

 <span data-ttu-id="fb20f-115">次の例では、<xref:System.Linq.Enumerable.ToList%2A> メソッドを使用して、シーケンスを <xref:System.Collections.Generic.List%601> として即時評価します。ここで、`T` は <xref:System.Data.DataRow> 型を表します。</span><span class="sxs-lookup"><span data-stu-id="fb20f-115">The following example uses the <xref:System.Linq.Enumerable.ToList%2A> method to immediately evaluate a sequence into a <xref:System.Collections.Generic.List%601>, where `T` is of type <xref:System.Data.DataRow>.</span></span>  
  
 [!code-csharp[DP L2E Examples#ToList](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#tolist)]
 [!code-vb[DP L2E Examples#ToList](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#tolist)]  
  
## <a name="see-also"></a><span data-ttu-id="fb20f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb20f-116">See also</span></span>

- [<span data-ttu-id="fb20f-117">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="fb20f-117">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
