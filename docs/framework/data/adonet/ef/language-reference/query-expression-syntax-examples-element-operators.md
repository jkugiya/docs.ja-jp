---
description: '詳細情報: クエリ式の構文例:要素演算子'
title: クエリ式の構文例:要素演算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 0dc6d49959abba712cef572eaa549138af646bd5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696244"
---
# <a name="query-expression-syntax-examples-element-operators"></a><span data-ttu-id="6096d-103">クエリ式の構文例:要素演算子</span><span class="sxs-lookup"><span data-stu-id="6096d-103">Query Expression Syntax Examples: Element Operators</span></span>

<span data-ttu-id="6096d-104">このトピックでは、クエリ式構文で、<xref:System.Linq.Enumerable.First%2A> メソッドを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="6096d-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using the query expression syntax.</span></span> <span data-ttu-id="6096d-105">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="6096d-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6096d-106">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="6096d-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="6096d-107">First</span><span class="sxs-lookup"><span data-stu-id="6096d-107">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="6096d-108">例</span><span class="sxs-lookup"><span data-stu-id="6096d-108">Example</span></span>  

 <span data-ttu-id="6096d-109">次の例では、<xref:System.Linq.Enumerable.First%2A> メソッドを使用して、名が "Brooke" である最初の連絡先を取得します。</span><span class="sxs-lookup"><span data-stu-id="6096d-109">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to return the first contact whose first name is "Brooke".</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="6096d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="6096d-110">See also</span></span>

- [<span data-ttu-id="6096d-111">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="6096d-111">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
