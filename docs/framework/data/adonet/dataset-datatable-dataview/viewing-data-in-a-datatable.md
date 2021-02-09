---
description: '詳細情報: DataTable 内のデータの表示'
title: DataTable 内のデータの表示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
ms.openlocfilehash: ffaa8283da17c98fc58486af8dad741a61bbafc8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651380"
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="260a2-103">DataTable 内のデータの表示</span><span class="sxs-lookup"><span data-stu-id="260a2-103">Viewing Data in a DataTable</span></span>

<span data-ttu-id="260a2-104"><xref:System.Data.DataTable> の内容には、**DataTable** の **Rows** コレクションと **Columns** コレクションを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="260a2-104">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="260a2-105">また、<xref:System.Data.DataTable.Select%2A> メソッドを使用すると、検索条件、並べ替え順序、行の状態などの基準に基づいて **DataTable** 内のデータのサブセットを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="260a2-105">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="260a2-106">さらに、主キー値を使用して特定の行を検索するときは、**DataRowCollection** の <xref:System.Data.DataRowCollection.Find%2A> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="260a2-106">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>

<span data-ttu-id="260a2-107">**DataTable** オブジェクトの **Select** メソッドからは、指定した条件と一致する <xref:System.Data.DataRow> オブジェクトのセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="260a2-107">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="260a2-108">**Select** は、オプションの引数として、フィルター式、並べ替え式、**DataViewRowState** を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="260a2-108">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="260a2-109">フィルター式では、**DataColumn** の値に基づいて返す行が特定されます (`LastName = 'Smith'` など)。</span><span class="sxs-lookup"><span data-stu-id="260a2-109">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="260a2-110">並べ替え式は、列の並べ替えについての標準 SQL 規則に基づく `LastName ASC, FirstName ASC` などの式です。</span><span class="sxs-lookup"><span data-stu-id="260a2-110">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="260a2-111">式の記述の規則については、**DataColumn** クラスの <xref:System.Data.DataColumn.Expression%2A> プロパティのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="260a2-111">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>

> [!TIP]
> <span data-ttu-id="260a2-112">**DataTable** の **Select** メソッドへの呼び出しを多数実行する場合は、最初に **DataTable** の <xref:System.Data.DataView> を作成することにより、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="260a2-112">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="260a2-113">**DataView** を作成すると、テーブルの行にインデックスが付けられます。</span><span class="sxs-lookup"><span data-stu-id="260a2-113">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="260a2-114">**Select** メソッドでそのインデックスを使用すると、クエリ結果を生成するまでの時間が大幅に短縮されます。</span><span class="sxs-lookup"><span data-stu-id="260a2-114">The **Select** method then uses that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="260a2-115">**DataTable** の **DataView** を作成する方法については、「[DataView](dataviews.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260a2-115">For information about creating a **DataView** for a **DataTable**, see [DataViews](dataviews.md).</span></span>

<span data-ttu-id="260a2-116">**Select** メソッドでは、<xref:System.Data.DataViewRowState> に基づいて、表示または操作する行のバージョンが決定されます。</span><span class="sxs-lookup"><span data-stu-id="260a2-116">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="260a2-117">有効な **DataViewRowState** 列挙値の説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="260a2-117">The following table describes the possible **DataViewRowState** enumeration values.</span></span>

|<span data-ttu-id="260a2-118">DataViewRowState の値</span><span class="sxs-lookup"><span data-stu-id="260a2-118">DataViewRowState value</span></span>|<span data-ttu-id="260a2-119">説明</span><span class="sxs-lookup"><span data-stu-id="260a2-119">Description</span></span>|
|----------------------------|-----------------|
|<span data-ttu-id="260a2-120">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="260a2-120">**CurrentRows**</span></span>|<span data-ttu-id="260a2-121">変更されていない行、追加された行、および変更された行を含む現在の行。</span><span class="sxs-lookup"><span data-stu-id="260a2-121">Current rows including unchanged, added, and modified rows.</span></span>|
|<span data-ttu-id="260a2-122">**削除済み**</span><span class="sxs-lookup"><span data-stu-id="260a2-122">**Deleted**</span></span>|<span data-ttu-id="260a2-123">削除された行。</span><span class="sxs-lookup"><span data-stu-id="260a2-123">A deleted row.</span></span>|
|<span data-ttu-id="260a2-124">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="260a2-124">**ModifiedCurrent**</span></span>|<span data-ttu-id="260a2-125">元のデータを変更した後のバージョンである、現在のバージョン。</span><span class="sxs-lookup"><span data-stu-id="260a2-125">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="260a2-126">(**ModifiedOriginal** を参照)</span><span class="sxs-lookup"><span data-stu-id="260a2-126">(See **ModifiedOriginal**.)</span></span>|
|<span data-ttu-id="260a2-127">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="260a2-127">**ModifiedOriginal**</span></span>|<span data-ttu-id="260a2-128">変更されたすべての行の元のバージョン。</span><span class="sxs-lookup"><span data-stu-id="260a2-128">The original version of all modified rows.</span></span> <span data-ttu-id="260a2-129">現在のバージョンは、**ModifiedCurrent** を使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="260a2-129">The current version is available using **ModifiedCurrent**.</span></span>|
|<span data-ttu-id="260a2-130">**追加**</span><span class="sxs-lookup"><span data-stu-id="260a2-130">**Added**</span></span>|<span data-ttu-id="260a2-131">新しい行。</span><span class="sxs-lookup"><span data-stu-id="260a2-131">A new row.</span></span>|
|<span data-ttu-id="260a2-132">**None**</span><span class="sxs-lookup"><span data-stu-id="260a2-132">**None**</span></span>|<span data-ttu-id="260a2-133">なし。</span><span class="sxs-lookup"><span data-stu-id="260a2-133">None.</span></span>|
|<span data-ttu-id="260a2-134">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="260a2-134">**OriginalRows**</span></span>|<span data-ttu-id="260a2-135">変更されていない行および削除された行を含む元の行。</span><span class="sxs-lookup"><span data-stu-id="260a2-135">Original rows, including unchanged and deleted rows.</span></span>|
|<span data-ttu-id="260a2-136">**Unchanged**</span><span class="sxs-lookup"><span data-stu-id="260a2-136">**Unchanged**</span></span>|<span data-ttu-id="260a2-137">変更されていない行。</span><span class="sxs-lookup"><span data-stu-id="260a2-137">An unchanged row.</span></span>|

<span data-ttu-id="260a2-138">次の例では、**DataSet** オブジェクトをフィルター処理して、**DataViewRowState** が **CurrentRows** に設定されている行だけを操作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="260a2-138">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>

```vb
Dim column As DataColumn
Dim row As DataRow

Dim currentRows() As DataRow = _
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)

If (currentRows.Length < 1 ) Then
  Console.WriteLine("No Current Rows Found")
Else
  For Each column in workTable.Columns
    Console.Write(vbTab & column.ColumnName)
  Next

  Console.WriteLine(vbTab & "RowState")

  For Each row In currentRows
    For Each column In workTable.Columns
      Console.Write(vbTab & row(column).ToString())
    Next

    Dim rowState As String = _
        System.Enum.GetName(row.RowState.GetType(), row.RowState)
    Console.WriteLine(vbTab & rowState)
  Next
End If
```

```csharp
DataRow[] currentRows = workTable.Select(
    null, null, DataViewRowState.CurrentRows);

if (currentRows.Length < 1 )
  Console.WriteLine("No Current Rows Found");
else
{
  foreach (DataColumn column in workTable.Columns)
    Console.Write("\t{0}", column.ColumnName);

  Console.WriteLine("\tRowState");

  foreach (DataRow row in currentRows)
  {
    foreach (DataColumn column in workTable.Columns)
      Console.Write("\t{0}", row[column]);

    Console.WriteLine("\t" + row.RowState);
  }
}
```

<span data-ttu-id="260a2-139">**Select** メソッドを使用して、異なる **RowState** 値またはフィールド値を持つ行を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="260a2-139">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="260a2-140">次の例では、削除されたすべての行を参照する **DataRow** 配列と、**CustID** 列が 5 より大きいすべての行 (**CustLName** の順に並べ替えられたもの) を参照する別の **DataRow** 配列が返されます。</span><span class="sxs-lookup"><span data-stu-id="260a2-140">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="260a2-141">**Deleted** 行の情報を表示する方法については、「[行の状態とバージョン](row-states-and-row-versions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="260a2-141">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>

```vb
' Retrieve all deleted rows.
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)

' Retrieve rows where CustID > 5, and order by CustLName.
Dim custRows() As DataRow = workTable.Select( _
    "CustID > 5", "CustLName ASC")
```

```csharp
// Retrieve all deleted rows.
DataRow[] deletedRows = workTable.Select(
    null, null, DataViewRowState.Deleted);

// Retrieve rows where CustID > 5, and order by CustLName.
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");
```

## <a name="see-also"></a><span data-ttu-id="260a2-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="260a2-142">See also</span></span>

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataViewRowState>
- [<span data-ttu-id="260a2-143">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="260a2-143">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="260a2-144">行の状態とバージョン</span><span class="sxs-lookup"><span data-stu-id="260a2-144">Row States and Row Versions</span></span>](row-states-and-row-versions.md)
- [<span data-ttu-id="260a2-145">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="260a2-145">ADO.NET Overview</span></span>](../ado-net-overview.md)
