---
description: '詳細情報: DataSet と XmlDataDocument の同期'
title: DataSet と XmlDataDocument の同期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fbc96fa9-b5d1-4f97-b099-c89b0e14ce2c
ms.openlocfilehash: 5b5d95ef78746bb5b78146557a6ebd307895db13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651549"
---
# <a name="synchronizing-a-dataset-with-an-xmldatadocument"></a><span data-ttu-id="0a60a-103">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="0a60a-103">Synchronizing a DataSet with an XmlDataDocument</span></span>

<span data-ttu-id="0a60a-104">このセクションでは、<xref:System.Xml.XmlDataDocument> と同期され、厳密に型指定された <xref:System.Data.DataSet> を使用して、注文書を処理する手順の 1 ステップを例に説明します。</span><span class="sxs-lookup"><span data-stu-id="0a60a-104">This section demonstrates one step in the processing of a purchase order, using a strongly typed <xref:System.Data.DataSet> synchronized with an <xref:System.Xml.XmlDataDocument>.</span></span> <span data-ttu-id="0a60a-105">この例では、**DataSet** をソース XML ドキュメントの一部だけと一致する最小限のスキーマと共に作成します。</span><span class="sxs-lookup"><span data-stu-id="0a60a-105">The examples that follow create a **DataSet** with a minimized schema that matches only a portion of the source XML document.</span></span> <span data-ttu-id="0a60a-106">この例では、**XmlDataDocument** を使用してソース XML ドキュメントが完全に保持されるため、XML ドキュメントのサブセットを公開するときに **DataSet** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0a60a-106">The examples use an **XmlDataDocument** to preserve the fidelity of the source XML document, enabling the **DataSet** to be used to expose a subset of the XML document.</span></span>  
  
 <span data-ttu-id="0a60a-107">注文書に関する情報 (顧客情報、発注品目、出荷情報など) をすべて含む XML ドキュメントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0a60a-107">The following XML document contains all the information pertaining to a purchase order: customer information, items ordered, shipping information, and so on.</span></span>  
  
```xml  
<?xml version="1.0" standalone="yes"?>  
<PurchaseOrder>  
  <Customers>  
    <CustomerID>CHOPS</CustomerID>  
    <Orders>  
      <OrderID>10966</OrderID>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>37</ProductID>  
        <UnitPrice>26</UnitPrice>  
        <Quantity>8</Quantity>  
        <Discount>0</Discount>  
      </OrderDetails>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>56</ProductID>  
        <UnitPrice>38</UnitPrice>  
        <Quantity>12</Quantity>  
        <Discount>0.15</Discount>  
      </OrderDetails>  
      <OrderDetails>  
        <OrderID>10966</OrderID>  
        <ProductID>62</ProductID>  
        <UnitPrice>49.3</UnitPrice>  
        <Quantity>12</Quantity>  
        <Discount>0.15</Discount>  
      </OrderDetails>  
      <CustomerID>CHOPS</CustomerID>  
      <EmployeeID>4</EmployeeID>  
      <OrderDate>1998-03-20T00:00:00.0000000</OrderDate>  
      <RequiredDate>1998-04-17T00:00:00.0000000</RequiredDate>  
      <ShippedDate>1998-04-08T00:00:00.0000000</ShippedDate>  
      <ShipVia>1</ShipVia>  
      <Freight>27.19</Freight>  
      <ShipName>Chop-suey Chinese</ShipName>  
      <ShipAddress>Hauptstr. 31</ShipAddress>  
      <ShipCity>Bern</ShipCity>  
      <ShipPostalCode>3012</ShipPostalCode>  
      <ShipCountry>Switzerland</ShipCountry>  
    </Orders>  
    <CompanyName>Chop-suey Chinese</CompanyName>  
    <ContactName>Yang Wang</ContactName>  
    <ContactTitle>Owner</ContactTitle>  
    <Address>Hauptstr. 29</Address>  
    <City>Bern</City>  
    <PostalCode>3012</PostalCode>  
    <Country>Switzerland</Country>  
    <Phone>0452-076545</Phone>  
  </Customers>  
  <Shippers>  
    <ShipperID>1</ShipperID>  
    <CompanyName>Speedy Express</CompanyName>  
    <Phone>(503) 555-0100</Phone>  
  </Shippers>  
  <Shippers>  
    <ShipperID>2</ShipperID>  
    <CompanyName>United Package</CompanyName>  
    <Phone>(503) 555-0101</Phone>  
  </Shippers>  
  <Shippers>  
    <ShipperID>3</ShipperID>  
    <CompanyName>Federal Shipping</CompanyName>  
    <Phone>(503) 555-0102</Phone>  
  </Shippers>  
  <Products>  
    <ProductID>37</ProductID>  
    <ProductName>Gravad lax</ProductName>  
    <QuantityPerUnit>12 - 500 g pkgs.</QuantityPerUnit>  
    <UnitsInStock>11</UnitsInStock>  
    <UnitsOnOrder>50</UnitsOnOrder>  
    <ReorderLevel>25</ReorderLevel>  
  </Products>  
  <Products>  
    <ProductID>56</ProductID>  
    <ProductName>Gnocchi di nonna Alice</ProductName>  
    <QuantityPerUnit>24 - 250 g pkgs.</QuantityPerUnit>  
    <UnitsInStock>21</UnitsInStock>  
    <UnitsOnOrder>10</UnitsOnOrder>  
    <ReorderLevel>30</ReorderLevel>  
  </Products>  
  <Products>  
    <ProductID>62</ProductID>  
    <ProductName>Tarte au sucre</ProductName>  
    <QuantityPerUnit>48 pies</QuantityPerUnit>  
    <UnitsInStock>17</UnitsInStock>  
    <UnitsOnOrder>0</UnitsOnOrder>  
    <ReorderLevel>0</ReorderLevel>  
  </Products>  
</PurchaseOrder>  
```  
  
 <span data-ttu-id="0a60a-108">前述の XML ドキュメントに含まれている注文書の情報を処理する手順の 1 ステップとして、企業の現在の在庫のデータを使用してこの注文書が処理されます。</span><span class="sxs-lookup"><span data-stu-id="0a60a-108">One step in processing the purchase order information contained in the preceding XML document is for the order to be filled from the company's current inventory.</span></span> <span data-ttu-id="0a60a-109">企業の倉庫で注文を処理する従業員は、注文書の内容をすべて確認する必要はありません。確認する必要がある情報は、注文書の製品情報だけです。</span><span class="sxs-lookup"><span data-stu-id="0a60a-109">The employee responsible for filling the order from the company's warehouse does not need to see the entire contents of the purchase order; they only need to see the product information for the order.</span></span> <span data-ttu-id="0a60a-110">XML ドキュメントの製品情報だけを公開するには、厳密に型指定した DataSet を作成し、XML スキーマ定義言語 (XSD) スキーマとして記述されているスキーマをこの **DataSet** に読み込みます。このスキーマは、注文の製品と数量に対応しています。</span><span class="sxs-lookup"><span data-stu-id="0a60a-110">To expose only the product information from the XML document, create a strongly typed **DataSet** with a schema, written as XML Schema definition language (XSD) schema, that maps to the products and quantities ordered.</span></span> <span data-ttu-id="0a60a-111">厳密に型指定された **DataSet** オブジェクトの詳細については、「[型指定されたデータセット](typed-datasets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a60a-111">For more information about strongly typed **DataSet** objects, see [Typed DataSets](typed-datasets.md).</span></span>  
  
 <span data-ttu-id="0a60a-112">このサンプルの厳密に型指定された **DataSet** の生成元となるスキーマを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="0a60a-112">The following code shows the schema from which the strongly typed **DataSet** is generated for this sample.</span></span>  
  
```xml  
<?xml version="1.0" standalone="yes"?>  
<xs:schema id="OrderDetail" xmlns=""
                            xmlns:xs="http://www.w3.org/2001/XMLSchema"
                            xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"
                            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="OrderDetail" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetails" codegen:typedName="LineItem" codegen:typedPlural="LineItems">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" type="xs:int" minOccurs="0" codegen:typedName="OrderID"/>  
              <xs:element name="Quantity" type="xs:short" minOccurs="0" codegen:typedName="Quantity"/>  
              <xs:element name="ProductID" type="xs:int" minOccurs="0" codegen:typedName="ProductID"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Products" codegen:typedName="Product" codegen:typedPlural="Products">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="ProductID" type="xs:int" minOccurs="0" codegen:typedName="ProductID"/>  
              <xs:element name="ProductName" type="xs:string" minOccurs="0" codegen:typedName="ProductName"/>  
              <xs:element name="QuantityPerUnit" type="xs:string" minOccurs="0" codegen:typedName="QuantityPerUnit"/>  
              <xs:element name="UnitsInStock" type="xs:short" minOccurs="0" codegen:typedName="UnitsInStock"/>  
              <xs:element name="UnitsOnOrder" type="xs:short" minOccurs="0" codegen:typedName="UnitsOnOrder"/>  
              <xs:element name="ReorderLevel" type="xs:short" minOccurs="0" codegen:typedName="ReorderLevel"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Products" />  
      <xs:field xpath="ProductID" />  
    </xs:unique>  
    <xs:keyref name="Relation1" refer="Constraint1" codegen:typedChildren="GetLineItems" codegen:typedParent="Product">  
      <xs:selector xpath=".//OrderDetails" />  
      <xs:field xpath="ProductID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="0a60a-113">元の XML ドキュメントの **OrderDetails** 要素と **Products** 要素の情報だけが **DataSet** のスキーマにインクルードされます。</span><span class="sxs-lookup"><span data-stu-id="0a60a-113">Notice that only information from the **OrderDetails** and **Products** elements of the original XML document are included in the schema for the **DataSet**.</span></span> <span data-ttu-id="0a60a-114">**DataSet** を **XmlDataDocument** と同期させることで、**DataSet** にインクルードされていない要素も XML ドキュメントに保持されます。</span><span class="sxs-lookup"><span data-stu-id="0a60a-114">Synchronizing the **DataSet** with an **XmlDataDocument** ensures that the elements not included in the **DataSet** will persist with the XML document.</span></span>  
  
 <span data-ttu-id="0a60a-115">**Northwind.FillOrder** の名前空間を使用して XML スキーマから生成される、厳密に型指定された **DataSet** を使用すると、**DataSet** とソース XML ドキュメントから読み込まれた **XmlDataDocument** を同期させることで、元の XML ドキュメントの一部を公開できます。</span><span class="sxs-lookup"><span data-stu-id="0a60a-115">With the strongly typed **DataSet** generated from the XML Schema (with a namespace of **Northwind.FillOrder**), a portion of the original XML document can be exposed by synchronizing the **DataSet** with the **XmlDataDocument** loaded from the source XML document.</span></span> <span data-ttu-id="0a60a-116">このスキーマから生成された **DataSet** には構造が含まれていますが、データは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="0a60a-116">Notice that the **DataSet** generated from the schema contains structure but no data.</span></span> <span data-ttu-id="0a60a-117">XML を **XmlDataDocument** に読み込むと、データが格納されます。</span><span class="sxs-lookup"><span data-stu-id="0a60a-117">The data is filled in when you load the XML into the **XmlDataDocument**.</span></span> <span data-ttu-id="0a60a-118">データが既に含まれている **DataSet** と同期された **XmlDataDocument** を読み込もうとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0a60a-118">If you attempt to load an **XmlDataDocument** that has been synchronized with a **DataSet** that already contains data, an exception will be thrown.</span></span>  
  
 <span data-ttu-id="0a60a-119">**DataSet** (および **XmlDataDocument**) が更新された後、**XmlDataDocument** によって、変更後の XML ドキュメントと、**DataSet** によって無視された要素を出力できます。この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0a60a-119">After the **DataSet** (and the **XmlDataDocument**) has been updated, the **XmlDataDocument** can then write out the modified XML document with the elements ignored by the **DataSet** still intact, as shown below.</span></span> <span data-ttu-id="0a60a-120">注文書の処理手順では、注文品目の入力後に、変更された XML ドキュメントが注文処理の次のステップ (社内の出荷部門) に渡されます。</span><span class="sxs-lookup"><span data-stu-id="0a60a-120">In the purchase order scenario, after the order items have been filled, the modified XML document can then be passed on to the next step in the order process, perhaps to the company's shipping department.</span></span>  
  
```vb  
Imports System  
Imports System.Data  
Imports System.Xml  
Imports Northwind.FillOrder  
  
Public class Sample  
  Public Shared Sub Main()  
  
    Dim orderDS As OrderDetail = New OrderDetail  
  
    Dim xmlDocument As XmlDataDocument = New XmlDataDocument(orderDS)
  
    xmlDocument.Load("Order.xml")  
  
    Dim orderItem As OrderDetail.LineItem  
    Dim product As OrderDetail.Product  
  
    For Each orderItem In orderDS.LineItems  
      product = orderItem.Product  
  
      ' Remove quantity from the current stock.  
      product.UnitsInStock = CType(product.UnitsInStock - orderItem.Quantity, Short)  
  
      ' If the remaining stock is less than the reorder level, order more.  
      If ((product.UnitsInStock + product.UnitsOnOrder) < product.ReorderLevel) Then  
        product.UnitsOnOrder = CType(product.UnitsOnOrder + product.ReorderLevel, Short)  
      End If  
    Next  
  
    xmlDocument.Save("Order_out.xml")  
  End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Xml;  
using Northwind.FillOrder;  
  
public class Sample  
{  
  public static void Main()  
  {  
    OrderDetail orderDS = new OrderDetail();
  
    XmlDataDocument xmlDocument = new XmlDataDocument(orderDS);
  
    xmlDocument.Load("Order.xml");  
  
    foreach (OrderDetail.LineItem orderItem in orderDS.LineItems)  
    {  
      OrderDetail.Product product = orderItem.Product;  
  
      // Remove quantity from the current stock.  
      product.UnitsInStock = (short)(product.UnitsInStock - orderItem.Quantity);  
  
      // If the remaining stock is less than the reorder level, order more.  
      if ((product.UnitsInStock + product.UnitsOnOrder) < product.ReorderLevel)  
        product.UnitsOnOrder = (short)(product.UnitsOnOrder + product.ReorderLevel);  
    }  
  
    xmlDocument.Save("Order_out.xml");  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a60a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a60a-121">See also</span></span>

- [<span data-ttu-id="0a60a-122">DataSet と XmlDataDocument の同期</span><span class="sxs-lookup"><span data-stu-id="0a60a-122">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)
- [<span data-ttu-id="0a60a-123">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="0a60a-123">ADO.NET Overview</span></span>](../ado-net-overview.md)
