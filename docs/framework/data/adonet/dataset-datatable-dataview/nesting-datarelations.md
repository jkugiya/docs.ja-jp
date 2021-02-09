---
description: '詳細情報: DataRelation の入れ子化'
title: DataRelation の入れ子化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9530f9c9-dd98-4b93-8cdb-40d7f1e8d0ab
ms.openlocfilehash: d998802a11fbb2bf414aa28b4beee95cac70a819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651757"
---
# <a name="nesting-datarelations"></a><span data-ttu-id="a995b-103">DataRelation の入れ子化</span><span class="sxs-lookup"><span data-stu-id="a995b-103">Nesting DataRelations</span></span>

<span data-ttu-id="a995b-104">データのリレーショナル表現では、各テーブルに含まれている行が、列または列セットを使用して相互に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="a995b-104">In a relational representation of data, individual tables contain rows that are related to one another using a column or set of columns.</span></span> <span data-ttu-id="a995b-105">ADO.NET の <xref:System.Data.DataSet> では、テーブル間のリレーションシップは <xref:System.Data.DataRelation> を使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="a995b-105">In the ADO.NET <xref:System.Data.DataSet>, the relationship between tables is implemented using a <xref:System.Data.DataRelation>.</span></span> <span data-ttu-id="a995b-106">**DataRelation** を作成すると、列の親子リレーションシップはこのリレーションだけをとおして管理されます。</span><span class="sxs-lookup"><span data-stu-id="a995b-106">When you create a **DataRelation**, the parent-child relationships of the columns are managed only through the relation.</span></span> <span data-ttu-id="a995b-107">テーブルと列はそれぞれ別個のエンティティです。</span><span class="sxs-lookup"><span data-stu-id="a995b-107">The tables and columns are separate entities.</span></span> <span data-ttu-id="a995b-108">XML のデータ階層表現では、子要素が入れ子の状態で含まれている親要素によって親子のリレーションシップが表現されます。</span><span class="sxs-lookup"><span data-stu-id="a995b-108">In the hierarchical representation of data that XML provides, the parent-child relationships are represented by parent elements that contain nested child elements.</span></span>  
  
 <span data-ttu-id="a995b-109">**DataSet** が <xref:System.Xml.XmlDataDocument> と同期されているとき、または **WriteXml** を使用して XML データとして書き込まれるときに、子オブジェクトの入れ子を容易にするため、**DataRelation** では **Nested** プロパティが公開されています。</span><span class="sxs-lookup"><span data-stu-id="a995b-109">To facilitate the nesting of child objects when a **DataSet** is synchronized with an <xref:System.Xml.XmlDataDocument> or written as XML data using **WriteXml**, the **DataRelation** exposes a **Nested** property.</span></span> <span data-ttu-id="a995b-110">**DataRelation** の **Nested** プロパティを **true** に設定すると、XML データとして書き込まれるとき、または **XmlDataDocument** と同期されるときに、リレーションの子の行が親の列に入れ子にされます。</span><span class="sxs-lookup"><span data-stu-id="a995b-110">Setting the **Nested** property of a **DataRelation** to **true** causes the child rows of the relation to be nested within the parent column when written as XML data or synchronized with an **XmlDataDocument**.</span></span> <span data-ttu-id="a995b-111">**DataRelation** の **Nested** プロパティは、既定では **false** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a995b-111">The **Nested** property of the **DataRelation** is **false**, by default.</span></span>  
  
 <span data-ttu-id="a995b-112">たとえば、次のような **DataSet** があるとします。</span><span class="sxs-lookup"><span data-stu-id="a995b-112">For example, consider the following **DataSet**.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers", connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection)  
  
connection.Open()  
  
Dim dataSet As DataSet = New DataSet("CustomerOrders")  
customerAdapter.Fill(dataSet, "Customers")  
orderAdapter.Fill(dataSet, "Orders")  
  
connection.Close()  
  
Dim customerOrders As DataRelation = dataSet.Relations.Add( _  
  "CustOrders", dataSet.Tables("Customers").Columns("CustomerID"), _  
  dataSet.Tables("Orders").Columns("CustomerID"))  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers", connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
  "SELECT OrderID, CustomerID, OrderDate FROM Orders", connection);  
  
connection.Open();  
  
DataSet dataSet = new DataSet("CustomerOrders");  
customerAdapter.Fill(dataSet, "Customers");  
orderAdapter.Fill(dataSet, "Orders");  
  
connection.Close();  
  
DataRelation customerOrders = dataSet.Relations.Add(  
  "CustOrders", dataSet.Tables["Customers"].Columns["CustomerID"],  
  dataSet.Tables["Orders"].Columns["CustomerID"]);  
```  
  
 <span data-ttu-id="a995b-113">この **DataSet** では **DataRelation** オブジェクトの **Nested** プロパティが **true** に設定されていないため、この **DataSet** が XML データとして表されるときに、子オブジェクトは親要素内に入れ子にされません。</span><span class="sxs-lookup"><span data-stu-id="a995b-113">Because the **Nested** property of the **DataRelation** object is not set to **true** for this **DataSet**, the child objects are not nested within the parent elements when this **DataSet** is represented as XML data.</span></span> <span data-ttu-id="a995b-114">データ リレーションが入れ子になっていない関連 **DataSet** が含まれる **DataSet** の XML 表現を変換すると、パフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a995b-114">Transforming the XML representation of a **DataSet** that contains related **DataSet** s with non-nested data relations can cause slow performance.</span></span> <span data-ttu-id="a995b-115">データ リレーションシップは入れ子にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a995b-115">We recommend that you nest the data relations.</span></span> <span data-ttu-id="a995b-116">そのためには、**Nested** プロパティを **true** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a995b-116">To do this, set the **Nested** property to **true**.</span></span> <span data-ttu-id="a995b-117">次に、トップダウン階層形式の XPath クエリ式を使用してデータを検索、変換するコードを XSLT スタイル シートに記述します。</span><span class="sxs-lookup"><span data-stu-id="a995b-117">Then write code in the XSLT style sheet that uses top-down hierarchical XPath query expressions to locate and transform the data.</span></span>  
  
 <span data-ttu-id="a995b-118">次のコード例では、**DataSet** に対して **WriteXml** を呼び出した結果を示します。</span><span class="sxs-lookup"><span data-stu-id="a995b-118">The following code example shows the result from calling **WriteXml** on the **DataSet**.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
  <Orders>  
    <OrderID>10643</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-08-25T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10692</OrderID>  
    <CustomerID>ALFKI</CustomerID>  
    <OrderDate>1997-10-03T00:00:00</OrderDate>  
  </Orders>  
  <Orders>  
    <OrderID>10308</OrderID>  
    <CustomerID>ANATR</CustomerID>  
    <OrderDate>1996-09-18T00:00:00</OrderDate>  
  </Orders>  
</CustomerOrders>  
```  
  
 <span data-ttu-id="a995b-119">**Customers** 要素と **Orders** 要素が兄弟要素として示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a995b-119">Note that the **Customers** element and the **Orders** elements are shown as sibling elements.</span></span> <span data-ttu-id="a995b-120">**Orders** 要素が該当する親要素の子として示されるようにするには、**DataRelation** の **Nested** プロパティを **true** に設定する必要があり、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a995b-120">If you wanted the **Orders** elements to show up as children of their respective parent elements, the **Nested** property of the **DataRelation** would need to be set to **true** and you would add the following:</span></span>  
  
```vb  
customerOrders.Nested = True  
```  
  
```csharp  
customerOrders.Nested = true;  
```  
  
 <span data-ttu-id="a995b-121">上記のコードを追加した結果の出力を次のコードに示します。この例では、**Orders** 要素がそれぞれ該当する親要素の中で入れ子になっています。</span><span class="sxs-lookup"><span data-stu-id="a995b-121">The following code shows what the resulting output would look like, with the **Orders** elements nested within their respective parent elements.</span></span>  
  
```xml  
<CustomerOrders>  
  <Customers>  
    <CustomerID>ALFKI</CustomerID>  
    <Orders>  
      <OrderID>10643</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-08-25T00:00:00</OrderDate>  
    </Orders>  
    <Orders>  
      <OrderID>10692</OrderID>  
      <CustomerID>ALFKI</CustomerID>  
      <OrderDate>1997-10-03T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Alfreds Futterkiste</CompanyName>  
  </Customers>  
  <Customers>  
    <CustomerID>ANATR</CustomerID>  
    <Orders>  
      <OrderID>10308</OrderID>  
      <CustomerID>ANATR</CustomerID>  
      <OrderDate>1996-09-18T00:00:00</OrderDate>  
    </Orders>  
    <CompanyName>Ana Trujillo Emparedados y helados</CompanyName>  
  </Customers>  
</CustomerOrders>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a995b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a995b-122">See also</span></span>

- [<span data-ttu-id="a995b-123">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="a995b-123">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="a995b-124">DataRelation の追加</span><span class="sxs-lookup"><span data-stu-id="a995b-124">Adding DataRelations</span></span>](adding-datarelations.md)
- [<span data-ttu-id="a995b-125">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="a995b-125">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="a995b-126">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="a995b-126">ADO.NET Overview</span></span>](../ado-net-overview.md)
