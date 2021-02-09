---
description: '詳細情報: DataSet の内容のコピー'
title: DataSet の内容のコピー
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
ms.openlocfilehash: 4b49ad367c96dd7c99363c7c4282930a6e4da37d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739691"
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="1b24d-103">DataSet の内容のコピー</span><span class="sxs-lookup"><span data-stu-id="1b24d-103">Copying DataSet Contents</span></span>

<span data-ttu-id="1b24d-104"><xref:System.Data.DataSet> のコピーを作成すると、元のデータに影響せずにデータを使用したり、**DataSet** のデータのサブセットを使用したりできます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-104">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="1b24d-105">**DataSet** をコピーすると、次の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-105">When copying a **DataSet**, you can:</span></span>  
  
- <span data-ttu-id="1b24d-106">スキーマ、データ、行状態情報、行バージョンなどの **DataSet** の正確なコピーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-106">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
- <span data-ttu-id="1b24d-107">既存の **DataSet** のスキーマを含み、行だけを変更した **DataSet** を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-107">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="1b24d-108">変更されたすべての行を返したり、特定の **DataRowState** を指定したりできます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-108">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="1b24d-109">行の状態の詳細については、「[行の状態とバージョン](row-states-and-row-versions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b24d-109">For more information about row states, see [Row States and Row Versions](row-states-and-row-versions.md).</span></span>  
  
- <span data-ttu-id="1b24d-110">行をコピーせずに、**DataSet** のスキーマ (リレーショナル構造) だけをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-110">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="1b24d-111">行は、<xref:System.Data.DataTable> を使用して、既存の <xref:System.Data.DataTable.ImportRow%2A> にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-111">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="1b24d-112">スキーマとデータを含む **DataSet** の正確なコピーを作成するには、**DataSet** の <xref:System.Data.DataSet.Copy%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b24d-112">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="1b24d-113">**DataSet** の正確なコピーを作成する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="1b24d-113">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="1b24d-114">スキーマと、**Added**、**Modified**、または **Deleted** の行を表すデータだけが含まれる **DataSet** のコピーを作成するには、**DataSet** の <xref:System.Data.DataSet.GetChanges%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b24d-114">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="1b24d-115">また、**GetChanges** の呼び出し時に **DataRowState** の値を渡すことによって、**GetChanges** を使用して特定の行状態の行だけを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-115">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="1b24d-116">**GetChanges** の呼び出し時に **DataRowState** を渡す方法のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1b24d-116">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="1b24d-117">スキーマだけを含む **DataSet** のコピーを作成するには、**DataSet** の <xref:System.Data.DataSet.Clone%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1b24d-117">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="1b24d-118">また、**DataTable** の **ImportRow** メソッドを使用して、複製した **DataSet** に既存の行を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-118">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="1b24d-119">**ImportRow** メソッドを使用すると、データ、行の状態、および行バージョンの情報が指定したテーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-119">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="1b24d-120">列名が一致し、データ型が互換性のある型の場合には、列の値だけが追加されます。</span><span class="sxs-lookup"><span data-stu-id="1b24d-120">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="1b24d-121">**DataSet** の複製を作成し、**CountryRegion** 列の値が "Germany" の顧客に対する **DataSet** の複製内の **Customers** テーブルに、元の **DataSet** の行を追加するコードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1b24d-121">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b24d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b24d-122">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [<span data-ttu-id="1b24d-123">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="1b24d-123">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1b24d-124">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="1b24d-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
