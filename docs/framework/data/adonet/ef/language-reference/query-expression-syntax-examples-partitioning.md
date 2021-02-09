---
description: '詳細情報: クエリ式の構文例:パーティション分割'
title: クエリ式の構文例:パーティション分割
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: 9322f43874054ac864bda5c84ae02dfe0a49ec4f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695997"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="c72a2-103">クエリ式の構文例:パーティション分割</span><span class="sxs-lookup"><span data-stu-id="c72a2-103">Query Expression Syntax Examples: Partitioning</span></span>

<span data-ttu-id="c72a2-104">このトピックでは、クエリ式構文で、<xref:System.Linq.Enumerable.Skip%2A> メソッドおよび <xref:System.Linq.Enumerable.Take%2A> メソッドを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="c72a2-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="c72a2-105">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="c72a2-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c72a2-106">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="c72a2-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="c72a2-107">Skip</span><span class="sxs-lookup"><span data-stu-id="c72a2-107">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="c72a2-108">例</span><span class="sxs-lookup"><span data-stu-id="c72a2-108">Example</span></span>  

 <span data-ttu-id="c72a2-109">次の例では、Seattle から最初の 2 つを除くすべての住所を、<xref:System.Linq.Enumerable.Skip%2A> メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="c72a2-109">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="c72a2-110">Take</span><span class="sxs-lookup"><span data-stu-id="c72a2-110">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="c72a2-111">例</span><span class="sxs-lookup"><span data-stu-id="c72a2-111">Example</span></span>  

 <span data-ttu-id="c72a2-112">次の例では、Seattle から最初の 3 つの住所を、<xref:System.Linq.Enumerable.Take%2A> メソッドを使って取得します。</span><span class="sxs-lookup"><span data-stu-id="c72a2-112">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="c72a2-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c72a2-113">See also</span></span>

- [<span data-ttu-id="c72a2-114">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="c72a2-114">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
