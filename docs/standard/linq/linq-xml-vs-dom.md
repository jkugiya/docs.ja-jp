---
title: LINQ to XML およびDOM
description: LINQ to XML と DOM の間には大きな違いがあります。 LINQ to XML では、関数型構築と XML リテラルをサポートしています。これらは、ビルドする XML ツリーの構造をわかりやすくします。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 905fe1b47361e2b96c79bc56cb831b3cb298e4de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412021"
---
# <a name="linq-to-xml-vs-dom"></a><span data-ttu-id="6c588-104">LINQ to XML およびDOM</span><span class="sxs-lookup"><span data-stu-id="6c588-104">LINQ to XML vs. DOM</span></span>

<span data-ttu-id="6c588-105">この記事では、LINQ to XML と、現在主流の XML プログラミング API である W3C ドキュメント オブジェクト モデル (DOM) との主な違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="6c588-105">This article describes some key differences between LINQ to XML and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>

## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="6c588-106">XML ツリーを構築する新しい方法</span><span class="sxs-lookup"><span data-stu-id="6c588-106">New ways to construct XML trees</span></span>

<span data-ttu-id="6c588-107">W3C DOM では、XML ツリーをボトムアップ方式で作成します。つまり、ドキュメントを作成し、要素を作成して、要素をドキュメントに追加することによって作成します。</span><span class="sxs-lookup"><span data-stu-id="6c588-107">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>

<span data-ttu-id="6c588-108">たとえば、次の例は、Microsoft の DOM の実装である <xref:System.Xml.XmlDocument> を使用して XML ツリーを作成する典型的な方法を使用しています。</span><span class="sxs-lookup"><span data-stu-id="6c588-108">For example, the following example uses a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>.</span></span>

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
XmlElement phone1 = doc.CreateElement("Phone");
phone1.SetAttribute("Type", "Home");
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");
phone2.SetAttribute("Type", "Work");
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";
XmlElement city = doc.CreateElement("City");
city.InnerText = "Mercer Island";
XmlElement state = doc.CreateElement("State");
state.InnerText = "WA";
XmlElement postal = doc.CreateElement("Postal");
postal.InnerText = "68042";
XmlElement address = doc.CreateElement("Address");
address.AppendChild(street1);
address.AppendChild(city);
address.AppendChild(state);
address.AppendChild(postal);
XmlElement contact = doc.CreateElement("Contact");
contact.AppendChild(name);
contact.AppendChild(phone1);
contact.AppendChild(phone2);
contact.AppendChild(address);
XmlElement contacts = doc.CreateElement("Contacts");
contacts.AppendChild(contact);
doc.AppendChild(contacts);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
Dim phone1 As XmlElement = doc.CreateElement("Phone")
phone1.SetAttribute("Type", "Home")
phone1.InnerText = "206-555-0144"
Dim phone2 As XmlElement = doc.CreateElement("Phone")
phone2.SetAttribute("Type", "Work")
phone2.InnerText = "425-555-0145"
Dim street1 As XmlElement = doc.CreateElement("Street1")
street1.InnerText = "123 Main St"
Dim city As XmlElement = doc.CreateElement("City")
city.InnerText = "Mercer Island"
Dim state As XmlElement = doc.CreateElement("State")
state.InnerText = "WA"
Dim postal As XmlElement = doc.CreateElement("Postal")
postal.InnerText = "68042"
Dim address As XmlElement = doc.CreateElement("Address")
address.AppendChild(street1)
address.AppendChild(city)
address.AppendChild(state)
address.AppendChild(postal)
Dim contact As XmlElement = doc.CreateElement("Contact")
contact.AppendChild(name)
contact.AppendChild(phone1)
contact.AppendChild(phone2)
contact.AppendChild(address)
Dim contacts As XmlElement = doc.CreateElement("Contacts")
contacts.AppendChild(contact)
doc.AppendChild(contacts)
Console.WriteLine(doc.OuterXml)
```

<span data-ttu-id="6c588-109">このコーディング形式では、XML ツリーの構造は表示されません。</span><span class="sxs-lookup"><span data-stu-id="6c588-109">This style of coding hides the structure of the XML tree.</span></span> <span data-ttu-id="6c588-110">LINQ to XML では、構造をよりよく示す、"*関数型構築*" という別の方法もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6c588-110">LINQ to XML also supports an alternative approach, *functional construction*, that better shows the structure.</span></span> <span data-ttu-id="6c588-111">この方法は、<xref:System.Xml.Linq.XElement> と <xref:System.Xml.Linq.XAttribute> コンストラクターを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="6c588-111">This approach can be done with the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors.</span></span> <span data-ttu-id="6c588-112">Visual Basic では、XML リテラルで行うことも可能です。</span><span class="sxs-lookup"><span data-stu-id="6c588-112">In Visual Basic, it can also be done with XML literals.</span></span> <span data-ttu-id="6c588-113">次の例では、関数型構築を使用して同じ XML ツリーを構築する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6c588-113">This example demonstrates construction of the same XML tree using functional construction:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144",
                new XAttribute("Type", "Home")),
            new XElement("phone", "425-555-0145",
                new XAttribute("Type", "Work")),
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
Dim contacts = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="Home">206-555-0144</Phone>
            <Phone Type="Work">425-555-0145</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

<span data-ttu-id="6c588-114">このように、XML ツリーを構築するコードのインデントにより、基になる XML の構造が示されます。</span><span class="sxs-lookup"><span data-stu-id="6c588-114">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span> <span data-ttu-id="6c588-115">Visual Basic のバージョンでは、XML リテラルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="6c588-115">The Visual Basic version uses XML literals.</span></span>

<span data-ttu-id="6c588-116">詳細については、[XML ツリー](functional-construction.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c588-116">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="work-directly-with-xml-elements"></a><span data-ttu-id="6c588-117">XML 要素を直接操作する</span><span class="sxs-lookup"><span data-stu-id="6c588-117">Work directly with XML elements</span></span>

<span data-ttu-id="6c588-118">一般に、XML によるプログラミングで重視されるのは XML 要素であり、その属性が重要となる場合が多くあります。</span><span class="sxs-lookup"><span data-stu-id="6c588-118">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="6c588-119">LINQ to XML では、XML の要素と属性を直接操作できます。</span><span class="sxs-lookup"><span data-stu-id="6c588-119">In LINQ to XML, you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="6c588-120">たとえば、次のようなことが可能です。</span><span class="sxs-lookup"><span data-stu-id="6c588-120">For example, you can do the following:</span></span>

- <span data-ttu-id="6c588-121">ドキュメント オブジェクトを一切使用せずに XML 要素を作成する。</span><span class="sxs-lookup"><span data-stu-id="6c588-121">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="6c588-122">これにより、XML ツリーのフラグメントを操作する際のプログラミングが単純化されます。</span><span class="sxs-lookup"><span data-stu-id="6c588-122">This simplifies programming when you have to work with fragments of XML trees.</span></span>
- <span data-ttu-id="6c588-123">`T:System.Xml.Linq.XElement` オブジェクトを直接 XML ファイルから読み込む。</span><span class="sxs-lookup"><span data-stu-id="6c588-123">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>
- <span data-ttu-id="6c588-124">`T:System.Xml.Linq.XElement` オブジェクトをファイルやストリームにシリアル化する。</span><span class="sxs-lookup"><span data-stu-id="6c588-124">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>

<span data-ttu-id="6c588-125">これに対して、XML ドキュメントが XML ツリーの論理的コンテナーとして使用される W3C DOM では、</span><span class="sxs-lookup"><span data-stu-id="6c588-125">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="6c588-126">XML ノード (要素や属性を含む) は XML ドキュメントのコンテキストで作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c588-126">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="6c588-127">DOM で name 要素を作成するコードの断片を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6c588-127">Here is a fragment of code to create a name element in DOM:</span></span>

```csharp
XmlDocument doc = new XmlDocument();
XmlElement name = doc.CreateElement("Name");
name.InnerText = "Patrick Hines";
doc.AppendChild(name);
```

```vb
Dim doc As XmlDocument = New XmlDocument()
Dim name As XmlElement = doc.CreateElement("Name")
name.InnerText = "Patrick Hines"
doc.AppendChild(name)
```

<span data-ttu-id="6c588-128">要素を複数のドキュメントで使用する場合は、ノードをドキュメント間でインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c588-128">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> <span data-ttu-id="6c588-129">LINQ to XML では、こうした複雑さを回避できます。</span><span class="sxs-lookup"><span data-stu-id="6c588-129">LINQ to XML avoids this layer of complexity.</span></span>

<span data-ttu-id="6c588-130">LINQ to XML を使用する場合、<xref:System.Xml.Linq.XDocument> クラスを使用するのは、ドキュメントのルート レベルにコメントや処理命令を追加する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="6c588-130">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>

## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="6c588-131">名前と名前空間の処理の単純化</span><span class="sxs-lookup"><span data-stu-id="6c588-131">Simplified handling of names and namespaces</span></span>

<span data-ttu-id="6c588-132">一般に XML プログラミングでは、名前、名前空間、および名前空間プレフィックスの処理が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="6c588-132">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> <span data-ttu-id="6c588-133">LINQ to XML では、名前空間のプレフィックスを処理する必要がないため、名前と名前空間が単純になっています。</span><span class="sxs-lookup"><span data-stu-id="6c588-133">LINQ to XML simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="6c588-134">必要に応じて名前空間プレフィックスを制御することはできますが、</span><span class="sxs-lookup"><span data-stu-id="6c588-134">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="6c588-135">明示的に制御しないようにすることもできます。その場合、LINQ to XML がシリアル中に名前空間プレフィックスを必要に応じて割り当てます。必要ない場合は、既定の名前空間を使用してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="6c588-135">But if you decide to not explicitly control namespace prefixes, LINQ to XML will assign namespace prefixes during serialization if they're required, or will serialize using default namespaces if they're not.</span></span> <span data-ttu-id="6c588-136">既定の名前空間が使用された場合は、結果のドキュメントには名前空間プレフィックスは含まれません。</span><span class="sxs-lookup"><span data-stu-id="6c588-136">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="6c588-137">詳細については、[名前空間の概要](namespaces-overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c588-137">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="6c588-138">DOM にはその他に、ノードの名前を変更できない問題があります。</span><span class="sxs-lookup"><span data-stu-id="6c588-138">Another problem with the DOM is that it doesn't let you change the name of a node.</span></span> <span data-ttu-id="6c588-139">ノード名の変更が必要な場合は、新しいノードを作成し、そこにすべての子ノードをコピーする必要があります。この場合、元のノード固有の特性は失われます。</span><span class="sxs-lookup"><span data-stu-id="6c588-139">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> <span data-ttu-id="6c588-140">LINQ to XML では、この問題を回避するために、ノードに <xref:System.Xml.Linq.XName> プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="6c588-140">LINQ to XML avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>

## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="6c588-141">XML を読み込む静的メソッドのサポート</span><span class="sxs-lookup"><span data-stu-id="6c588-141">Static method support for loading XML</span></span>

<span data-ttu-id="6c588-142">LINQ to XML では、インスタンス メソッドではなく静的メソッドを使用して XML を読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="6c588-142">LINQ to XML lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="6c588-143">これにより、読み込みと解析が簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="6c588-143">This simplifies loading and parsing.</span></span> <span data-ttu-id="6c588-144">詳細については、[ファイルから XML を読み込む方法](load-xml-file.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c588-144">For more information, see [How to load XML from a file](load-xml-file.md).</span></span>

## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="6c588-145">DTD コンストラクトのサポートの削除</span><span class="sxs-lookup"><span data-stu-id="6c588-145">Removal of support for DTD constructs</span></span>

<span data-ttu-id="6c588-146">LINQ to XML では、XML のプログラミングをさらに簡単にするために、エンティティとエンティティ参照のサポートが削除されています。</span><span class="sxs-lookup"><span data-stu-id="6c588-146">LINQ to XML further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="6c588-147">エンティティの管理は複雑で、ほとんど利用されていません。</span><span class="sxs-lookup"><span data-stu-id="6c588-147">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="6c588-148">これらのサポートを削除することにより、パフォーマンスが向上し、プログラミング インターフェイスが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="6c588-148">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="6c588-149">LINQ to XML ツリーが設定されると、すべての DTD エンティティが展開されます。</span><span class="sxs-lookup"><span data-stu-id="6c588-149">When a LINQ to XML tree is populated, all DTD entities are expanded.</span></span>

## <a name="support-for-fragments"></a><span data-ttu-id="6c588-150">フラグメントのサポート</span><span class="sxs-lookup"><span data-stu-id="6c588-150">Support for fragments</span></span>

<span data-ttu-id="6c588-151">LINQ to XML には、`XmlDocumentFragment` クラスに相当するものがありません。</span><span class="sxs-lookup"><span data-stu-id="6c588-151">LINQ to XML doesn't provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="6c588-152">ただし、`XmlDocumentFragment` の概念は、多くの場合、<xref:System.Xml.Linq.XNode> の <xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> として型指定したクエリの結果で処理できます。</span><span class="sxs-lookup"><span data-stu-id="6c588-152">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that's typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>

## <a name="support-for-xpathnavigator"></a><span data-ttu-id="6c588-153">XPathNavigator のサポート</span><span class="sxs-lookup"><span data-stu-id="6c588-153">Support for XPathNavigator</span></span>

<span data-ttu-id="6c588-154">LINQ to XML では、<xref:System.Xml.XPath?displayProperty=nameWithType> 名前空間の拡張メソッドで <xref:System.Xml.XPath.XPathNavigator> をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6c588-154">LINQ to XML provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6c588-155">詳細については、「<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c588-155">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>

## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="6c588-156">空白とインデントのサポート</span><span class="sxs-lookup"><span data-stu-id="6c588-156">Support for white space and indentation</span></span>

<span data-ttu-id="6c588-157">LINQ to XML での空白の処理は、DOM よりも単純です。</span><span class="sxs-lookup"><span data-stu-id="6c588-157">LINQ to XML handles white space more simply than the DOM.</span></span>

<span data-ttu-id="6c588-158">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="6c588-158">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), do some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="6c588-159">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="6c588-159">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="6c588-160">これが LINQ to XML の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="6c588-160">This is the default behavior for LINQ to XML.</span></span>

<span data-ttu-id="6c588-161">もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="6c588-161">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="6c588-162">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c588-162">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="6c588-163">LINQ to XML では、次の方法でこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="6c588-163">In LINQ to XML, you can do this by:</span></span>

- <span data-ttu-id="6c588-164">XML の読み込み時または解析時に空白を維持する。</span><span class="sxs-lookup"><span data-stu-id="6c588-164">Preserving white space when you load or parse the XML.</span></span>
- <span data-ttu-id="6c588-165">XML をシリアル化するときに書式設定を無効にする。</span><span class="sxs-lookup"><span data-stu-id="6c588-165">Disabling formatting when you serialize the XML.</span></span>

<span data-ttu-id="6c588-166">LINQ to XML で空白は、DOM にある専用の <xref:System.Xml.XmlNodeType.Whitespace> ノード型ではなく、<xref:System.Xml.Linq.XText> ノードとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="6c588-166">LINQ to XML stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>

## <a name="support-for-annotations"></a><span data-ttu-id="6c588-167">注釈のサポート</span><span class="sxs-lookup"><span data-stu-id="6c588-167">Support for annotations</span></span>

<span data-ttu-id="6c588-168">LINQ to XML 要素は、拡張可能な注釈のセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6c588-168">LINQ to XML elements support an extensible set of annotations.</span></span> <span data-ttu-id="6c588-169">このサポートは、スキーマの情報、要素が UI にバインドされているかどうかの情報、またはアプリケーション固有のその他の情報など、要素に関するさまざまな情報を追跡する場合に利用できます。</span><span class="sxs-lookup"><span data-stu-id="6c588-169">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="6c588-170">詳細については、[LINQ to XML の注釈](linq-xml-annotations.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c588-170">For more information, see [LINQ to XML annotations](linq-xml-annotations.md).</span></span>

## <a name="support-for-schema-information"></a><span data-ttu-id="6c588-171">スキーマ情報のサポート</span><span class="sxs-lookup"><span data-stu-id="6c588-171">Support for schema information</span></span>

<span data-ttu-id="6c588-172">LINQ to XML では、<xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間の拡張メソッドで XSD 検証をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="6c588-172">LINQ to XML provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="6c588-173">これにより、XML ツリーが XSD に準拠しているかどうかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="6c588-173">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="6c588-174">また、スキーマ検証後の情報セット (PSVI) を使用して XML ツリーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="6c588-174">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="6c588-175">詳細については、「[XSD を使用して検証する方法](validate-xsd.md)」および「<xref:System.Xml.Schema.Extensions>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c588-175">For more information, see [How to validate using XSD](validate-xsd.md) and <xref:System.Xml.Schema.Extensions>.</span></span>

## <a name="see-also"></a><span data-ttu-id="6c588-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c588-176">See also</span></span>

- [<span data-ttu-id="6c588-177">LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="6c588-177">LINQ to XML overview</span></span>](linq-xml-overview.md)
