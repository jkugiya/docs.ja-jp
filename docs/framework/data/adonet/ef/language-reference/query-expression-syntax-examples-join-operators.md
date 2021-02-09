---
description: '詳細情報: クエリ式の構文例:結合演算子'
title: クエリ式の構文例:結合演算子
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: 01ca3157ef13097c5c89ac1e6bafd03873c05977
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696205"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="01728-103">クエリ式の構文例:結合演算子</span><span class="sxs-lookup"><span data-stu-id="01728-103">Query Expression Syntax Examples: Join Operators</span></span>

<span data-ttu-id="01728-104">結合は、リレーショナル データベース テーブルのように互いにナビゲート可能なリレーションシップを持たないデータ ソースをターゲットとするクエリにおいて重要な操作です。</span><span class="sxs-lookup"><span data-stu-id="01728-104">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="01728-105">2 つのデータ ソースを結合する操作とは、あるデータ ソース内のオブジェクトを、他方のデータ ソース内で共通の属性を持つオブジェクトと関連付けることです。</span><span class="sxs-lookup"><span data-stu-id="01728-105">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="01728-106">詳細については、「[標準クエリ演算子の概要](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01728-106">For more information, see [Standard Query Operators Overview](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="01728-107">このトピックでは、クエリ式構文で、<xref:System.Linq.Enumerable.GroupJoin%2A> メソッドおよび <xref:System.Linq.Enumerable.Join%2A> メソッドを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="01728-107">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="01728-108">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="01728-108">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="01728-109">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="01728-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="01728-110">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="01728-110">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="01728-111">例</span><span class="sxs-lookup"><span data-stu-id="01728-111">Example</span></span>  

 <span data-ttu-id="01728-112">次の例では、SalesOrderHeader テーブルおよび SalesOrderDetail テーブルに対して <xref:System.Linq.Enumerable.GroupJoin%2A> を実行することによって、顧客ごとの注文数を調べます。</span><span class="sxs-lookup"><span data-stu-id="01728-112">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="01728-113">GroupJoin は、左外部結合に相当します。つまり、1 つ目 (左側) のデータ ソースに存在するすべての要素は、関連する要素がもう一方のデータ ソースに存在するかどうかに関係なく返されます。</span><span class="sxs-lookup"><span data-stu-id="01728-113">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="01728-114">例</span><span class="sxs-lookup"><span data-stu-id="01728-114">Example</span></span>  

 <span data-ttu-id="01728-115">次の例では、Contact テーブルおよび SalesOrderHeader テーブルに対して <xref:System.Linq.Enumerable.GroupJoin%2A> を実行して、連絡先ごとの注文数を調べます。</span><span class="sxs-lookup"><span data-stu-id="01728-115">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="01728-116">各連絡先の注文数と ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01728-116">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="01728-117">Join</span><span class="sxs-lookup"><span data-stu-id="01728-117">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="01728-118">例</span><span class="sxs-lookup"><span data-stu-id="01728-118">Example</span></span>  

 <span data-ttu-id="01728-119">次の例では、SalesOrderHeader テーブルと SalesOrderDetail テーブルを結合し、8 月以降のオンラインでの注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="01728-119">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="01728-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="01728-120">See also</span></span>

- [<span data-ttu-id="01728-121">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="01728-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
