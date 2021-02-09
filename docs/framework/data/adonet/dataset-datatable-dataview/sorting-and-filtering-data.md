---
description: '詳細情報: データの並べ替えとフィルター処理'
title: データの並べ替えとフィルター処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fdd9c753-39df-48cd-9822-2781afe76200
ms.openlocfilehash: a8b74dc13e88f8d5e70bb27291e0e6e34817f0ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651614"
---
# <a name="sorting-and-filtering-data"></a><span data-ttu-id="fd43d-103">データの並べ替えとフィルター処理</span><span class="sxs-lookup"><span data-stu-id="fd43d-103">Sorting and Filtering Data</span></span>

<span data-ttu-id="fd43d-104"><xref:System.Data.DataView> には、<xref:System.Data.DataTable> のデータの並べ替えとフィルター処理を行うさまざまな方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="fd43d-104">The <xref:System.Data.DataView> provides several ways of sorting and filtering data in a <xref:System.Data.DataTable>:</span></span>  
  
- <span data-ttu-id="fd43d-105"><xref:System.Data.DataView.Sort%2A> プロパティを使用すれば、1 列または複数列の並べ替え順序を指定し、ASC (昇順) パラメーターと DESC (降順) パラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-105">You can use the <xref:System.Data.DataView.Sort%2A> property to specify single or multiple column sort orders and include ASC (ascending) and DESC (descending) parameters.</span></span>  
  
- <span data-ttu-id="fd43d-106"><xref:System.Data.DataView.ApplyDefaultSort%2A> プロパティを使用すると、テーブルの主キー列 (1 列または複数列) に基づいて、昇順の並べ替え順序を自動的に作成できます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-106">You can use the <xref:System.Data.DataView.ApplyDefaultSort%2A> property to automatically create a sort order, in ascending order, based on the primary key column or columns of the table.</span></span> <span data-ttu-id="fd43d-107">**Sort** プロパティが null 参照または空の文字列の場合、およびテーブルに主キーが定義されている場合は、<xref:System.Data.DataView.ApplyDefaultSort%2A> だけが適用されます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-107"><xref:System.Data.DataView.ApplyDefaultSort%2A> only applies when the **Sort** property is a null reference or an empty string, and when the table has a primary key defined.</span></span>  
  
- <span data-ttu-id="fd43d-108"><xref:System.Data.DataView.RowFilter%2A> プロパティを使用すると、列の値に基づいて行のサブセットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-108">You can use the <xref:System.Data.DataView.RowFilter%2A> property to specify subsets of rows based on their column values.</span></span> <span data-ttu-id="fd43d-109">**RowFilter** プロパティの有効な式の詳細については、<xref:System.Data.DataColumn> クラスの <xref:System.Data.DataColumn.Expression%2A> プロパティの情報を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd43d-109">For details about valid expressions for the **RowFilter** property, see the reference information for the <xref:System.Data.DataColumn.Expression%2A> property of the <xref:System.Data.DataColumn> class.</span></span>  
  
     <span data-ttu-id="fd43d-110">データ サブセットの動的ビューの作成とは対照的に、データに対して特定のクエリの実行結果を返す場合、パフォーマンスを最大限に引き出すには、**RowFilter** プロパティを設定する代わりに **DataView** の <xref:System.Data.DataView.Find%2A> メソッドまたは <xref:System.Data.DataView.FindRows%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fd43d-110">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the **DataView** to achieve best performance rather than setting the **RowFilter** property.</span></span> <span data-ttu-id="fd43d-111">**RowFilter** プロパティを設定すると、データのインデックスが再作成され、アプリケーションのオーバーヘッドが増加してパフォーマンスの低下を招きます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-111">Setting the **RowFilter** property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="fd43d-112">**RowFilter** プロパティは、データ連結アプリケーションでの使用に適しています。このアプリケーションでは、連結されたコントロールによってフィルター処理結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-112">The **RowFilter** property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="fd43d-113">**Find** メソッドと **FindRows** メソッドでは、現在のインデックスが使用されます。このため、インデックスを再作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fd43d-113">The **Find** and **FindRows** methods leverage the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="fd43d-114">**Find** メソッドと **FindRows** メソッドの詳細については、「[行の検索](finding-rows.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd43d-114">For more information about the **Find** and **FindRows** methods, see [Finding Rows](finding-rows.md).</span></span>  
  
- <span data-ttu-id="fd43d-115"><xref:System.Data.DataView.RowStateFilter%2A> プロパティを使用して、表示する行バージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-115">You can use the <xref:System.Data.DataView.RowStateFilter%2A> property to specify which row versions to view.</span></span> <span data-ttu-id="fd43d-116">**DataView** では、基になる行の **RowState** に応じて、公開する行バージョンが暗黙的に管理されます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-116">The **DataView** implicitly manages which row version to expose depending upon the **RowState** of the underlying row.</span></span> <span data-ttu-id="fd43d-117">たとえば、**RowStateFilter** が **DataViewRowState.Deleted** に設定されている場合は、**Current** 行バージョンが存在しないため、**DataView** ではすべての **Deleted** 行の **Original** 行バージョンが公開されます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-117">For example, if the **RowStateFilter** is set to **DataViewRowState.Deleted**, the **DataView** exposes the **Original** row version of all **Deleted** rows because there is no **Current** row version.</span></span> <span data-ttu-id="fd43d-118">**DataRowView** の **RowVersion** プロパティを使用すると、公開される行のバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="fd43d-118">You can determine which row version of a row is being exposed by using the **RowVersion** property of the **DataRowView**.</span></span>  
  
     <span data-ttu-id="fd43d-119">**DataViewRowState** のオプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="fd43d-119">The following table shows the options for **DataViewRowState**.</span></span>  
  
    |<span data-ttu-id="fd43d-120">DataViewRowState のオプション</span><span class="sxs-lookup"><span data-stu-id="fd43d-120">DataViewRowState options</span></span>|<span data-ttu-id="fd43d-121">説明</span><span class="sxs-lookup"><span data-stu-id="fd43d-121">Description</span></span>|  
    |------------------------------|-----------------|  
    |<span data-ttu-id="fd43d-122">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="fd43d-122">**CurrentRows**</span></span>|<span data-ttu-id="fd43d-123">すべての **Unchanged** 行、**Added** 行、**Modified** 行の **Current** 行バージョン。</span><span class="sxs-lookup"><span data-stu-id="fd43d-123">The **Current** row version of all **Unchanged**, **Added**, and **Modified** rows.</span></span> <span data-ttu-id="fd43d-124">既定値です。</span><span class="sxs-lookup"><span data-stu-id="fd43d-124">This is the default.</span></span>|  
    |<span data-ttu-id="fd43d-125">**追加**</span><span class="sxs-lookup"><span data-stu-id="fd43d-125">**Added**</span></span>|<span data-ttu-id="fd43d-126">すべての **Added** 行の **Current** 行バージョン。</span><span class="sxs-lookup"><span data-stu-id="fd43d-126">The **Current** row version of all **Added** rows.</span></span>|  
    |<span data-ttu-id="fd43d-127">**削除済み**</span><span class="sxs-lookup"><span data-stu-id="fd43d-127">**Deleted**</span></span>|<span data-ttu-id="fd43d-128">すべての **Deleted** 行の **Original** 行バージョン。</span><span class="sxs-lookup"><span data-stu-id="fd43d-128">The **Original** row version of all **Deleted** rows.</span></span>|  
    |<span data-ttu-id="fd43d-129">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="fd43d-129">**ModifiedCurrent**</span></span>|<span data-ttu-id="fd43d-130">すべての **Modified** 行の **Current** 行バージョン。</span><span class="sxs-lookup"><span data-stu-id="fd43d-130">The **Current** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="fd43d-131">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="fd43d-131">**ModifiedOriginal**</span></span>|<span data-ttu-id="fd43d-132">すべての **Modified** 行の **Original** 行バージョン。</span><span class="sxs-lookup"><span data-stu-id="fd43d-132">The **Original** row version of all **Modified** rows.</span></span>|  
    |<span data-ttu-id="fd43d-133">**None**</span><span class="sxs-lookup"><span data-stu-id="fd43d-133">**None**</span></span>|<span data-ttu-id="fd43d-134">行がありません。</span><span class="sxs-lookup"><span data-stu-id="fd43d-134">No rows.</span></span>|  
    |<span data-ttu-id="fd43d-135">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="fd43d-135">**OriginalRows**</span></span>|<span data-ttu-id="fd43d-136">すべての **Unchanged** 行、**Modified** 行、**Deleted** 行の **Original** 行バージョン。</span><span class="sxs-lookup"><span data-stu-id="fd43d-136">The **Original** row version of all **Unchanged**, **Modified**, and **Deleted** rows.</span></span>|  
    |<span data-ttu-id="fd43d-137">**Unchanged**</span><span class="sxs-lookup"><span data-stu-id="fd43d-137">**Unchanged**</span></span>|<span data-ttu-id="fd43d-138">すべての **Unchanged** 行の **Current** 行バージョン。</span><span class="sxs-lookup"><span data-stu-id="fd43d-138">The **Current** row version of all **Unchanged** rows.</span></span>|  
  
 <span data-ttu-id="fd43d-139">行の状態と行バージョンの詳細については、「[行の状態とバージョン](row-states-and-row-versions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd43d-139">For more information about row states and row versions, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
 <span data-ttu-id="fd43d-140">在庫数が標準在庫数以下である製品を、仕入先 ID (supplier ID) で並べ替え、さらに製品名 (product name) で並べ替えたビューを作成するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="fd43d-140">The following code example creates a view that shows all the products where the number of units in stock is less than or equal to the reorder level, sorted first by supplier ID and then by product name.</span></span>  
  
```vb  
Dim prodView As DataView = New DataView(prodDS.Tables("Products"), _  
   "UnitsInStock <= ReorderLevel", _  
   "SupplierID, ProductName", _  
   DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView prodView = new DataView(prodDS.Tables["Products"],  
   "UnitsInStock <= ReorderLevel",  
   "SupplierID, ProductName",  
   DataViewRowState.CurrentRows);  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd43d-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd43d-141">See also</span></span>

- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [<span data-ttu-id="fd43d-142">DataViews</span><span class="sxs-lookup"><span data-stu-id="fd43d-142">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="fd43d-143">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="fd43d-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
