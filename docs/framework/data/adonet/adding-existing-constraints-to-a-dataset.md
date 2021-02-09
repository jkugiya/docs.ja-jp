---
description: '詳細情報: DataSet への既存の制約の追加'
title: DataSet への既存の制約の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: cad0dd1bd16747a5e76e10784d00c14cd9aa8c2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729573"
---
# <a name="adding-existing-constraints-to-a-dataset"></a><span data-ttu-id="bbdc7-103">DataSet への既存の制約の追加</span><span class="sxs-lookup"><span data-stu-id="bbdc7-103">Adding Existing Constraints to a DataSet</span></span>

<span data-ttu-id="bbdc7-104">**DataAdapter** の **Fill** メソッドを使うと、<xref:System.Data.DataSet> にデータ ソースからのテーブルの列および行だけが格納されます。制約は一般にデータ ソースで設定されますが、既定では **Fill** メソッドによって **DataSet** にこのスキーマ情報は追加されません。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-104">The **Fill** method of the **DataAdapter** fills a <xref:System.Data.DataSet> only with table columns and rows from a data source; though constraints are commonly set by the data source, the **Fill** method does not add this schema information to the **DataSet** by default.</span></span> <span data-ttu-id="bbdc7-105">データ ソースからの既存の主キー制約情報を **DataSet** に設定するには、**DataAdapter** の **FillSchema** メソッドを呼び出すか、または **Fill** を呼び出す前に **DataAdapter** の **MissingSchemaAction** プロパティを **AddWithKey** に設定します。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-105">To populate a **DataSet** with existing primary key constraint information from a data source, you can either call the **FillSchema** method of the **DataAdapter**, or set the **MissingSchemaAction** property of the **DataAdapter** to **AddWithKey** before calling **Fill**.</span></span> <span data-ttu-id="bbdc7-106">これにより、データ ソースの主キー制約が **DataSet** の主キー制約に反映されます。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-106">This will ensure that primary key constraints in the **DataSet** reflect those at the data source.</span></span> <span data-ttu-id="bbdc7-107">外部キー制約情報はインクルードされないため、「[DataTable の制約](./dataset-datatable-dataview/datatable-constraints.md)」で示されているように明示的に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-107">Foreign key constraint information is not included and must be created explicitly, as shown in [DataTable Constraints](./dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
<span data-ttu-id="bbdc7-108">データを格納する前に **DataSet** にスキーマ情報を追加すると、**DataSet** 内の <xref:System.Data.DataTable> オブジェクトに主キー制約が含まれるようになります。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-108">Adding schema information to a **DataSet** before filling it with data ensures that primary key constraints are included with the <xref:System.Data.DataTable> objects in the **DataSet**.</span></span> <span data-ttu-id="bbdc7-109">その結果、**DataSet** に対して格納を行う追加の呼び出しを行うと、主キー列の情報を使用して、データ ソースからの新しい行と、各 **DataTable** の現在の行が照合されて、テーブルの現在のデータがデータ ソースのデータで上書きされます。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-109">As a result, when additional calls to fill the **DataSet** are made, the primary key column information is used to match new rows from the data source with current rows in each **DataTable**, and current data in the tables is overwritten with data from the data source.</span></span> <span data-ttu-id="bbdc7-110">スキーマ情報がないと、**DataSet** にデータ ソースからの新しい行が付け加えられ、重複行が発生します。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-110">Without the schema information, the new rows from the data source are appended to the **DataSet**, resulting in duplicate rows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbdc7-111">データ ソースの列が自動インクリメントとして指定されている場合、**FillSchema** メソッドまたは **MissingSchemaAction** が **AddWithKey** に設定された **Fill** メソッドでは、**AutoIncrement** プロパティが `true` に設定された **DataColumn** が作成されます。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-111">If a column in a data source is identified as auto-incrementing, the **FillSchema** method, or the **Fill** method with a **MissingSchemaAction** of **AddWithKey**, creates a **DataColumn** with an **AutoIncrement** property set to `true`.</span></span> <span data-ttu-id="bbdc7-112">ただし、**AutoIncrementStep** 値と **AutoIncrementSeed** 値は開発者自身が明示的に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-112">However, you will need to set the **AutoIncrementStep** and **AutoIncrementSeed** values yourself.</span></span> <span data-ttu-id="bbdc7-113">自動インクリメント列について詳しくは、「[AutoIncrement 列の作成](./dataset-datatable-dataview/creating-autoincrement-columns.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-113">For more information about auto-incrementing columns, see [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md).</span></span>  
  
<span data-ttu-id="bbdc7-114">**FillSchema** を使用したり、**MissingSchemaAction** を **AddWithKey** に設定したりすると、データ ソースで主キー列情報を確認するための追加の処理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-114">Using **FillSchema** or setting the **MissingSchemaAction** to **AddWithKey** requires extra processing at the data source to determine primary key column information.</span></span> <span data-ttu-id="bbdc7-115">この追加の処理によりパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-115">This additional processing can hinder performance.</span></span> <span data-ttu-id="bbdc7-116">デザイン時に主キー情報がわかっている場合は、最適のパフォーマンスを得るために主キー列 (複数の場合もある) を明示的に指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-116">If you know the primary key information at design time, we recommend that you explicitly specify the primary key column or columns in order to achieve optimal performance.</span></span> <span data-ttu-id="bbdc7-117">テーブルに関する主キー情報を明示的に設定する方法については、「[主キーの定義](./dataset-datatable-dataview/defining-primary-keys.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-117">For information about explicitly setting primary key information for a table, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>
  
<span data-ttu-id="bbdc7-118">次のコード例では、**FillSchema** を使用して **DataSet** にスキーマ情報を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-118">The following code example shows how to add schema information to a **DataSet** using **FillSchema**:</span></span>
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
<span data-ttu-id="bbdc7-119">次のコード例では、**Fill** メソッドの **MissingSchemaAction.AddWithKey** プロパティを使用して **DataSet** にスキーマ情報を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-119">The following code example shows how to add schema information to a **DataSet** using the **MissingSchemaAction.AddWithKey** property of the **Fill** method:</span></span>
  
```vb  
Dim custDataSet As New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
var custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="bbdc7-120">複数の結果セットの処理</span><span class="sxs-lookup"><span data-stu-id="bbdc7-120">Handling multiple result sets</span></span>  

<span data-ttu-id="bbdc7-121">**DataAdapter** では、**SelectCommand** から複数の結果セットが返された場合、**DataSet** に複数のテーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-121">If the **DataAdapter** encounters multiple result sets returned from the **SelectCommand**, it will create multiple tables in the **DataSet**.</span></span> <span data-ttu-id="bbdc7-122">テーブルには、**Table** *N* という既定の名前が設定されます。N は 0 から始まりインクリメントされますが、"Table0" ではなく **Table** から始まります。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-122">The tables will be given a zero-based incremental default name of **Table** *N*, starting with **Table** instead of "Table0".</span></span> <span data-ttu-id="bbdc7-123">テーブル名が **FillSchema** メソッドに引数として渡された場合は、テーブルには、**TableName** *N* という名前が設定されます。N は 0 から始まりインクリメントされますが、"TableName0" ではなく **TableName** から始まります。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-123">If a table name is passed as an argument to the **FillSchema** method, the tables will be given a zero-based incremental name of **TableName** *N*, starting with **TableName** instead of "TableName0".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbdc7-124">**OleDbDataAdapter** オブジェクトの **FillSchema** メソッドが、複数の結果セットを返すコマンドに対して呼び出された場合は、最初の結果セットのスキーマ情報のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-124">If the **FillSchema** method of the **OleDbDataAdapter** object is called for a command that returns multiple result sets, only the schema information from the first result set is returned.</span></span> <span data-ttu-id="bbdc7-125">**OleDbDataAdapter** を使用して複数の結果セットに対するスキーマ情報を返すときは、**Fill** メソッドを呼び出すときに **AddWithKey** に設定した **MissingSchemaAction** を指定して、スキーマ情報を取得することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbdc7-125">When returning schema information for multiple result sets using the **OleDbDataAdapter**, it is recommended that you specify a **MissingSchemaAction** of **AddWithKey** and obtain the schema information when calling the **Fill** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbdc7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbdc7-126">See also</span></span>

- [<span data-ttu-id="bbdc7-127">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="bbdc7-127">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="bbdc7-128">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="bbdc7-128">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="bbdc7-129">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="bbdc7-129">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="bbdc7-130">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="bbdc7-130">ADO.NET Overview</span></span>](ado-net-overview.md)
