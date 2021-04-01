---
title: XDocument クラスの概要
description: LINQ to XML XDocument クラスには、有効な XML ドキュメントに必要な情報が含まれています。 多くの場合、XDocument オブジェクトの機能は必要なく、代わりに XElement オブジェクトを使用できます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411954"
---
# <a name="xdocument-class-overview"></a><span data-ttu-id="74e8f-104">XDocument クラスの概要</span><span class="sxs-lookup"><span data-stu-id="74e8f-104">XDocument class overview</span></span>

<span data-ttu-id="74e8f-105"><xref:System.Xml.Linq.XDocument> クラスには、XML 宣言、処理命令、コメントなど、有効な XML ドキュメントに必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="74e8f-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document, which includes an XML declaration, processing instructions, and comments.</span></span>

<span data-ttu-id="74e8f-106"><xref:System.Xml.Linq.XDocument> クラスが提供する特定の機能が必要な場合は、<xref:System.Xml.Linq.XDocument> オブジェクトを作成するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="74e8f-106">You only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="74e8f-107">多くの場合、<xref:System.Xml.Linq.XElement> を直接操作できます。</span><span class="sxs-lookup"><span data-stu-id="74e8f-107">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="74e8f-108"><xref:System.Xml.Linq.XElement> を直接操作するのは、比較的単純なプログラミング モデルです。</span><span class="sxs-lookup"><span data-stu-id="74e8f-108">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>

<span data-ttu-id="74e8f-109"><xref:System.Xml.Linq.XDocument> は <xref:System.Xml.Linq.XContainer> から派生するため、子ノードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="74e8f-109"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>, so it can contain child nodes.</span></span> <span data-ttu-id="74e8f-110">ただし、<xref:System.Xml.Linq.XDocument> オブジェクトに格納できる子 <xref:System.Xml.Linq.XElement> ノードは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="74e8f-110">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="74e8f-111">これは、XML ドキュメントにルート要素を 1 つしか持てないという XML 標準を反映しています。</span><span class="sxs-lookup"><span data-stu-id="74e8f-111">This reflects the XML standard that there can be only one root element in an XML document.</span></span>

## <a name="components-of-xdocument"></a><span data-ttu-id="74e8f-112">XDocument のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="74e8f-112">Components of XDocument</span></span>

<span data-ttu-id="74e8f-113"><xref:System.Xml.Linq.XDocument> には、次の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="74e8f-113">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>

- <span data-ttu-id="74e8f-114">1 つの <xref:System.Xml.Linq.XDeclaration> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="74e8f-114">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="74e8f-115"><xref:System.Xml.Linq.XDeclaration> では、XML 宣言の関連部分である XML バージョン、ドキュメントのエンコード、および XML ドキュメントがスタンドアロンかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="74e8f-115"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is standalone.</span></span>
- <span data-ttu-id="74e8f-116">1 つの <xref:System.Xml.Linq.XElement> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="74e8f-116">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="74e8f-117">このオブジェクトは XML ドキュメントのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="74e8f-117">This object is the root node of the XML document.</span></span>
- <span data-ttu-id="74e8f-118">任意の数の <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="74e8f-118">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="74e8f-119">処理命令は、XML を処理するアプリケーションに情報を伝達します。</span><span class="sxs-lookup"><span data-stu-id="74e8f-119">A processing instruction communicates information to an application that processes the XML.</span></span>
- <span data-ttu-id="74e8f-120">任意の数の <xref:System.Xml.Linq.XComment> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="74e8f-120">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="74e8f-121">コメントは、ルート要素の兄弟になります。</span><span class="sxs-lookup"><span data-stu-id="74e8f-121">The comments will be siblings to the root element.</span></span> <span data-ttu-id="74e8f-122">XML ドキュメントをコメントで始めることは無効であるため、<xref:System.Xml.Linq.XComment> オブジェクトをリストの最初の引数にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="74e8f-122">The <xref:System.Xml.Linq.XComment> object can't be the first argument in the list, because it's not valid for an XML document to start with a comment.</span></span>
- <span data-ttu-id="74e8f-123">DTD 用の 1 つの <xref:System.Xml.Linq.XDocumentType>。</span><span class="sxs-lookup"><span data-stu-id="74e8f-123">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>

<span data-ttu-id="74e8f-124"><xref:System.Xml.Linq.XDocument> をシリアル化すると、`XDocument.Declaration` が `null` である場合でも、作成者が `Writer.Settings.OmitXmlDeclaration` を `false` (既定値) に設定していれば、出力には XML 宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="74e8f-124">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>

<span data-ttu-id="74e8f-125">既定では、LINQ to XML によってバージョンが "1.0" に、エンコードが "UTF-8" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="74e8f-125">By default, LINQ to XML sets the version to "1.0", and sets the encoding to "utf-8".</span></span>

## <a name="use-xelement-without-xdocument"></a><span data-ttu-id="74e8f-126">XDocument なしで XElement を使用する</span><span class="sxs-lookup"><span data-stu-id="74e8f-126">Use XElement without XDocument</span></span>

<span data-ttu-id="74e8f-127">既に説明したように、<xref:System.Xml.Linq.XElement> クラスは LINQ to XML プログラミング インターフェイスのメイン クラスです。</span><span class="sxs-lookup"><span data-stu-id="74e8f-127">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the LINQ to XML programming interface.</span></span> <span data-ttu-id="74e8f-128">多くの場合、アプリケーションはドキュメントの作成を必要としません。</span><span class="sxs-lookup"><span data-stu-id="74e8f-128">In many cases, your application won't require that you create a document.</span></span> <span data-ttu-id="74e8f-129"><xref:System.Xml.Linq.XElement> クラスを使用すると次のことが可能です。</span><span class="sxs-lookup"><span data-stu-id="74e8f-129">By using the <xref:System.Xml.Linq.XElement> class, you can:</span></span>

- <span data-ttu-id="74e8f-130">XML ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="74e8f-130">Create an XML tree.</span></span>
- <span data-ttu-id="74e8f-131">それに他の XML ツリーを追加します。</span><span class="sxs-lookup"><span data-stu-id="74e8f-131">Add other XML trees to it.</span></span>
- <span data-ttu-id="74e8f-132">XML ツリーを変更します。</span><span class="sxs-lookup"><span data-stu-id="74e8f-132">Modify the XML tree.</span></span>
- <span data-ttu-id="74e8f-133">ファイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="74e8f-133">Save it.</span></span>

## <a name="use-xdocument"></a><span data-ttu-id="74e8f-134">XDocument を使用する</span><span class="sxs-lookup"><span data-stu-id="74e8f-134">Use XDocument</span></span>

<span data-ttu-id="74e8f-135"><xref:System.Xml.Linq.XDocument> を構築するには、<xref:System.Xml.Linq.XElement> オブジェクトを構築する場合と同様に関数型構築を使用します。</span><span class="sxs-lookup"><span data-stu-id="74e8f-135">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="74e8f-136">次の例は、<xref:System.Xml.Linq.XDocument> オブジェクトおよび関連する格納されるオブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="74e8f-136">The following example creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>

```csharp
XDocument d = new XDocument(
    new XComment("This is a comment."),
    new XProcessingInstruction("xml-stylesheet",
        "href='mystyle.css' title='Compact' type='text/css'"),
    new XElement("Pubs",
        new XElement("Book",
            new XElement("Title", "Artifacts of Roman Civilization"),
            new XElement("Author", "Moreno, Jordao")
        ),
        new XElement("Book",
            new XElement("Title", "Midieval Tools and Implements"),
            new XElement("Author", "Gazit, Inbar")
        )
    ),
    new XComment("This is another comment.")
);
d.Declaration = new XDeclaration("1.0", "utf-8", "true");
Console.WriteLine(d);

d.Save("test.xml");
```

```vb
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>
                       <!--This is a comment.-->
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
                       <Pubs>
                           <Book>
                               <Title>Artifacts of Roman Civilization</Title>
                               <Author>Moreno, Jordao</Author>
                           </Book>
                           <Book>
                               <Title>Midieval Tools and Implements</Title>
                               <Author>Gazit, Inbar</Author>
                           </Book>
                       </Pubs>
                       <!--This is another comment.-->
doc.Save("test.xml")
```

<span data-ttu-id="74e8f-137">この例では、test.xml に次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="74e8f-137">The example produces this output in test.xml:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--This is a comment.-->
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
<Pubs>
  <Book>
    <Title>Artifacts of Roman Civilization</Title>
    <Author>Moreno, Jordao</Author>
  </Book>
  <Book>
    <Title>Midieval Tools and Implements</Title>
    <Author>Gazit, Inbar</Author>
  </Book>
</Pubs>
<!--This is another comment.-->
```

## <a name="see-also"></a><span data-ttu-id="74e8f-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="74e8f-138">See also</span></span>

- [<span data-ttu-id="74e8f-139">LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="74e8f-139">LINQ to XML overview</span></span>](linq-xml-overview.md)
