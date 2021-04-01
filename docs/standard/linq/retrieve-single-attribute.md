---
title: 単一の属性を取得する方法 - LINQ to XML
description: 属性名を指定して要素の単一の属性を取得します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: a8a56ec62275f2376d19d7fc9090414b74fc77ad
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412073"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml"></a><span data-ttu-id="adde2-103">単一の属性を取得する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="adde2-103">How to retrieve a single attribute (LINQ to XML)</span></span>

<span data-ttu-id="adde2-104">この記事では、属性名を指定して要素の単一の属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="adde2-104">This article explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="adde2-105">これは、特定の属性を持つ要素を検索するクエリ式を記述する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="adde2-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>

<span data-ttu-id="adde2-106"><xref:System.Xml.Linq.XElement.Attribute%2A> クラスの <xref:System.Xml.Linq.XElement> メソッドは、指定された名前を持つ <xref:System.Xml.Linq.XAttribute> を返します。</span><span class="sxs-lookup"><span data-stu-id="adde2-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>

## <a name="example-retrieve-attribute-values-given-the-element-and-attribute-names"></a><span data-ttu-id="adde2-107">例: 要素名と属性名を指定して属性値を取得する</span><span class="sxs-lookup"><span data-stu-id="adde2-107">Example: Retrieve attribute values, given the element and attribute names</span></span>

<span data-ttu-id="adde2-108">次の例では、<xref:System.Xml.Linq.XElement> メソッドを使用して、`PhoneNumbers` という名前の要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="adde2-108">The following example uses the <xref:System.Xml.Linq.XElement> method to create an element named `PhoneNumbers`.</span></span> <span data-ttu-id="adde2-109">次に、`Phone` という名前の子孫要素をすべて検索し、それぞれに対して、<xref:System.Xml.Linq.XElement.Attribute%2A> メソッドを使用して `type` という名前の属性の値を取得して出力します。</span><span class="sxs-lookup"><span data-stu-id="adde2-109">It then finds all the descendant elements named `Phone` and, for each, uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method to obtain and output the value of the attribute named `type`:</span></span>

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList = From el In cust...<Phone>
For Each e As XElement In elList
    Console.WriteLine(e.@type)
Next
```

<span data-ttu-id="adde2-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="adde2-110">This example produces the following output:</span></span>

```output
home
work
```

## <a name="example-retrieve-an-attribute-value-with-a-cast"></a><span data-ttu-id="adde2-111">例: キャストを使用して属性値を取得する</span><span class="sxs-lookup"><span data-stu-id="adde2-111">Example: Retrieve an attribute value with a cast</span></span>

<span data-ttu-id="adde2-112"><xref:System.Xml.Linq.XElement> オブジェクトの場合と同じように、キャストすることで属性の値を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="adde2-112">You can retrieve the value of an attribute by casting it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="adde2-113">この動作を次の例で示します。</span><span class="sxs-lookup"><span data-stu-id="adde2-113">The following example demonstrates this:</span></span>

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList As IEnumerable(Of XElement) = _
    From el In cust...<Phone> _
    Select el
For Each el As XElement In elList
    Console.WriteLine(el.@type)
Next
```

<span data-ttu-id="adde2-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="adde2-114">This example produces the following output:</span></span>

```output
home
work
```

<span data-ttu-id="adde2-115">LINQ to XML には、`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID`、`GUID?` に対する <xref:System.Xml.Linq.XAttribute> クラスのための明示的なキャスト演算子が用意されています。</span><span class="sxs-lookup"><span data-stu-id="adde2-115">LINQ to XML provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>

## <a name="example-cast-for-an-attribute-in-a-namespace"></a><span data-ttu-id="adde2-116">例: 名前空間内の属性にキャストする</span><span class="sxs-lookup"><span data-stu-id="adde2-116">Example: Cast for an attribute in a namespace</span></span>

<span data-ttu-id="adde2-117">上記と同じコードを使用して、名前空間内の属性を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="adde2-117">The following example shows the same code for an attribute that's in a namespace.</span></span> <span data-ttu-id="adde2-118">詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adde2-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement cust = new XElement(aw + "PhoneNumbers",
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "home"),
        "555-555-5555"),
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants(aw + "Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute(aw + "type"));
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cust As XElement = _
            <aw:PhoneNumbers>
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>
            </aw:PhoneNumbers>
        Dim elList As IEnumerable(Of XElement) = _
            From el In cust...<aw:Phone> _
            Select el
        For Each el As XElement In elList
            Console.WriteLine(el.@aw:type)
        Next
    End Sub
End Module
```

<span data-ttu-id="adde2-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="adde2-119">This example produces the following output:</span></span>

```output
home
work
```

## <a name="see-also"></a><span data-ttu-id="adde2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="adde2-120">See also</span></span>

- [<span data-ttu-id="adde2-121">LINQ to XML 軸の概要</span><span class="sxs-lookup"><span data-stu-id="adde2-121">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
