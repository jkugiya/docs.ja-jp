---
description: '詳細情報: XPathNavigator による XML データの削除'
title: XPathNavigator による XML データの削除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: 22c150618df54b9915ff8c4474f2582da8c11a9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783145"
---
# <a name="remove-xml-data-using-xpathnavigator"></a><span data-ttu-id="7600c-103">XPathNavigator による XML データの削除</span><span class="sxs-lookup"><span data-stu-id="7600c-103">Remove XML Data using XPathNavigator</span></span>

<span data-ttu-id="7600c-104"><xref:System.Xml.XPath.XPathNavigator> クラスは、XML ドキュメントからノードを削除するためのメソッドのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="7600c-104">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="7600c-105">これらのメソッドを使用するには、<xref:System.Xml.XPath.XPathNavigator> オブジェクトが編集可能である必要があります。つまり、その <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> プロパティを `true` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7600c-105">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="7600c-106">XML ドキュメントを編集できる <xref:System.Xml.XPath.XPathNavigator> オブジェクトは、<xref:System.Xml.XmlDocument.CreateNavigator%2A> クラスの <xref:System.Xml.XmlDocument> メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="7600c-106"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="7600c-107"><xref:System.Xml.XPath.XPathNavigator> クラスによって作成される <xref:System.Xml.XPath.XPathDocument> オブジェクトは読み取り専用であり、<xref:System.Xml.XPath.XPathNavigator> オブジェクトによって作成される <xref:System.Xml.XPath.XPathDocument> オブジェクトの編集メソッドを使用しようとすると、<xref:System.NotSupportedException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="7600c-107"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="7600c-108">編集可能な <xref:System.Xml.XPath.XPathNavigator> オブジェクトの作成方法については、「[XPathDocument および XmlDocument を使用した XML データの読み取り](reading-xml-data-using-xpathdocument-and-xmldocument.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7600c-108">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="removing-nodes"></a><span data-ttu-id="7600c-109">ノードの削除</span><span class="sxs-lookup"><span data-stu-id="7600c-109">Removing Nodes</span></span>  

 <span data-ttu-id="7600c-110"><xref:System.Xml.XPath.XPathNavigator> クラスは、XML ドキュメントからノードを削除する <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7600c-110">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to remove nodes from an XML document.</span></span>  
  
### <a name="removing-a-node"></a><span data-ttu-id="7600c-111">1 つのノードの削除</span><span class="sxs-lookup"><span data-stu-id="7600c-111">Removing a Node</span></span>  

 <span data-ttu-id="7600c-112"><xref:System.Xml.XPath.XPathNavigator> クラスは、XML ドキュメントから、<xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> オブジェクトが現在位置している現在のノードを削除する <xref:System.Xml.XPath.XPathNavigator> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7600c-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method to delete the current node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on from an XML document.</span></span>  
  
 <span data-ttu-id="7600c-113"><xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> メソッドを使用してノードを削除した後は、<xref:System.Xml.XmlDocument> オブジェクトのルートからそのノードに到達することはできません。</span><span class="sxs-lookup"><span data-stu-id="7600c-113">After a node has been deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method, it is no longer reachable from the root of the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="7600c-114">ノードの削除後、<xref:System.Xml.XPath.XPathNavigator> は削除されたノードの親ノード上に位置します。</span><span class="sxs-lookup"><span data-stu-id="7600c-114">After a node has been deleted, the <xref:System.Xml.XPath.XPathNavigator> is positioned on the parent node of the deleted node.</span></span>  
  
 <span data-ttu-id="7600c-115">削除操作により、削除されたノード上に位置していた <xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置に影響はありません。</span><span class="sxs-lookup"><span data-stu-id="7600c-115">A delete operation doesn't affect the position of any <xref:System.Xml.XPath.XPathNavigator> object positioned on the deleted node.</span></span> <span data-ttu-id="7600c-116">これらの <xref:System.Xml.XPath.XPathNavigator> オブジェクトは削除されたサブツリー内を移動できるという点で有効ですが、<xref:System.Xml.XPath.XPathNavigator> クラスの通常のノード セットの移動メソッドを使用して、主ノード ツリーには移動できません。</span><span class="sxs-lookup"><span data-stu-id="7600c-116">These <xref:System.Xml.XPath.XPathNavigator> objects are valid in the sense that they can move within the deleted subtree, but cannot be moved to the main node tree using the regular node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7600c-117"><xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドは、これらの <xref:System.Xml.XPath.XPathNavigator> オブジェクトを主ノード ツリーに戻したり、主ノード ツリーから削除されたサブツリーに移動したりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="7600c-117">The <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class can be used to move these <xref:System.Xml.XPath.XPathNavigator> objects back into the main node tree, or from the main node tree to the deleted subtree.</span></span>  
  
 <span data-ttu-id="7600c-118">次の例では、`price` ファイルの最初の `book` 要素の `contosoBooks.xml` 要素を、<xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> メソッドを使用して削除します。</span><span class="sxs-lookup"><span data-stu-id="7600c-118">In the following example, the `price` element of the first `book` element of the `contosoBooks.xml` file is deleted using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span> <span data-ttu-id="7600c-119"><xref:System.Xml.XPath.XPathNavigator> 要素が削除された後の `price` オブジェクトの位置は、親の `book` 要素上です。</span><span class="sxs-lookup"><span data-stu-id="7600c-119">The position of the <xref:System.Xml.XPath.XPathNavigator> object after the `price` element is deleted is on the parent `book` element.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="7600c-120">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="7600c-120">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a><span data-ttu-id="7600c-121">属性ノードの削除</span><span class="sxs-lookup"><span data-stu-id="7600c-121">Removing an Attribute Node</span></span>  

 <span data-ttu-id="7600c-122">属性ノードは <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> メソッドを使用して XML ドキュメントから削除します。</span><span class="sxs-lookup"><span data-stu-id="7600c-122">Attribute nodes are removed from an XML document using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method.</span></span>  
  
 <span data-ttu-id="7600c-123">削除後、<xref:System.Xml.XmlDocument> オブジェクトのルート ノードから属性ノードには到達できません。<xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置は親要素上になります。</span><span class="sxs-lookup"><span data-stu-id="7600c-123">After an attribute node has been deleted, it is no longer reachable from the root node of an <xref:System.Xml.XmlDocument> object and the <xref:System.Xml.XPath.XPathNavigator> object is positioned on the parent element.</span></span>  
  
#### <a name="default-attributes"></a><span data-ttu-id="7600c-124">既定の属性</span><span class="sxs-lookup"><span data-stu-id="7600c-124">Default Attributes</span></span>  

 <span data-ttu-id="7600c-125">XML ドキュメントの既定の属性として、DTD または XML スキーマに定義されている属性を削除するときは、使用するメソッドにかかわらず、特別な制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="7600c-125">Regardless of the method used to remove attributes, there are special limitations on removing attributes that are defined as default attributes in the DTD or XML Schema for the XML document.</span></span> <span data-ttu-id="7600c-126">既定の属性は、その属性が含まれている要素も削除しない限り削除できません。</span><span class="sxs-lookup"><span data-stu-id="7600c-126">Default attributes cannot be removed unless the element they belong to is also removed.</span></span> <span data-ttu-id="7600c-127">既定の属性が宣言されている要素に既定の属性は常に存在します。その結果、既定の属性を削除すると、その要素に代替の属性が挿入され、宣言された既定の値に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="7600c-127">Default attributes are always present for elements that have default attributes declared, and as a result, deleting a default attribute results in a replacement attribute being inserted into the element and initialized to the default value that was declared.</span></span>  
  
## <a name="removing-values"></a><span data-ttu-id="7600c-128">値の削除</span><span class="sxs-lookup"><span data-stu-id="7600c-128">Removing Values</span></span>  

 <span data-ttu-id="7600c-129"><xref:System.Xml.XPath.XPathNavigator> クラスには、XML ドキュメントから型指定された値と型指定されていない値を削除する <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> メソッドと <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="7600c-129">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to remove untyped and typed values from an XML document.</span></span>  
  
### <a name="removing-untyped-values"></a><span data-ttu-id="7600c-130">型指定されていない値の削除</span><span class="sxs-lookup"><span data-stu-id="7600c-130">Removing Untyped Values</span></span>  

 <span data-ttu-id="7600c-131"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> メソッドは、パラメーターとして渡された型指定されていない `string` 値を挿入するだけです。このパラメーターは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にあるノードの値です。</span><span class="sxs-lookup"><span data-stu-id="7600c-131">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="7600c-132"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> メソッドに空の文字列を渡すと、現在のノードの値が削除されます。</span><span class="sxs-lookup"><span data-stu-id="7600c-132">Passing an empty string to the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method removes the value of the current node.</span></span>  
  
 <span data-ttu-id="7600c-133">次の例では、`price` メソッドを使用して、`book` ファイル内の最初の `contosoBooks.xml` 要素の <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> 要素の値を削除します。</span><span class="sxs-lookup"><span data-stu-id="7600c-133">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
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
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 <span data-ttu-id="7600c-134">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="7600c-134">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a><span data-ttu-id="7600c-135">型指定された値の削除</span><span class="sxs-lookup"><span data-stu-id="7600c-135">Removing Typed Values</span></span>  

 <span data-ttu-id="7600c-136">ノードの型が W3C XML スキーマの単純型の場合、<xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> メソッドによって挿入される新しい値は、値の設定前に、単純型のファセットに対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="7600c-136">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="7600c-137">新しい値がノードの型に対して無効な場合 (たとえば、型が `-1` の要素に、値 `xs:positiveInteger` を設定するような場合)、例外が返されます。</span><span class="sxs-lookup"><span data-stu-id="7600c-137">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span> <span data-ttu-id="7600c-138"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> メソッドにもパラメーターとして `null` を渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="7600c-138">The <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method also cannot be passed `null` as a parameter.</span></span> <span data-ttu-id="7600c-139">結果として、型指定されたノードの値の削除は、ノードのスキーマの型に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="7600c-139">As a result removing the value of a typed node must comply with the schema type of the node.</span></span>  
  
 <span data-ttu-id="7600c-140">次の例では、`price` メソッドを使用して、値を `book` に設定することにより、`contosoBooks.xml` ファイル内の最初の <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> 要素の `0` 要素の値を削除します。</span><span class="sxs-lookup"><span data-stu-id="7600c-140">The following example removes the value of the `price` element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method by setting the value to `0`.</span></span> <span data-ttu-id="7600c-141">ノードの値は削除されませんが、本の価格はそのデータ型 `xs:decimal` に従って削除されました。</span><span class="sxs-lookup"><span data-stu-id="7600c-141">The value of the node is not removed, but the price of the book has been removed according to its data type of `xs:decimal`.</span></span>  
  
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
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
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
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a><span data-ttu-id="7600c-142">名前空間ノード</span><span class="sxs-lookup"><span data-stu-id="7600c-142">Namespace Nodes</span></span>  

 <span data-ttu-id="7600c-143">名前空間ノードは <xref:System.Xml.XmlDocument> オブジェクトから削除できません。</span><span class="sxs-lookup"><span data-stu-id="7600c-143">Namespace nodes cannot be deleted from an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="7600c-144"><xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> メソッドを使用して名前空間ノードを削除しようとすると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="7600c-144">Attempts to delete namespace nodes using the <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> method results in an exception.</span></span>  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="7600c-145">InnerXml および OuterXml プロパティ</span><span class="sxs-lookup"><span data-stu-id="7600c-145">The InnerXml and OuterXml Properties</span></span>  

 <span data-ttu-id="7600c-146"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> および <xref:System.Xml.XPath.XPathNavigator> プロパティは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にある XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="7600c-146">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="7600c-147"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> プロパティは、与えられた XML <xref:System.Xml.XPath.XPathNavigator> の解析済みの内容を使用して `string` オブジェクトの現在位置にある子ノードの XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="7600c-147">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="7600c-148">同様に、<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> プロパティは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にある子ノードと現在のノード自体の XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="7600c-148">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="7600c-149">このトピックで説明したメソッドに加えて、<xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> プロパティと <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> プロパティは、XML ドキュメントからノードと値を削除するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="7600c-149">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to remove nodes and values from an XML document.</span></span> <span data-ttu-id="7600c-150"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> プロパティと <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> プロパティを使用してノードを変更する方法の詳細については「[XpathNavigator による XML データの変更](modify-xml-data-using-xpathnavigator.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7600c-150">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to modify nodes, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="7600c-151">XML ドキュメントの保存</span><span class="sxs-lookup"><span data-stu-id="7600c-151">Saving an XML Document</span></span>  

 <span data-ttu-id="7600c-152">ここに記載されているメソッドによる <xref:System.Xml.XmlDocument> オブジェクトに対する変更の保存は、<xref:System.Xml.XmlDocument> クラスのメソッドを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="7600c-152">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="7600c-153"><xref:System.Xml.XmlDocument> オブジェクトに対する変更の保存に関する詳細については、「[ドキュメントの保存と書き込み](saving-and-writing-a-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7600c-153">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7600c-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="7600c-154">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="7600c-155">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="7600c-155">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="7600c-156">XPathNavigator による XML データの挿入</span><span class="sxs-lookup"><span data-stu-id="7600c-156">Insert XML Data using XPathNavigator</span></span>](insert-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="7600c-157">XpathNavigator による XML データの変更</span><span class="sxs-lookup"><span data-stu-id="7600c-157">Modify XML Data using XPathNavigator</span></span>](modify-xml-data-using-xpathnavigator.md)
