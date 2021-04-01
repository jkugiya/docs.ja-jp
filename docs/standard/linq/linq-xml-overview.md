---
title: 概要 - LINQ to XML
description: LINQ to XML には、.NET 機能に基づくメモリ内 XML プログラミング インターフェイスが用意されており、更新された DOM API と同等の機能を備えています。
ms.date: 10/30/2018
dev_langs:
- csharp
- vb
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: f805d757c9059a07988c6cb16e41ffed017fe853
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412027"
---
# <a name="linq-to-xml-overview"></a><span data-ttu-id="b71de-103">LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="b71de-103">LINQ to XML overview</span></span>

<span data-ttu-id="b71de-104">LINQ to XML には、.NET 統合言語クエリ (LINQ) フレームワークを利用したメモリ内 XML プログラミング インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b71de-104">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="b71de-105">LINQ to XML では、.NET 機能を利用しており、更新および再設計されたドキュメント オブジェクト モデル (DOM) XML プログラミング インターフェイスと同等の機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="b71de-105">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="b71de-106">XML は、多くのコンテキストでデータを書式設定する方法として広く採用されてきました。</span><span class="sxs-lookup"><span data-stu-id="b71de-106">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="b71de-107">たとえば、Web、構成ファイル、Microsoft Office Word ファイル、データベースで XML が使用されています。</span><span class="sxs-lookup"><span data-stu-id="b71de-107">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

<span data-ttu-id="b71de-108">LINQ to XML は、XML によるプログラミングのために再設計された最新の方法です。</span><span class="sxs-lookup"><span data-stu-id="b71de-108">LINQ to XML is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="b71de-109">ドキュメント オブジェクト モデル (DOM) のインメモリでのドキュメント変更機能を提供し、LINQ クエリ式をサポートします。</span><span class="sxs-lookup"><span data-stu-id="b71de-109">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="b71de-110">このクエリ式は、XPath と構文は異なりますが、機能が似ています。</span><span class="sxs-lookup"><span data-stu-id="b71de-110">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="b71de-111">LINQ to XML の開発者</span><span class="sxs-lookup"><span data-stu-id="b71de-111">LINQ to XML developers</span></span>

<span data-ttu-id="b71de-112">LINQ to XML は、さまざまな開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="b71de-112">LINQ to XML targets a variety of developers.</span></span> <span data-ttu-id="b71de-113">何らかの処理を行うだけの平均的な開発者にとっては、LINQ to XML を使用すると、SQL と同じようにクエリを作成できるので、XML の操作がより簡単になります。</span><span class="sxs-lookup"><span data-stu-id="b71de-113">For an average developer who just wants to get something done, LINQ to XML makes XML easier by providing a query experience that's similar to SQL.</span></span> <span data-ttu-id="b71de-114">プログラマは、短時間の学習で簡潔かつ強力なクエリを、選択したプログラミング言語で記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b71de-114">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="b71de-115">熟練した開発者は、LINQ to XML を使用することで、生産性を大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="b71de-115">Professional developers can use LINQ to XML to greatly increase their productivity.</span></span> <span data-ttu-id="b71de-116">LINQ to XML を使用すると、表現性がさらに優れ、より簡潔で強力なコードを、数を抑えて記述できます。</span><span class="sxs-lookup"><span data-stu-id="b71de-116">With LINQ to XML, they can write less code that's more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="b71de-117">また、同時に複数のデータ ドメインからクエリ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b71de-117">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="linq-to-xml-is-an-xml-programming-interface"></a><span data-ttu-id="b71de-118">XML プログラミング インターフェイスとしての LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="b71de-118">LINQ to XML is an XML programming interface</span></span>

<span data-ttu-id="b71de-119">LINQ to XML は、.NET プログラミング言語内で XML を操作できるようにする、LINQ に対応したメモリ内 XML プログラミング インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b71de-119">LINQ to XML is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

<span data-ttu-id="b71de-120">LINQ to XML は、XML ドキュメントをメモリに読み込むという点で、ドキュメント オブジェクト モデル (DOM) に似ています。</span><span class="sxs-lookup"><span data-stu-id="b71de-120">LINQ to XML is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="b71de-121">ドキュメントに対するクエリや変更を行うことができ、変更したドキュメントをファイルに保存したり、シリアル化してインターネット経由で送信したりできます。</span><span class="sxs-lookup"><span data-stu-id="b71de-121">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="b71de-122">ただし、LINQ to XML は DOM とは異なります。</span><span class="sxs-lookup"><span data-stu-id="b71de-122">However, LINQ to XML differs from DOM:</span></span>

- <span data-ttu-id="b71de-123">より軽量で使いやすい、新しいオブジェクト モデルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b71de-123">It provides a new object model that's lighter weight and easier to work with.</span></span>
- <span data-ttu-id="b71de-124">C# と Visual Basic の言語機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="b71de-124">It takes advantage of language features in C# and Visual Basic.</span></span>

<span data-ttu-id="b71de-125">LINQ to XML の最も重要な利点は、統合言語クエリ (LINQ) と統合されている点です。</span><span class="sxs-lookup"><span data-stu-id="b71de-125">The most important advantage of LINQ to XML is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="b71de-126">この統合により、メモリ内の XML ドキュメントに対するクエリを記述して、要素および属性のコレクションを取得できます。</span><span class="sxs-lookup"><span data-stu-id="b71de-126">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="b71de-127">LINQ to XML のクエリ機能は、構文については異なりますが、XPath および XQuery と機能面で同等です。</span><span class="sxs-lookup"><span data-stu-id="b71de-127">The query capability of LINQ to XML is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="b71de-128">LINQ に C# と Visual Basic が統合されていることで、厳密な型指定とコンパイル時のチェックが可能となり、デバッガー サポートが強化されます。</span><span class="sxs-lookup"><span data-stu-id="b71de-128">The integration of LINQ in C# and Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="b71de-129">LINQ to XML のもう 1 つの利点は、クエリの結果を <xref:System.Xml.Linq.XElement> と <xref:System.Xml.Linq.XAttribute> の各オブジェクト コンストラクターに対するパラメーターとして使用できるので、強力な方法で XML ツリーを作成できるという点です。</span><span class="sxs-lookup"><span data-stu-id="b71de-129">Another advantage of LINQ to XML is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="b71de-130">*関数型構築* と呼ばれるこの方法では、開発者が XML ツリーの構造を簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="b71de-130">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="b71de-131">たとえば、[サンプル XML ファイル (一般的な発注書)](sample-xml-file-typical-purchase-order.md) に関する記事で説明されているような、一般的な XML 発注書があるとします。</span><span class="sxs-lookup"><span data-stu-id="b71de-131">For example, you might have a typical XML purchase order as described in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span> <span data-ttu-id="b71de-132">LINQ to XML を使用すると、発注書に記載されたすべての品目要素の部品番号属性を、次のクエリを実行して取得することができます。</span><span class="sxs-lookup"><span data-stu-id="b71de-132">By using LINQ to XML, you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
    From item In purchaseOrder...<Item> _
    Select item.@PartNumber
```

<span data-ttu-id="b71de-133">C# では、これをメソッド構文形式で書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="b71de-133">In C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="b71de-134">もう 1 つの例として、金額が $100 を超える品目を部品番号順に並べた一覧が必要であるとします。</span><span class="sxs-lookup"><span data-stu-id="b71de-134">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="b71de-135">この情報を取得するには、次のクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="b71de-135">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
From item In purchaseOrder...<Item> _
Where (item.<Quantity>.Value * _
       item.<USPrice>.Value) > 100 _
Order By item.<PartNumber>.Value _
Select item
```

<span data-ttu-id="b71de-136">ここでも、C# では、これをメソッド構文形式で書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="b71de-136">Again, in C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="b71de-137">これらの LINQ 機能に加え、LINQ to XML では、XML プログラミング インターフェイスが機能強化されています。</span><span class="sxs-lookup"><span data-stu-id="b71de-137">In addition to these LINQ capabilities, LINQ to XML provides an improved XML programming interface.</span></span> <span data-ttu-id="b71de-138">LINQ to XML を使用すると、次の操作が可能です。</span><span class="sxs-lookup"><span data-stu-id="b71de-138">Using LINQ to XML, you can:</span></span>

- <span data-ttu-id="b71de-139">[ファイル](load-xml-file.md)または[ストリーム](stream-xml-fragments-xmlreader.md)からの XML の読み込み</span><span class="sxs-lookup"><span data-stu-id="b71de-139">Load XML from [files](load-xml-file.md) or [streams](stream-xml-fragments-xmlreader.md).</span></span>
- <span data-ttu-id="b71de-140">ファイルまたはストリームへの XML のシリアル化</span><span class="sxs-lookup"><span data-stu-id="b71de-140">Serialize XML to files or streams.</span></span>
- <span data-ttu-id="b71de-141">関数型構築を使用した XML の新規作成</span><span class="sxs-lookup"><span data-stu-id="b71de-141">Create XML from scratch by using functional construction.</span></span>
- <span data-ttu-id="b71de-142">XPath に類似した軸を使用した XML に対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="b71de-142">Query XML using XPath-like axes.</span></span>
- <span data-ttu-id="b71de-143"><xref:System.Xml.Linq.XContainer.Add%2A>、<xref:System.Xml.Linq.XNode.Remove%2A>、<xref:System.Xml.Linq.XNode.ReplaceWith%2A>、<xref:System.Xml.Linq.XElement.SetValue%2A> などのメソッドを使用した、メモリ内の XML ツリーの操作</span><span class="sxs-lookup"><span data-stu-id="b71de-143">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>
- <span data-ttu-id="b71de-144">XSD を使用した XML ツリーの検証</span><span class="sxs-lookup"><span data-stu-id="b71de-144">Validate XML trees using XSD.</span></span>
- <span data-ttu-id="b71de-145">上記の機能を組み合わせて使用した XML ツリーの構造の変換</span><span class="sxs-lookup"><span data-stu-id="b71de-145">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="create-xml-trees"></a><span data-ttu-id="b71de-146">XML ツリーを作成する</span><span class="sxs-lookup"><span data-stu-id="b71de-146">Create XML trees</span></span>

<span data-ttu-id="b71de-147">LINQ to XML でのプログラミングで最も重要な利点の 1 つは、XML ツリーを簡単に作成できるという点です。</span><span class="sxs-lookup"><span data-stu-id="b71de-147">One of the most significant advantages of programming with LINQ to XML is that it's easy to create XML trees.</span></span> <span data-ttu-id="b71de-148">たとえば、小さな XML ツリーを作成するには、次のようにコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="b71de-148">For example, to create a small XML tree, you can write code as follows:</span></span>

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

> [!NOTE]
> <span data-ttu-id="b71de-149">この例の Visual Basic バージョンでは、XML リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="b71de-149">The Visual Basic version of the example uses XML literals.</span></span> <span data-ttu-id="b71de-150">C# バージョンのように、Visual Basic で <xref:System.Xml.Linq.XElement> を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b71de-150">You can also use <xref:System.Xml.Linq.XElement> in Visual Basic, as in the C# version.</span></span>

<span data-ttu-id="b71de-151">詳細については、[XML ツリー](functional-construction.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b71de-151">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b71de-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="b71de-152">See also</span></span>

- [<span data-ttu-id="b71de-153">参照</span><span class="sxs-lookup"><span data-stu-id="b71de-153">Reference</span></span>](reference.md)
- [<span data-ttu-id="b71de-154">LINQ to XML およびDOM</span><span class="sxs-lookup"><span data-stu-id="b71de-154">LINQ to XML vs. DOM</span></span>](linq-xml-vs-dom.md)
- [<span data-ttu-id="b71de-155">LINQ to XML とその他の XML テクノロジ</span><span class="sxs-lookup"><span data-stu-id="b71de-155">LINQ to XML vs. other XML technologies</span></span>](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
