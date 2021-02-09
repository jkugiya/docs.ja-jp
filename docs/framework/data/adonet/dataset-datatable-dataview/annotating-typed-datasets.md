---
description: '詳細情報: 型指定された DataSet の注釈'
title: 型指定された DataSet の注釈
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 6f5838e94d88fd6c9b3a1991d4c8023d5892b784
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739704"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="3d495-103">型指定された DataSet の注釈</span><span class="sxs-lookup"><span data-stu-id="3d495-103">Annotating Typed DataSets</span></span>

<span data-ttu-id="3d495-104">注釈を使用すると、基になるスキーマを変更せずに型指定された <xref:System.Data.DataSet> の要素の名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="3d495-104">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="3d495-105">基になるスキーマの要素の名前を変更すると、データ ソースにあるオブジェクトへの参照が失われるだけでなく、型指定された **DataSet** がデータ ソースにないオブジェクトを参照することになります。</span><span class="sxs-lookup"><span data-stu-id="3d495-105">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="3d495-106">注釈を使用すると、基になるスキーマを変更せずに、型指定された **DataSet** のオブジェクトをわかりやすい名前にカスタマイズできるため、コードが読みやすくなり、型指定された **DataSet** がクライアントで使用しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="3d495-106">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="3d495-107">たとえば、次の **Northwind** データベースの **Customers** テーブルのスキーマ要素は、**CustomersRow** という名前の **DataRow** オブジェクト名および **Customers** という名前の <xref:System.Data.DataRowCollection> となります。</span><span class="sxs-lookup"><span data-stu-id="3d495-107">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="3d495-108">**Customers** という **DataRowCollection** 名は、クライアント コードでは意味がありますが、**CustomersRow** という **DataRow** 名は単一のオブジェクトであるため、誤解が生じます。</span><span class="sxs-lookup"><span data-stu-id="3d495-108">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="3d495-109">また、一般的なシナリオでは、オブジェクトは **Row** ID を指定せずに参照されるため、単に **Customer** オブジェクトとして参照されます。</span><span class="sxs-lookup"><span data-stu-id="3d495-109">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="3d495-110">この問題を解決するには、スキーマに注釈を付け、**DataRow** オブジェクトと **DataRowCollection** オブジェクトに新しい名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d495-110">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="3d495-111">上記のスキーマに注釈を付けたスキーマを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d495-111">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="3d495-112">**Customer** という **typedName** 値を指定すると、**Customer** という **DataRow** オブジェクト名になります。</span><span class="sxs-lookup"><span data-stu-id="3d495-112">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="3d495-113">**Customers** という **typedPlural** 値を指定すると、**Customers** という **DataRowCollection** 名が保存されます。</span><span class="sxs-lookup"><span data-stu-id="3d495-113">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="3d495-114">使用できる注釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="3d495-114">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="3d495-115">注釈</span><span class="sxs-lookup"><span data-stu-id="3d495-115">Annotation</span></span>|<span data-ttu-id="3d495-116">説明</span><span class="sxs-lookup"><span data-stu-id="3d495-116">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="3d495-117">**typedName**</span><span class="sxs-lookup"><span data-stu-id="3d495-117">**typedName**</span></span>|<span data-ttu-id="3d495-118">オブジェクト名。</span><span class="sxs-lookup"><span data-stu-id="3d495-118">Name of the object.</span></span>|  
|<span data-ttu-id="3d495-119">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="3d495-119">**typedPlural**</span></span>|<span data-ttu-id="3d495-120">オブジェクトのコレクション名。</span><span class="sxs-lookup"><span data-stu-id="3d495-120">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="3d495-121">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="3d495-121">**typedParent**</span></span>|<span data-ttu-id="3d495-122">親のリレーションシップで参照される場合のオブジェクト名。</span><span class="sxs-lookup"><span data-stu-id="3d495-122">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="3d495-123">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="3d495-123">**typedChildren**</span></span>|<span data-ttu-id="3d495-124">子のリレーションシップからオブジェクトを返すメソッド名。</span><span class="sxs-lookup"><span data-stu-id="3d495-124">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="3d495-125">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="3d495-125">**nullValue**</span></span>|<span data-ttu-id="3d495-126">基になる値が **DBNull** の場合の値。</span><span class="sxs-lookup"><span data-stu-id="3d495-126">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="3d495-127">**nullValue** の注釈については、次の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d495-127">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="3d495-128">既定値は **_throw** です。</span><span class="sxs-lookup"><span data-stu-id="3d495-128">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="3d495-129">**nullValue** 注釈に指定できる値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="3d495-129">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="3d495-130">nullValue の値</span><span class="sxs-lookup"><span data-stu-id="3d495-130">nullValue Value</span></span>|<span data-ttu-id="3d495-131">説明</span><span class="sxs-lookup"><span data-stu-id="3d495-131">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="3d495-132">*置換値*</span><span class="sxs-lookup"><span data-stu-id="3d495-132">*Replacement Value*</span></span>|<span data-ttu-id="3d495-133">返される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="3d495-133">Specify a value to be returned.</span></span> <span data-ttu-id="3d495-134">返された値は要素の型と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d495-134">The returned value must match the type of the element.</span></span> <span data-ttu-id="3d495-135">たとえば、整数型フィールドが null の場合に 0 を返すために `nullValue="0"` を使用します。</span><span class="sxs-lookup"><span data-stu-id="3d495-135">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="3d495-136">**_throw**</span><span class="sxs-lookup"><span data-stu-id="3d495-136">**_throw**</span></span>|<span data-ttu-id="3d495-137">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3d495-137">Throw an exception.</span></span> <span data-ttu-id="3d495-138">既定値です。</span><span class="sxs-lookup"><span data-stu-id="3d495-138">This is the default.</span></span>|  
|<span data-ttu-id="3d495-139">**_null**</span><span class="sxs-lookup"><span data-stu-id="3d495-139">**_null**</span></span>|<span data-ttu-id="3d495-140">プリミティブ型が見つかった場合は、null 参照を返すか、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3d495-140">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="3d495-141">**_empty**</span><span class="sxs-lookup"><span data-stu-id="3d495-141">**_empty**</span></span>|<span data-ttu-id="3d495-142">文字列の場合は **String.Empty** を、それ以外の場合は空のコンストラクターから作成されたオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="3d495-142">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="3d495-143">プリミティブ型が見つかった場合、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="3d495-143">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="3d495-144">型指定された **DataSet** のオブジェクトの既定値と使用できる注釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="3d495-144">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="3d495-145">オブジェクト/メソッド/イベント</span><span class="sxs-lookup"><span data-stu-id="3d495-145">Object/Method/Event</span></span>|<span data-ttu-id="3d495-146">Default</span><span class="sxs-lookup"><span data-stu-id="3d495-146">Default</span></span>|<span data-ttu-id="3d495-147">注釈</span><span class="sxs-lookup"><span data-stu-id="3d495-147">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="3d495-148">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="3d495-148">**DataTable**</span></span>|<span data-ttu-id="3d495-149">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="3d495-149">TableNameDataTable</span></span>|<span data-ttu-id="3d495-150">typedPlural</span><span class="sxs-lookup"><span data-stu-id="3d495-150">typedPlural</span></span>|  
|<span data-ttu-id="3d495-151">**DataTable** のメソッド</span><span class="sxs-lookup"><span data-stu-id="3d495-151">**DataTable** Methods</span></span>|<span data-ttu-id="3d495-152">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="3d495-152">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="3d495-153">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="3d495-153">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="3d495-154">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="3d495-154">DeleteTableNameRow</span></span>|<span data-ttu-id="3d495-155">typedName</span><span class="sxs-lookup"><span data-stu-id="3d495-155">typedName</span></span>|  
|<span data-ttu-id="3d495-156">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="3d495-156">**DataRowCollection**</span></span>|<span data-ttu-id="3d495-157">TableName</span><span class="sxs-lookup"><span data-stu-id="3d495-157">TableName</span></span>|<span data-ttu-id="3d495-158">typedPlural</span><span class="sxs-lookup"><span data-stu-id="3d495-158">typedPlural</span></span>|  
|<span data-ttu-id="3d495-159">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="3d495-159">**DataRow**</span></span>|<span data-ttu-id="3d495-160">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="3d495-160">TableNameRow</span></span>|<span data-ttu-id="3d495-161">typedName</span><span class="sxs-lookup"><span data-stu-id="3d495-161">typedName</span></span>|  
|<span data-ttu-id="3d495-162">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="3d495-162">**DataColumn**</span></span>|<span data-ttu-id="3d495-163">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="3d495-163">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="3d495-164">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="3d495-164">DataRow.ColumnName</span></span>|<span data-ttu-id="3d495-165">typedName</span><span class="sxs-lookup"><span data-stu-id="3d495-165">typedName</span></span>|  
|<span data-ttu-id="3d495-166">**Property**</span><span class="sxs-lookup"><span data-stu-id="3d495-166">**Property**</span></span>|<span data-ttu-id="3d495-167">PropertyName</span><span class="sxs-lookup"><span data-stu-id="3d495-167">PropertyName</span></span>|<span data-ttu-id="3d495-168">typedName</span><span class="sxs-lookup"><span data-stu-id="3d495-168">typedName</span></span>|  
|<span data-ttu-id="3d495-169">**Child** アクセサー</span><span class="sxs-lookup"><span data-stu-id="3d495-169">**Child** Accessor</span></span>|<span data-ttu-id="3d495-170">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="3d495-170">GetChildTableNameRows</span></span>|<span data-ttu-id="3d495-171">typedChildren</span><span class="sxs-lookup"><span data-stu-id="3d495-171">typedChildren</span></span>|  
|<span data-ttu-id="3d495-172">**Parent** アクセサー</span><span class="sxs-lookup"><span data-stu-id="3d495-172">**Parent** Accessor</span></span>|<span data-ttu-id="3d495-173">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="3d495-173">TableNameRow</span></span>|<span data-ttu-id="3d495-174">typedParent</span><span class="sxs-lookup"><span data-stu-id="3d495-174">typedParent</span></span>|  
|<span data-ttu-id="3d495-175">**DataSet** イベント</span><span class="sxs-lookup"><span data-stu-id="3d495-175">**DataSet** Events</span></span>|<span data-ttu-id="3d495-176">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="3d495-176">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="3d495-177">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="3d495-177">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="3d495-178">typedName</span><span class="sxs-lookup"><span data-stu-id="3d495-178">typedName</span></span>|  
  
 <span data-ttu-id="3d495-179">型指定された **DataSet** の注釈を使用するには、XML スキーマ定義言語 (XSD) スキーマに次の **xmlns** 参照をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3d495-179">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="3d495-180">データベース テーブルから xsd を作成するには、<xref:System.Data.DataSet.WriteXmlSchema%2A> に関するトピック、または「[Visual Studio でのデータセットの操作](/visualstudio/data-tools/dataset-tools-in-visual-studio)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d495-180">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="3d495-181">**Orders** テーブルとのリレーションを持つ **Northwind** データベースの **Customers** テーブルを公開する、注釈の付いたスキーマのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d495-181">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="3d495-182">サンプル スキーマから作成された厳密に型指定された **DataSet** を次のコード サンプルで使用します。</span><span class="sxs-lookup"><span data-stu-id="3d495-182">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="3d495-183">また、一方の <xref:System.Data.SqlClient.SqlDataAdapter> を使用して **Customers** テーブルを、他方の <xref:System.Data.SqlClient.SqlDataAdapter> を使用して **Orders** テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d495-183">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="3d495-184">厳密に型指定された **DataSet** により、**DataRelations** が定義されます。</span><span class="sxs-lookup"><span data-stu-id="3d495-184">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d495-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d495-185">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="3d495-186">型指定されたデータセット</span><span class="sxs-lookup"><span data-stu-id="3d495-186">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="3d495-187">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="3d495-187">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="3d495-188">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="3d495-188">ADO.NET Overview</span></span>](../ado-net-overview.md)
