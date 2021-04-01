---
title: 'サンプル XSD ファイル: 顧客と注文 - LINQ to XML'
description: '例で使用されているこの XSD ファイルには、"サンプル XML ファイル: 顧客と注文" のスキーマが定義されています。'
ms.date: 07/20/2015
ms.assetid: ef9911a3-7ac4-44fd-b36e-a0c0ad0a157d
ms.openlocfilehash: 660d1dae764882199c8f2516057f8fc07ad0a9af
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366018"
---
# <a name="sample-xsd-file-customers-and-orders-linq-to-xml"></a><span data-ttu-id="8fb66-103">サンプル XSD ファイル: 顧客と注文 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8fb66-103">Sample XSD file: Customers and orders (LINQ to XML)</span></span>

<span data-ttu-id="8fb66-104">次の XSD ファイルは、LINQ to XML ドキュメントのさまざまな例で使用されます。</span><span class="sxs-lookup"><span data-stu-id="8fb66-104">The following XSD file is used in various examples in the LINQ to XML documentation.</span></span> <span data-ttu-id="8fb66-105">このファイルには、「[サンプル XML ファイル: 顧客と注文](sample-xml-file-customers-orders.md)」のスキーマ定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8fb66-105">This file contains a schema definition for the [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md).</span></span> <span data-ttu-id="8fb66-106">このスキーマは、XSD の `xs:key` 機能と `xs:keyref` 機能を使用して、`CustomerID` 要素の `Customer` 属性がキーであることを確立し、各 `CustomerID` 要素の `Order` 要素と各 `CustomerID` 要素の `Customer` 属性の間にリレーションシップを確立します。</span><span class="sxs-lookup"><span data-stu-id="8fb66-106">The schema uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="8fb66-107">`Join` 句を使用してこのリレーションシップを利用する LINQ クエリの作成例については、「[2 つのコレクションを結合する方法](join-two-collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fb66-107">For an example of writing LINQ queries that take advantage of this relationship using the `Join` clause, see [How to join two collections](join-two-collections.md).</span></span>

## <a name="customersordersxsd"></a><span data-ttu-id="8fb66-108">CustomersOrders.xsd</span><span class="sxs-lookup"><span data-stu-id="8fb66-108">CustomersOrders.xsd</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name='Root'>
    <xs:complexType>
      <xs:sequence>
        <xs:element name='Customers'>
          <xs:complexType>
            <xs:sequence>
              <xs:element name='Customer' type='CustomerType' minOccurs='0' maxOccurs='unbounded' />
            </xs:sequence>
          </xs:complexType>
        </xs:element>
        <xs:element name='Orders'>
          <xs:complexType>
            <xs:sequence>
              <xs:element name='Order' type='OrderType' minOccurs='0' maxOccurs='unbounded' />
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
    <xs:key name='CustomerIDKey'>
      <xs:selector xpath='Customers/Customer'/>
      <xs:field xpath='@CustomerID'/>
    </xs:key>
    <xs:keyref name='CustomerIDKeyRef' refer='CustomerIDKey'>
      <xs:selector xpath='Orders/Order'/>
      <xs:field xpath='CustomerID'/>
    </xs:keyref>
  </xs:element>
  <xs:complexType name='CustomerType'>
    <xs:sequence>
      <xs:element name='CompanyName' type='xs:string'/>
      <xs:element name='ContactName' type='xs:string'/>
      <xs:element name='ContactTitle' type='xs:string'/>
      <xs:element name='Phone' type='xs:string'/>
      <xs:element name='Fax' minOccurs='0' type='xs:string'/>
      <xs:element name='FullAddress' type='AddressType'/>
    </xs:sequence>
    <xs:attribute name='CustomerID' type='xs:token'/>
  </xs:complexType>
  <xs:complexType name='AddressType'>
    <xs:sequence>
      <xs:element name='Address' type='xs:string'/>
      <xs:element name='City' type='xs:string'/>
      <xs:element name='Region' type='xs:string'/>
      <xs:element name='PostalCode' type='xs:string' />
      <xs:element name='Country' type='xs:string'/>
    </xs:sequence>
    <xs:attribute name='CustomerID' type='xs:token'/>
  </xs:complexType>
  <xs:complexType name='OrderType'>
    <xs:sequence>
      <xs:element name='CustomerID' type='xs:token'/>
      <xs:element name='EmployeeID' type='xs:token'/>
      <xs:element name='OrderDate' type='xs:dateTime'/>
      <xs:element name='RequiredDate' type='xs:dateTime'/>
      <xs:element name='ShipInfo' type='ShipInfoType'/>
    </xs:sequence>
  </xs:complexType>
  <xs:complexType name='ShipInfoType'>
    <xs:sequence>
      <xs:element name='ShipVia' type='xs:integer'/>
      <xs:element name='Freight' type='xs:decimal'/>
      <xs:element name='ShipName' type='xs:string'/>
      <xs:element name='ShipAddress' type='xs:string'/>
      <xs:element name='ShipCity' type='xs:string'/>
      <xs:element name='ShipRegion' type='xs:string'/>
      <xs:element name='ShipPostalCode' type='xs:string'/>
      <xs:element name='ShipCountry' type='xs:string'/>
    </xs:sequence>
    <xs:attribute name='ShippedDate' type='xs:dateTime'/>
  </xs:complexType>
</xs:schema>
```
