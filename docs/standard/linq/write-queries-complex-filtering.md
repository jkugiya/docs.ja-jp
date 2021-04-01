---
title: 複雑なフィルターを使用してクエリを記述する方法 - LINQ to XML
description: 複雑なフィルターを使用して LINQ to XML クエリを記述することが必要になる場合があります。 たとえば、特定の名前と値を持つ子要素を含む要素をすべて検索しなければならない場合があります。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: c5e7f812364e7e96e3a4b8f5515d07a3524ec979
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412110"
---
# <a name="how-to-write-queries-with-complex-filtering-linq-to-xml"></a><span data-ttu-id="bf3d6-104">複雑なフィルターを使用してクエリを記述する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-104">How to write queries with complex filtering (LINQ to XML)</span></span>

<span data-ttu-id="bf3d6-105">複雑なフィルターを使用して LINQ to XML クエリを記述することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-105">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="bf3d6-106">たとえば、特定の名前と値を持つ子要素を含む要素をすべて検索しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-106">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="bf3d6-107">この記事では、複雑なフィルターを使用してクエリを記述する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-107">This article gives an example of writing a query with complex filtering.</span></span>

## <a name="example-find-with-a-nested-query-in-the-where-clause"></a><span data-ttu-id="bf3d6-108">例: `Where` 句で入れ子になったクエリを使用して検索する</span><span class="sxs-lookup"><span data-stu-id="bf3d6-108">Example: Find with a nested query in the `Where` clause</span></span>

<span data-ttu-id="bf3d6-109">この例では、次を持つ `PurchaseOrder` 要素を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-109">This example shows how to find all `PurchaseOrder` elements that have:</span></span>

- <span data-ttu-id="bf3d6-110">`Type` 属性が "Shipping" の `Address` 子要素。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-110">A child `Address` element whose `Type` attribute equals "Shipping".</span></span>
- <span data-ttu-id="bf3d6-111">"NY" と等しい `State` 子要素。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-111">A child `State` element that equals "NY".</span></span>

<span data-ttu-id="bf3d6-112">この例では、入れ子になったクエリを `Where` 句で使用しています。コレクションに要素が含まれる場合、`Any` 演算子は `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-112">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="bf3d6-113">この例では、「[サンプル XML ファイル: 複数の購買発注書](sample-xml-file-multiple-purchase-orders.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-113">The example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

<span data-ttu-id="bf3d6-114">`Any` 演算子の詳細については、「[量指定子操作 (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md)」および「[量指定子操作 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-114">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../docs/csharp/programming-guide/concepts/linq/quantifier-operations.md) and [Quantifier Operations (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements("PurchaseOrder")
    where
        (from add in el.Elements("Address")
        where
            (string)add.Attribute("Type") == "Shipping" &&
            (string)add.Element("State") == "NY"
        select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrders.xml")
Dim purchaseOrders As IEnumerable(Of XElement) = _
    From el In root.<PurchaseOrder> _
    Where _
        (From add In el.<Address> _
        Where _
             add.@Type = "Shipping" And _
             add.<State>.Value = "NY" _
        Select add) _
    .Any() _
    Select el
For Each el As XElement In purchaseOrders
    Console.WriteLine(el.@PurchaseOrderNumber)
Next
```

<span data-ttu-id="bf3d6-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-115">This example produces the following output:</span></span>

```output
99505
```

## <a name="example-find-in-xml-thats-in-a-namespace"></a><span data-ttu-id="bf3d6-116">例: 名前空間にある XML で検索する</span><span class="sxs-lookup"><span data-stu-id="bf3d6-116">Example: Find in XML that's in a namespace</span></span>

<span data-ttu-id="bf3d6-117">次の例のクエリは上のものと同じですが、ある名前空間にある XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-117">The following example shows the same query as above, but for XML that's in a namespace.</span></span> <span data-ttu-id="bf3d6-118">詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="bf3d6-119">この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](sample-xml-file-multiple-purchase-orders-namespace.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-119">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> purchaseOrders =
    from el in root.Elements(aw + "PurchaseOrder")
    where
        (from add in el.Elements(aw + "Address")
         where
             (string)add.Attribute(aw + "Type") == "Shipping" &&
             (string)add.Element(aw + "State") == "NY"
         select add)
        .Any()
    select el;
foreach (XElement el in purchaseOrders)
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim purchaseOrders As IEnumerable(Of XElement) = _
            From el In root.<aw:PurchaseOrder> _
            Where _
                (From add In el.<aw:Address> _
                Where _
                     add.@aw:Type = "Shipping" And _
                     add.<aw:State>.Value = "NY" _
                Select add) _
            .Any() _
            Select el
        For Each el As XElement In purchaseOrders
            Console.WriteLine(el.@aw:PurchaseOrderNumber)
        Next
    End Sub
End Module
```

<span data-ttu-id="bf3d6-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf3d6-120">This example produces the following output:</span></span>

```output
99505
```

## <a name="see-also"></a><span data-ttu-id="bf3d6-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf3d6-121">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="bf3d6-122">射影操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-122">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="bf3d6-123">量指定子操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-123">Quantifier Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
- [<span data-ttu-id="bf3d6-124">XML 子軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-124">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="bf3d6-125">XML 属性軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-125">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="bf3d6-126">XML Value プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-126">XML Value Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="bf3d6-127">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-127">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="bf3d6-128">量指定子操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf3d6-128">Quantifier Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
