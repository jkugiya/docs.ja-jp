---
description: '詳細情報: DataView による並べ替え (LINQ to DataSet)'
title: DataView による並べ替え (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: ac07e5bc2c74a5724a4497d630d7352694ac9a7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718682"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="0064e-103">DataView による並べ替え (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="0064e-103">Sorting with DataView (LINQ to DataSet)</span></span>

<span data-ttu-id="0064e-104">特定の条件に基づいてデータを並べ替え、UI コントロールを介してそのデータをクライアントに提供する機能は、データ バインディングの重要な特徴です。</span><span class="sxs-lookup"><span data-stu-id="0064e-104">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="0064e-105"><xref:System.Data.DataView> には、データを並べ替え、特定の並べ替え条件に従って並べ替えられたデータ行を返す方法がいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="0064e-105"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="0064e-106">文字列ベースの並べ替え機能に加え、<xref:System.Data.DataView> では、並べ替え条件として LINQ (統合言語クエリ) の式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0064e-106">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use Language-Integrated Query (LINQ) expressions for the sorting criteria.</span></span> <span data-ttu-id="0064e-107">LINQ 式を使用すると、文字列ベースの並べ替え処理よりもはるかに複雑で強力な並べ替え処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="0064e-107">LINQ expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="0064e-108">このトピックでは、<xref:System.Data.DataView> を使用して並べ替えを行うこの 2 つの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0064e-108">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="0064e-109">並べ替え情報を含むクエリによる DataView の作成</span><span class="sxs-lookup"><span data-stu-id="0064e-109">Creating DataView from a Query with Sorting Information</span></span>  

 <span data-ttu-id="0064e-110"><xref:System.Data.DataView> オブジェクトは LINQ to DataSet クエリから作成できます。</span><span class="sxs-lookup"><span data-stu-id="0064e-110">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="0064e-111">そのクエリに <xref:System.Linq.Enumerable.OrderBy%2A> 句、<xref:System.Linq.Enumerable.OrderByDescending%2A> 句、<xref:System.Linq.Enumerable.ThenBy%2A> 句、または <xref:System.Linq.Enumerable.ThenByDescending%2A> 句が含まれている場合、これらの句の式が、<xref:System.Data.DataView> 内のデータを並べ替えるための基準として使用されます。</span><span class="sxs-lookup"><span data-stu-id="0064e-111">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="0064e-112">たとえば、クエリに `Order By…` 句と `Then By…` 句が含まれている場合、結果の <xref:System.Data.DataView> では、指定された両方の列によってデータが並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="0064e-112">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="0064e-113">式ベースの並べ替えは、文字列ベースの並べ替えよりもはるかに強力で複雑な並べ替え機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="0064e-113">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="0064e-114">文字列ベースの並べ替え機能と式ベースの並べ替え機能は、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="0064e-114">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="0064e-115"><xref:System.Data.DataView.Sort%2A> をクエリから作成した後に文字列ベースの <xref:System.Data.DataView> を設定した場合、クエリから推論される式ベースの並べ替えはクリアされます (再設定できません)。</span><span class="sxs-lookup"><span data-stu-id="0064e-115">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="0064e-116"><xref:System.Data.DataView> のインデックスは、<xref:System.Data.DataView> の作成時に構築されるほか、並べ替えまたはフィルター処理の情報が変更されたときにも構築されます。</span><span class="sxs-lookup"><span data-stu-id="0064e-116">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="0064e-117">最高のパフォーマンスを得るには、<xref:System.Data.DataView> の作成元である LINQ to DataSet クエリで並べ替え条件を指定し、後で並べ替え情報を変更しないようにします。</span><span class="sxs-lookup"><span data-stu-id="0064e-117">You get the best performance by supplying sorting criteria in the LINQ to DataSet query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="0064e-118">詳しくは、「[DataView のパフォーマンス](dataview-performance.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0064e-118">For more information, see [DataView Performance](dataview-performance.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0064e-119">ほとんどの場合、並べ替えに使用する式は、副作用のない確定的な式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0064e-119">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="0064e-120">また、並べ替え処理は任意の回数実行されるため、特定の実行回数に依存するロジックが式に含まれないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="0064e-120">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0064e-121">例</span><span class="sxs-lookup"><span data-stu-id="0064e-121">Example</span></span>  

 <span data-ttu-id="0064e-122">次の例では、SalesOrderHeader テーブルに対してクエリを実行し、返された行を発注日順に並べ替えます。次にこのクエリから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView> を <xref:System.Windows.Forms.BindingSource> にバインドします。</span><span class="sxs-lookup"><span data-stu-id="0064e-122">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="0064e-123">例</span><span class="sxs-lookup"><span data-stu-id="0064e-123">Example</span></span>  

 <span data-ttu-id="0064e-124">次の例では、SalesOrderHeader テーブルに対してクエリを実行し、返された行を合計支払額順に並べ替えます。次にこのクエリから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView> を <xref:System.Windows.Forms.BindingSource> にバインドします。</span><span class="sxs-lookup"><span data-stu-id="0064e-124">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="0064e-125">例</span><span class="sxs-lookup"><span data-stu-id="0064e-125">Example</span></span>  

 <span data-ttu-id="0064e-126">次の例では、SalesOrderDetail テーブルに対してクエリを実行し、返された行を注文数量順および販売注文 ID 順に並べ替えます。次にこのクエリから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView> を <xref:System.Windows.Forms.BindingSource> にバインドします。</span><span class="sxs-lookup"><span data-stu-id="0064e-126">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="0064e-127">文字列ベースの Sort プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="0064e-127">Using the String-Based Sort Property</span></span>  

 <span data-ttu-id="0064e-128"><xref:System.Data.DataView> の文字列ベースの並べ替え機能は LINQ to DataSet で動作します。</span><span class="sxs-lookup"><span data-stu-id="0064e-128">The string-based sorting functionality of <xref:System.Data.DataView> still works with LINQ to DataSet.</span></span> <span data-ttu-id="0064e-129"><xref:System.Data.DataView> を LINQ to DataSet クエリから作成した後、<xref:System.Data.DataView.Sort%2A> プロパティを使用して、<xref:System.Data.DataView> の並べ替えを設定できます。</span><span class="sxs-lookup"><span data-stu-id="0064e-129">After a <xref:System.Data.DataView> has been created from a LINQ to DataSet query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="0064e-130">文字列ベースの並べ替え機能と式ベースの並べ替え機能は、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="0064e-130">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="0064e-131"><xref:System.Data.DataView.Sort%2A> プロパティを設定すると、<xref:System.Data.DataView> の作成元のクエリから推論される式ベースの並べ替えはクリアされます。</span><span class="sxs-lookup"><span data-stu-id="0064e-131">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="0064e-132">文字列ベースの <xref:System.Data.DataView.Sort%2A> のフィルター処理について詳しくは、「[データの並べ替えとフィルター処理](./dataset-datatable-dataview/sorting-and-filtering-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0064e-132">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="0064e-133">例</span><span class="sxs-lookup"><span data-stu-id="0064e-133">Example</span></span>  

 <span data-ttu-id="0064e-134">次の例では、<xref:System.Data.DataView> を Contact テーブルから作成した後、姓を降順に並べ替え、名を昇順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="0064e-134">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="0064e-135">例</span><span class="sxs-lookup"><span data-stu-id="0064e-135">Example</span></span>  

 <span data-ttu-id="0064e-136">次の例では、姓が "S" で始まる連絡先を取得するクエリを Contact テーブルに対して実行します。</span><span class="sxs-lookup"><span data-stu-id="0064e-136">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="0064e-137">このクエリから <xref:System.Data.DataView> が作成され、<xref:System.Windows.Forms.BindingSource> オブジェクトにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="0064e-137">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="0064e-138">並べ替えのクリア</span><span class="sxs-lookup"><span data-stu-id="0064e-138">Clearing the Sort</span></span>  

 <span data-ttu-id="0064e-139"><xref:System.Data.DataView> の並べ替え情報は、<xref:System.Data.DataView.Sort%2A> プロパティを使用すると、並べ替えが設定された後にクリアできます。</span><span class="sxs-lookup"><span data-stu-id="0064e-139">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="0064e-140"><xref:System.Data.DataView> の並べ替え情報は、2 つの方法でクリアできます。</span><span class="sxs-lookup"><span data-stu-id="0064e-140">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="0064e-141"><xref:System.Data.DataView.Sort%2A> プロパティを `null`に設定します。</span><span class="sxs-lookup"><span data-stu-id="0064e-141">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="0064e-142"><xref:System.Data.DataView.Sort%2A> プロパティを空の文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="0064e-142">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0064e-143">例</span><span class="sxs-lookup"><span data-stu-id="0064e-143">Example</span></span>  

 <span data-ttu-id="0064e-144">次の例では、クエリから <xref:System.Data.DataView> を作成した後、<xref:System.Data.DataView.Sort%2A> プロパティを空の文字列に設定して並べ替えをクリアします。</span><span class="sxs-lookup"><span data-stu-id="0064e-144">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="0064e-145">例</span><span class="sxs-lookup"><span data-stu-id="0064e-145">Example</span></span>  

 <span data-ttu-id="0064e-146">次の例では、Contact テーブルから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView.Sort%2A> プロパティを設定して、連絡先の姓を降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="0064e-146">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="0064e-147">次に、<xref:System.Data.DataView.Sort%2A> プロパティを `null` に設定して並べ替え情報をクリアします。</span><span class="sxs-lookup"><span data-stu-id="0064e-147">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="0064e-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="0064e-148">See also</span></span>

- [<span data-ttu-id="0064e-149">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="0064e-149">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="0064e-150">DataView によるフィルター処理</span><span class="sxs-lookup"><span data-stu-id="0064e-150">Filtering with DataView</span></span>](filtering-with-dataview-linq-to-dataset.md)
- <span data-ttu-id="0064e-151">[データの並べ替え](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="0064e-151">[Sorting Data](/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span></span>
