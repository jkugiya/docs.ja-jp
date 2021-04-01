---
title: LINQ to XML クラスの概要
description: この記事では、LINQ to XML クラスの一覧を示し、各クラスついて説明します。
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 83258425b464d8547def5cce6a3e8da19ef21966
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412026"
---
# <a name="linq-to-xml-classes-overview"></a><span data-ttu-id="d33ea-103">LINQ to XML クラスの概要</span><span class="sxs-lookup"><span data-stu-id="d33ea-103">LINQ to XML classes overview</span></span>

<span data-ttu-id="d33ea-104">このトピックでは、<xref:System.Xml.Linq> 名前空間内の LINQ to XML クラスの一覧を示し、各クラスについて簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-104">This article provides a list of the LINQ to XML classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>

## <a name="linq-to-xml-classes"></a><span data-ttu-id="d33ea-105">LINQ to XML クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-105">LINQ to XML classes</span></span>

### <a name="xattribute-class"></a><span data-ttu-id="d33ea-106">XAttribute クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-106">XAttribute class</span></span>

<span data-ttu-id="d33ea-107"><xref:System.Xml.Linq.XAttribute> は XML 属性を表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-107"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="d33ea-108">詳細および例については、「[XAttribute クラスの概要](xattribute-class-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d33ea-108">For detailed information and examples, see [XAttribute class overview](xattribute-class-overview.md).</span></span>

### <a name="xcdata-class"></a><span data-ttu-id="d33ea-109">XCData クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-109">XCData class</span></span>

<span data-ttu-id="d33ea-110"><xref:System.Xml.Linq.XCData> は、CDATA テキスト ノードを表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-110"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>

### <a name="xcomment-class"></a><span data-ttu-id="d33ea-111">XComment クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-111">XComment class</span></span>

<span data-ttu-id="d33ea-112"><xref:System.Xml.Linq.XComment> は XML コメントを表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-112"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>

### <a name="xcontainer-class"></a><span data-ttu-id="d33ea-113">XContainer クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-113">XContainer class</span></span>

<span data-ttu-id="d33ea-114"><xref:System.Xml.Linq.XContainer> は、子ノードを持つ可能性があるすべてのノードの抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="d33ea-114"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="d33ea-115"><xref:System.Xml.Linq.XContainer> からは次のクラスが派生します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-115">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XDocument>

### <a name="xdeclaration-class"></a><span data-ttu-id="d33ea-116">XDeclaration クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-116">XDeclaration class</span></span>

<span data-ttu-id="d33ea-117"><xref:System.Xml.Linq.XDeclaration> は、XML 宣言を表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-117"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="d33ea-118">XML 宣言は、ドキュメントの XML バージョンとエンコーディングを宣言するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d33ea-118">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="d33ea-119">また、XML 宣言では、XML ドキュメントがスタンドアロンかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-119">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="d33ea-120">ドキュメントがスタンドアロンである場合、外部 DTD、または内部サブセットから参照されている外部パラメーター エンティティのいずれかに外部マークアップ宣言がありません。</span><span class="sxs-lookup"><span data-stu-id="d33ea-120">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>

### <a name="xdocument-class"></a><span data-ttu-id="d33ea-121">XDocument クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-121">XDocument class</span></span>

<span data-ttu-id="d33ea-122"><xref:System.Xml.Linq.XDocument> は、XML ドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-122"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="d33ea-123">詳細および例については、「[XDocument クラスの概要](xdocument-class-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d33ea-123">For detailed information and examples, see [XDocument class overview](xdocument-class-overview.md).</span></span>

### <a name="xdocumenttype-class"></a><span data-ttu-id="d33ea-124">XDocumentType クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-124">XDocumentType class</span></span>

<span data-ttu-id="d33ea-125"><xref:System.Xml.Linq.XDocumentType> は、XML ドキュメント型定義 (DTD) を表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-125"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>

### <a name="xelement-class"></a><span data-ttu-id="d33ea-126">XElement クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-126">XElement class</span></span>

<span data-ttu-id="d33ea-127"><xref:System.Xml.Linq.XElement> は、XML 要素を表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-127"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="d33ea-128">詳細および例については、「[XElement クラスの概要](xelement-class-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d33ea-128">For detailed information and examples, see [XElement class overview](xelement-class-overview.md).</span></span>

### <a name="xname-class"></a><span data-ttu-id="d33ea-129">XName クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-129">XName class</span></span>

<span data-ttu-id="d33ea-130"><xref:System.Xml.Linq.XName> は、要素の名前 (<xref:System.Xml.Linq.XElement>) および属性 (<xref:System.Xml.Linq.XAttribute>) を表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-130"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="d33ea-131">詳細および例については、「[XDocument クラスの概要](xdocument-class-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d33ea-131">For detailed information and examples, see [XDocument class overview](xdocument-class-overview.md).</span></span>

<span data-ttu-id="d33ea-132">LINQ to XML は、XML 名ができる限り単純になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d33ea-132">LINQ to XML is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="d33ea-133">XML 名は、その複雑さのために XML の高度な領域として扱われることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="d33ea-133">Due to their complexity, XML names are often considered to be an advanced article in XML.</span></span> <span data-ttu-id="d33ea-134">この複雑さの原因として考えられるのは、開発者がプログラミングで通常使用する名前空間ではなく、名前空間プレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="d33ea-134">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="d33ea-135">名前空間プレフィックスは、XML を入力するときに必要なキー ストロークを減らしたり、XML を読みやすくしたりするために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d33ea-135">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="d33ea-136">しかし、プレフィックスは、完全な XML 名前空間を使用するためのショートカットに過ぎず、必要ない場合がほとんどです。</span><span class="sxs-lookup"><span data-stu-id="d33ea-136">However, prefixes are often just a shortcut for using the full XML namespace, and aren't required in most cases.</span></span> <span data-ttu-id="d33ea-137">LINQ to XML では、すべてのプレフィックスを、対応する XML 名前空間に解決することで、XML 名を簡素化しています。</span><span class="sxs-lookup"><span data-stu-id="d33ea-137">LINQ to XML simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="d33ea-138">プレフィックスが必要であれば、<xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> メソッドで使用できます。</span><span class="sxs-lookup"><span data-stu-id="d33ea-138">Prefixes are available, if they're required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>

<span data-ttu-id="d33ea-139">必要に応じて名前空間プレフィックスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="d33ea-139">it's possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="d33ea-140">XSLT や XAML などの他の XML システムを使用する場合は、状況によって名前空間プレフィックスを制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d33ea-140">In some circumstances, if you're working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="d33ea-141">たとえば、名前空間プレフィックスを使用し、XSLT スタイルシートに組み込まれている XPath 式がある場合は、XPath 式内で使用しているものと一致する名前空間プレフィックスで XML ドキュメントがシリアル化されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d33ea-141">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>

### <a name="xnamespace-class"></a><span data-ttu-id="d33ea-142">XNamespace クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-142">XNamespace class</span></span>

<span data-ttu-id="d33ea-143"><xref:System.Xml.Linq.XNamespace> は、<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XAttribute> の名前空間を表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-143"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="d33ea-144">名前空間は、<xref:System.Xml.Linq.XName> のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="d33ea-144">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>

### <a name="xnode-class"></a><span data-ttu-id="d33ea-145">XNode クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-145">XNode class</span></span>

<span data-ttu-id="d33ea-146"><xref:System.Xml.Linq.XNode> は、XML ツリーのノードを表す抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="d33ea-146"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="d33ea-147"><xref:System.Xml.Linq.XNode> からは次のクラスが派生します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-147">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>

- <xref:System.Xml.Linq.XText>
- <xref:System.Xml.Linq.XContainer>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XDocumentType>

### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="d33ea-148">XNodeDocumentOrderComparer クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-148">XNodeDocumentOrderComparer class</span></span>

<span data-ttu-id="d33ea-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> には、ノードをドキュメント順で比較する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d33ea-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>

### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="d33ea-150">XNodeEqualityComparer クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-150">XNodeEqualityComparer class</span></span>

<span data-ttu-id="d33ea-151"><xref:System.Xml.Linq.XNodeEqualityComparer> には、ノードを値の等価性で比較する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d33ea-151"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>

### <a name="xobject-class"></a><span data-ttu-id="d33ea-152">XObject クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-152">XObject class</span></span>

<span data-ttu-id="d33ea-153"><xref:System.Xml.Linq.XObject> は、<xref:System.Xml.Linq.XNode> および <xref:System.Xml.Linq.XAttribute> の抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="d33ea-153"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="d33ea-154">このクラスには、注釈およびイベント機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d33ea-154">It provides annotation and event functionality.</span></span>

### <a name="xobjectchange-class"></a><span data-ttu-id="d33ea-155">XObjectChange クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-155">XObjectChange class</span></span>

<span data-ttu-id="d33ea-156"><xref:System.Xml.Linq.XObjectChange> は、<xref:System.Xml.Linq.XObject> に対してイベントが生成されるときのイベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-156"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>

### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="d33ea-157">XObjectChangeEventArgs クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-157">XObjectChangeEventArgs class</span></span>

<span data-ttu-id="d33ea-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> には、<xref:System.Xml.Linq.XObject.Changing> イベントと <xref:System.Xml.Linq.XObject.Changed> イベントのデータが用意されています。</span><span class="sxs-lookup"><span data-stu-id="d33ea-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>

### <a name="xprocessinginstruction-class"></a><span data-ttu-id="d33ea-159">XProcessingInstruction クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-159">XProcessingInstruction class</span></span>

<span data-ttu-id="d33ea-160"><xref:System.Xml.Linq.XProcessingInstruction> は、XML 処理命令を表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-160"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="d33ea-161">処理命令は、XML を処理するアプリケーションに情報を伝達します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-161">A processing instruction communicates information to an application that processes the XML.</span></span>

### <a name="xtext-class"></a><span data-ttu-id="d33ea-162">XText クラス</span><span class="sxs-lookup"><span data-stu-id="d33ea-162">XText class</span></span>

<span data-ttu-id="d33ea-163"><xref:System.Xml.Linq.XText> は、テキスト ノードを表します。</span><span class="sxs-lookup"><span data-stu-id="d33ea-163"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="d33ea-164">このクラスを使用する必要はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="d33ea-164">In most cases, you don't have to use this class.</span></span> <span data-ttu-id="d33ea-165">このクラスは、主に混合コンテンツに使用されます。</span><span class="sxs-lookup"><span data-stu-id="d33ea-165">This class is primarily used for mixed content.</span></span>
