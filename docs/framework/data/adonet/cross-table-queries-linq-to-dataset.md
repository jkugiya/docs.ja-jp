---
description: '詳細情報: 複数テーブルにまたがるクエリ (LINQ to DataSet)'
title: 複数テーブルにまたがるクエリ (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: c1fa31f6908808f3369987b9b180655f26092529
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663795"
---
# <a name="cross-table-queries-linq-to-dataset"></a><span data-ttu-id="ad344-103">複数テーブルにまたがるクエリ (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="ad344-103">Cross-Table Queries (LINQ to DataSet)</span></span>

<span data-ttu-id="ad344-104">LINQ to DataSet では、1 つのテーブルを対象とするクエリに加え、複数テーブルにまたがるクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad344-104">In addition to querying a single table, you can also perform cross-table queries in LINQ to DataSet.</span></span> <span data-ttu-id="ad344-105">これは、"*結合*" を使用することで実現されます。</span><span class="sxs-lookup"><span data-stu-id="ad344-105">This is done by using a *join*.</span></span> <span data-ttu-id="ad344-106">結合とは、あるデータ ソース内のオブジェクトを、他方のデータ ソース内で共通の属性 (たとえば製品や連絡先 ID) を持つオブジェクトと関連付けることです。</span><span class="sxs-lookup"><span data-stu-id="ad344-106">A join is the association of objects in one data source with objects that share a common attribute in another data source, such as a product or contact ID.</span></span> <span data-ttu-id="ad344-107">オブジェクト指向プログラミングでは、それぞれのオブジェクトは別のオブジェクトを参照するメンバーを持つため、オブジェクト間のリレーションシップのナビゲーションは比較的簡単です。</span><span class="sxs-lookup"><span data-stu-id="ad344-107">In object-oriented programming, relationships between objects are relatively easy to navigate because each object has a member that references another object.</span></span> <span data-ttu-id="ad344-108">ただし、外部データベース テーブル内でのリレーションシップのナビゲーションは単純ではありません。</span><span class="sxs-lookup"><span data-stu-id="ad344-108">In external database tables, however, navigating relationships is not as straightforward.</span></span> <span data-ttu-id="ad344-109">データベース テーブルは、組み込みのリレーションシップを持ちません。</span><span class="sxs-lookup"><span data-stu-id="ad344-109">Database tables do not contain built-in relationships.</span></span> <span data-ttu-id="ad344-110">このようなケースでは、結合操作を使用して、互いのソースの要素を対応付けることができます。</span><span class="sxs-lookup"><span data-stu-id="ad344-110">In these cases, the join operation can be used to match elements from each source.</span></span> <span data-ttu-id="ad344-111">たとえば、製品情報と売上情報が 2 つのテーブルに格納されている場合、結合操作を使用して、同じ販売注文の売上情報と製品を対応付けることができます。</span><span class="sxs-lookup"><span data-stu-id="ad344-111">For example, given two tables that contain product information and sales information, you could use a join operation to match sales information and products for the same sales order.</span></span>  
  
 <span data-ttu-id="ad344-112">LINQ (統合言語クエリ) フレームワークには、<xref:System.Linq.Enumerable.Join%2A> と <xref:System.Linq.Enumerable.GroupJoin%2A> の 2 つの結合演算子が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ad344-112">The Language-Integrated Query (LINQ) framework provides two join operators, <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="ad344-113">これらの演算子では、キーが等しいときにだけ 2 つのデータ ソースを一致させる結合方法である "*等結合*" が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad344-113">These operators perform *equi-joins*: that is, joins that match two data sources only when their keys are equal.</span></span> <span data-ttu-id="ad344-114">(これに対し、Transact-SQL では、`equals` 以外に `less than` 演算子などの結合演算子がサポートされています)。</span><span class="sxs-lookup"><span data-stu-id="ad344-114">(By contrast, Transact-SQL supports join operators other than `equals`, such as the `less than` operator.)</span></span>  
  
 <span data-ttu-id="ad344-115">リレーショナル データベース用語では、<xref:System.Linq.Enumerable.Join%2A> は内部結合を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad344-115">In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join.</span></span> <span data-ttu-id="ad344-116">内部結合とは、対応するデータセット内で一致するオブジェクトがあるオブジェクトのみが返される結合です。</span><span class="sxs-lookup"><span data-stu-id="ad344-116">An inner join is a type of join in which only those objects that have a match in the opposite data set are returned.</span></span>  
  
 <span data-ttu-id="ad344-117">リレーショナル データベースの用語で <xref:System.Linq.Enumerable.GroupJoin%2A> 演算子に直接相当するものはありません。これらの演算子では、内部結合と左外部結合のスーパーセットが実装されています。</span><span class="sxs-lookup"><span data-stu-id="ad344-117">The <xref:System.Linq.Enumerable.GroupJoin%2A> operators have no direct equivalent in relational database terms; they implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="ad344-118">左外部結合とは、最初 (左側) のコレクションの各要素が返される結合であり、第 2 のコレクションに相関する要素がない場合でも返されます。</span><span class="sxs-lookup"><span data-stu-id="ad344-118">A left outer join is a join that returns each element of the first (left) collection, even if it has no correlated elements in the second collection.</span></span>  
  
 <span data-ttu-id="ad344-119">結合について詳しくは、「[結合演算](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ad344-119">For more information about joins, see [Join Operations](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad344-120">例</span><span class="sxs-lookup"><span data-stu-id="ad344-120">Example</span></span>  

 <span data-ttu-id="ad344-121">次の例では、AdventureWorks サンプル データベースの `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルを従来の方法で結合し、8 月以降のオンラインでの注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad344-121">The following example performs a traditional join of the `SalesOrderHeader` and `SalesOrderDetail` tables from the AdventureWorks sample database to obtain online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="ad344-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad344-122">See also</span></span>

- [<span data-ttu-id="ad344-123">DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="ad344-123">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="ad344-124">単一テーブルのクエリ</span><span class="sxs-lookup"><span data-stu-id="ad344-124">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="ad344-125">型指定された DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="ad344-125">Querying Typed DataSets</span></span>](querying-typed-datasets.md)
- <span data-ttu-id="ad344-126">[結合演算](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="ad344-126">[Join Operations](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))</span></span>
- [<span data-ttu-id="ad344-127">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="ad344-127">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
