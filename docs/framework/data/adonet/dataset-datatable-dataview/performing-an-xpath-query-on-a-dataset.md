---
description: '詳細情報: DataSet に対する XPath クエリの実行'
title: DataSet に対する XPath クエリの実行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e828566-fffe-4d38-abb2-4d68fd73f663
ms.openlocfilehash: 9febcc545f86f048b2d693f8aa6558a1b7883a60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651718"
---
# <a name="performing-an-xpath-query-on-a-dataset"></a><span data-ttu-id="bd1e7-103">DataSet に対する XPath クエリの実行</span><span class="sxs-lookup"><span data-stu-id="bd1e7-103">Performing an XPath Query on a DataSet</span></span>

<span data-ttu-id="bd1e7-104">同期された <xref:System.Data.DataSet> と <xref:System.Xml.XmlDataDocument> との間のリレーションシップによって、XPath (XML Path Language) クエリなどの XML サービスが使用できます。XML サービスは **XmlDataDocument** にアクセスし、**DataSet** に直接アクセスするよりも、特定の機能を効率的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="bd1e7-104">The relationship between a synchronized <xref:System.Data.DataSet> and <xref:System.Xml.XmlDataDocument> allows you to make use of XML services, such as the XML Path Language (XPath) query, that access the **XmlDataDocument** and can perform certain functionality more conveniently than accessing the **DataSet** directly.</span></span> <span data-ttu-id="bd1e7-105">たとえば、<xref:System.Data.DataTable> の **Select** メソッドを使用して **DataSet** の他のテーブルとのリレーションシップをナビゲートする代わりに、**DataSet** と同期化された **XmlDataDocument** に対して XPath クエリを実行すると、<xref:System.Xml.XmlNodeList> 形式で XML 要素のリストを取得できます。</span><span class="sxs-lookup"><span data-stu-id="bd1e7-105">For example, rather than using the **Select** method of a <xref:System.Data.DataTable> to navigate relationships to other tables in a **DataSet**, you can perform an XPath query on an **XmlDataDocument** that is synchronized with the **DataSet**, to get a list of XML elements in the form of an <xref:System.Xml.XmlNodeList>.</span></span> <span data-ttu-id="bd1e7-106"><xref:System.Xml.XmlElement> ノードとしてキャストされた **XmlNodeList** のノードを **XmlDataDocument** の **GetRowFromElement** メソッドに渡すと、同期化された **DataSet** のテーブルの行に一致する <xref:System.Data.DataRow> 参照が返されます。</span><span class="sxs-lookup"><span data-stu-id="bd1e7-106">The nodes in the **XmlNodeList**, cast as <xref:System.Xml.XmlElement> nodes, can then be passed to the **GetRowFromElement** method of the **XmlDataDocument**, to return matching <xref:System.Data.DataRow> references to the rows of the table in the synchronized **DataSet**.</span></span>  
  
 <span data-ttu-id="bd1e7-107">たとえば、次に示すコード サンプルでは孫 XPath クエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="bd1e7-107">For example, the following code sample performs a "grandchild" XPath query.</span></span> <span data-ttu-id="bd1e7-108">**DataSet** には、次の 3 つのテーブルが格納されます: **Customers**、**Orders**、**OrderDetails**。</span><span class="sxs-lookup"><span data-stu-id="bd1e7-108">The **DataSet** is filled with three tables: **Customers**, **Orders**, and **OrderDetails**.</span></span> <span data-ttu-id="bd1e7-109">このサンプルでは、**Customers** テーブルと **Orders** テーブルの間に親子のリレーションが作成され、次に **Orders** テーブルと **OrderDetails** テーブルの間に親子のリレーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bd1e7-109">In the sample, a parent-child relation is first created between the **Customers** and **Orders** tables, and between the **Orders** and **OrderDetails** tables.</span></span> <span data-ttu-id="bd1e7-110">XPath クエリが実行され、値 43 の **ProductID** ノードを持つ孫 **OrderDetails** ノードのある **Customers** ノードの **XmlNodeList** リストが返されます。</span><span class="sxs-lookup"><span data-stu-id="bd1e7-110">An XPath query is then performed to return an **XmlNodeList** of **Customers** nodes where a grandchild **OrderDetails** node has a **ProductID** node with the value of 43.</span></span> <span data-ttu-id="bd1e7-111">つまり、このサンプルでは、XPath クエリを使用して **ProductID** が 43 の製品を注文した顧客を確認します。</span><span class="sxs-lookup"><span data-stu-id="bd1e7-111">In essence, the sample is using the XPath query to determine which customers have ordered the product that has the **ProductID** of 43.</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection.  
connection.Open()  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Customers", connection)  
customerAdapter.Fill(dataSet, "Customers")  
  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM Orders", connection)  
orderAdapter.Fill(dataSet, "Orders")  
  
Dim detailAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM [Order Details]", connection)  
detailAdapter.Fill(dataSet, "OrderDetails")  
  
connection.Close()  
  
dataSet.Relations.Add("CustOrders", _  
dataSet.Tables("Customers").Columns("CustomerID"), _  
dataSet.Tables("Orders").Columns("CustomerID")).Nested = true  
  
dataSet.Relations.Add("OrderDetail", _  
  dataSet.Tables("Orders").Columns("OrderID"), _  
dataSet.Tables("OrderDetails").Columns("OrderID"), false).Nested = true  
  
Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)
  
Dim nodeList As XmlNodeList = xmlDoc.DocumentElement.SelectNodes( _  
  "descendant::Customers[*/OrderDetails/ProductID=43]")  
  
Dim dataRow As DataRow  
Dim xmlNode As XmlNode  
  
For Each xmlNode In nodeList  
  dataRow = xmlDoc.GetRowFromElement(CType(xmlNode, XmlElement))  
  
  If Not dataRow Is Nothing then Console.WriteLine(xmlRow(0).ToString())  
Next  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection.  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT * FROM Customers", connection);  
customerAdapter.Fill(dataSet, "Customers");  
  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT * FROM Orders", connection);  
orderAdapter.Fill(dataSet, "Orders");  
  
SqlDataAdapter detailAdapter = new SqlDataAdapter(  
  "SELECT * FROM [Order Details]", connection);  
detailAdapter.Fill(dataSet, "OrderDetails");  
  
connection.Close();  
  
dataSet.Relations.Add("CustOrders",  
  dataSet.Tables["Customers"].Columns["CustomerID"],  
 dataSet.Tables["Orders"].Columns["CustomerID"]).Nested = true;  
  
dataSet.Relations.Add("OrderDetail",  
  dataSet.Tables["Orders"].Columns["OrderID"],  
  dataSet.Tables["OrderDetails"].Columns["OrderID"],
  false).Nested = true;  
  
XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);
  
XmlNodeList nodeList = xmlDoc.DocumentElement.SelectNodes(  
  "descendant::Customers[*/OrderDetails/ProductID=43]");  
  
DataRow dataRow;  
foreach (XmlNode xmlNode in nodeList)  
{  
  dataRow = xmlDoc.GetRowFromElement((XmlElement)xmlNode);  
  if (dataRow != null)  
    Console.WriteLine(dataRow[0]);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd1e7-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd1e7-112">See also</span></span>

- [<span data-ttu-id="bd1e7-113">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="bd1e7-113">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="bd1e7-114">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="bd1e7-114">ADO.NET Overview</span></span>](../ado-net-overview.md)
