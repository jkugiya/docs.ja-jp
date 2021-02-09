---
description: '詳細情報: DataAdapter DataTable と DataColumn のマップ'
title: DataAdapter DataTable と DataColumn のマップ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 25007925afa57dd0cb6e75f808444f1bfaeea9b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739734"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="42427-103">DataAdapter DataTable と DataColumn のマップ</span><span class="sxs-lookup"><span data-stu-id="42427-103">DataAdapter DataTable and DataColumn Mappings</span></span>

<span data-ttu-id="42427-104">**DataAdapter** の **TableMappings** プロパティには、0 個以上の <xref:System.Data.Common.DataTableMapping> オブジェクトのコレクションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="42427-104">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="42427-105">**DataTableMapping** では、データ ソースに対するクエリで返されたデータと <xref:System.Data.DataTable> の間のマスター マッピングが提供されます。</span><span class="sxs-lookup"><span data-stu-id="42427-105">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="42427-106">**DataTableMapping** 名は、**DataAdapter** の **Fill** メソッドに **DataTable** 名の代わりとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="42427-106">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="42427-107">**Authors** テーブルに対して **AuthorsMapping** という名前の **DataTableMapping** を作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="42427-107">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="42427-108">**DataTableMapping** を使用すると、**DataTable** 内でデータベースの列名とは異なる列名を使用できます。</span><span class="sxs-lookup"><span data-stu-id="42427-108">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="42427-109">**DataAdapter** では、テーブルの更新時にこのマップを使用して列が照合されます。</span><span class="sxs-lookup"><span data-stu-id="42427-109">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="42427-110">**DataAdapter** の **Fill** メソッドまたは **Update** メソッドを呼び出すときに **TableName** または **DataTableMapping** 名を指定しなかった場合、**DataAdapter** では "Table" という名前の **DataTableMapping** が検索されます。</span><span class="sxs-lookup"><span data-stu-id="42427-110">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="42427-111">その **DataTableMapping** が存在しない場合は、**DataTable** の **TableName** が "Table" になります。</span><span class="sxs-lookup"><span data-stu-id="42427-111">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="42427-112">"Table" という名前の **DataTableMapping** を作成することで既定の **DataTableMapping** を指定できます。</span><span class="sxs-lookup"><span data-stu-id="42427-112">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="42427-113">次に示すのは、<xref:System.Data.Common> 名前空間から **DataTableMapping** を作成し、それに "Table" という名前を付けて、指定した **DataAdapter** の既定のマップとして設定するコード サンプルです。</span><span class="sxs-lookup"><span data-stu-id="42427-113">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="42427-114">この例では、その後、クエリ結果の最初のテーブル (**Northwind** データベースの **Customers** テーブル) の列を <xref:System.Data.DataSet> の **Northwind Customers** テーブルにある、よりわかりやすい名前のセットに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="42427-114">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="42427-115">割り当てられない列には、データ ソースの列名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="42427-115">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="42427-116">より高度な条件下では、同じ **DataAdapter** を使用して複数の割り当てが設定された複数テーブルの読み込みのサポートが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="42427-116">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="42427-117">この場合、**DataTableMapping** オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="42427-117">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="42427-118">**Fill** メソッドに **DataSet** のインスタンスと **DataTableMapping** 名が渡されたとき、その名前の割り当てが存在する場合はその名前が使用され、存在しない場合はその名前の **DataTable** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="42427-118">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="42427-119">次に示すのは、**Customers** という名前と **BizTalkSchema** という **DataTable** 名を持つ **DataTableMapping** を作成する例です。</span><span class="sxs-lookup"><span data-stu-id="42427-119">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="42427-120">この例では、その後で、SELECT ステートメントで返された行を **BizTalkSchema** **DataTable** に割り当てています。</span><span class="sxs-lookup"><span data-stu-id="42427-120">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="42427-121">列マップにソースの列名を指定しなかった場合、またはテーブル マップにソース テーブル名を指定しなかった場合は、自動的に既定の名前が生成されます。</span><span class="sxs-lookup"><span data-stu-id="42427-121">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="42427-122">列マップにソース列を指定しなかった場合は、列マップに **SourceColumn1** から始まるインクリメンタル既定名 \**SourceColumn\*\*\*N* が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="42427-122">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="42427-123">テーブル マップにソース テーブル名を指定しなかった場合は、テーブル マップに **SourceTable1** から始まるインクリメンタル既定名 \**SourceTable\*\*\*N* が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="42427-123">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42427-124">列マップには、\**SourceColumn\*\*\*N* の命名規則を使用しないこと、また、テーブルの割り当てには \**SourceTable\*\*\*N* を使用しないことをお勧めします。これは、指定した名前が **ColumnMappingCollection** 内の既存する既定の列マップ名または **DataTableMappingCollection** 内のテーブル マップ名と競合しないようにするためです。</span><span class="sxs-lookup"><span data-stu-id="42427-124">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="42427-125">指定した名前が既に存在する場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="42427-125">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="42427-126">複数の結果セットの処理</span><span class="sxs-lookup"><span data-stu-id="42427-126">Handling Multiple Result Sets</span></span>  

 <span data-ttu-id="42427-127">**SelectCommand** で複数のテーブルが返される場合、**Fill** では **DataSet** 内のテーブルに対する、インクリメント値を含むテーブル名が自動的に生成されます。これは、指定したテーブル名で開始し、\**TableName\*\*\*N* の形式で **TableName1** から数値を加算していく名前になります。</span><span class="sxs-lookup"><span data-stu-id="42427-127">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="42427-128">自動的に生成されたテーブル名は、テーブルの割り当てを使用して **DataSet** 内でテーブルに指定する名前に変換できます。</span><span class="sxs-lookup"><span data-stu-id="42427-128">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="42427-129">たとえば、**Customers** および **Orders** という 2 つのテーブルを返す **SelectCommand** に対して、次の **Fill** 呼び出しを実行します。</span><span class="sxs-lookup"><span data-stu-id="42427-129">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="42427-130">**DataSet** には、次の 2 つのテーブルが作成されます: **Customers** と **Customers1**。</span><span class="sxs-lookup"><span data-stu-id="42427-130">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="42427-131">テーブル マップを使用して、2 つ目のテーブルに **Customers1** という名前の代わりに **Orders** という名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="42427-131">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="42427-132">それには、次の例に示すように、ソース テーブル **Customers1** を **DataSet** テーブルの **Orders** に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="42427-132">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="42427-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="42427-133">See also</span></span>

- [<span data-ttu-id="42427-134">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="42427-134">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="42427-135">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="42427-135">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="42427-136">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="42427-136">ADO.NET Overview</span></span>](ado-net-overview.md)
