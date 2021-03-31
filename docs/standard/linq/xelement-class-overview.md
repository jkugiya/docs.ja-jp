---
title: XElement クラスの概要
description: XElement クラスは XML 要素を表します。 これを使用し、要素を作成または変更したり、属性と子を追加したり、シリアル化したりできます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411995"
---
# <a name="xelement-class-overview"></a><span data-ttu-id="cb97c-104">XElement クラスの概要</span><span class="sxs-lookup"><span data-stu-id="cb97c-104">XElement class overview</span></span>

<span data-ttu-id="cb97c-105"><xref:System.Xml.Linq.XElement> クラスは、LINQ to XML の基本的なクラスの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="cb97c-105">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in LINQ to XML.</span></span> <span data-ttu-id="cb97c-106">これは XML 要素を表します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-106">It represents an XML element.</span></span> <span data-ttu-id="cb97c-107">次の一覧は、このクラスでできることをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="cb97c-107">The following list shows what you can use this class for:</span></span>

- <span data-ttu-id="cb97c-108">要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-108">Create elements.</span></span>
- <span data-ttu-id="cb97c-109">要素のコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-109">Change the content of the element.</span></span>
- <span data-ttu-id="cb97c-110">子要素を追加、変更、削除します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-110">Add, change, or delete child elements.</span></span>
- <span data-ttu-id="cb97c-111">要素に属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-111">Add attributes to an element.</span></span>
- <span data-ttu-id="cb97c-112">要素のコンテンツをテキスト形式でシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-112">Serialize the contents of an element in text form.</span></span>

<span data-ttu-id="cb97c-113"><xref:System.Xml?displayProperty=nameWithType>、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> などの、<xref:System.Xml.Xsl.XslCompiledTransform> の他のクラスと相互運用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-113">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="cb97c-114">この記事では、<xref:System.Xml.Linq.XElement> クラスによって提供される機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-114">This article describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>

## <a name="construct-xml-trees"></a><span data-ttu-id="cb97c-115">XML ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="cb97c-115">Construct XML trees</span></span>

<span data-ttu-id="cb97c-116">次のようなさまざまな方法で XML ツリーを構築できます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-116">You can construct XML trees in different ways, including the following:</span></span>

- <span data-ttu-id="cb97c-117">コードで XML ツリーを構築できます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-117">You can construct an XML tree in code.</span></span> <span data-ttu-id="cb97c-118">詳細については、[XML ツリー](functional-construction.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb97c-118">For more information, see [XML trees](functional-construction.md).</span></span>
- <span data-ttu-id="cb97c-119"><xref:System.IO.TextReader>、テキスト ファイル、Web アドレス (URL) など、さまざまなソースから XML を解析できます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-119">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="cb97c-120">詳細については、[XML の解析](parse-string.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb97c-120">For more information, see [Parse XML](parse-string.md).</span></span>
- <span data-ttu-id="cb97c-121"><xref:System.Xml.XmlReader> を使用してツリーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-121">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="cb97c-122">詳細については、「<xref:System.Xml.Linq.XNode.ReadFrom%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb97c-122">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>
- <span data-ttu-id="cb97c-123"><xref:System.Xml.XmlWriter> にコンテンツを書き込むことができるモジュールがある場合は、<xref:System.Xml.Linq.XContainer.CreateWriter%2A> メソッドを使用してライターを作成し、このライターをモジュールに渡し、<xref:System.Xml.XmlWriter> に書き込まれたコンテンツを使用して XML ツリーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-123">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that's written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>

<span data-ttu-id="cb97c-124">ツリーを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-124">The following example creates a tree.</span></span> <span data-ttu-id="cb97c-125">C# バージョンでは、入れ子になった要素の作成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-125">The C# version uses nested element creations.</span></span> <span data-ttu-id="cb97c-126">Visual Basic でも同じ手法を使用できますが、この例では XML リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb97c-126">You can use the same technique in Visual Basic, but this example uses XML literals.</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

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

<span data-ttu-id="cb97c-127">また、次の例に示すように、LINQ to XML クエリを使用して XML ツリーを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-127">You can also use a LINQ to XML query to populate an XML tree, as shown in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="cb97c-128">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-128">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a><span data-ttu-id="cb97c-129">XML ツリーをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="cb97c-129">Serialize XML trees</span></span>

<span data-ttu-id="cb97c-130">XML ツリーは、<xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-130">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="cb97c-131">詳しくは、[XML ツリーのシリアル化](preserve-white-space-serializing.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb97c-131">For more information, see [Serialize XML trees](preserve-white-space-serializing.md).</span></span>

## <a name="retrieve-xml-data-via-axis-methods"></a><span data-ttu-id="cb97c-132">軸メソッドによる XML データの取得</span><span class="sxs-lookup"><span data-stu-id="cb97c-132">Retrieve XML data via axis methods</span></span>

<span data-ttu-id="cb97c-133">軸メソッドを使用すると、属性、子要素、子孫要素、および祖先要素を取得できます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-133">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="cb97c-134">LINQ to XML クエリは、軸メソッドに対して機能し、XML ツリーを操作して処理するための、柔軟で強力な複数の機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="cb97c-134">LINQ to XML queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>

<span data-ttu-id="cb97c-135">詳しくは、「[LINQ to XML 軸の概要](linq-xml-axes-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb97c-135">For more information, see [LINQ to XML axes overview](linq-xml-axes-overview.md).</span></span>

## <a name="query-xml-trees"></a><span data-ttu-id="cb97c-136">XML ツリーのクエリ</span><span class="sxs-lookup"><span data-stu-id="cb97c-136">Query XML trees</span></span>

<span data-ttu-id="cb97c-137">XML ツリーからデータを抽出する LINQ to XML クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-137">You can write LINQ to XML queries that extract data from an XML tree.</span></span>

<span data-ttu-id="cb97c-138">詳しくは、「[XML ツリーのクエリの概要](query-xml-trees-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cb97c-138">For more information, see [Query XML trees overview](query-xml-trees-overview.md).</span></span>

## <a name="modify-xml-trees"></a><span data-ttu-id="cb97c-139">XML ツリーを変更する</span><span class="sxs-lookup"><span data-stu-id="cb97c-139">Modify XML trees</span></span>

<span data-ttu-id="cb97c-140">要素を変更するには、そのコンテンツや属性を変更するなど、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="cb97c-140">You can modify an element in different ways, including changing its content or attributes.</span></span> <span data-ttu-id="cb97c-141">要素を親から削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="cb97c-141">You can also remove an element from its parent.</span></span>

<span data-ttu-id="cb97c-142">詳細については、[XML ツリーの変更](in-memory-xml-tree-modification-vs-functional-construction.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cb97c-142">For more information, see [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb97c-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb97c-143">See also</span></span>

- [<span data-ttu-id="cb97c-144">LINQ to XML プログラミングの概要</span><span class="sxs-lookup"><span data-stu-id="cb97c-144">LINQ to XML programming overview</span></span>](functional-vs-procedural-programming.md)
