---
description: '詳細情報: メソッド ベースのクエリ構文例:要素演算子'
title: メソッド ベースのクエリ構文例:要素演算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8438b995-bd07-4223-b22d-13adadef33fb
ms.openlocfilehash: 8a83602c4d374ae02b4f39ee75821718f8b53f3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673584"
---
# <a name="method-based-query-syntax-examples-element-operators"></a><span data-ttu-id="8f210-103">メソッド ベースのクエリ構文例:要素演算子</span><span class="sxs-lookup"><span data-stu-id="8f210-103">Method-Based Query Syntax Examples: Element Operators</span></span>

<span data-ttu-id="8f210-104">このトピックでは、メソッド ベースのクエリ構文で、<xref:System.Linq.Enumerable.First%2A> メソッドを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="8f210-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="8f210-105">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="8f210-105">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="8f210-106">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="8f210-106">The example in this topic uses the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a><span data-ttu-id="8f210-107">First</span><span class="sxs-lookup"><span data-stu-id="8f210-107">First</span></span>  
  
### <a name="example"></a><span data-ttu-id="8f210-108">例</span><span class="sxs-lookup"><span data-stu-id="8f210-108">Example</span></span>  

 <span data-ttu-id="8f210-109">次の例では、<xref:System.Linq.Enumerable.First%2A> メソッドを使用して、'caroline' で始まる最初の電子メール アドレスを検索します。</span><span class="sxs-lookup"><span data-stu-id="8f210-109">The following example uses the <xref:System.Linq.Enumerable.First%2A> method to find the first email address that starts with 'caroline'.</span></span>  
  
 [!code-csharp[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstcondition_mq)]
 [!code-vb[DP L2E Examples#FirstCondition_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstcondition_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="8f210-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f210-110">See also</span></span>

- [<span data-ttu-id="8f210-111">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="8f210-111">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
