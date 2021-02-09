---
description: '詳細情報: DataView によるフィルター処理 (LINQ to DataSet)'
title: DataView によるフィルター処理 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5632d74a-ff53-4ea7-9fe7-4a148eeb1c68
ms.openlocfilehash: 152b2e1d82cd5cf0eac24fd952de26d83fbffe58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724142"
---
# <a name="filtering-with-dataview-linq-to-dataset"></a><span data-ttu-id="7e898-103">DataView によるフィルター処理 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7e898-103">Filtering with DataView (LINQ to DataSet)</span></span>

<span data-ttu-id="7e898-104">特定の条件に基づいてデータをフィルター処理し、UI コントロールを介してそのデータをクライアントに提供する機能は、データ バインドの重要な特徴です。</span><span class="sxs-lookup"><span data-stu-id="7e898-104">The ability to filter data using specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="7e898-105"><xref:System.Data.DataView> は、データにフィルターを適用し、特定のフィルター条件を満たすデータ行のサブセットを返す方法をいくつか提供します。</span><span class="sxs-lookup"><span data-stu-id="7e898-105"><xref:System.Data.DataView> provides several ways to filter data and return subsets of data rows meeting specific filter criteria.</span></span> <span data-ttu-id="7e898-106">文字列ベースのフィルター処理機能に加え、<xref:System.Data.DataView> には、フィルター条件として LINQ 式を使用する機能も用意されています。</span><span class="sxs-lookup"><span data-stu-id="7e898-106">In addition to the string-based filtering capabilities, <xref:System.Data.DataView> also provides the ability to use LINQ expressions for the filtering criteria.</span></span> <span data-ttu-id="7e898-107">LINQ 式を使用すると、文字列ベースのフィルター処理よりはるかに複雑で強力なフィルター処理を実現できます。</span><span class="sxs-lookup"><span data-stu-id="7e898-107">LINQ expressions allow for much more complex and powerful filtering operations than the string-based filtering.</span></span>  
  
 <span data-ttu-id="7e898-108"><xref:System.Data.DataView> を使用してデータをフィルター処理する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="7e898-108">There are two ways to filter data using a <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="7e898-109">Where 句を含む LINQ to DataSet クエリから <xref:System.Data.DataView> を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e898-109">Create a <xref:System.Data.DataView> from a LINQ to DataSet query with a Where clause.</span></span>  
  
- <span data-ttu-id="7e898-110"><xref:System.Data.DataView> の既存の文字列ベースのフィルター機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e898-110">Use the existing, string-based filtering capabilities of <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-filtering-information"></a><span data-ttu-id="7e898-111">フィルター情報を含むクエリによる DataView の作成</span><span class="sxs-lookup"><span data-stu-id="7e898-111">Creating DataView from a Query with Filtering Information</span></span>  

 <span data-ttu-id="7e898-112"><xref:System.Data.DataView> オブジェクトは LINQ to DataSet クエリから作成できます。</span><span class="sxs-lookup"><span data-stu-id="7e898-112">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="7e898-113">このクエリに `Where` 句が含まれている場合、<xref:System.Data.DataView> はクエリのフィルター情報を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="7e898-113">If that query contains a `Where` clause, the <xref:System.Data.DataView> is created with the filtering information from the query.</span></span> <span data-ttu-id="7e898-114">`Where` 句内の式は、<xref:System.Data.DataView> に含めるデータ行の決定に使用され、これがフィルターの基礎となります。</span><span class="sxs-lookup"><span data-stu-id="7e898-114">The expression in the `Where` clause is used to determine which data rows will be included in the <xref:System.Data.DataView>, and is the basis for the filter.</span></span>  
  
 <span data-ttu-id="7e898-115">式ベースのフィルターは、文字列ベースのフィルターよりもはるかに強力で複雑なフィルター機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="7e898-115">Expression-based filters offer more powerful and complex filtering than the simpler string-based filters.</span></span> <span data-ttu-id="7e898-116">文字列ベースのフィルターと式ベースのフィルターは、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="7e898-116">The string-based and expression-based filters are mutually exclusive.</span></span> <span data-ttu-id="7e898-117"><xref:System.Data.DataView.RowFilter%2A> をクエリから作成した後に文字列ベースの <xref:System.Data.DataView> を設定した場合、クエリから推論される式ベースのフィルターはクリアされます。</span><span class="sxs-lookup"><span data-stu-id="7e898-117">When the string-based <xref:System.Data.DataView.RowFilter%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression based filter inferred from the query is cleared.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e898-118">ほとんどの場合、フィルターに使用する式は、副作用のない確定的な式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e898-118">In most cases, the expressions used for filtering should not have side effects and must be deterministic.</span></span> <span data-ttu-id="7e898-119">また、フィルター処理は任意の回数実行されるため、特定の実行回数に依存するロジックが式に含まれないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="7e898-119">Also, the expressions should not contain any logic that depends on a set number of executions, because the filtering operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7e898-120">例</span><span class="sxs-lookup"><span data-stu-id="7e898-120">Example</span></span>  

 <span data-ttu-id="7e898-121">次の例では、SalesOrderDetail テーブルに対して数量が 3 個以上 5 個以下の注文を取得するクエリを実行し、このクエリから <xref:System.Data.DataView> を作成します。次に、<xref:System.Data.DataView> を <xref:System.Windows.Forms.BindingSource> にバインドします。</span><span class="sxs-lookup"><span data-stu-id="7e898-121">The following example queries the SalesOrderDetail table for orders with a quantity greater than 2 and less than 6; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere)]  
  
### <a name="example"></a><span data-ttu-id="7e898-122">例</span><span class="sxs-lookup"><span data-stu-id="7e898-122">Example</span></span>  

 <span data-ttu-id="7e898-123">次の例では、2001 年 6 月 6 日以降に受けた注文に対するクエリから <xref:System.Data.DataView> を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e898-123">The following example creates a <xref:System.Data.DataView> from a query for orders placed after June 6, 2001:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhere3)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhere3](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhere3)]  
  
### <a name="example"></a><span data-ttu-id="7e898-124">例</span><span class="sxs-lookup"><span data-stu-id="7e898-124">Example</span></span>  

 <span data-ttu-id="7e898-125">フィルターは並べ替えと組み合わせることもできます。</span><span class="sxs-lookup"><span data-stu-id="7e898-125">Filtering can also be combined with sorting.</span></span> <span data-ttu-id="7e898-126">次の例では、姓が "S" で始まる連絡先を姓、名の順に並べ替えるクエリから <xref:System.Data.DataView> を作成します。</span><span class="sxs-lookup"><span data-stu-id="7e898-126">The following example creates a <xref:System.Data.DataView> from a query for contacts whose last name start with "S" and sorted by last name, then first name:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywhereorderbythenby)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywhereorderbythenby)]  
  
### <a name="example"></a><span data-ttu-id="7e898-127">例</span><span class="sxs-lookup"><span data-stu-id="7e898-127">Example</span></span>  

 <span data-ttu-id="7e898-128">次の例では、SoundEx アルゴリズムを使用して、"Zhu" に類似する姓を持つ連絡先を検索します。</span><span class="sxs-lookup"><span data-stu-id="7e898-128">The following example uses the SoundEx algorithm to find contacts whose last name is similar to "Zhu".</span></span> <span data-ttu-id="7e898-129">SoundEx アルゴリズムは、SoundEx メソッドに実装されています。</span><span class="sxs-lookup"><span data-stu-id="7e898-129">The SoundEx algorithm is implemented in the SoundEx method.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvsoundexfilter)]
 [!code-vb[DP DataView Samples#LDVSoundExFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvsoundexfilter)]  
  
 <span data-ttu-id="7e898-130">SoundEx は、米国国勢調査局 (U.S. Census Bureau) で最初に開発された、名前を英語の発音でインデックス化する音声アルゴリズム国勢調査局から無料で入手できます。</span><span class="sxs-lookup"><span data-stu-id="7e898-130">SoundEx is a phonetic algorithm used for indexing names by sound, as they are pronounced in English, originally developed by the U.S. Census Bureau.</span></span> <span data-ttu-id="7e898-131">SoundEx メソッドは、1 つの名前に対して、1 つの英字とそれに続く 3 つの数字から構成される 4 文字のコードを返します。</span><span class="sxs-lookup"><span data-stu-id="7e898-131">The SoundEx method returns a four character code for a name consisting of an English letter followed by three numbers.</span></span> <span data-ttu-id="7e898-132">文字は名前の最初の文字であり、数字は名前に含まれる残りの子音をコード化したものです。</span><span class="sxs-lookup"><span data-stu-id="7e898-132">The letter is the first letter of the name and the numbers encode the remaining consonants in the name.</span></span> <span data-ttu-id="7e898-133">発音が近い名前には、同じ SoundEx コードが与えられます。</span><span class="sxs-lookup"><span data-stu-id="7e898-133">Similar sounding names share the same SoundEx code.</span></span> <span data-ttu-id="7e898-134">前の例の SoundEx メソッドに使用されている SoundEx 実装を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7e898-134">The SoundEx implementation used in the SoundEx method of the previous example is shown here:</span></span>  
  
 [!code-csharp[DP DataView Samples#SoundEx](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#soundex)]
 [!code-vb[DP DataView Samples#SoundEx](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#soundex)]  
  
## <a name="using-the-rowfilter-property"></a><span data-ttu-id="7e898-135">RowFilter プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="7e898-135">Using the RowFilter Property</span></span>  

 <span data-ttu-id="7e898-136"><xref:System.Data.DataView> の既存の文字列ベースのフィルター機能は、LINQ to DataSet のコンテキストでそのまま動作します。</span><span class="sxs-lookup"><span data-stu-id="7e898-136">The existing string-based filtering functionality of <xref:System.Data.DataView> still works in the LINQ to DataSet context.</span></span> <span data-ttu-id="7e898-137">文字列ベースの <xref:System.Data.DataView.RowFilter%2A> のフィルター処理について詳しくは、「[データの並べ替えとフィルター処理](./dataset-datatable-dataview/sorting-and-filtering-data.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7e898-137">For more information about string-based <xref:System.Data.DataView.RowFilter%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="7e898-138">次の例では、Contact テーブルから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView.RowFilter%2A> プロパティを設定して、連絡先の姓が "Zhu" である行を返します。</span><span class="sxs-lookup"><span data-stu-id="7e898-138">The following example creates a <xref:System.Data.DataView> from the Contact table and then sets the <xref:System.Data.DataView.RowFilter%2A> property to return rows where the contact's last name is "Zhu":</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvrowfilter)]
 [!code-vb[DP DataView Samples#LDVRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvrowfilter)]  
  
 <span data-ttu-id="7e898-139"><xref:System.Data.DataView> または LINQ to DataSet クエリから <xref:System.Data.DataTable> を作成した後は、<xref:System.Data.DataView.RowFilter%2A> プロパティを使用して、列の値に基づいて行のサブセットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7e898-139">After a <xref:System.Data.DataView> has been created from a <xref:System.Data.DataTable> or LINQ to DataSet query, you can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="7e898-140">文字列ベースのフィルターと式ベースのフィルターは、相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="7e898-140">The string-based and expression-based filters are mutually exclusive.</span></span> <span data-ttu-id="7e898-141"><xref:System.Data.DataView.RowFilter%2A> プロパティを設定すると、LINQ to DataSet クエリから推論されたフィルター式はクリアされ、フィルター式を再設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="7e898-141">Setting the <xref:System.Data.DataView.RowFilter%2A> property will clear the filter expression inferred from the LINQ to DataSet query, and the filter expression cannot be reset.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromquerywheresetrowfilter)]
 [!code-vb[DP DataView Samples#LDVFromQueryWhereSetRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromquerywheresetrowfilter)]  
  
 <span data-ttu-id="7e898-142">データ サブセットの動的ビューの作成とは対照的に、データに対する特定のクエリの結果を取得する場合は、<xref:System.Data.DataView.Find%2A> プロパティを設定する代わりに <xref:System.Data.DataView.FindRows%2A> の <xref:System.Data.DataView> メソッドまたは <xref:System.Data.DataView.RowFilter%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e898-142">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="7e898-143"><xref:System.Data.DataView.RowFilter%2A> プロパティは、データ連結アプリケーションでの使用に適しています。このアプリケーションでは、連結されたコントロールによってフィルター処理結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e898-143">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="7e898-144"><xref:System.Data.DataView.RowFilter%2A> プロパティを設定すると、データのインデックスが再構築され、アプリケーションのオーバーヘッドが増加してパフォーマンスの低下を招きます。</span><span class="sxs-lookup"><span data-stu-id="7e898-144">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="7e898-145"><xref:System.Data.DataView.Find%2A> メソッドと <xref:System.Data.DataView.FindRows%2A> メソッドでは、現在のインデックスが使用されます。このため、インデックスを再構築する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7e898-145">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="7e898-146"><xref:System.Data.DataView.Find%2A> または <xref:System.Data.DataView.FindRows%2A> を 1 回だけ呼び出す場合は、既存の <xref:System.Data.DataView> を使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="7e898-146">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="7e898-147"><xref:System.Data.DataView.Find%2A> または <xref:System.Data.DataView.FindRows%2A> を複数回呼び出す場合は、新しい <xref:System.Data.DataView> を作成して検索対象の列のインデックスを再構築した後、<xref:System.Data.DataView.Find%2A> メソッドまたは <xref:System.Data.DataView.FindRows%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7e898-147">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="7e898-148"><xref:System.Data.DataView.Find%2A> メソッドと <xref:System.Data.DataView.FindRows%2A> メソッドについて詳しくは、「[行の検索](./dataset-datatable-dataview/finding-rows.md)」および「[DataView のパフォーマンス](dataview-performance.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7e898-148">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods see [Finding Rows](./dataset-datatable-dataview/finding-rows.md) and [DataView Performance](dataview-performance.md).</span></span>  
  
## <a name="clearing-the-filter"></a><span data-ttu-id="7e898-149">フィルターのクリア</span><span class="sxs-lookup"><span data-stu-id="7e898-149">Clearing the Filter</span></span>  

 <span data-ttu-id="7e898-150"><xref:System.Data.DataView> のフィルターは、<xref:System.Data.DataView.RowFilter%2A> プロパティを使用すると、フィルタリングが設定された後にクリアできます。</span><span class="sxs-lookup"><span data-stu-id="7e898-150">The filter on a <xref:System.Data.DataView> can be cleared after filtering has been set using the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="7e898-151"><xref:System.Data.DataView> のフィルターは、2 つの異なる方法でクリアできます。</span><span class="sxs-lookup"><span data-stu-id="7e898-151">The filter on a <xref:System.Data.DataView> can be cleared in two different ways:</span></span>  
  
- <span data-ttu-id="7e898-152"><xref:System.Data.DataView.RowFilter%2A> プロパティを `null`に設定します。</span><span class="sxs-lookup"><span data-stu-id="7e898-152">Set the <xref:System.Data.DataView.RowFilter%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="7e898-153"><xref:System.Data.DataView.RowFilter%2A> プロパティを空の文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="7e898-153">Set the <xref:System.Data.DataView.RowFilter%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7e898-154">例</span><span class="sxs-lookup"><span data-stu-id="7e898-154">Example</span></span>  

 <span data-ttu-id="7e898-155">次の例では、クエリから <xref:System.Data.DataView> を作成した後、<xref:System.Data.DataView.RowFilter%2A> プロパティを `null` に設定してフィルターをクリアします。</span><span class="sxs-lookup"><span data-stu-id="7e898-155">The following example creates a <xref:System.Data.DataView> from a query and then clears the filter by setting <xref:System.Data.DataView.RowFilter%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter2)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter2)]  
  
### <a name="example"></a><span data-ttu-id="7e898-156">例</span><span class="sxs-lookup"><span data-stu-id="7e898-156">Example</span></span>  

 <span data-ttu-id="7e898-157">次の例では、テーブルから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView.RowFilter%2A> プロパティを設定します。その後、<xref:System.Data.DataView.RowFilter%2A> プロパティを空の文字列に設定してフィルターをクリアします。</span><span class="sxs-lookup"><span data-stu-id="7e898-157">The following example creates a <xref:System.Data.DataView> from a table sets the <xref:System.Data.DataView.RowFilter%2A> property, and then clears the filter by setting the <xref:System.Data.DataView.RowFilter%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearrowfilter)]
 [!code-vb[DP DataView Samples#LDVClearRowFilter](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearrowfilter)]  
  
## <a name="see-also"></a><span data-ttu-id="7e898-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e898-158">See also</span></span>

- [<span data-ttu-id="7e898-159">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7e898-159">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="7e898-160">DataView による並べ替え</span><span class="sxs-lookup"><span data-stu-id="7e898-160">Sorting with DataView</span></span>](sorting-with-dataview-linq-to-dataset.md)
