---
title: 2 つのコレクションを結合する方法 - LINQ to XML
description: XSD ファイルでは、新しい型の要素を作成する目的で要素を結合できるよう、XML ファイル内でリレーションシップを確立できます。 この記事では、要素を結合し、新しい XML ドキュメントを作成する C# と Visual Basic の例を提供します。
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2ab74f861cfd046e202a861378b8fd8792c7bac4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366000"
---
# <a name="how-to-join-two-collections-linq-to-xml"></a>2 つのコレクションを結合する方法 (LINQ to XML)

XSD ファイルでは、新しい型の要素を作成する目的で要素を結合できるよう、XML ファイル内でリレーションシップを確立できます。 この記事では、要素を結合し、新しい XML ドキュメントを作成する C# と Visual Basic の例を提供します。

XML ドキュメント内の要素または属性は、別の要素または属性を参照することがあります。 たとえば、XML ドキュメント「[サンプル XML ファイル: 顧客と注文](sample-xml-file-customers-orders.md)」には、顧客の一覧と注文の一覧が含まれています。 すべての `Customer` 要素に `CustomerID` 属性が含まれ、すべての `Order` 要素に `CustomerID` 要素が含まれます。 `Order` 要素の `CustomerID` 要素値は、`CustomerID` 属性値が一致する `Customer` 要素を参照します。

「[サンプル XSD ファイル: 顧客と注文](sample-xsd-file-customers-orders.md)」という記事には、`Customers and orders` ドキュメントの検証に使用できる XSD が含まれています。 XSD の `xs:key` 機能と `xs:keyref` 機能を使用し、`Customer` 要素の `CustomerID` 属性がキーになるようにし、そのキーと、`Order` 要素の `CustomerID` 要素の間にリレーションシップを確立します。

LINQ to XML では、`join` 句を使用して顧客情報と注文情報を結合することで、このリレーションシップを活用できます。

`join` の詳細については、「[結合操作 (C#)](../../csharp/programming-guide/concepts/linq/join-operations.md)」と「[結合操作 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/join-operations.md)」を参照してください。
> [!NOTE]
> 結合は順次検索を使用して行われます。 検索パフォーマンスを上げるインデックスはありません。

## <a name="example-create-a-new-xml-document-that-has-customer-and-order-elements-joined"></a>例: `Customer` 要素と `Order` 要素が結合された新しい XML ドキュメントを作成する

次の例では、「[サンプル XML ファイル: 顧客と注文](sample-xml-file-customers-orders.md)」の `Customer` 要素を `Order` 要素に結合し、注文に `CompanyName` 要素が含まれる新しい XML ドキュメントが生成されます。

クエリを実行する前に、この例では、ドキュメントが「[サンプル XSD ファイル: 顧客と注文](sample-xsd-file-customers-orders.md)」のスキーマに準拠しているかどうかを検証します。 これにより、結合句が機能するようになります。

このクエリでは、"K" より大きい `CustomerID` を持つ顧客の注文のみが選択されます。 各注文内に顧客情報を含む新しい `Order` 要素が出力されます。

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

```vb
Public Class Program
    Public Shared errors As Boolean = False

    Public Shared Function LamValidEvent(ByVal o As Object, _
                 ByVal e As ValidationEventArgs) As Boolean
        Console.WriteLine("{0}", e.Message)
        errors = True
    End Function

    Shared Sub Main()
        Dim schemas As New XmlSchemaSet()
        schemas.Add("", "CustomersOrders.xsd")

        Console.Write("Attempting to validate, ")
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")

        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))
        If errors Then
            Console.WriteLine("custOrdDoc did not validate")
        Else
            Console.WriteLine("custOrdDoc validated")
        End If

        If Not errors Then
            'Join customers and orders, and create a new XML document with
            ' a different shape.
            'The new document contains orders only for customers with a
            ' CustomerID > 'K'.
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault
            Dim newCustOrd As XElement = _
                <Root>
                    <%= From c In custOrd.<Customers>.<Customer> _
                        Join o In custOrd.<Orders>.<Order> _
                        On c.@CustomerID Equals o.<CustomerID>.Value _
                        Where c.@CustomerID.CompareTo("K") > 0 _
                        Select _
                        <Order>
                            <CustomerID><%= c.@CustomerID %></CustomerID>
                            <%= c.<CompanyName> %>
                            <%= c.<ContactName> %>
                            <%= o.<EmployeeID> %>
                            <%= o.<OrderDate> %>
                        </Order> _
                    %>
                </Root>
            Console.WriteLine(newCustOrd)
        End If
    End Sub
End Class
```

この例を実行すると、次の出力が生成されます。

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```
