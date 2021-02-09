---
description: '詳細情報: 行の状態とバージョン'
title: 行の状態とバージョン
ms.date: 07/19/2018
dev_langs:
- csharp
- vb
ms.assetid: 2e6642c9-bfc6-425c-b3a7-e4912ffa6c1f
ms.openlocfilehash: 7d436ffcfcf59f5daa4fc6eaa9f9018b92e5c608
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651679"
---
# <a name="row-states-and-row-versions"></a><span data-ttu-id="8fa87-103">行の状態とバージョン</span><span class="sxs-lookup"><span data-stu-id="8fa87-103">Row States and Row Versions</span></span>

<span data-ttu-id="8fa87-104">ADO.NET は、行の状態とバージョンを使用してテーブル内の行を管理します。</span><span class="sxs-lookup"><span data-stu-id="8fa87-104">ADO.NET manages rows in tables using row states and versions.</span></span> <span data-ttu-id="8fa87-105">行状態は、1 つの行のステータスを示します。行バージョンは、1 つの行の値が変更されるときに、変更に応じてその行に格納される現在の値、元の値、既定値などを維持します。</span><span class="sxs-lookup"><span data-stu-id="8fa87-105">A row state indicates the status of a row; row versions maintain the values stored in a row as it is modified, including current, original, and default values.</span></span> <span data-ttu-id="8fa87-106">たとえば、ある行の 1 つの列を変更すると、この行の状態は `Modified` になり、次の 2 つの行バージョンが存在することになります。`Current` には現在の行値が格納され、`Original` にはその列が変更される前の行値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-106">For example, after you have made a modification to a column in a row, the row will have a row state of `Modified`, and two row versions: `Current`, which contains the current row values, and `Original`, which contains the row values before the column was modified.</span></span>  
  
 <span data-ttu-id="8fa87-107">各 <xref:System.Data.DataRow> オブジェクトにある <xref:System.Data.DataRow.RowState%2A> プロパティを調べると、行の現在の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-107">Each <xref:System.Data.DataRow> object has a <xref:System.Data.DataRow.RowState%2A> property that you can examine to determine the current state of the row.</span></span> <span data-ttu-id="8fa87-108">`RowState` 列挙値ごとの簡単な説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="8fa87-108">The following table gives a brief description of each `RowState` enumeration value.</span></span>  
  
|<span data-ttu-id="8fa87-109">RowState の値</span><span class="sxs-lookup"><span data-stu-id="8fa87-109">RowState value</span></span>|<span data-ttu-id="8fa87-110">説明</span><span class="sxs-lookup"><span data-stu-id="8fa87-110">Description</span></span>|  
|--------------------|-----------------|  
|<xref:System.Data.DataRowState.Unchanged>|<span data-ttu-id="8fa87-111">`AcceptChanges` が最後に呼び出されてから、または `DataAdapter.Fill` によって行が作成されてから変更は行われていません。</span><span class="sxs-lookup"><span data-stu-id="8fa87-111">No changes have been made since the last call to `AcceptChanges` or since the row was created by `DataAdapter.Fill`.</span></span>|  
|<xref:System.Data.DataRowState.Added>|<span data-ttu-id="8fa87-112">行がテーブルに追加されましたが、`AcceptChanges` が呼び出されていません。</span><span class="sxs-lookup"><span data-stu-id="8fa87-112">The row has been added to the table, but `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Modified>|<span data-ttu-id="8fa87-113">行のいくつかの要素が変更されました。</span><span class="sxs-lookup"><span data-stu-id="8fa87-113">Some element of the row has been changed.</span></span>|  
|<xref:System.Data.DataRowState.Deleted>|<span data-ttu-id="8fa87-114">行がテーブルから削除されましたが、`AcceptChanges` が呼び出されていません。</span><span class="sxs-lookup"><span data-stu-id="8fa87-114">The row has been deleted from a table, and `AcceptChanges` has not been called.</span></span>|  
|<xref:System.Data.DataRowState.Detached>|<span data-ttu-id="8fa87-115">行がどの `DataRowCollection` にも属していません。</span><span class="sxs-lookup"><span data-stu-id="8fa87-115">The row is not part of any `DataRowCollection`.</span></span> <span data-ttu-id="8fa87-116">新しく作成された行の `RowState` は `Detached` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-116">The `RowState` of a newly created row is set to `Detached`.</span></span> <span data-ttu-id="8fa87-117">`DataRow` メソッドを呼び出して新しい `DataRowCollection` を `Add` に追加すると、`RowState` プロパティの値は `Added` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-117">After the new `DataRow` is added to the `DataRowCollection` by calling the `Add` method, the value of the `RowState` property is set to `Added`.</span></span><br /><br /> <span data-ttu-id="8fa87-118">`Detached` は、`DataRowCollection` メソッドを使用するか、または `Remove` メソッドに続いて `Delete` メソッドを使用して `AcceptChanges` から削除された行に対しても設定されます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-118">`Detached` is also set for a row that has been removed from a `DataRowCollection` using the `Remove` method, or by the `Delete` method followed by the `AcceptChanges` method.</span></span>|  
  
 <span data-ttu-id="8fa87-119">`AcceptChanges`、<xref:System.Data.DataSet>、または <xref:System.Data.DataTable> の <xref:System.Data.DataRow> が呼び出されると、`Deleted` の行状態を持つすべての行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-119">When `AcceptChanges` is called on a <xref:System.Data.DataSet>, <xref:System.Data.DataTable> , or <xref:System.Data.DataRow>, all rows with a row state of `Deleted` are removed.</span></span> <span data-ttu-id="8fa87-120">残りの行の行状態は `Unchanged` になり、`Original` 行バージョンの値は `Current` 行バージョンの値で上書きされます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-120">The remaining rows are given a row state of `Unchanged`, and the values in the `Original` row version are overwritten with the `Current` row version values.</span></span> <span data-ttu-id="8fa87-121">`RejectChanges` が呼び出されると、`Added` の行状態を持つすべての行が削除されます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-121">When `RejectChanges` is called, all rows with a row state of `Added` are removed.</span></span> <span data-ttu-id="8fa87-122">残りの行の行状態は `Unchanged` になり、`Current` 行バージョンの値は `Original` 行バージョンの値で上書きされます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-122">The remaining rows are given a row state of `Unchanged`, and the values in the `Current` row version are overwritten with the `Original` row version values.</span></span>  
  
 <span data-ttu-id="8fa87-123"><xref:System.Data.DataRowVersion> パラメーターと列参照を渡すことにより、ある行の行バージョンを表示する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8fa87-123">You can view the different row versions of a row by passing a <xref:System.Data.DataRowVersion> parameter with the column reference, as shown in the following example.</span></span>  
  
```vb  
Dim custRow As DataRow = custTable.Rows(0)  
Dim custID As String = custRow("CustomerID", DataRowVersion.Original).ToString()  
```  
  
```csharp  
DataRow custRow = custTable.Rows[0];  
string custID = custRow["CustomerID", DataRowVersion.Original].ToString();  
```  
  
 <span data-ttu-id="8fa87-124">`DataRowVersion` 列挙値ごとの簡単な説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="8fa87-124">The following table gives a brief description of each `DataRowVersion` enumeration value.</span></span>  
  
|<span data-ttu-id="8fa87-125">DataRowVersion の値</span><span class="sxs-lookup"><span data-stu-id="8fa87-125">DataRowVersion value</span></span>|<span data-ttu-id="8fa87-126">説明</span><span class="sxs-lookup"><span data-stu-id="8fa87-126">Description</span></span>|  
|--------------------------|-----------------|  
|<xref:System.Data.DataRowVersion.Current>|<span data-ttu-id="8fa87-127">行の現在の値。</span><span class="sxs-lookup"><span data-stu-id="8fa87-127">The current values for the row.</span></span> <span data-ttu-id="8fa87-128">この行バージョンは、`RowState` の `Deleted` を持つ行については存在しません。</span><span class="sxs-lookup"><span data-stu-id="8fa87-128">This row version does not exist for rows with a `RowState` of `Deleted`.</span></span>|  
|<xref:System.Data.DataRowVersion.Default>|<span data-ttu-id="8fa87-129">特定の行の既定の行バージョン。</span><span class="sxs-lookup"><span data-stu-id="8fa87-129">The default row version for a particular row.</span></span> <span data-ttu-id="8fa87-130">`Added`、`Modified`、または `Deleted` 行の既定の行バージョンは、`Current` です。</span><span class="sxs-lookup"><span data-stu-id="8fa87-130">The default row version for an `Added`, `Modified`, or `Deleted` row is `Current`.</span></span> <span data-ttu-id="8fa87-131">`Detached` 行の既定の行バージョンは、`Proposed` です。</span><span class="sxs-lookup"><span data-stu-id="8fa87-131">The default row version for a `Detached` row is `Proposed`.</span></span>|  
|<xref:System.Data.DataRowVersion.Original>|<span data-ttu-id="8fa87-132">行の元の値。</span><span class="sxs-lookup"><span data-stu-id="8fa87-132">The original values for the row.</span></span> <span data-ttu-id="8fa87-133">この行バージョンは、`RowState` の `Added` を持つ行については存在しません。</span><span class="sxs-lookup"><span data-stu-id="8fa87-133">This row version does not exist for rows with a `RowState` of `Added`.</span></span>|  
|<xref:System.Data.DataRowVersion.Proposed>|<span data-ttu-id="8fa87-134">行に対して提示された値。</span><span class="sxs-lookup"><span data-stu-id="8fa87-134">The proposed values for the row.</span></span> <span data-ttu-id="8fa87-135">この行バージョンは、行、つまり `DataRowCollection` の一部ではない行に対する編集操作の間存在します。</span><span class="sxs-lookup"><span data-stu-id="8fa87-135">This row version exists during an edit operation on a row, or for a row that is not part of a `DataRowCollection`.</span></span>|  
  
 <span data-ttu-id="8fa87-136">`DataRow` メソッドを呼び出して <xref:System.Data.DataRow.HasVersion%2A> を引数として渡すことにより、`DataRowVersion` が特定の行バージョンを持っているかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8fa87-136">You can test whether a `DataRow` has a particular row version by calling the <xref:System.Data.DataRow.HasVersion%2A> method and passing a `DataRowVersion` as an argument.</span></span> <span data-ttu-id="8fa87-137">たとえば、`DataRow.HasVersion(DataRowVersion.Original)` は、新しく追加された行に対して `false` が呼び出されていない場合に `AcceptChanges` を返します。</span><span class="sxs-lookup"><span data-stu-id="8fa87-137">For example, `DataRow.HasVersion(DataRowVersion.Original)` will return `false` for newly added rows before `AcceptChanges` has been called.</span></span>  
  
 <span data-ttu-id="8fa87-138">テーブルから削除されたすべての行の値を表示するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8fa87-138">The following code example displays the values in all the deleted rows of a table.</span></span> <span data-ttu-id="8fa87-139">`Deleted` 行には `Current` 行バージョンがないため、列値にアクセスするときに `DataRowVersion.Original` を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8fa87-139">`Deleted` rows do not have a `Current` row version, so you must pass `DataRowVersion.Original` when accessing the column values.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
  
Dim delRows() As DataRow = catTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
Console.WriteLine("Deleted rows:" & vbCrLf)  
  
Dim catCol As DataColumn  
Dim delRow As DataRow  
  
For Each catCol In catTable.Columns  
  Console.Write(catCol.ColumnName & vbTab)  
Next  
Console.WriteLine()  
  
For Each delRow In delRows  
  For Each catCol In catTable.Columns  
    Console.Write(delRow(catCol, DataRowVersion.Original) & vbTab)  
  Next  
  Console.WriteLine()  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
  
DataRow[] delRows = catTable.Select(null, null, DataViewRowState.Deleted);  
  
Console.WriteLine("Deleted rows:\n");  
  
foreach (DataColumn catCol in catTable.Columns)  
  Console.Write(catCol.ColumnName + "\t");  
Console.WriteLine();  
  
foreach (DataRow delRow in delRows)  
{  
  foreach (DataColumn catCol in catTable.Columns)  
    Console.Write(delRow[catCol, DataRowVersion.Original] + "\t");  
  Console.WriteLine();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fa87-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fa87-140">See also</span></span>

- [<span data-ttu-id="8fa87-141">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="8fa87-141">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="8fa87-142">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="8fa87-142">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8fa87-143">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="8fa87-143">DataAdapters and DataReaders</span></span>](../dataadapters-and-datareaders.md)
- [<span data-ttu-id="8fa87-144">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="8fa87-144">ADO.NET Overview</span></span>](../ado-net-overview.md)
