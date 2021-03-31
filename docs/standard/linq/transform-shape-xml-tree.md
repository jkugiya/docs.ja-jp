---
title: XML ツリーの構造を変換する方法 - LINQ to XML
description: 関数型構築を使用し、XML ドキュメントの構造を変更できます。つまり、データは維持し、要素名、属性名、階層などを変更します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 7f78cb2542357be674d771f93825b7f4a56abea0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412138"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-linq-to-xml"></a><span data-ttu-id="3a38f-103">XML ツリーの構造を変換する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3a38f-103">How to transform the shape of an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="3a38f-104">XML ドキュメントの "*構造*" とは、XML ドキュメントの要素名、属性名、およびその階層の特性を表すものです。</span><span class="sxs-lookup"><span data-stu-id="3a38f-104">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>

<span data-ttu-id="3a38f-105">XML ドキュメントの構造を変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3a38f-105">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="3a38f-106">たとえば、既存の XML ドキュメントを、異なる要素名と属性名を必要とする別のシステムに送信するとします。</span><span class="sxs-lookup"><span data-stu-id="3a38f-106">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="3a38f-107">ドキュメント全体を調べ、必要に応じて要素の削除や要素名の変更を行うことも可能ですが、関数型構築を使用する方が、読みやすく保守しやすいコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="3a38f-107">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="3a38f-108">関数型構築の詳細については、「[関数型構築](functional-construction.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a38f-108">For more information about functional construction, see [Functional construction](functional-construction.md).</span></span>

<span data-ttu-id="3a38f-109">この記事の最初の例では、XML ドキュメントの構成が変更されます。</span><span class="sxs-lookup"><span data-stu-id="3a38f-109">The first example in this article changes the organization of an XML document.</span></span> <span data-ttu-id="3a38f-110">ここでは、複合要素をツリー内で移動します。</span><span class="sxs-lookup"><span data-stu-id="3a38f-110">It moves complex elements from one location in the tree to another.</span></span>

<span data-ttu-id="3a38f-111">2 番目の例では、構造がソース ドキュメントの構造とは異なる XML ドキュメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3a38f-111">The second example creates an XML document whose shape differs from that of the source document.</span></span> <span data-ttu-id="3a38f-112">一部の要素が省略され、名前が変更され、要素名の大文字と小文字の使い分けが変更されます。</span><span class="sxs-lookup"><span data-stu-id="3a38f-112">It omits some elements, renames others, and changes the casing of the element names.</span></span>

## <a name="example-use-embedded-query-expressions-to-change-the-shape-of-an-xml-tree"></a><span data-ttu-id="3a38f-113">例: 組み込まれたクエリ式を使用して XML ツリーの構造を変更する</span><span class="sxs-lookup"><span data-stu-id="3a38f-113">Example: Use embedded query expressions to change the shape of an XML tree</span></span>

<span data-ttu-id="3a38f-114">次の例では、組み込まれたクエリ式を使用して、XML ファイルの構造を変更します。</span><span class="sxs-lookup"><span data-stu-id="3a38f-114">The following example changes the shape of an XML file using embedded query expressions.</span></span>

<span data-ttu-id="3a38f-115">この例のソース XML ドキュメント「[サンプル XML ファイル: 顧客と注文](sample-xml-file-customers-orders.md)」では、`Root` 要素の下にある `Customers` 要素にすべての顧客が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a38f-115">The source XML document for this example, [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="3a38f-116">また、`Orders` 要素の下には `Root` 要素もあり、すべての注文が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a38f-116">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="3a38f-117">例では、各顧客の注文が `Orders` 要素内の `Customer` 要素に含まれるような、新しい XML ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a38f-117">The example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="3a38f-118">元のドキュメントでは、`CustomerID` 要素内に `Order` 要素も含まれています。この要素は新しいツリーから除外されます。</span><span class="sxs-lookup"><span data-stu-id="3a38f-118">The original document also contains a `CustomerID` element in the `Order` element; this element is omitted from the new tree.</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");
XElement newCustOrd =
    new XElement("Root",
        from cust in co.Element("Customers").Elements("Customer")
        select new XElement("Customer",
            cust.Attributes(),
            cust.Elements(),
            new XElement("Orders",
                from ord in co.Element("Orders").Elements("Order")
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")
                select new XElement("Order",
                    ord.Attributes(),
                    ord.Element("EmployeeID"),
                    ord.Element("OrderDate"),
                    ord.Element("RequiredDate"),
                    ord.Element("ShipInfo")
                )
            )
        )
    );
Console.WriteLine(newCustOrd);
```

 ```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim newCustOrd = _
    <Root>
        <%= From cust In co.<Customers>.<Customer> _
            Select _
            <Customer>
                <%= cust.Attributes() %>
                <%= cust.Elements() %>
                <Orders>
                    <%= From ord In co.<Orders>.<Order> _
                        Where ord.<CustomerID>.Value = cust.@CustomerID _
                        Select _
                        <Order>
                            <%= ord.Attributes() %>
                            <%= ord.<EmployeeID> %>
                            <%= ord.<OrderDate> %>
                            <%= ord.<RequiredDate> %>
                            <%= ord.<ShipInfo> %>
                        </Order> _
                    %>
                </Orders>
            </Customer> _
        %>
    </Root>
Console.WriteLine(newCustOrd)
```

<span data-ttu-id="3a38f-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3a38f-119">This example produces the following output:</span></span>

```xml
<Root>
  <Customer CustomerID="GREAL">
    <CompanyName>Great Lakes Food Market</CompanyName>
    <ContactName>Howard Snyder</ContactName>
    <ContactTitle>Marketing Manager</ContactTitle>
    <Phone>(503) 555-7555</Phone>
    <FullAddress>
      <Address>2732 Baker Blvd.</Address>
      <City>Eugene</City>
      <Region>OR</Region>
      <PostalCode>97403</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
  <Customer CustomerID="HUNGC">
    <CompanyName>Hungry Coyote Import Store</CompanyName>
    <ContactName>Yoshi Latimer</ContactName>
    <ContactTitle>Sales Representative</ContactTitle>
    <Phone>(503) 555-6874</Phone>
    <Fax>(503) 555-2376</Fax>
    <FullAddress>
      <Address>City Center Plaza 516 Main St.</Address>
      <City>Elgin</City>
      <Region>OR</Region>
      <PostalCode>97827</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
  ...
</Root>
```

## <a name="example-create-a-document-whose-shape-differs-from-that-of-the-source-document"></a><span data-ttu-id="3a38f-120">例: 構造がソース ドキュメントの構造とは異なるドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="3a38f-120">Example: Create a document whose shape differs from that of the source document</span></span>

<span data-ttu-id="3a38f-121">この例では、一部の要素の名前を変更し、一部の属性を要素に変換します。</span><span class="sxs-lookup"><span data-stu-id="3a38f-121">This example renames some elements and converts some attributes to elements.</span></span> <span data-ttu-id="3a38f-122">`ConvertAddress` が呼び出され、<xref:System.Xml.Linq.XElement> オブジェクトの一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="3a38f-122">It calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="3a38f-123">メソッドの引数は、`Address` 属性の値が `Type` である `"Shipping"` 複合要素を特定するクエリです。</span><span class="sxs-lookup"><span data-stu-id="3a38f-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span> <span data-ttu-id="3a38f-124">この例では、XML ドキュメント「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="3a38f-124">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
static IEnumerable<XElement> ConvertAddress(XElement add)
{
    List<XElement> fragment = new List<XElement>() {
        new XElement("NAME", (string)add.Element("Name")),
        new XElement("STREET", (string)add.Element("Street")),
        new XElement("CITY", (string)add.Element("City")),
        new XElement("ST", (string)add.Element("State")),
        new XElement("POSTALCODE", (string)add.Element("Zip")),
        new XElement("COUNTRY", (string)add.Element("Country"))
    };
    return fragment;
}

static void Main(string[] args)
{
    XElement po = XElement.Load("PurchaseOrder.xml");
    XElement newPo = new XElement("PO",
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),
        ConvertAddress(
            (from el in po.Elements("Address")
            where (string)el.Attribute("Type") == "Shipping"
            select el)
            .First()
        )
    );
    Console.WriteLine(newPo);
}
```

```vb
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)
    Dim fragment = New List(Of XElement)
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)
    fragment.Add(<ST><%= add.<State>.Value %></ST>)
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)
    Return fragment
End Function

Sub Main()
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")
    Dim newPo As XElement = _
        <PO>
            <ID><%= po.@PurchaseOrderNumber %></ID>
            <DATE><%= CDate(po.@OrderDate) %></DATE>
            <%= _
                ConvertAddress( _
                (From el In po.<Address> _
                Where el.@Type = "Shipping" _
                Select el) _
                .First() _
                ) _
            %>
        </PO>
    Console.WriteLine(newPo)
End Sub
```

<span data-ttu-id="3a38f-125">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3a38f-125">This example produces the following output:</span></span>

```xml
<PO>
  <ID>99503</ID>
  <DATE>1999-10-20T00:00:00</DATE>
  <NAME>Ellen Adams</NAME>
  <STREET>123 Maple Street</STREET>
  <CITY>Mill Valley</CITY>
  <ST>CA</ST>
  <POSTALCODE>10999</POSTALCODE>
  <COUNTRY>USA</COUNTRY>
</PO>
```

## <a name="see-also"></a><span data-ttu-id="3a38f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a38f-126">See also</span></span>

- [<span data-ttu-id="3a38f-127">プロジェクションと変換 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a38f-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](./work-dictionaries-linq-xml.md)
