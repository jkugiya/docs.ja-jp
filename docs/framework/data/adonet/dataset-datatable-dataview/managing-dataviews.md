---
description: '詳細情報: DataViews の管理'
title: DataViews の管理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b67fab5-1722-4d2b-bfc1-247a75f0f1ee
ms.openlocfilehash: cdd9da9c4f67321dba36d22610704fc2e2561930
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652095"
---
# <a name="managing-dataviews"></a><span data-ttu-id="b0d2e-103">DataViews の管理</span><span class="sxs-lookup"><span data-stu-id="b0d2e-103">Managing DataViews</span></span>

<span data-ttu-id="b0d2e-104"><xref:System.Data.DataViewManager> のすべてのテーブルのビュー設定を管理するには、<xref:System.Data.DataView> を使用します。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-104">You can use a <xref:System.Data.DataViewManager> to manage view settings for all the tables in a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="b0d2e-105">リレーションシップを移動するグリッドなどのように、1 つのコントロールを複数のテーブルに連結する場合は、**DataViewManager** が適しています。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-105">If you have a control that you want to bind to multiple tables, such as a grid that navigates relationships, a **DataViewManager** is ideal.</span></span>  
  
 <span data-ttu-id="b0d2e-106">**DataViewManager** には、<xref:System.Data.DataSet> のテーブルのビュー設定に使用される <xref:System.Data.DataViewSetting> オブジェクトのコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-106">The **DataViewManager** contains a collection of <xref:System.Data.DataViewSetting> objects that are used to set the view setting of the tables in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="b0d2e-107"><xref:System.Data.DataViewSettingCollection> には、**DataSet** の各テーブルに対応する <xref:System.Data.DataViewSetting> オブジェクトが 1 つずつ含まれています。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-107">The <xref:System.Data.DataViewSettingCollection> contains one <xref:System.Data.DataViewSetting> object for each table in a **DataSet**.</span></span> <span data-ttu-id="b0d2e-108">**DataViewSetting** を使用することで、参照テーブルの既定の **ApplyDefaultSort**、**Sort**、**RowFilter**、**RowStateFilter** の各プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-108">You can set the default **ApplyDefaultSort**, **Sort**, **RowFilter**, and **RowStateFilter** properties of the referenced table by using its **DataViewSetting**.</span></span> <span data-ttu-id="b0d2e-109">名前または序数参照によって、または参照をその特定のテーブル オブジェクトに渡すことによって、特定のテーブルの **DataViewSetting** を参照できます。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-109">You can reference the **DataViewSetting** for a particular table by name or ordinal reference, or by passing a reference to that specific table object.</span></span> <span data-ttu-id="b0d2e-110">**DataViewSettings** プロパティを使用することで、**DataViewManager** の **DataViewSetting** オブジェクトのコレクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-110">You can access the collection of **DataViewSetting** objects in a **DataViewManager** by using the **DataViewSettings** property.</span></span>  
  
 <span data-ttu-id="b0d2e-111">次のコード例では、**DataSet** に、SQL Server の **Northwind** データベースの **Customers**、**Orders**、**Order Details** の各テーブルを格納し、テーブル間のリレーションシップを作成し、**DataViewManager** を使用して既定の **DataView** の設定を指定し、**DataGrid** を **DataViewManager** にバインドします。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-111">The following code example fills a **DataSet** with the SQL Server **Northwind** database tables **Customers**, **Orders**, and **Order Details**, creates the relationships between the tables, uses a **DataViewManager** to set default **DataView** settings, and binds a **DataGrid** to the **DataViewManager**.</span></span> <span data-ttu-id="b0d2e-112">この例では、**DataSet** のすべてのテーブルに対して、テーブルの主キーによって並べ替えるように (**ApplyDefaultSort** = **true**) **DataView** の既定の設定を指定した後、**Customers** テーブルの並べ替え順序を **CompanyName** で並べ替えるように変更します。</span><span class="sxs-lookup"><span data-stu-id="b0d2e-112">The example sets the default **DataView** settings for all tables in the **DataSet** to sort by the primary key of the table (**ApplyDefaultSort** = **true**), and then modifies the sort order of the **Customers** table to sort by **CompanyName**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection to Northwind.  
' Create a Connection, DataAdapters, and a DataSet.  
Dim custDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID FROM Orders", connection)  
Dim ordDetDA As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection)  
  
Dim custDS As DataSet = New DataSet()  
  
' Open the Connection.  
connection.Open()  
  
    ' Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey  
  
    custDA.Fill(custDS, "Customers")  
    orderDA.Fill(custDS, "Orders")  
    ordDetDA.Fill(custDS, "OrderDetails")  
  
    ' Close the Connection.  
    connection.Close()  
  
    ' Create relationships.  
    custDS.Relations.Add("CustomerOrders", _  
          custDS.Tables("Customers").Columns("CustomerID"), _  
          custDS.Tables("Orders").Columns("CustomerID"))  
  
    custDS.Relations.Add("OrderDetails", _  
          custDS.Tables("Orders").Columns("OrderID"), _  
          custDS.Tables("OrderDetails").Columns("OrderID"))  
  
' Create default DataView settings.  
Dim viewManager As DataViewManager = New DataViewManager(custDS)  
  
Dim viewSetting As DataViewSetting  
For Each viewSetting In viewManager.DataViewSettings  
  viewSetting.ApplyDefaultSort = True  
Next  
  
viewManager.DataViewSettings("Customers").Sort = "CompanyName"  
  
' Bind to a DataGrid.  
Dim grid As System.Windows.Forms.DataGrid = New System.Windows.Forms.DataGrid()  
grid.SetDataBinding(viewManager, "Customers")  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection to Northwind.  
// Create a Connection, DataAdapters, and a DataSet.  
SqlDataAdapter custDA = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderDA = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID FROM Orders", connection);  
SqlDataAdapter ordDetDA = new SqlDataAdapter(  
  "SELECT OrderID, ProductID, Quantity FROM [Order Details]", connection);  
  
DataSet custDS = new DataSet();  
  
// Open the Connection.  
connection.Open();  
  
    // Fill the DataSet with schema information and data.  
    custDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    orderDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
    ordDetDA.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
  
    custDA.Fill(custDS, "Customers");  
    orderDA.Fill(custDS, "Orders");  
    ordDetDA.Fill(custDS, "OrderDetails");  
  
    // Close the Connection.  
    connection.Close();  
  
    // Create relationships.  
    custDS.Relations.Add("CustomerOrders",  
          custDS.Tables["Customers"].Columns["CustomerID"],  
          custDS.Tables["Orders"].Columns["CustomerID"]);  
  
    custDS.Relations.Add("OrderDetails",  
          custDS.Tables["Orders"].Columns["OrderID"],  
          custDS.Tables["OrderDetails"].Columns["OrderID"]);  
  
// Create default DataView settings.  
DataViewManager viewManager = new DataViewManager(custDS);  
  
foreach (DataViewSetting viewSetting in viewManager.DataViewSettings)  
  viewSetting.ApplyDefaultSort = true;  
  
viewManager.DataViewSettings["Customers"].Sort = "CompanyName";  
  
// Bind to a DataGrid.  
System.Windows.Forms.DataGrid grid = new System.Windows.Forms.DataGrid();  
grid.SetDataBinding(viewManager, "Customers");  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0d2e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0d2e-113">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataViewManager>
- <xref:System.Data.DataViewSetting>
- <xref:System.Data.DataViewSettingCollection>
- [<span data-ttu-id="b0d2e-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="b0d2e-114">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="b0d2e-115">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="b0d2e-115">ADO.NET Overview</span></span>](../ado-net-overview.md)
