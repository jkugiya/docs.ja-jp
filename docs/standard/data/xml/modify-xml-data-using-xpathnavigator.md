---
description: '詳細情報: XPathNavigator による XML データの変更'
title: XpathNavigator による XML データの変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 609957cfad0ea6c9f14acd4b43b241f76167fae0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713612"
---
# <a name="modify-xml-data-using-xpathnavigator"></a><span data-ttu-id="36fed-103">XpathNavigator による XML データの変更</span><span class="sxs-lookup"><span data-stu-id="36fed-103">Modify XML Data using XPathNavigator</span></span>

<span data-ttu-id="36fed-104"><xref:System.Xml.XPath.XPathNavigator> クラスは、XML ドキュメント内のノードを変更するためのメソッドのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="36fed-104">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to modify nodes and values in an XML document.</span></span> <span data-ttu-id="36fed-105">これらのメソッドを使用するには、<xref:System.Xml.XPath.XPathNavigator> オブジェクトが編集可能である必要があります。つまり、その <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> プロパティを `true` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="36fed-105">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="36fed-106">XML ドキュメントを編集できる <xref:System.Xml.XPath.XPathNavigator> オブジェクトは、<xref:System.Xml.XmlDocument.CreateNavigator%2A> クラスの <xref:System.Xml.XmlDocument> メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-106"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="36fed-107"><xref:System.Xml.XPath.XPathNavigator> クラスによって作成される <xref:System.Xml.XPath.XPathDocument> オブジェクトは読み取り専用で、<xref:System.Xml.XPath.XPathNavigator> オブジェクトによって作成される <xref:System.Xml.XPath.XPathDocument> オブジェクトの編集メソッドを使用しようとすると、<xref:System.NotSupportedException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="36fed-107"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object result in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="36fed-108">編集可能な <xref:System.Xml.XPath.XPathNavigator> オブジェクトの作成方法については、「[XPathDocument および XmlDocument を使用した XML データの読み取り](reading-xml-data-using-xpathdocument-and-xmldocument.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36fed-108">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="modifying-nodes"></a><span data-ttu-id="36fed-109">ノードの変更</span><span class="sxs-lookup"><span data-stu-id="36fed-109">Modifying Nodes</span></span>  

 <span data-ttu-id="36fed-110">ノードの値を簡単に変更するには、<xref:System.Xml.XPath.XPathNavigator.SetValue%2A> と <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="36fed-110">A simple technique for changing the value of a node is to use the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="36fed-111">次の表は、異なるノード型に対するこれらメソッドの効果の一覧です。</span><span class="sxs-lookup"><span data-stu-id="36fed-111">The following table lists the effects of these methods on different node types.</span></span>  
  
|<xref:System.Xml.XPath.XPathNodeType>|<span data-ttu-id="36fed-112">変更されるデータ。</span><span class="sxs-lookup"><span data-stu-id="36fed-112">Data Changed</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|<span data-ttu-id="36fed-113">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="36fed-113">Not supported.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|<span data-ttu-id="36fed-114">要素のコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="36fed-114">The content of the element.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|<span data-ttu-id="36fed-115">属性の値。</span><span class="sxs-lookup"><span data-stu-id="36fed-115">The value of the attribute.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|<span data-ttu-id="36fed-116">テキスト コンテンツ。</span><span class="sxs-lookup"><span data-stu-id="36fed-116">The text content.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|<span data-ttu-id="36fed-117">ターゲットを除くコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="36fed-117">The content, excluding the target.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|<span data-ttu-id="36fed-118">コメントの内容。</span><span class="sxs-lookup"><span data-stu-id="36fed-118">The content of the comment.</span></span>|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|<span data-ttu-id="36fed-119">サポート範囲外。</span><span class="sxs-lookup"><span data-stu-id="36fed-119">Not Supported.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="36fed-120"><xref:System.Xml.XPath.XPathNodeType.Namespace> ノードまたは <xref:System.Xml.XPath.XPathNodeType.Root> ノードの編集はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="36fed-120">Editing <xref:System.Xml.XPath.XPathNodeType.Namespace> nodes or the <xref:System.Xml.XPath.XPathNodeType.Root> node is not supported.</span></span>  
  
 <span data-ttu-id="36fed-121"><xref:System.Xml.XPath.XPathNavigator> クラスは、ノードの挿入および削除に使用されるメソッドのセットも提供しています。</span><span class="sxs-lookup"><span data-stu-id="36fed-121">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of methods used to insert and remove nodes.</span></span> <span data-ttu-id="36fed-122">XML ドキュメントのノードの挿入と削除の詳細については、「[XPathNavigator による XML データの挿入](insert-xml-data-using-xpathnavigator.md)」と「[XPathNavigator による XML データの削除](remove-xml-data-using-xpathnavigator.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="36fed-122">For more information about inserting and removing nodes from an XML document, see the [Insert XML Data using XPathNavigator](insert-xml-data-using-xpathnavigator.md) and [Remove XML Data using XPathNavigator](remove-xml-data-using-xpathnavigator.md) topics.</span></span>  
  
### <a name="modifying-untyped-values"></a><span data-ttu-id="36fed-123">型指定されていない値の変更</span><span class="sxs-lookup"><span data-stu-id="36fed-123">Modifying Untyped Values</span></span>  

 <span data-ttu-id="36fed-124"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> メソッドは、パラメーターとして渡された型指定されていない `string` 値を挿入するだけです。このパラメーターは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にあるノードの値です。</span><span class="sxs-lookup"><span data-stu-id="36fed-124">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="36fed-125">値に型は設定されず、スキーマ情報が使用可能な場合でも、ノードの型に対して新しい値が有効どうかを検証せずに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-125">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="36fed-126"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> メソッドを使用して `price` フィァイル内のすべての `contosoBooks.xml` 要素を更新する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="36fed-126">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="36fed-127">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="36fed-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a><span data-ttu-id="36fed-128">型指定された値の変更</span><span class="sxs-lookup"><span data-stu-id="36fed-128">Modifying Typed Values</span></span>  

 <span data-ttu-id="36fed-129">ノードの型が W3C XML スキーマの単純型の場合、<xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> メソッドによって挿入される新しい値は、値の設定前に、単純型のファセットに対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="36fed-129">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="36fed-130">新しい値がノードの型に対して無効な場合 (たとえば、型が `-1` の要素に、値 `xs:positiveInteger` を設定するような場合)、例外が返されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-130">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="36fed-131">次の例では、`price` ファイル内の最初の `book` 要素の `contosoBooks.xml` 要素の値を <xref:System.DateTime> 値に変更しようとしています。</span><span class="sxs-lookup"><span data-stu-id="36fed-131">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="36fed-132">`price` 要素の XML スキーマ型は、`xs:decimal` ファイル内で `contosoBooks.xsd` として定義されているため、結果は例外になります。</span><span class="sxs-lookup"><span data-stu-id="36fed-132">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="36fed-133">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="36fed-133">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="36fed-134">また、`contosoBooks.xsd` ファイルも入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="36fed-134">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a><span data-ttu-id="36fed-135">厳密に型指定された XML データの効果</span><span class="sxs-lookup"><span data-stu-id="36fed-135">The Effects of Editing Strongly Typed XML Data</span></span>  

 <span data-ttu-id="36fed-136"><xref:System.Xml.XPath.XPathNavigator> クラスは、厳密に型指定された XML の記述の基本に W3C XML スキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="36fed-136">The <xref:System.Xml.XPath.XPathNavigator> class uses the W3C XML Schema as a basis for describing strongly typed XML.</span></span> <span data-ttu-id="36fed-137">要素および属性には、W3C XML スキーマ ドキュメントに対する検証に基づいて、型情報を使用して注釈を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="36fed-137">Elements and attributes can be annotated with type information based on validation against a W3C XML Schema document.</span></span> <span data-ttu-id="36fed-138">他の要素または属性を含めることができる要素は、複合型と呼ばれ、テキストの内容だけを含めることのできる要素は単純型と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="36fed-138">Elements that can contain other elements or attributes are called complex types, while those that can only contain textual content are called simple types.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36fed-139">属性には単純型しかありません。</span><span class="sxs-lookup"><span data-stu-id="36fed-139">Attributes can only have simple types.</span></span>  
  
 <span data-ttu-id="36fed-140">要素または属性は、その型定義に固有のすべての規則に準拠している場合、スキーマ有効と見なされます。</span><span class="sxs-lookup"><span data-stu-id="36fed-140">An element or attribute can be considered to be schema-valid if it conforms to all the rules specific to its type definition.</span></span> <span data-ttu-id="36fed-141">単純型の要素 `xs:int` がスキーマ有効であるためには、-2,147,483,648 ～ 2,147,483,647 の数値を含む必要があります。</span><span class="sxs-lookup"><span data-stu-id="36fed-141">An element that has the simple type `xs:int` has to contain a numeric value between -2147483648 and 2147483647 to be schema-valid.</span></span> <span data-ttu-id="36fed-142">複合型の場合、要素のスキーマ有効性は、その子の要素および属性のスキーマ有効性に依存します。</span><span class="sxs-lookup"><span data-stu-id="36fed-142">For complex types, the schema-validity of the element is dependent on the schema-validity of its child elements and attributes.</span></span> <span data-ttu-id="36fed-143">したがって、要素が複合型定義に対して有効な場合、その子の要素および属性はすべて、それらの型定義に対して有効です。</span><span class="sxs-lookup"><span data-stu-id="36fed-143">Thus if an element is valid against its complex type definition, all its child elements and attributes are valid against their type definitions.</span></span> <span data-ttu-id="36fed-144">同様に、要素の子の要素または属性のうち 1 つでもその型定義に対して無効か有効性が不明な場合、その要素も無効か有効性が不明になります。</span><span class="sxs-lookup"><span data-stu-id="36fed-144">Similarly, if even one of the child elements or attributes of an element is invalid against its type definition, or has an unknown validity, the element is also either invalid or of unknown validity.</span></span>  
  
 <span data-ttu-id="36fed-145">要素の有効性がその子の要素および属性の有効性に依存することを考えると、要素が以前有効だった場合、どちらを変更しても要素の有効性が変わる結果になります。</span><span class="sxs-lookup"><span data-stu-id="36fed-145">Given that the validity of an element is dependent on the validity of its child elements and attributes, modifications to either result in altering the validity of the element if it was previously valid.</span></span> <span data-ttu-id="36fed-146">具体的には、要素の子要素または属性が挿入、更新または削除されると、その要素の有効性は不明になります。</span><span class="sxs-lookup"><span data-stu-id="36fed-146">Specifically, if the child elements or attributes of an element are inserted, updated, or deleted, then the validity of the element becomes unknown.</span></span> <span data-ttu-id="36fed-147">これは、要素の <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> プロパティの <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> プロパティが <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown> に設定されることによって表されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-147">This is represented by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the element's <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property being set to <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>.</span></span> <span data-ttu-id="36fed-148">さらに、要素の親要素 (およびその親、そのまた親と続く) の有効性も不明になるため、この効果は、XML ドキュメント全体で再帰的に上方向にカスケードされます。</span><span class="sxs-lookup"><span data-stu-id="36fed-148">Furthermore, this effect cascades upwards recursively across the XML document, because the validity of the element's parent element (and its parent element, and so on) also becomes unknown.</span></span>  
  
 <span data-ttu-id="36fed-149">スキーマ検証および <xref:System.Xml.XPath.XPathNavigator> クラスの詳細については、「[XPathNavigator を使用したスキーマ検証](schema-validation-using-xpathnavigator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36fed-149">For more information about schema validation and the <xref:System.Xml.XPath.XPathNavigator> class, see [Schema Validation using XPathNavigator](schema-validation-using-xpathnavigator.md).</span></span>  
  
### <a name="modifying-attributes"></a><span data-ttu-id="36fed-150">属性の変更</span><span class="sxs-lookup"><span data-stu-id="36fed-150">Modifying Attributes</span></span>  

 <span data-ttu-id="36fed-151"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> および <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> メソッドは、型指定されていない属性ノードと型指定された属性ノード、および「ノードの変更」に記載されているその他のノード型の変更に使用できます。</span><span class="sxs-lookup"><span data-stu-id="36fed-151">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods can be used to modify untyped and typed attribute nodes as well as the other node types listed in the "Modifying Nodes" section.</span></span>  
  
 <span data-ttu-id="36fed-152">次の例では、`genre` ファイル内の最初の `book` 要素の `books.xml` 属性の値を変更しています。</span><span class="sxs-lookup"><span data-stu-id="36fed-152">The following example changes the value of the `genre` attribute of the first `book` element in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="36fed-153"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> および <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> メソッドに関する詳細については、「型指定されていない値の変更」および「型指定された値の変更」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36fed-153">For more information about the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods, see the "Modifying Untyped Values" and "Modifying Typed Values" sections.</span></span>  
  
## <a name="innerxml-and-outerxml-properties"></a><span data-ttu-id="36fed-154">InnerXml および OuterXml プロパティ</span><span class="sxs-lookup"><span data-stu-id="36fed-154">InnerXml and OuterXml Properties</span></span>  

 <span data-ttu-id="36fed-155"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> および <xref:System.Xml.XPath.XPathNavigator> プロパティは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にある XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="36fed-155">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="36fed-156"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> プロパティは、与えられた XML <xref:System.Xml.XPath.XPathNavigator> の解析済みの内容を使用して `string` オブジェクトの現在位置にある子ノードの XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="36fed-156">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="36fed-157">同様に、<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> プロパティは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にある子ノードと現在のノード自体の XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="36fed-157">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="36fed-158">次の例では、<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> プロパティを使用して、`price` ファイル内の最初の `discount` 要素に対して `book` 要素の値を変更し、新しい `contosoBooks.xml` 属性を挿入しています。</span><span class="sxs-lookup"><span data-stu-id="36fed-158">The following example uses the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property to modify the value of the `price` element and insert a new `discount` attribute on the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="36fed-159">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="36fed-159">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a><span data-ttu-id="36fed-160">名前空間ノードの変更</span><span class="sxs-lookup"><span data-stu-id="36fed-160">Modifying Namespace Nodes</span></span>  

 <span data-ttu-id="36fed-161">ドキュメント オブジェクト モデル (DOM) で、名前空間宣言は挿入、更新、および削除が可能な普通の属性のように扱われます。</span><span class="sxs-lookup"><span data-stu-id="36fed-161">In the Document Object Model (DOM), namespace declarations are treated as if they are regular attributes that can be inserted, updated and deleted.</span></span> <span data-ttu-id="36fed-162"><xref:System.Xml.XPath.XPathNavigator> クラスでは、名前空間ノードに対してそのような操作は許可されません。これは、次の例で説明されているように、名前空間ノードの値を変更すると、名前空間ノードのスコープ内の要素および属性の ID が変更される可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="36fed-162">The <xref:System.Xml.XPath.XPathNavigator> class does not allow such operations on namespace nodes because altering the value of a namespace node can change the identity of the elements and attributes within the scope of the namespace node as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="36fed-163">上記の XML 例を次のように変更すると、各要素の名前空間 URI が変更されるため、事実上、ドキュメント内のすべての要素の名前が変更されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-163">If the XML example above is changed in the following way, this effectively renames every element in the document because the value of each element's namespace URI is changed.</span></span>  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 <span data-ttu-id="36fed-164">挿入先のスコープでの名前空間宣言と競合しない名前空間の挿入は、<xref:System.Xml.XPath.XPathNavigator> クラスによって許可されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-164">Inserting namespace nodes that do not conflict with namespace declarations at the scope that they are inserted in is allowed by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="36fed-165">この場合、次の例で説明されているように、名前空間宣言は XML ドキュメント内の下位のスコープで宣言されず、名前の変更が発生しません。</span><span class="sxs-lookup"><span data-stu-id="36fed-165">In this case, the namespace declarations are not declared at lower scopes in the XML document and does not result in renaming as illustrated in the following example.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="36fed-166">上記の XML 例を次のように変更すると、名前空間宣言が XML ドキュメント全体で他の名前空間宣言のスコープより下位に正しく反映されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-166">If the XML example above is changed in the following way, the namespace declarations are correctly propagated across the XML document below the scope of the other namespace declaration.</span></span>  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 <span data-ttu-id="36fed-167">上記の XML の例では、属性 `a:parent-id` が `parent` 名前空間名の `http://www.contoso.com/parent-id` 要素に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-167">In the XML example above, the attribute `a:parent-id` is inserted on the `parent` element in the `http://www.contoso.com/parent-id` namespace.</span></span> <span data-ttu-id="36fed-168"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> メソッドは、`parent` 要素上に位置しているときの属性の挿入に使用されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-168">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method is used to insert the attribute while positioned on the `parent` element.</span></span> <span data-ttu-id="36fed-169">XML ドキュメントの残りの部分の一貫性を保持するために、`http://www.contoso.com` 名前空間宣言が <xref:System.Xml.XPath.XPathNavigator> クラスによって自動的に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-169">The `http://www.contoso.com` namespace declaration is automatically inserted by the <xref:System.Xml.XPath.XPathNavigator> class to preserve the consistency of the rest of the XML document.</span></span>  
  
## <a name="modifying-entity-reference-nodes"></a><span data-ttu-id="36fed-170">エンティティ参照ノードの変更</span><span class="sxs-lookup"><span data-stu-id="36fed-170">Modifying Entity Reference Nodes</span></span>  

 <span data-ttu-id="36fed-171"><xref:System.Xml.XmlDocument> オブジェクト内のエンティティ参照ノードは、読み取り専用で、<xref:System.Xml.XPath.XPathNavigator> または <xref:System.Xml.XmlNode> クラスのどちらを使用しても編集できません。</span><span class="sxs-lookup"><span data-stu-id="36fed-171">Entity reference nodes in an <xref:System.Xml.XmlDocument> object are read-only and cannot be edited using either the <xref:System.Xml.XPath.XPathNavigator> or <xref:System.Xml.XmlNode> classes.</span></span> <span data-ttu-id="36fed-172">エンティティ参照ノードを変更しようとすると、<xref:System.InvalidOperationException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="36fed-172">Any attempt to modify an entity reference node results in an <xref:System.InvalidOperationException>.</span></span>  
  
## <a name="modifying-xsinil-nodes"></a><span data-ttu-id="36fed-173">xsi:nil ノードの変更</span><span class="sxs-lookup"><span data-stu-id="36fed-173">Modifying xsi:nil Nodes</span></span>  

 <span data-ttu-id="36fed-174">W3C XML スキーマ勧告では、nillable 状態の要素という概念が導入されました。</span><span class="sxs-lookup"><span data-stu-id="36fed-174">The W3C XML Schema recommendation introduces the concept of an element being nillable.</span></span> <span data-ttu-id="36fed-175">要素が nillable の場合、要素は内容を持たなくても有効になります。</span><span class="sxs-lookup"><span data-stu-id="36fed-175">When an element is nillable, it is possible for the element to have no content and still be valid.</span></span> <span data-ttu-id="36fed-176">nillable 状態の要素という概念は、`null` 状態のオブジェクトという概念に似ています。</span><span class="sxs-lookup"><span data-stu-id="36fed-176">The concept of an element being nillable is similar to the concept of an object being `null`.</span></span> <span data-ttu-id="36fed-177">主な相違点は、`null` オブジェクトにはアクセスできないのに対して、`xsi:nil` 要素には、内容 (子要素またはテキスト) はなくとも、アクセスできる属性などのプロパティがあることです。</span><span class="sxs-lookup"><span data-stu-id="36fed-177">The main difference is that a `null` object cannot be accessed in any way, while an `xsi:nil` element still has properties such as attributes that can be accessed, but has no content (child elements or text).</span></span> <span data-ttu-id="36fed-178">XML ドキュメント内では、要素に内容がないことを示すために、要素に `xsi:nil` の値を持つ `true` 属性が使用されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-178">The existence of the `xsi:nil` attribute with a value of `true` on an element in an XML document is used to indicate that an element has no content.</span></span>  
  
 <span data-ttu-id="36fed-179"><xref:System.Xml.XPath.XPathNavigator> オブジェクトを使用して、`xsi:nil` の値の `true` 属性を持つ有効な要素に内容を追加すると、その `xsi:nil` 属性の値は `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-179">If an <xref:System.Xml.XPath.XPathNavigator> object is used to add content to a valid element with an `xsi:nil` attribute with a value of `true`, the value of its `xsi:nil` attribute is set to `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36fed-180">`xsi:nil` 属性が `false` に設定された要素のコンテンツが削除されても、その属性の値は `true` に変更されません。</span><span class="sxs-lookup"><span data-stu-id="36fed-180">If the content of an element with an `xsi:nil` attribute set to `false` is deleted, the value of the attribute is not changed to `true`.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="36fed-181">XML ドキュメントの保存</span><span class="sxs-lookup"><span data-stu-id="36fed-181">Saving an XML Document</span></span>  

 <span data-ttu-id="36fed-182">ここに記載されている編集メソッドによる <xref:System.Xml.XmlDocument> オブジェクトに対する変更の保存は、<xref:System.Xml.XmlDocument> クラスのメソッドを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="36fed-182">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the editing methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="36fed-183"><xref:System.Xml.XmlDocument> オブジェクトに対する変更の保存に関する詳細については、「[ドキュメントの保存と書き込み](saving-and-writing-a-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36fed-183">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36fed-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="36fed-184">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="36fed-185">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="36fed-185">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="36fed-186">XPathNavigator による XML データの挿入</span><span class="sxs-lookup"><span data-stu-id="36fed-186">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="36fed-187">XPathNavigator による XML データの削除</span><span class="sxs-lookup"><span data-stu-id="36fed-187">Remove XML Data using XPathNavigator</span></span>](remove-xml-data-using-xpathnavigator.md)
