---
title: XDocument のクエリと XElement のクエリ - LINQ to XML
description: XDocument.Load と XElement.Load によって読み込まれた XML ドキュメントに対しては、記述するクエリが若干異なります。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 46221ff5-62ee-4de8-93ba-66465facb5c1
ms.openlocfilehash: 96d706bcc1871c9e420bafd984d08ca9616b5c18
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412082"
---
# <a name="query-an-xdocument-vs-query-an-xelement-linq-to-xml"></a><span data-ttu-id="46d4d-103">`XDocument` のクエリと `XElement` のクエリ (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="46d4d-103">Query an `XDocument` vs. query an `XElement` (LINQ to XML)</span></span>

<span data-ttu-id="46d4d-104"><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> を使用してドキュメントを読み込むときに記述するクエリは、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> を使用して読み込む場合に記述するものと若干異なります。</span><span class="sxs-lookup"><span data-stu-id="46d4d-104">The query you write when you load a document via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> differs slighty from what you write when you load via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>.</span></span>

## <a name="comparison-of-xdocumentload-and-xelementload"></a><span data-ttu-id="46d4d-105">`XDocument.Load` と `XElement.Load` の比較</span><span class="sxs-lookup"><span data-stu-id="46d4d-105">Comparison of `XDocument.Load` and `XElement.Load`</span></span>

<span data-ttu-id="46d4d-106"><xref:System.Xml.Linq.XElement> によって XML ドキュメントを <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> に読み込む場合、XML ツリーのルートの <xref:System.Xml.Linq.XElement> には読み込んだドキュメントのルート要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="46d4d-106">When you load an XML document into an <xref:System.Xml.Linq.XElement> via <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, the <xref:System.Xml.Linq.XElement> at the root of the XML tree contains the root element of the loaded document.</span></span> <span data-ttu-id="46d4d-107">一方、<xref:System.Xml.Linq.XDocument> によって同じ XML ドキュメントを <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> に読み込む場合は、ツリーのルートは <xref:System.Xml.Linq.XDocument> ノードで、読み込んだドキュメントのルート要素は <xref:System.Xml.Linq.XElement> の許可されている 1 つの子 <xref:System.Xml.Linq.XDocument> ノードになります。</span><span class="sxs-lookup"><span data-stu-id="46d4d-107">However, when you load the same XML document into an <xref:System.Xml.Linq.XDocument> via <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>, the root of the tree is an <xref:System.Xml.Linq.XDocument> node, and the root element of the loaded document is the one allowed child <xref:System.Xml.Linq.XElement> node of the <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="46d4d-108">LINQ to XML 軸は、ルート ノードを基準に動作します。</span><span class="sxs-lookup"><span data-stu-id="46d4d-108">The LINQ to XML axes operate relative to the root node.</span></span>

## <a name="example-load-an-xml-tree-using-xelementload-then-query-for-child-elements"></a><span data-ttu-id="46d4d-109">例: `XElement.Load` を使用して XML ツリーを読み込み、子要素をクエリする</span><span class="sxs-lookup"><span data-stu-id="46d4d-109">Example: Load an XML tree using `XElement.Load`, then query for child elements</span></span>

<span data-ttu-id="46d4d-110">この最初の例では、<xref:System.Xml.Linq.XElement.Load%2A> を使用して XML ツリー読み込みます。</span><span class="sxs-lookup"><span data-stu-id="46d4d-110">This first example loads an XML tree using <xref:System.Xml.Linq.XElement.Load%2A>.</span></span> <span data-ttu-id="46d4d-111">次に、ツリーのルートの子要素をクエリします。</span><span class="sxs-lookup"><span data-stu-id="46d4d-111">It then queries for the child elements of the root of the tree.</span></span>

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XElement.Load");
Console.WriteLine("----");
XElement doc = XElement.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XElement.Load")
Console.WriteLine("----")
Dim doc As XElement = XElement.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

<span data-ttu-id="46d4d-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="46d4d-112">This example produces the following output:</span></span>

```output
Querying tree loaded with XElement.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```

## <a name="example-load-an-xml-tree-using-xdocumentload-then-query-for-child-elements"></a><span data-ttu-id="46d4d-113">例: `XDocument.Load` を使用して XML ツリーを読み込み、子要素をクエリする</span><span class="sxs-lookup"><span data-stu-id="46d4d-113">Example: Load an XML tree using `XDocument.Load`, then query for child elements</span></span>

<span data-ttu-id="46d4d-114">次の例は上記と同じように動作しますが、XML ツリーは <xref:System.Xml.Linq.XElement> ではなく、<xref:System.Xml.Linq.XDocument> に読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="46d4d-114">The next example does the same as the one above, but the XML tree has been loaded into an <xref:System.Xml.Linq.XDocument>, rather than an <xref:System.Xml.Linq.XElement>.</span></span>

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XDocument.Load");
Console.WriteLine("----");
XDocument doc = XDocument.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XDocument.Load")
Console.WriteLine("----")
Dim doc As XDocument = XDocument.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

<span data-ttu-id="46d4d-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="46d4d-115">This example produces the following output:</span></span>

```output
Querying tree loaded with XDocument.Load
----
<Root>
  <Child1>1</Child1>
  <Child2>2</Child2>
  <Child3>3</Child3>
</Root>
```

<span data-ttu-id="46d4d-116">この同じクエリでは、3 つの子ノードではなく 1 つの `Root` ノードが返されたことがわかります。</span><span class="sxs-lookup"><span data-stu-id="46d4d-116">Notice that the same query returned the one `Root` node instead of the three child nodes.</span></span>

<span data-ttu-id="46d4d-117">これに対処する 1 つの方法は、次のように、軸メソッドにアクセスする前に <xref:System.Xml.Linq.XDocument.Root%2A> プロパティを使用することです。</span><span class="sxs-lookup"><span data-stu-id="46d4d-117">One approach to dealing with this is to use the <xref:System.Xml.Linq.XDocument.Root%2A> property before accessing the axes methods, as follows:</span></span>

```csharp
// Create a simple document and write it to a file
File.WriteAllText("Test.xml", @"<Root>
    <Child1>1</Child1>
    <Child2>2</Child2>
    <Child3>3</Child3>
</Root>");

Console.WriteLine("Querying tree loaded with XDocument.Load");
Console.WriteLine("----");
XDocument doc = XDocument.Load("Test.xml");
IEnumerable<XElement> childList =
    from el in doc.Root.Elements()
    select el;
foreach (XElement e in childList)
    Console.WriteLine(e);
```

```vb
' Create a simple document and  write it to a file
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _
    "    <Child1>1</Child1>" + Environment.NewLine + _
    "    <Child2>2</Child2>" + Environment.NewLine + _
    "    <Child3>3</Child3>" + Environment.NewLine + _
    "</Root>")

Console.WriteLine("Querying tree loaded with XDocument.Load")
Console.WriteLine("----")
Dim doc As XDocument = XDocument.Load("Test.xml")
Dim childList As IEnumerable(Of XElement) = _
        From el In doc.Root.Elements() _
        Select el
For Each e As XElement In childList
    Console.WriteLine(e)
Next
```

<span data-ttu-id="46d4d-118">このクエリは、<xref:System.Xml.Linq.XElement> をルートとするツリーのクエリと同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="46d4d-118">This query now performs in the same way as the query on the tree rooted in <xref:System.Xml.Linq.XElement>.</span></span>

<span data-ttu-id="46d4d-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="46d4d-119">This example produces the following output:</span></span>

```output
Querying tree loaded with XDocument.Load
----
<Child1>1</Child1>
<Child2>2</Child2>
<Child3>3</Child3>
```
