---
title: 複数のキーで要素を並べ替える方法 - LINQ to XML
description: 複数のキーで XML 要素を並べ替える方法について学習します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3b2760b6-d607-4ac7-b784-5c6524e2a0e0
ms.openlocfilehash: 161f354192b3bc5cecec7e7e1b457b23c415c073
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412200"
---
# <a name="how-to-sort-elements-on-multiple-keys-linq-to-xml"></a><span data-ttu-id="4eb84-103">複数のキーで要素を並べ替える方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="4eb84-103">How to sort elements on multiple keys (LINQ to XML)</span></span>

<span data-ttu-id="4eb84-104">この記事では、C# および Visual Basic で複数のキーに基づいて並べ替える方法について示します。</span><span class="sxs-lookup"><span data-stu-id="4eb84-104">This article shows how to sort on multiple keys in C# and Visual Basic.</span></span>

## <a name="example-sort-xml-elements-on-multiple-keys"></a><span data-ttu-id="4eb84-105">例: 複数のキーで XML 要素を並べ替える</span><span class="sxs-lookup"><span data-stu-id="4eb84-105">Example: Sort XML elements on multiple keys</span></span>

<span data-ttu-id="4eb84-106">この例では、郵便番号 (プライマリ) と注文日の 2 つのキーで並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="4eb84-106">This example sorts on two keys: shipping postal code (primary) and order date.</span></span> <span data-ttu-id="4eb84-107">ここでは、XML ドキュメントの「[サンプル XML ファイル: 顧客と注文](sample-xml-file-customers-orders.md)」が使用されています。</span><span class="sxs-lookup"><span data-stu-id="4eb84-107">It uses XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md).</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");
var sortedElements =
    from c in co.Element("Orders").Elements("Order")
    orderby (string)c.Element("ShipInfo").Element("ShipPostalCode"),
            (DateTime)c.Element("OrderDate")
    select new {
        CustomerID = (string)c.Element("CustomerID"),
        EmployeeID = (string)c.Element("EmployeeID"),
        ShipPostalCode = (string)c.Element("ShipInfo").Element("ShipPostalCode"),
        OrderDate = (DateTime)c.Element("OrderDate")
    };
foreach (var r in sortedElements)
    Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}",
        r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate);
```

```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim result = _
    From c In co.<Orders>.<Order> _
    Order By c.<ShipInfo>.<ShipPostalCode>.Value, Convert.ToDateTime(c.<OrderDate>.Value) _
    Select New With { _
        .CustomerID = c.<CustomerID>.Value, _
        .EmployeeID = c.<EmployeeID>.Value, _
        .ShipPostalCode = c.<ShipInfo>.<ShipPostalCode>.Value, _
        .OrderDate = Convert.ToDateTime(c.<OrderDate>.Value) _
    }
For Each r In result
    Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}", _
                r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate)
Next
```

<span data-ttu-id="4eb84-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4eb84-108">This example produces the following output:</span></span>

```output
CustomerID:LETSS EmployeeID:1 ShipPostalCode:94117 OrderDate:6/25/1997
CustomerID:LETSS EmployeeID:8 ShipPostalCode:94117 OrderDate:10/27/1997
CustomerID:LETSS EmployeeID:6 ShipPostalCode:94117 OrderDate:11/10/1997
CustomerID:LETSS EmployeeID:4 ShipPostalCode:94117 OrderDate:2/12/1998
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:5/6/1997
CustomerID:GREAL EmployeeID:8 ShipPostalCode:97403 OrderDate:7/4/1997
CustomerID:GREAL EmployeeID:1 ShipPostalCode:97403 OrderDate:7/31/1997
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:7/31/1997
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:9/4/1997
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:9/25/1997
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:1/6/1998
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:3/9/1998
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:4/7/1998
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/22/1998
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/30/1998
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:12/6/1996
CustomerID:HUNGC EmployeeID:1 ShipPostalCode:97827 OrderDate:12/25/1996
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:1/15/1997
CustomerID:HUNGC EmployeeID:4 ShipPostalCode:97827 OrderDate:7/16/1997
CustomerID:HUNGC EmployeeID:8 ShipPostalCode:97827 OrderDate:9/8/1997
CustomerID:LAZYK EmployeeID:1 ShipPostalCode:99362 OrderDate:3/21/1997
CustomerID:LAZYK EmployeeID:8 ShipPostalCode:99362 OrderDate:5/22/1997
```

## <a name="example-sort-xml-thats-in-a-namespace"></a><span data-ttu-id="4eb84-109">例: 名前空間にある XML を並べ替える</span><span class="sxs-lookup"><span data-stu-id="4eb84-109">Example: Sort XML that's in a namespace</span></span>

<span data-ttu-id="4eb84-110">この例では、最初と同じ並べ替えを行いますが、名前空間にある XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="4eb84-110">This example does the same sort as the first, but for XML that's in a namespace.</span></span> <span data-ttu-id="4eb84-111">ここでは、XML ドキュメントの[サンプル XML ファイル: 名前空間内の顧客と注文](sample-xml-file-customers-orders-namespace.md)を使用しています。</span><span class="sxs-lookup"><span data-stu-id="4eb84-111">It uses XML document [Sample XML file: Customers and orders in a namespace](sample-xml-file-customers-orders-namespace.md).</span></span>

<span data-ttu-id="4eb84-112">詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4eb84-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement co = XElement.Load("CustomersOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
var sortedElements =
    from c in co.Element(aw + "Orders").Elements(aw + "Order")
    orderby (string)c.Element(aw + "ShipInfo").Element(aw + "ShipPostalCode"),
            (DateTime)c.Element(aw + "OrderDate")
    select new
    {
        CustomerID = (string)c.Element(aw + "CustomerID"),
        EmployeeID = (string)c.Element(aw + "EmployeeID"),
        ShipPostalCode = (string)c.Element(aw + "ShipInfo").Element(aw + "ShipPostalCode"),
        OrderDate = (DateTime)c.Element(aw + "OrderDate")
    };
foreach (var r in sortedElements)
    Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}",
        r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate);
```

```vb
Imports <xmlns='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim co As XElement = XElement.Load("CustomersOrdersInNamespace.xml")
        Dim result = _
            From c In co.<Orders>.<Order> _
            Order By c.<ShipInfo>.<ShipPostalCode>.Value, Convert.ToDateTime(c.<OrderDate>.Value) _
            Select New With { _
                .CustomerID = c.<CustomerID>.Value, _
                .EmployeeID = c.<EmployeeID>.Value, _
                .ShipPostalCode = c.<ShipInfo>.<ShipPostalCode>.Value, _
                .OrderDate = Convert.ToDateTime(c.<OrderDate>.Value) _
            }
        For Each r In result
            Console.WriteLine("CustomerID:{0} EmployeeID:{1} ShipPostalCode:{2} OrderDate:{3:d}", _
                        r.CustomerID, r.EmployeeID, r.ShipPostalCode, r.OrderDate)
        Next
    End Sub
End Module
```

<span data-ttu-id="4eb84-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4eb84-113">This example produces the following output:</span></span>

```output
CustomerID:LETSS EmployeeID:1 ShipPostalCode:94117 OrderDate:6/25/1997
CustomerID:LETSS EmployeeID:8 ShipPostalCode:94117 OrderDate:10/27/1997
CustomerID:LETSS EmployeeID:6 ShipPostalCode:94117 OrderDate:11/10/1997
CustomerID:LETSS EmployeeID:4 ShipPostalCode:94117 OrderDate:2/12/1998
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:5/6/1997
CustomerID:GREAL EmployeeID:8 ShipPostalCode:97403 OrderDate:7/4/1997
CustomerID:GREAL EmployeeID:1 ShipPostalCode:97403 OrderDate:7/31/1997
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:7/31/1997
CustomerID:GREAL EmployeeID:6 ShipPostalCode:97403 OrderDate:9/4/1997
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:9/25/1997
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:1/6/1998
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:3/9/1998
CustomerID:GREAL EmployeeID:3 ShipPostalCode:97403 OrderDate:4/7/1998
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/22/1998
CustomerID:GREAL EmployeeID:4 ShipPostalCode:97403 OrderDate:4/30/1998
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:12/6/1996
CustomerID:HUNGC EmployeeID:1 ShipPostalCode:97827 OrderDate:12/25/1996
CustomerID:HUNGC EmployeeID:3 ShipPostalCode:97827 OrderDate:1/15/1997
CustomerID:HUNGC EmployeeID:4 ShipPostalCode:97827 OrderDate:7/16/1997
CustomerID:HUNGC EmployeeID:8 ShipPostalCode:97827 OrderDate:9/8/1997
CustomerID:LAZYK EmployeeID:1 ShipPostalCode:99362 OrderDate:3/21/1997
CustomerID:LAZYK EmployeeID:8 ShipPostalCode:99362 OrderDate:5/22/1997
```

## <a name="see-also"></a><span data-ttu-id="4eb84-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4eb84-114">See also</span></span>

- [<span data-ttu-id="4eb84-115">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4eb84-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
