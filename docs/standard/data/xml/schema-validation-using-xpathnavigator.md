---
description: '詳細情報: XPathNavigator を使用したスキーマ検証'
title: XPathNavigator を使用したスキーマ検証
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81fa0e41-d9c9-46f0-b22b-50da839c77f5
ms.openlocfilehash: 69b57aa4f2efc08ba196e0abe1f4d8a0b91887db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782989"
---
# <a name="schema-validation-using-xpathnavigator"></a><span data-ttu-id="f9b1a-103">XPathNavigator を使用したスキーマ検証</span><span class="sxs-lookup"><span data-stu-id="f9b1a-103">Schema Validation using XPathNavigator</span></span>

<span data-ttu-id="f9b1a-104"><xref:System.Xml.XmlDocument> クラスを使用して、<xref:System.Xml.XmlDocument> オブジェクトに含まれる XML コンテンツを 2 つの方法で検証することができます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-104">Using the <xref:System.Xml.XmlDocument> class, you can validate the XML content contained in an <xref:System.Xml.XmlDocument> object in two ways.</span></span> <span data-ttu-id="f9b1a-105">最初の方法は、検証型 <xref:System.Xml.XmlReader> オブジェクトを使用して XML コンテンツを検証する方法で、2 番目の方法は、<xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-105">The first way is to validate the XML content using a validating <xref:System.Xml.XmlReader> object and the second way is to use the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f9b1a-106"><xref:System.Xml.XPath.XPathDocument> クラスを使用して XML コンテンツの読み取り専用の検証を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-106">You can also perform read-only validation of XML content using the <xref:System.Xml.XPath.XPathDocument> class.</span></span>  
  
## <a name="validating-xml-data"></a><span data-ttu-id="f9b1a-107">XML データの検証</span><span class="sxs-lookup"><span data-stu-id="f9b1a-107">Validating XML Data</span></span>  

 <span data-ttu-id="f9b1a-108"><xref:System.Xml.XmlDocument> クラスは、既定では DTD または XML スキーマ定義言語 (XSD) のスキーマ検証を使用した XML ドキュメントの検証は行いません。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-108">The <xref:System.Xml.XmlDocument> class does not validate an XML document using either DTD or XML schema definition language (XSD) schema validation by default.</span></span> <span data-ttu-id="f9b1a-109">XML ドキュメントが整形式であることを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-109">It only verifies that the XML document is well formed.</span></span>  
  
 <span data-ttu-id="f9b1a-110">XML ドキュメントを検証する最初の方法は、検証型の <xref:System.Xml.XmlDocument> オブジェクトを使用して、ドキュメントが <xref:System.Xml.XmlReader> オブジェクトに読み込まれる際に検証する方法です。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-110">The first way to validate an XML document is to validate the document as it is loaded into an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f9b1a-111">2 番目の方法は、<xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドを使用して、以前に型指定されていない XML ドキュメントを検証する方法です。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-111">The second way is to validate a previously untyped XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f9b1a-112">いずれの場合も、検証済みの XML ドキュメントに対して行った変更は、<xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドを使用して再度検証することができます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-112">In both cases, changes to the validated XML document can be revalidated using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
### <a name="validating-a-document-as-it-is-loaded"></a><span data-ttu-id="f9b1a-113">読み込み時のドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="f9b1a-113">Validating a Document as it is Loaded</span></span>  

 <span data-ttu-id="f9b1a-114">検証型 <xref:System.Xml.XmlReader> オブジェクトは、<xref:System.Xml.XmlReaderSettings> オブジェクトをパラメーターとして受け取る <xref:System.Xml.XmlReader.Create%2A> クラスの <xref:System.Xml.XmlReader> メソッドに <xref:System.Xml.XmlReaderSettings> オブジェクトを渡すことで作成できます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-114">A validating <xref:System.Xml.XmlReader> object is created by passing an <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class that takes an <xref:System.Xml.XmlReaderSettings> object as a parameter.</span></span> <span data-ttu-id="f9b1a-115">パラメーターとして渡された <xref:System.Xml.XmlReaderSettings> オブジェクトには、<xref:System.Xml.XmlReaderSettings.ValidationType%2A> が設定された `Schema` プロパティがあり、<xref:System.Xml.XmlDocument> オブジェクトに含まれる XML ドキュメントの XML スキーマが <xref:System.Xml.XmlReaderSettings.Schemas%2A> プロパティに追加されています。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-115">The <xref:System.Xml.XmlReaderSettings> object passed as a parameter has a <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property set to `Schema` and an XML Schema for the XML document contained in the <xref:System.Xml.XmlDocument> object added to its <xref:System.Xml.XmlReaderSettings.Schemas%2A> property.</span></span> <span data-ttu-id="f9b1a-116">検証型 <xref:System.Xml.XmlReader> オブジェクトは、次に <xref:System.Xml.XmlDocument> オブジェクトを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-116">The validating <xref:System.Xml.XmlReader> object is then used to create the <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="f9b1a-117">次の例では、検証型 `contosoBooks.xml` オブジェクトを使用して、<xref:System.Xml.XmlDocument> オブジェクトを作成することにより、<xref:System.Xml.XmlDocument> ファイルを <xref:System.Xml.XmlReader> オブジェクトに読み込む際に検証を行います。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-117">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f9b1a-118">この XML ドキュメントはそのスキーマに照らして有効なので、スキーマの検証エラーや警告は何も生成されません。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-118">Because the XML document is valid according to its schema, no schema validation errors or warnings are generated.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f9b1a-119">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-119">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f9b1a-120">また、`contosoBooks.xsd` ファイルも入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-120">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="f9b1a-121">上記の例では、<xref:System.Xml.Schema.XmlSchemaValidationException> を呼び出したときに属性や要素の型が検証スキーマで指定されている型と一致しなかった場合、<xref:System.Xml.XmlDocument.Load%2A> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-121">In the above example, an <xref:System.Xml.Schema.XmlSchemaValidationException> will be thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span> <span data-ttu-id="f9b1a-122">検証を行う <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> に <xref:System.Xml.XmlReader> が設定されている場合、無効な型が検出されるたびに <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-122">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is set on the validating <xref:System.Xml.XmlReader>, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> will get called whenever an invalid type is encountered.</span></span>  
  
 <span data-ttu-id="f9b1a-123"><xref:System.Xml.Schema.XmlSchemaException> が <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> に設定されている属性または要素が `invalid` によりアクセスされると、<xref:System.Xml.XPath.XPathNavigator> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-123">An <xref:System.Xml.Schema.XmlSchemaException> will be thrown when an attribute or element with <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> set to `invalid` is accessed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="f9b1a-124"><xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> を使用して属性または要素にアクセスするとき、<xref:System.Xml.XPath.XPathNavigator> プロパティを使用して、個々の属性または要素が有効かどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-124">The <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> property can be used to determine whether or not an individual attribute or element is valid when accessing attributes or elements with the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9b1a-125">XML ドキュメントが既定値を定義した関連付けられたスキーマと共に <xref:System.Xml.XmlDocument> オブジェクトに読み込まれる場合、<xref:System.Xml.XmlDocument> オブジェクトは、これらの既定値があたかも XML ドキュメント内にあるかのように扱います。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-125">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> object treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="f9b1a-126">これは、XML ドキュメントで空要素として書かれていても、スキーマから既定値を得た要素に対して <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> プロパティは常に `false` を返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-126">This means that the <xref:System.Xml.XPath.XPathNavigator.IsEmptyElement%2A> property  always returns `false` for an element that was defaulted from the schema, even if in the XML document it was written as an empty element.</span></span>  
  
### <a name="validating-a-document-using-the-validate-method"></a><span data-ttu-id="f9b1a-127">Validate メソッドを使用したドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="f9b1a-127">Validating a Document using the Validate Method</span></span>  

 <span data-ttu-id="f9b1a-128"><xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドは、<xref:System.Xml.XmlDocument> オブジェクトの <xref:System.Xml.XmlDocument> プロパティで指定されたスキーマに対して、<xref:System.Xml.XmlDocument.Schemas%2A> オブジェクトに含まれる XML ドキュメントを検証し、情報セットの拡大を実施します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-128">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML document contained in an <xref:System.Xml.XmlDocument> object against the schemas specified in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property and performs infoset augmentation.</span></span> <span data-ttu-id="f9b1a-129">結果として、<xref:System.Xml.XmlDocument> オブジェクト中の以前は型指定されていない XML ドキュメントは型指定されたドキュメントに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-129">The result is a previously untyped XML document in the <xref:System.Xml.XmlDocument> object replaced with a typed document.</span></span>  
  
 <span data-ttu-id="f9b1a-130"><xref:System.Xml.XmlDocument> オブジェクトは、<xref:System.Xml.Schema.ValidationEventHandler> メソッドへのパラメーターとして渡された <xref:System.Xml.XmlDocument.Validate%2A> デリゲートを使用してスキーマ検証のエラーと警告を報告します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-130">The <xref:System.Xml.XmlDocument> object reports schema validation errors and warnings using the <xref:System.Xml.Schema.ValidationEventHandler> delegate passed as a parameter to the <xref:System.Xml.XmlDocument.Validate%2A> method.</span></span>  
  
 <span data-ttu-id="f9b1a-131">次の例では、`contosoBooks.xml` オブジェクトの <xref:System.Xml.XmlDocument> プロパティに含まれる `contosoBooks.xsd` スキーマに対して、<xref:System.Xml.XmlDocument> オブジェクトに含まれる <xref:System.Xml.XmlDocument.Schemas%2A> ファイルを検証します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-131">The following example validates the `contosoBooks.xml` file contained in the <xref:System.Xml.XmlDocument> object against the `contosoBooks.xsd` schema contained in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidateExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Dim document As XmlDocument = New XmlDocument()  
        document.Load("contosoBooks.xml")  
        Dim navigator As XPathNavigator = document.CreateNavigator()  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
        Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
        document.Validate(validation)  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidateExample  
{  
    static void Main(string[] args)  
    {  
        XmlDocument document = new XmlDocument();  
        document.Load("contosoBooks.xml");  
        XPathNavigator navigator = document.CreateNavigator();  
  
        document.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
        ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
        document.Validate(validation);  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f9b1a-132">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-132">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f9b1a-133">また、`contosoBooks.xsd` ファイルも入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-133">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
### <a name="validating-modifications"></a><span data-ttu-id="f9b1a-134">変更点の検証</span><span class="sxs-lookup"><span data-stu-id="f9b1a-134">Validating Modifications</span></span>  

 <span data-ttu-id="f9b1a-135">XML ドキュメントに変更が施された後、<xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドを使用して、変更点を XML ドキュメントのスキーマに対して検証できます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-135">After modifications are made to an XML document, you can validate the modifications against the schema for the XML document using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="f9b1a-136">次の例では、検証型 `contosoBooks.xml` オブジェクトを使用して、<xref:System.Xml.XmlDocument> オブジェクトを作成することにより、<xref:System.Xml.XmlDocument> ファイルを <xref:System.Xml.XmlReader> オブジェクトに読み込む際に検証を行います。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-136">The following example validates the `contosoBooks.xml` file as it is loaded into the <xref:System.Xml.XmlDocument> object by creating the <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="f9b1a-137">XML ドキュメントは、スキーマ検証のエラーや警告を生成せずに、読み込み時に問題なく検証されます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-137">The XML document is validated successfully as it is loaded without generating any schema validation errors or warnings.</span></span> <span data-ttu-id="f9b1a-138">次に、この例で `contosoBooks.xsd` スキーマに従うと無効な 2 つの変更が XML ドキュメントに施されます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-138">The example then makes two modifications to the XML document that are invalid according to the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="f9b1a-139">最初の変更点は、無効な子要素を挿入してスキーマ検証エラーを引き起こします。2 番目の変更点は、型指定されたノードにノードの型に反して無効な値を設定し、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-139">The first modification inserts an invalid child element resulting in a schema validation error, and the second modification sets the value of a typed node to a value that is invalid according to the type of the node resulting in an exception.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
Imports System.Xml.Schema  
Imports System.Xml.XPath  
  
Class ValidatingReaderExample  
  
    Shared Sub Main(ByVal args() As String)  
  
        Try  
            Dim settings As XmlReaderSettings = New XmlReaderSettings()  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
            settings.ValidationType = ValidationType.Schema  
  
            Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
            Dim document As XmlDocument = New XmlDocument()  
            document.Load(reader)  
            Dim navigator As XPathNavigator = document.CreateNavigator()  
  
            Dim validation As ValidationEventHandler = New ValidationEventHandler(AddressOf SchemaValidationHandler)  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
            navigator.MoveToChild("book", "http://www.contoso.com/books")  
            navigator.MoveToChild("author", "http://www.contoso.com/books")  
  
            navigator.AppendChild("<title>Book Title</title>")  
  
            document.Validate(validation)  
  
            navigator.MoveToParent()  
            navigator.MoveToChild("price", "http://www.contoso.com/books")  
            navigator.SetTypedValue(DateTime.Now)  
        Catch e As Exception  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message)  
        End Try  
  
    End Sub  
  
    Shared Sub SchemaValidationHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
        Select Case e.Severity  
            Case XmlSeverityType.Error  
                Console.WriteLine("Schema Validation Error: {0}", e.Message)  
                Exit Sub  
            Case XmlSeverityType.Warning  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message)  
                Exit Sub  
        End Select  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Schema;  
using System.Xml.XPath;  
  
class ValidatingReaderExample  
{  
    static void Main(string[] args)  
    {  
        try  
        {  
            XmlReaderSettings settings = new XmlReaderSettings();  
            settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
            settings.ValidationType = ValidationType.Schema;  
  
            XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
            XmlDocument document = new XmlDocument();  
            document.Load(reader);  
            XPathNavigator navigator = document.CreateNavigator();  
  
            ValidationEventHandler validation = new ValidationEventHandler(SchemaValidationHandler);  
  
            navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
            navigator.MoveToChild("book", "http://www.contoso.com/books");  
            navigator.MoveToChild("author", "http://www.contoso.com/books");  
  
            navigator.AppendChild("<title>Book Title</title>");  
  
            document.Validate(validation);  
  
            navigator.MoveToParent();  
            navigator.MoveToChild("price", "http://www.contoso.com/books");  
            navigator.SetTypedValue(DateTime.Now);  
        }  
        catch (Exception e)  
        {  
            Console.WriteLine("ValidatingReaderExample.Exception: {0}", e.Message);  
        }  
    }  
  
    static void SchemaValidationHandler(object sender, ValidationEventArgs e)  
    {  
        switch (e.Severity)  
        {  
            case XmlSeverityType.Error:  
                Console.WriteLine("Schema Validation Error: {0}", e.Message);  
                break;  
            case XmlSeverityType.Warning:  
                Console.WriteLine("Schema Validation Warning: {0}", e.Message);  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f9b1a-140">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-140">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="f9b1a-141">また、`contosoBooks.xsd` ファイルも入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-141">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
 <span data-ttu-id="f9b1a-142">上の例では、<xref:System.Xml.XmlDocument> オブジェクトに含まれる XML ドキュメントに 2 つの変更が施されます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-142">In the example above, two modifications are made to the XML document contained in the <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="f9b1a-143">XML ドキュメントが読み込まれるに従い、発見されたスキーマ検証エラーは検証イベント ハンドラー メソッドで処理され、コンソールに書き出されました。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-143">As the XML document was loaded, any schema validation errors encountered would have been handled by the validation event handler method and written to the console.</span></span>  
  
 <span data-ttu-id="f9b1a-144">この例では、XML ドキュメントが読み込まれた後に検証エラーが挿入され、<xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドを使用して発見されました。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-144">In this example, the validation errors were introduced after the XML document was loaded and were found using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="f9b1a-145"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドを使用して行われた変更は、新しい値がノードのスキーマ型に照らして無効だったので、<xref:System.InvalidCastException> が発生しました。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-145">Modifications made using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class resulted in an <xref:System.InvalidCastException> because the new value was invalid according to the schema type of the node.</span></span>  
  
 <span data-ttu-id="f9b1a-146"><xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> メソッドを使用して値を変更する方法の詳細については、「[XpathNavigator による XML データの変更](modify-xml-data-using-xpathnavigator.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-146">For more information about modifying values using the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method, see the [Modify XML Data using XPathNavigator](modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
### <a name="read-only-validation"></a><span data-ttu-id="f9b1a-147">読み取り専用の検証</span><span class="sxs-lookup"><span data-stu-id="f9b1a-147">Read-Only Validation</span></span>  

 <span data-ttu-id="f9b1a-148"><xref:System.Xml.XPath.XPathDocument> クラスは、XML ドキュメントの読み取り専用のメモリ内表現です。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-148">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory representation of an XML document.</span></span> <span data-ttu-id="f9b1a-149"><xref:System.Xml.XPath.XPathDocument> クラスと <xref:System.Xml.XmlDocument> クラスは両方とも、XML ドキュメントを編集しナビゲートするために <xref:System.Xml.XPath.XPathNavigator> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-149">Both the <xref:System.Xml.XPath.XPathDocument> class and the <xref:System.Xml.XmlDocument> class create <xref:System.Xml.XPath.XPathNavigator> objects to navigate and edit XML documents.</span></span> <span data-ttu-id="f9b1a-150"><xref:System.Xml.XPath.XPathDocument> クラスは読み取り専用のクラスなので、<xref:System.Xml.XPath.XPathNavigator> オブジェクトから返された <xref:System.Xml.XPath.XPathDocument> オブジェクトは <xref:System.Xml.XPath.XPathDocument> オブジェクトに含まれる XML ドキュメントを編集できません。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-150">Because the <xref:System.Xml.XPath.XPathDocument> class is a read-only class, <xref:System.Xml.XPath.XPathNavigator> object's returned from <xref:System.Xml.XPath.XPathDocument> objects cannot edit the XML document contained in the <xref:System.Xml.XPath.XPathDocument> object.</span></span>  
  
 <span data-ttu-id="f9b1a-151">このトピックで前述したように、検証の場合は、検証型 <xref:System.Xml.XPath.XPathDocument> オブジェクトを使用して <xref:System.Xml.XmlDocument> オブジェクトを作成したのと同様にして、<xref:System.Xml.XmlReader> オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-151">In the case of validation, you can create an <xref:System.Xml.XPath.XPathDocument> object just like you create an <xref:System.Xml.XmlDocument> object using a validating <xref:System.Xml.XmlReader> object as described earlier in this topic.</span></span> <span data-ttu-id="f9b1a-152"><xref:System.Xml.XPath.XPathDocument> オブジェクトは読み込みの際に XML ドキュメントを検証しますが、<xref:System.Xml.XPath.XPathDocument> オブジェクト内の XML データは編集できないので、XML ドキュメントの再検証はできません。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-152">The <xref:System.Xml.XPath.XPathDocument> object validates the XML document as it is loaded, but because you cannot edit the XML data in the <xref:System.Xml.XPath.XPathDocument> object, you cannot revalidate the XML document.</span></span>  
  
 <span data-ttu-id="f9b1a-153">読み取り専用および編集可能な <xref:System.Xml.XPath.XPathNavigator> オブジェクトについては、「[XPathDocument および XmlDocument を使用した XML データの読み取り](reading-xml-data-using-xpathdocument-and-xmldocument.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9b1a-153">For more information about read-only and editable <xref:System.Xml.XPath.XPathNavigator> objects, see the [Reading XML Data using XPathDocument and XmlDocument](reading-xml-data-using-xpathdocument-and-xmldocument.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b1a-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9b1a-154">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f9b1a-155">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="f9b1a-155">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f9b1a-156">XPathDocument および XmlDocument を使用した XML データの読み取り</span><span class="sxs-lookup"><span data-stu-id="f9b1a-156">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="f9b1a-157">XPathNavigator を使用した XML データの選択、評価、および照合</span><span class="sxs-lookup"><span data-stu-id="f9b1a-157">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f9b1a-158">XPathNavigator による XML データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="f9b1a-158">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="f9b1a-159">XPathNavigator による XML データの編集</span><span class="sxs-lookup"><span data-stu-id="f9b1a-159">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
