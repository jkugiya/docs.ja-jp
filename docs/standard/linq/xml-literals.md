---
title: Visual Basic の XML リテラル - LINQ to XML
description: XML リテラルと組み込み式を使用し、Visual Basic で XML ツリーを作成できます。 組み込み式を使用すると、式を評価してその式の結果を XML ツリーに挿入できます。
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412003"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a><span data-ttu-id="0a3b9-104">Visual Basic の XML リテラル (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="0a3b9-104">XML Literals in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="0a3b9-105">この記事では、XML リテラルと組み込み式を使用し、Visual Basic で XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-105">This article provides information about creating XML trees in Visual Basic using XML literals and embedded expressions.</span></span>

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a><span data-ttu-id="0a3b9-106">例: XML リテラルを使用して XML ツリーを作成する</span><span class="sxs-lookup"><span data-stu-id="0a3b9-106">Example: Use XML literals to create an XML tree</span></span>

<span data-ttu-id="0a3b9-107">次の例では、XML リテラルを使用して <xref:System.Xml.Linq.XElement> (ここでは `contacts`) を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`, with XML literals:</span></span>

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a><span data-ttu-id="0a3b9-108">例: XML リテラルを使用し、簡単なコンテンツで XElement を作成する</span><span class="sxs-lookup"><span data-stu-id="0a3b9-108">Example: Use XML literals to create an XElement with simple content</span></span>

<span data-ttu-id="0a3b9-109">次のように、単純コンテンツを含む <xref:System.Xml.Linq.XElement> を作成できます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

<span data-ttu-id="0a3b9-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-110">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a><span data-ttu-id="0a3b9-111">例: XML リテラルを使用し、空の要素を作成する</span><span class="sxs-lookup"><span data-stu-id="0a3b9-111">Example: Use an XML literal to create an empty element</span></span>

<span data-ttu-id="0a3b9-112">次のように、空の <xref:System.Xml.Linq.XElement> を作成できます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

<span data-ttu-id="0a3b9-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-113">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a><span data-ttu-id="0a3b9-114">組み込み式を使用してコンテンツを作成する</span><span class="sxs-lookup"><span data-stu-id="0a3b9-114">Use embedded expressions to create content</span></span>

<span data-ttu-id="0a3b9-115">XML リテラルの重要な機能は、組み込み式を利用できることです。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="0a3b9-116">組み込み式を使用すると、式を評価してその式の結果を XML ツリーに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="0a3b9-117">式が <xref:System.Xml.Linq.XElement> の型に評価される場合、要素がツリーに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="0a3b9-118">式が <xref:System.Xml.Linq.XAttribute> の型に評価される場合は、属性がツリーに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="0a3b9-119">要素や属性は、それが有効となるツリーにのみ挿入できます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-119">You can insert elements and attributes into the tree only where they're valid.</span></span>

<span data-ttu-id="0a3b9-120">組み込み式に含めることができるのは 1 つの式だけであることに注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-120">it's important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="0a3b9-121">複数のステートメントを組み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-121">You can't embed multiple statements.</span></span> <span data-ttu-id="0a3b9-122">式が複数の行にまたがる場合は、行連結文字を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>

<span data-ttu-id="0a3b9-123">組み込み式を使用して既存のノード (要素を含む) や属性を新しい XML ツリーに追加する場合に、その既存のノードに既に親があるときは、ノードが複製されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="0a3b9-124">新しく複製されたノードは、新しい XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="0a3b9-125">既存のノードに親がない場合は、単にノードが新しい XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-125">If the existing nodes aren't parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="0a3b9-126">この記事の最後の例では、この動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-126">The last example in this article demonstrates this.</span></span>

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a><span data-ttu-id="0a3b9-127">例: 組み込み式を使用し、要素を挿入する</span><span class="sxs-lookup"><span data-stu-id="0a3b9-127">Example: Use an embedded expression to insert an element</span></span>

<span data-ttu-id="0a3b9-128">次の例では、組み込み式を使用して要素をツリーに挿入します。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-128">The following example uses an embedded expression to insert an element into the tree:</span></span>

```vb
xmlTree1 As XElement = _
    <Root>
        <Child>Contents</Child>
    </Root>
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child> %>
    </Root>
Console.WriteLine(xmlTree2)
```

<span data-ttu-id="0a3b9-129">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-129">This example produces the following output:</span></span>

```xml
<Root>
  <Child>Contents</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-for-content"></a><span data-ttu-id="0a3b9-130">例: コンテンツの組み込み式を使用する</span><span class="sxs-lookup"><span data-stu-id="0a3b9-130">Example: Use an embedded expression for content</span></span>

<span data-ttu-id="0a3b9-131">組み込み式を使用して要素のコンテンツを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-131">You can use an embedded expression to supply the content of an element:</span></span>

```vb
Dim str As String
str = "Some content"
Dim root As XElement = <Root><%= str %></Root>
Console.WriteLine(root)
```

<span data-ttu-id="0a3b9-132">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-132">This example produces the following output:</span></span>

```xml
<Root>Some content</Root>
```

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="0a3b9-133">例: 組み込み式で LINQ クエリを使用する</span><span class="sxs-lookup"><span data-stu-id="0a3b9-133">Example: Use a LINQ query in an embedded expression</span></span>

<span data-ttu-id="0a3b9-134">LINQ クエリの結果を使用し、ある要素のコンテンツを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-134">You can use the results of a LINQ query to provide the content of an element:</span></span>

```vb
Dim arr As Integer() = {1, 2, 3}

Dim n As XElement = _
    <Root>
        <%= From i In arr Select <Child><%= i %></Child> %>
    </Root>

Console.WriteLine(n)
```

<span data-ttu-id="0a3b9-135">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-135">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Child>3</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a><span data-ttu-id="0a3b9-136">例: 組み込み式を使用し、ノード名を指定する</span><span class="sxs-lookup"><span data-stu-id="0a3b9-136">Example: Use an embedded expression to provide node names</span></span>

<span data-ttu-id="0a3b9-137">組み込み式を使用して、属性名、属性値、要素名、要素値を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-137">You can also use an embedded expression to calculate attribute names, attribute values, element names, and element values:</span></span>

```vb
Dim eleName As String = "ele"
Dim attName As String = "att"
Dim attValue As String = "aValue"
Dim eleValue As String = "eValue"
Dim n As XElement = _
    <Root <%= attName %>=<%= attValue %>>
        <<%= eleName %>>
            <%= eleValue %>
        </>
    </Root>
Console.WriteLine(n)
```

<span data-ttu-id="0a3b9-138">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-138">This example produces the following output:</span></span>

```xml
<Root att="aValue">
  <ele>eValue</ele>
</Root>
```

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a><span data-ttu-id="0a3b9-139">例: 組み込み式を使用し、ノードを複製し、アタッチする</span><span class="sxs-lookup"><span data-stu-id="0a3b9-139">Example: Use an embedded expression to clone and attach nodes</span></span>

<span data-ttu-id="0a3b9-140">既に説明したとおり、組み込み式を使用して既存のノード (要素を含む) や属性を新しい XML ツリーに追加するとき、追加されるノードに既に親があるとき、ノードが複製され、複製が新しい XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-140">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, and if the nodes being added nodes are already parented, the nodes are cloned and the clones are attached to the new XML tree.</span></span> <span data-ttu-id="0a3b9-141">既存のノードに親がない場合は、そのままノードが新しい XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-141">If the existing nodes aren't parented, they're simply attached to the new XML tree.</span></span>

<span data-ttu-id="0a3b9-142">次のコードでは、親を持つ要素をツリーに追加する場合と親を持たない要素をツリーに追加する場合の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-142">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
Dim child2 As XElement = <Child2>2</Child2>

' Create a tree and add Child1 and Child2 to it.
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child1>(0) %>
        <%= child2 %>
    </Root>

' Compare Child1 identity.
Console.WriteLine("Child1 was {0}", _
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _
    "attached", "cloned"))

' Compare Child2 identity.
Console.WriteLine("Child2 was {0}", _
    IIf(child2 Is xmlTree2.Element("Child2"), _
    "attached", "cloned"))
```

<span data-ttu-id="0a3b9-143">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0a3b9-143">This example produces the following output:</span></span>

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="0a3b9-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a3b9-144">See also</span></span>

- [<span data-ttu-id="0a3b9-145">関数型構築</span><span class="sxs-lookup"><span data-stu-id="0a3b9-145">Functional construction</span></span>](functional-construction.md)
