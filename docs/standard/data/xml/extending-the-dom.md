---
description: '詳細情報: DOM の拡張'
title: DOM の拡張
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b5489c96-4afd-439a-a25d-fc82eb4a148d
ms.openlocfilehash: 46b721e093b2cf0247ddd7cf145381cdaec75773
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732151"
---
# <a name="extending-the-dom"></a><span data-ttu-id="18f4f-103">DOM の拡張</span><span class="sxs-lookup"><span data-stu-id="18f4f-103">Extending the DOM</span></span>

<span data-ttu-id="18f4f-104">Microsoft .NET Framework は、XML ドキュメント オブジェクト モデル (DOM) の実装を提供するクラスの基本セットを備えています。</span><span class="sxs-lookup"><span data-stu-id="18f4f-104">The Microsoft .NET Framework includes a base set of classes that provides an implementation of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="18f4f-105"><xref:System.Xml.XmlNode> およびその派生クラスのメソッドとプロパティを利用して、XML ドキュメントの内容および構造の中で移動し、それらに対してクエリを実行し、それらを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-105">The <xref:System.Xml.XmlNode>, and its derived classes, provides methods and properties that allow you to navigate, query, and modify the content and structure of an XML document.</span></span>

<span data-ttu-id="18f4f-106">DOM を使用して XML コンテンツをメモリに読み込むと、作成されたノードには、ノード名やノード型などの情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-106">When XML content is loaded into memory using the DOM, the nodes created contain information such as node name, node type, and so on.</span></span> <span data-ttu-id="18f4f-107">場合によっては、基本クラスによっては提供されない特定のノード情報が必要になることもあります。</span><span class="sxs-lookup"><span data-stu-id="18f4f-107">There may be occasions where you require specific node information that the base classes do not provide.</span></span> <span data-ttu-id="18f4f-108">たとえば、ノードの行番号と位置が必要な場合です。</span><span class="sxs-lookup"><span data-stu-id="18f4f-108">For example, you may want to see the line number and position of the node.</span></span> <span data-ttu-id="18f4f-109">このような場合は、既存の DOM クラスから新しいクラスを派生させ、追加機能を持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-109">In this case, you can derive new classes from the existing DOM classes and add additional functionality.</span></span>

<span data-ttu-id="18f4f-110">新しいクラスを派生させるときの一般的なガイドラインは、次の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="18f4f-110">There are two general guidelines when deriving new classes:</span></span>

- <span data-ttu-id="18f4f-111"><xref:System.Xml.XmlNode> クラスからはクラスを派生させないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18f4f-111">It is recommended that you never derive from the <xref:System.Xml.XmlNode> class.</span></span> <span data-ttu-id="18f4f-112">その代わりに、目的とするノード型に対応するクラスからクラスを派生させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18f4f-112">Instead, it is recommended that you derive classes from the class corresponding to the node type that you are interested in.</span></span> <span data-ttu-id="18f4f-113">たとえば、属性ノードの追加情報を返すようにする場合は、<xref:System.Xml.XmlAttribute> クラスからクラスを派生させます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-113">For example, if you want to return additional information on attribute nodes, you can derive from the <xref:System.Xml.XmlAttribute> class.</span></span>

- <span data-ttu-id="18f4f-114">ノード作成メソッド以外の関数をオーバーライドするときは、常にその関数の基本バージョンを呼び出してから、他の処理を追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18f4f-114">Except for the node creation methods, it is recommended that when overriding a function, you should always call the base version of the function and then add any additional processing.</span></span>

## <a name="creating-your-own-node-instances"></a><span data-ttu-id="18f4f-115">独自のノード インスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="18f4f-115">Creating Your Own Node Instances</span></span>

<span data-ttu-id="18f4f-116"><xref:System.Xml.XmlDocument> クラスは、ノード作成メソッドを持っています。</span><span class="sxs-lookup"><span data-stu-id="18f4f-116">The <xref:System.Xml.XmlDocument> class contains node creation methods.</span></span> <span data-ttu-id="18f4f-117">XML ファイルが読み込まれると、ノード作成メソッドが呼び出され、ノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-117">When an XML file is loaded, these methods are called to create the nodes.</span></span> <span data-ttu-id="18f4f-118">これらのメソッドをオーバーライドすると、ドキュメントが読み込まれるときに独自のノード インスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-118">You can override these methods so that your node instances are created when a document is loaded.</span></span> <span data-ttu-id="18f4f-119">たとえば、<xref:System.Xml.XmlElement> クラスを拡張すると、<xref:System.Xml.XmlDocument> クラスが継承され、<xref:System.Xml.XmlDocument.CreateElement%2A> メソッドがオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-119">For example, if you have extended the <xref:System.Xml.XmlElement> class, you would inherit the <xref:System.Xml.XmlDocument> class and override the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span>

<span data-ttu-id="18f4f-120"><xref:System.Xml.XmlDocument.CreateElement%2A> メソッドをオーバーライドし、<xref:System.Xml.XmlElement> クラスの独自の実装を返す方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="18f4f-120">The following example shows how to override the <xref:System.Xml.XmlDocument.CreateElement%2A> method to return your implementation of the <xref:System.Xml.XmlElement> class.</span></span>

```vb
Class LineInfoDocument
    Inherits XmlDocument
        Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
        Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
        Return elem
    End Function 'CreateElement
End Class 'LineInfoDocument
```

```csharp
class LineInfoDocument : XmlDocument
{
    public override XmlElement CreateElement(string prefix, string localname, string nsURI)
    {
        LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this);
        return elem;
    }
}
```

## <a name="extending-a-class"></a><span data-ttu-id="18f4f-121">クラスの拡張</span><span class="sxs-lookup"><span data-stu-id="18f4f-121">Extending a Class</span></span>

<span data-ttu-id="18f4f-122">クラスを拡張するには、既存の DOM クラスの 1 つから独自のクラスを派生させます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-122">To extend a class, derive your class from one of the existing DOM classes.</span></span> <span data-ttu-id="18f4f-123">その後、基本クラスの仮想メソッドやプロパティをオーバーライドしたり、独自のメソッドやプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="18f4f-123">You can then override any of the virtual methods or properties in the base class, or add your own.</span></span>

<span data-ttu-id="18f4f-124">次の例では、<xref:System.Xml.XmlElement> クラスと <xref:System.Xml.IXmlLineInfo> インターフェイスを実装する新しいクラスを作成しています。</span><span class="sxs-lookup"><span data-stu-id="18f4f-124">In the following example, a new class is created, which implements the <xref:System.Xml.XmlElement> class and the <xref:System.Xml.IXmlLineInfo> interface.</span></span> <span data-ttu-id="18f4f-125">行番号を収集できるようにする追加のメソッドとプロパティが定義されます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-125">Additional methods and properties are defined which allows users to gather line information.</span></span>

```vb
Class LineInfoElement
   Inherits XmlElement
   Implements IXmlLineInfo
   Private lineNumber As Integer = 0
   Private linePosition As Integer = 0

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub

   Public Sub SetLineInfo(linenum As Integer, linepos As Integer)
      lineNumber = linenum
      linePosition = linepos
   End Sub

   Public ReadOnly Property LineNumber() As Integer
      Get
         Return lineNumber
      End Get
   End Property

   Public ReadOnly Property LinePosition() As Integer
      Get
         Return linePosition
      End Get
   End Property

   Public Function HasLineInfo() As Boolean
      Return True
   End Function
End Class ' End LineInfoElement class.
```

```csharp
class LineInfoElement : XmlElement, IXmlLineInfo {
   int lineNumber = 0;
   int linePosition = 0;
   internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ) : base( prefix, localname, nsURI, doc ) {
       ( (LineInfoDocument)doc ).IncrementElementCount();
  }
  public void SetLineInfo( int linenum, int linepos ) {
      lineNumber = linenum;
      linePosition = linepos;
  }
  public int LineNumber {
     get {
       return lineNumber;
     }
  }
  public int LinePosition {
      get {
        return linePosition;
      }
  }
  public bool HasLineInfo() {
    return true;
  }
} // End LineInfoElement class.
```

### <a name="example"></a><span data-ttu-id="18f4f-126">例</span><span class="sxs-lookup"><span data-stu-id="18f4f-126">Example</span></span>

<span data-ttu-id="18f4f-127">XML ドキュメントの要素数を数える例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="18f4f-127">The following example counts the number of elements in an XML document:</span></span>

```vb
Imports System.Xml
Imports System.IO

Class LineInfoDocument
   Inherits XmlDocument

   Private elementCount As Integer

   Friend Sub New()
      elementCount = 0
   End Sub

   Public Overrides Function CreateElement(prefix As String, localname As String, nsURI As String) As XmlElement
      Dim elem As New LineInfoElement(prefix, localname, nsURI, Me)
      Return elem
   End Function

   Public Sub IncrementElementCount()
      elementCount += 1
   End Sub

   Public Function GetCount() As Integer
      Return elementCount
   End Function
End Class 'End LineInfoDocument class.

Class LineInfoElement
   Inherits XmlElement

   Friend Sub New(prefix As String, localname As String, nsURI As String, doc As XmlDocument)
      MyBase.New(prefix, localname, nsURI, doc)
      CType(doc, LineInfoDocument).IncrementElementCount()
   End Sub 'New
End Class 'LineInfoElement
 _ 'End LineInfoElement class.

Public Class Test

   Private filename As [String] = "book.xml"

   Public Shared Sub Main()

      Dim doc As New LineInfoDocument()
      doc.Load(filename)
      Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount())
   End Sub
End Class
```

```csharp
using System;
using System.Xml;
using System.IO;

class LineInfoDocument : XmlDocument {

  int elementCount;
  internal LineInfoDocument():base() {
    elementCount = 0;
  }

  public override XmlElement CreateElement( string prefix, string localname, string nsURI) {
    LineInfoElement elem = new LineInfoElement(prefix, localname, nsURI, this );
    return elem;
  }

  public void IncrementElementCount() {
     elementCount++;
  }

  public int GetCount() {
     return elementCount;
  }
} // End LineInfoDocument class.

class LineInfoElement:XmlElement {

    internal LineInfoElement( string prefix, string localname, string nsURI, XmlDocument doc ):base( prefix,localname,nsURI, doc ){
      ((LineInfoDocument)doc).IncrementElementCount();
    }
} // End LineInfoElement class.

public class Test {

  const String filename = "book.xml";
  public static void Main() {

     LineInfoDocument doc =new LineInfoDocument();
     doc.Load(filename);
     Console.WriteLine("Number of elements in {0}: {1}", filename, doc.GetCount());

  }
}
```

#### <a name="input"></a><span data-ttu-id="18f4f-128">入力</span><span class="sxs-lookup"><span data-stu-id="18f4f-128">Input</span></span>

<span data-ttu-id="18f4f-129">book.xml</span><span class="sxs-lookup"><span data-stu-id="18f4f-129">book.xml</span></span>

```xml
<!--sample XML fragment-->
<book genre='novel' ISBN='1-861001-57-5' misc='sale-item'>
  <title>The Handmaid's Tale</title>
  <price>14.95</price>
</book>
```

#### <a name="output"></a><span data-ttu-id="18f4f-130">Output</span><span class="sxs-lookup"><span data-stu-id="18f4f-130">Output</span></span>

```console
Number of elements in book.xml: 3
```

## <a name="node-event-handler"></a><span data-ttu-id="18f4f-131">ノード イベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="18f4f-131">Node Event Handler</span></span>

<span data-ttu-id="18f4f-132">.NET Framework による DOM の実装には、XML ドキュメントのノードが変更されたときにイベントを受け取って処理できるようにする、イベント システムも含まれています。</span><span class="sxs-lookup"><span data-stu-id="18f4f-132">The .NET Framework implementation of the DOM also includes an event system that enables you to receive and handle events when nodes in an XML document change.</span></span> <span data-ttu-id="18f4f-133"><xref:System.Xml.XmlNodeChangedEventHandler> クラスと <xref:System.Xml.XmlNodeChangedEventArgs> クラスを使用して、`NodeChanged` イベント、`NodeChanging` イベント、`NodeInserted` イベント、`NodeInserting` イベント、`NodeRemoved` イベント、および `NodeRemoving` イベントをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-133">Using the <xref:System.Xml.XmlNodeChangedEventHandler> and <xref:System.Xml.XmlNodeChangedEventArgs> classes, you can capture `NodeChanged`, `NodeChanging`, `NodeInserted`, `NodeInserting`, `NodeRemoved`, and `NodeRemoving` events.</span></span>

<span data-ttu-id="18f4f-134">イベント処理プロセスは、派生クラスでも、元の DOM クラスとまったく同じように動作します。</span><span class="sxs-lookup"><span data-stu-id="18f4f-134">The event-handling process works exactly the same in derived classes as it would in the original DOM classes.</span></span>

<span data-ttu-id="18f4f-135">ノード イベント処理については、「[イベント](../../events/index.md)」と「<xref:System.Xml.XmlNodeChangedEventHandler>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18f4f-135">For more information regarding node event handling, see [Events](../../events/index.md) and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>

## <a name="default-attributes-and-the-createelement-method"></a><span data-ttu-id="18f4f-136">既定の属性と CreateElement メソッド</span><span class="sxs-lookup"><span data-stu-id="18f4f-136">Default Attributes and the CreateElement Method</span></span>

<span data-ttu-id="18f4f-137">派生クラスの <xref:System.Xml.XmlDocument.CreateElement%2A> メソッドをオーバーライドした場合は、ドキュメントの編集中に新しい要素を作成しても、既定の属性は追加されません。</span><span class="sxs-lookup"><span data-stu-id="18f4f-137">If you are overriding the <xref:System.Xml.XmlDocument.CreateElement%2A> method in a derived class, default attributes are not added when you are creating new elements while editing the document.</span></span> <span data-ttu-id="18f4f-138">これは編集中だけの問題です。</span><span class="sxs-lookup"><span data-stu-id="18f4f-138">This is only an issue while editing.</span></span> <span data-ttu-id="18f4f-139"><xref:System.Xml.XmlDocument.CreateElement%2A> メソッドが既定の属性を <xref:System.Xml.XmlDocument> に追加する機能を実行するため、この機能は <xref:System.Xml.XmlDocument.CreateElement%2A> メソッドにコーディングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="18f4f-139">Because the <xref:System.Xml.XmlDocument.CreateElement%2A> method is responsible for adding default attributes to an <xref:System.Xml.XmlDocument>, you must code this functionality in the <xref:System.Xml.XmlDocument.CreateElement%2A> method.</span></span> <span data-ttu-id="18f4f-140">既定の属性が含まれた <xref:System.Xml.XmlDocument> を読み込めば、既定の属性が正しく処理されます。</span><span class="sxs-lookup"><span data-stu-id="18f4f-140">If you are loading an <xref:System.Xml.XmlDocument> that includes default attributes, they will be handled correctly.</span></span> <span data-ttu-id="18f4f-141">既定の属性の詳細については、「[DOM の要素に対する新しい属性の作成](creating-new-attributes-for-elements-in-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18f4f-141">For more information on default attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="18f4f-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="18f4f-142">See also</span></span>

- [<span data-ttu-id="18f4f-143">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="18f4f-143">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
