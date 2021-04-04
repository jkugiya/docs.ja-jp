---
title: 大きな XML ドキュメントのストリーミング変換を実行する方法 - LINQ to XML
description: 大きな XML ドキュメントのストリーミング変換を実行して、メモリ占有領域を小さくする方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5f16d1f8-5370-4b55-b0c8-e497df163037
ms.openlocfilehash: f4dc6613d53580050450d11e51fcbf82ddc7517a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412088"
---
# <a name="how-to-perform-streaming-transform-of-large-xml-documents-linq-to-xml"></a><span data-ttu-id="d5900-103">大きな XML ドキュメントのストリーミング変換を実行する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d5900-103">How to perform streaming transform of large XML documents (LINQ to XML)</span></span>

<span data-ttu-id="d5900-104">大きな XML ファイルを変換して、アプリケーションのメモリ使用量を予想できるようにアプリケーションを作成しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="d5900-104">Sometimes you have to transform large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="d5900-105">非常に大きな XML ファイルを XML ツリーに設定しようとすると、ファイルのサイズに比例してメモリが過剰に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5900-105">If you try to populate an XML tree with a very large XML file, your memory usage will be proportional to the size of the file (that is, excessive).</span></span> <span data-ttu-id="d5900-106">したがって、代わりにストリーミングの手法を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d5900-106">Therefore, you should use a streaming technique instead.</span></span>

<span data-ttu-id="d5900-107">ストリーミングの手法は、ソース ドキュメントを 1 回だけ処理する必要がある場合に適しており、ドキュメントの順序で要素を処理できます。</span><span class="sxs-lookup"><span data-stu-id="d5900-107">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="d5900-108"><xref:System.Linq.Enumerable.OrderBy%2A> などの一部の標準クエリ演算子では、ソースが反復処理され、すべてのデータが収集され並べ替えられて、最終的にはシーケンス内の最初の項目が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d5900-108">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="d5900-109">最初の項目を生成する前にソースを具体化するクエリ演算子を使用すると、アプリケーションのメモリ使用量を低く維持することができないので注意してください。</span><span class="sxs-lookup"><span data-stu-id="d5900-109">Note that if you use a query operator that materializes its source before yielding the first item, you won't retain a small memory footprint for your application.</span></span>

<span data-ttu-id="d5900-110">「[ヘッダー情報にアクセスして XML フラグメントをストリーム出力する方法](stream-xml-fragments-access-header-information.md)」の手法を使用しても、変換されたドキュメントが含まれた XML ツリーをアセンブルしようとすると、メモリが過剰に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d5900-110">Even if you use the technique described in [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md), if you try to assemble an XML tree that contains the transformed document, memory usage will be too great.</span></span>

<span data-ttu-id="d5900-111">主な方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="d5900-111">There are two main approaches.</span></span> <span data-ttu-id="d5900-112">1 つは、<xref:System.Xml.Linq.XStreamingElement> の遅延処理の特性を使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="d5900-112">One approach is to use the deferred processing characteristics of <xref:System.Xml.Linq.XStreamingElement>.</span></span> <span data-ttu-id="d5900-113">もう 1 つは、<xref:System.Xml.XmlWriter> を作成し、LINQ to XML の機能を使用して <xref:System.Xml.XmlWriter> に要素を書き込む方法です。</span><span class="sxs-lookup"><span data-stu-id="d5900-113">Another approach is to create an <xref:System.Xml.XmlWriter>, and use the capabilities of LINQ to XML to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="d5900-114">この記事では、両方の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d5900-114">This article demonstrates both approaches.</span></span>

## <a name="example-use-the-deferred-execution-capabilities-of-xstreamingelement-to-stream-the-output"></a><span data-ttu-id="d5900-115">例: `XStreamingElement` の遅延実行機能を使用してストリーム出力する</span><span class="sxs-lookup"><span data-stu-id="d5900-115">Example: Use the deferred execution capabilities of `XStreamingElement` to stream the output</span></span>

<span data-ttu-id="d5900-116">「[ヘッダー情報にアクセスして XML フラグメントをストリーム出力する方法](stream-xml-fragments-access-header-information.md)」の例を基に構築した例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d5900-116">The following example builds on the example in [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md).</span></span>

<span data-ttu-id="d5900-117">この例では、<xref:System.Xml.Linq.XStreamingElement> の遅延実行機能を使用してストリーム出力しています。</span><span class="sxs-lookup"><span data-stu-id="d5900-117">This example uses the deferred execution capabilities of <xref:System.Xml.Linq.XStreamingElement> to stream the output.</span></span> <span data-ttu-id="d5900-118">この例を使用すると、メモリ使用量を低く抑えながら、非常に大きなドキュメントを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="d5900-118">This example can transform a very large document while maintaining a small memory footprint.</span></span>

<span data-ttu-id="d5900-119">カスタム軸 (`StreamCustomerItem`) は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、次に示す Source.xml ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="d5900-119">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="d5900-120">ただし、より堅牢に実装する場合は、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="d5900-120">A more robust implementation, however, would be prepared to parse an invalid document.</span></span>

<span data-ttu-id="d5900-121">ソース ドキュメント Source.xml を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d5900-121">The following is the source document, Source.xml:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root>
  <Customer>
    <Name>A. Datum Corporation</Name>
    <Item>
      <Key>0001</Key>
    </Item>
    <Item>
      <Key>0002</Key>
    </Item>
    <Item>
      <Key>0003</Key>
    </Item>
    <Item>
      <Key>0004</Key>
    </Item>
  </Customer>
  <Customer>
    <Name>Fabrikam, Inc.</Name>
    <Item>
      <Key>0005</Key>
    </Item>
    <Item>
      <Key>0006</Key>
    </Item>
    <Item>
      <Key>0007</Key>
    </Item>
    <Item>
      <Key>0008</Key>
    </Item>
  </Customer>
  <Customer>
    <Name>Southridge Video</Name>
    <Item>
      <Key>0009</Key>
    </Item>
    <Item>
      <Key>0010</Key>
    </Item>
  </Customer>
</Root>
```

```csharp
static IEnumerable<XElement> StreamCustomerItem(string uri)
{
    using (XmlReader reader = XmlReader.Create(uri))
    {
        XElement name = null;
        XElement item = null;

        reader.MoveToContent();

        // Parse the file, save header information when encountered, and yield the
        // Item XElement objects as they're created.
        // Loop through Customer elements.
        while (reader.Read())
        {
            if (reader.NodeType == XmlNodeType.Element
                && reader.Name == "Customer")
            {
                // move to Name element
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.Element &&
                        reader.Name == "Name")
                    {
                        name = XElement.ReadFrom(reader) as XElement;
                        break;
                    }
                }

                // loop through Item elements
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.EndElement)
                        break;
                    if (reader.NodeType == XmlNodeType.Element
                        && reader.Name == "Item")
                    {
                        item = XElement.ReadFrom(reader) as XElement;
                        if (item != null)
                        {
                            XElement tempRoot = new XElement("Root",
                                new XElement(name)
                            );
                            tempRoot.Add(item);
                            yield return item;
                        }
                    }
                }
            }
        }
    }
}

static void Main(string[] args)
{
    XStreamingElement root = new XStreamingElement("Root",
        from el in StreamCustomerItem("Source.xml")
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        )
    );
    root.Save("Test.xml");
    Console.WriteLine(File.ReadAllText("Test.xml"));
}
```

```vb
Module Module1
    Sub Main()
        Dim root = New XStreamingElement("Root",
            From el In New StreamCustomerItem("Source.xml")
            Select <Item>
                       <Customer><%= el.Parent.<Name>.Value %></Customer>
                       <%= el.<Key> %>
                   </Item>
            )
        root.Save("Test.xml")
        Console.WriteLine(My.Computer.FileSystem.ReadAllText("Test.xml"))
    End Sub
End Module

Public Class StreamCustomerItem
    Implements IEnumerable(Of XElement)

    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
    End Sub

    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator
        Return New StreamCustomerItemEnumerator(_uri)
    End Function

    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator
        Return Me.GetEnumerator()
    End Function
End Class

Public Class StreamCustomerItemEnumerator
    Implements IEnumerator(Of XElement)

    Private _current As XElement
    Private _customerName As String
    Private _reader As Xml.XmlReader
    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
        _reader = Xml.XmlReader.Create(_uri)
        _reader.MoveToContent()
    End Sub

    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current
        Get
            Return _current
        End Get
    End Property

    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current
        Get
            Return Me.Current
        End Get
    End Property

    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext
        Dim item As XElement
        Dim name As XElement

        ' Parse the file, save header information when encountered, and return the
        ' current Item XElement.

        ' loop through Customer elements
        While _reader.Read()
            If _reader.NodeType = Xml.XmlNodeType.Element Then
                Select Case _reader.Name
                    Case "Customer"
                        ' move to Name element
                        While _reader.Read()

                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso
                                _reader.Name = "Name" Then

                                name = TryCast(XElement.ReadFrom(_reader), XElement)
                                _customerName = If(name IsNot Nothing, name.Value, "")
                                Exit While
                            End If

                        End While
                    Case "Item"
                        item = TryCast(XElement.ReadFrom(_reader), XElement)
                        Dim tempRoot = <Root>
                                           <Name><%= _customerName %></Name>
                                           <%= item %>
                                       </Root>
                        _current = item
                        Return True
                End Select
            End If
        End While

        Return False
    End Function

    Public Sub Reset() Implements IEnumerator.Reset
        _reader = Xml.XmlReader.Create(_uri)
        _reader.MoveToContent()
    End Sub

#Region "IDisposable Support"
    Private disposedValue As Boolean ' To detect redundant calls

    ' IDisposable
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)
        If Not Me.disposedValue Then
            If disposing Then
                _reader.Close()
            End If
        End If
        Me.disposedValue = True
    End Sub

    Public Sub Dispose() Implements IDisposable.Dispose
        Dispose(True)
        GC.SuppressFinalize(Me)
    End Sub
#End Region

End Class
```

<span data-ttu-id="d5900-122">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d5900-122">This example produces the following output:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0001</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0002</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0003</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0004</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0005</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0006</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0007</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0008</Key>
  </Item>
  <Item>
    <Customer>Southridge Video</Customer>
    <Key>0009</Key>
  </Item>
  <Item>
    <Customer>Southridge Video</Customer>
    <Key>0010</Key>
  </Item>
</Root>
```

## <a name="example-use-linq-to-xml-to-write-elements-to-an-xmlwriter"></a><span data-ttu-id="d5900-123">例: LINQ to XML を使用して XmlWriter に要素を書き込む</span><span class="sxs-lookup"><span data-stu-id="d5900-123">Example: Use LINQ to XML to write elements to an XmlWriter</span></span>

<span data-ttu-id="d5900-124">次の例も、「[ヘッダー情報にアクセスして XML フラグメントをストリーム出力する方法](stream-xml-fragments-access-header-information.md)」の例を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="d5900-124">The following example also builds on the example in [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md).</span></span>

<span data-ttu-id="d5900-125">この例では、LINQ to XML の機能を使用して <xref:System.Xml.XmlWriter> に要素を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="d5900-125">This example uses the capability of LINQ to XML to write elements to an <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="d5900-126">この例を使用すると、メモリ使用量を低く抑えながら、非常に大きなドキュメントを変換することができます。</span><span class="sxs-lookup"><span data-stu-id="d5900-126">This example can transform a very large document while maintaining a small memory footprint.</span></span>

<span data-ttu-id="d5900-127">カスタム軸 (`StreamCustomerItem`) は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、次に示す Source.xml ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="d5900-127">Note that the custom axis (`StreamCustomerItem`) is specifically written so that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the following Source.xml document.</span></span> <span data-ttu-id="d5900-128">ただし、より堅牢に実装する場合は、ソース ドキュメントを XSD で検証するか、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="d5900-128">A more robust implementation, however, would either validate the source document with an XSD, or would be prepared to parse an invalid document.</span></span>

<span data-ttu-id="d5900-129">この例でも、前の例と同じソース ドキュメント Source.xml を使用します。</span><span class="sxs-lookup"><span data-stu-id="d5900-129">This example uses the same source document, Source.xml, as the previous example.</span></span> <span data-ttu-id="d5900-130">生成される出力も同じになります。</span><span class="sxs-lookup"><span data-stu-id="d5900-130">It also produces exactly the same output.</span></span>

<span data-ttu-id="d5900-131"><xref:System.Xml.XmlWriter> に書き込むよりも、<xref:System.Xml.Linq.XStreamingElement> を使用して出力 XML をストリーミングすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d5900-131">Using <xref:System.Xml.Linq.XStreamingElement> for streaming the output XML is preferred to writing to an <xref:System.Xml.XmlWriter>.</span></span>

```csharp
static IEnumerable<XElement> StreamCustomerItem(string uri)
{
    using (XmlReader reader = XmlReader.Create(uri))
    {
        XElement name = null;
        XElement item = null;

        reader.MoveToContent();

        // Parse the file, save header information when encountered, and yield the
        // Item XElement objects as they're created.
        // Loop through Customer elements.
        while (reader.Read())
        {
            if (reader.NodeType == XmlNodeType.Element
                && reader.Name == "Customer")
            {
                // move to Name element
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.Element &&
                        reader.Name == "Name")
                    {
                        name = XElement.ReadFrom(reader) as XElement;
                        break;
                    }
                }

                // Loop through Item elements
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.EndElement)
                        break;
                    if (reader.NodeType == XmlNodeType.Element
                        && reader.Name == "Item")
                    {
                        item = XElement.ReadFrom(reader) as XElement;
                        if (item != null) {
                            XElement tempRoot = new XElement("Root",
                                new XElement(name)
                            );
                            tempRoot.Add(item);
                            yield return item;
                        }
                    }
                }
            }
        }
    }
}

static void Main(string[] args)
{
    IEnumerable<XElement> srcTree =
        from el in StreamCustomerItem("Source.xml")
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        );
    XmlWriterSettings xws = new XmlWriterSettings();
    xws.OmitXmlDeclaration = true;
    xws.Indent = true;
    using (XmlWriter xw = XmlWriter.Create("Output.xml", xws)) {
        xw.WriteStartElement("Root");
        foreach (XElement el in srcTree)
            el.WriteTo(xw);
        xw.WriteEndElement();
    }

    string str = File.ReadAllText("Output.xml");
    Console.WriteLine(str);
}
```

```vb
Module Module1
    Sub Main()
        Dim srcTree =
            From el In New StreamCustomerItem("Source.xml")
            Select <Item>
                       <Customer><%= el.Parent.<Name>.Value %></Customer>
                       <%= el.<Key> %>
                   </Item>

        Dim xws = New Xml.XmlWriterSettings()
        xws.OmitXmlDeclaration = True
        xws.Indent = True
        Using xw = Xml.XmlWriter.Create("Output.xml", xws)
            xw.WriteStartElement("Root")
            For Each el In srcTree
                el.WriteTo(xw)
            Next
            xw.WriteEndElement()
        End Using

        Dim s = My.Computer.FileSystem.ReadAllText("Output.xml")
        Console.WriteLine(s)
    End Sub
End Module

Public Class StreamCustomerItem
    Implements IEnumerable(Of XElement)

    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
    End Sub

    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator
        Return New StreamCustomerItemEnumerator(_uri)
    End Function

    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator
        Return Me.GetEnumerator()
    End Function
End Class

Public Class StreamCustomerItemEnumerator
    Implements IEnumerator(Of XElement)

    Private _current As XElement
    Private _customerName As String
    Private _reader As Xml.XmlReader
    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
        _reader = Xml.XmlReader.Create(_uri)
        _reader.MoveToContent()
    End Sub

    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current
        Get
            Return _current
        End Get
    End Property

    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current
        Get
            Return Me.Current
        End Get
    End Property

    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext
        Dim item As XElement
        Dim name As XElement

        ' Parse the file, save header information when encountered, and return the
        ' current Item XElement.

        ' loop through Customer elements
        While _reader.Read()
            If _reader.NodeType = Xml.XmlNodeType.Element Then
                Select Case _reader.Name
                    Case "Customer"
                        ' move to Name element
                        While _reader.Read()

                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso
                                _reader.Name = "Name" Then

                                name = TryCast(XElement.ReadFrom(_reader), XElement)
                                _customerName = If(name IsNot Nothing, name.Value, "")
                                Exit While
                            End If

                        End While
                    Case "Item"
                        item = TryCast(XElement.ReadFrom(_reader), XElement)
                        Dim tempRoot = <Root>
                                           <Name><%= _customerName %></Name>
                                           <%= item %>
                                       </Root>
                        _current = item
                        Return True
                End Select
            End If
        End While

        Return False
    End Function

    Public Sub Reset() Implements IEnumerator.Reset
        _reader = Xml.XmlReader.Create(_uri)
        _reader.MoveToContent()
    End Sub

#Region "IDisposable Support"
    Private disposedValue As Boolean ' To detect redundant calls

    ' IDisposable
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)
        If Not Me.disposedValue Then
            If disposing Then
                _reader.Close()
            End If
        End If
        Me.disposedValue = True
    End Sub

    Public Sub Dispose() Implements IDisposable.Dispose
        Dispose(True)
        GC.SuppressFinalize(Me)
    End Sub
#End Region

End Class
```

<span data-ttu-id="d5900-132">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d5900-132">This example produces the following output:</span></span>

```xml
<Root>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0001</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0002</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0003</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0004</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0005</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0006</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0007</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0008</Key>
  </Item>
  <Item>
    <Customer>Southridge Video</Customer>
    <Key>0009</Key>
  </Item>
  <Item>
    <Customer>Southridge Video</Customer>
    <Key>0010</Key>
  </Item>
</Root>
```