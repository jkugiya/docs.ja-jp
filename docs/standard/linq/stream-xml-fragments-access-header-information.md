---
title: ヘッダー情報にアクセスして XML フラグメントをストリーム配信する方法 - LINQ to XML
description: URI で指定されたファイルから XML フラグメントをストリーム配信するカスタムの軸メソッドを実装して使用する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: d50c29feb305341155257cd215e0292350689e7b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412008"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-linq-to-xml"></a><span data-ttu-id="c94c5-103">ヘッダー情報にアクセスして XML フラグメントをストリーム配信する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c94c5-103">How to stream XML fragments with access to header information (LINQ to XML)</span></span>

<span data-ttu-id="c94c5-104">大きな XML ファイルを任意に読み取り、アプリケーションのメモリ使用量を予想できるようにアプリケーションを作成しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c94c5-104">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="c94c5-105">大きな XML ファイルを XML ツリーに設定しようとすると、ファイルのサイズに比例してメモリが過剰に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-105">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="c94c5-106">したがって、代わりにストリーミングの手法を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c94c5-106">Therefore, you should use a streaming technique instead.</span></span>

<span data-ttu-id="c94c5-107">これを実現する 1 つの選択肢として、<xref:System.Xml.XmlReader> を使用してアプリケーションを作成する方法があります。</span><span class="sxs-lookup"><span data-stu-id="c94c5-107">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c94c5-108">ただし、場合によっては、XML ツリーに対してクエリを実行するとき、LINQ の使用が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="c94c5-108">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="c94c5-109">その場合は、カスタムの軸メソッドを独自に記述できます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-109">If so, you can write your own custom axis method.</span></span> <span data-ttu-id="c94c5-110">詳細については、[LINQ to XML 軸メソッドを記述する方法](write-linq-xml-axis-method.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c94c5-110">For more information, see [How to write a LINQ to XML axis method](write-linq-xml-axis-method.md).</span></span>

<span data-ttu-id="c94c5-111">独自の軸メソッドを記述するには、<xref:System.Xml.XmlReader> を使用して、対象となるノードの 1 つに到達するまでノードを読み取る小さなメソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="c94c5-111">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you're interested.</span></span> <span data-ttu-id="c94c5-112">このメソッドから <xref:System.Xml.Linq.XNode.ReadFrom%2A> が呼び出され、これにより <xref:System.Xml.XmlReader> からデータが読み取られ、XML フラグメントがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-112">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="c94c5-113">さらに、カスタムの軸メソッドを列挙するメソッドに対しては、`yield return` を使用して各フラグメントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-113">It then yields each fragment through `yield return` to the method that's enumerating your custom axis method.</span></span> <span data-ttu-id="c94c5-114">これで、カスタムの軸メソッド上に LINQ クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-114">You can then write LINQ queries on your custom axis method.</span></span>

<span data-ttu-id="c94c5-115">ストリーミングの手法は、ソース ドキュメントを 1 回だけ処理する必要がある場合に適しており、ドキュメントの順序で要素を処理できます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-115">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="c94c5-116"><xref:System.Linq.Enumerable.OrderBy%2A> などの一部の標準クエリ演算子では、ソースが反復処理され、すべてのデータが収集され並べ替えられて、最終的にはシーケンス内の最初の項目が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-116">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="c94c5-117">最初の項目を生成する前にソースを具体化するクエリ演算子を使用すると、メモリ占有領域を低く維持することができません。</span><span class="sxs-lookup"><span data-stu-id="c94c5-117">If you use a query operator that materializes its source before yielding the first item, you won't retain a small memory footprint.</span></span>

## <a name="example-implement-and-use-a-custom-axis-method-that-streams-xml-fragments-from-the-file-specified-by-a-uri"></a><span data-ttu-id="c94c5-118">例: URI で指定されたファイルから XML フラグメントをストリーム配信するカスタムの軸メソッドを実装して使用する</span><span class="sxs-lookup"><span data-stu-id="c94c5-118">Example: Implement and use a custom axis method that streams XML fragments from the file specified by a URI</span></span>

<span data-ttu-id="c94c5-119">ストリーム出力は関心の高い問題となる場合があるため、例を使って説明します。</span><span class="sxs-lookup"><span data-stu-id="c94c5-119">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="c94c5-120">次の XML ドキュメントでは、カスタムの軸メソッドのコンシューマーが、各項目が属している顧客の名前も認識している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c94c5-120">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>

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

<span data-ttu-id="c94c5-121">この例で採用している方法では、ヘッダー情報の監視と保存が行われ、その後でヘッダー情報と列挙される詳細情報の両方が含まれている小さな XML ツリーが構築されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-121">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you're enumerating.</span></span> <span data-ttu-id="c94c5-122">次に、軸メソッドによってこの新しい小さな XML ツリーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-122">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="c94c5-123">これでクエリは、詳細情報だけでなくヘッダー情報にもアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="c94c5-123">The query then has access to the header information as well as the detail information.</span></span>

<span data-ttu-id="c94c5-124">この方法で使用されるメモリは少量です。</span><span class="sxs-lookup"><span data-stu-id="c94c5-124">This approach has a small memory footprint.</span></span> <span data-ttu-id="c94c5-125">詳細な XML フラグメントが個々に生成されるときに、前のフラグメントへの参照は保持されず、そのフラグメントはガベージ コレクションの対象になります。</span><span class="sxs-lookup"><span data-stu-id="c94c5-125">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it's available for garbage collection.</span></span> <span data-ttu-id="c94c5-126">この手法を使用すると、存続期間の短いオブジェクトがヒープ上に多数作成されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-126">This technique creates many short lived objects on the heap.</span></span>

<span data-ttu-id="c94c5-127">次の例では、URI で指定されたファイルから XML フラグメントをストリーム出力する、カスタムの軸メソッドを実装して使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c94c5-127">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="c94c5-128">このカスタムの軸は、`Customer`、`Name`、`Item` の各要素を含んだドキュメントを前提として記述されています。また、それらの要素は、上記の `Source.xml` ドキュメントと同じように配置されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-128">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="c94c5-129">これは単純な実装です。</span><span class="sxs-lookup"><span data-stu-id="c94c5-129">It's a simplistic implementation.</span></span> <span data-ttu-id="c94c5-130">ただし、より堅牢に実装する場合は、無効なドキュメントの解析にも対応するようにします。</span><span class="sxs-lookup"><span data-stu-id="c94c5-130">A more robust implementation would be prepared to parse an invalid document.</span></span>

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

        // loop through Customer elements
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
    XElement xmlTree = new XElement("Root",
        from el in StreamCustomerItem("Source.xml")
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        )
    );
    Console.WriteLine(xmlTree);
}
```

```vb
Module Module1

    Sub Main()
        Dim xmlTree = <Root>
                          <%=
                              From el In New StreamCustomerItem("Source.xml")
                              Let itemKey = CInt(el.<Key>.Value)
                              Where itemKey >= 3 AndAlso itemKey <= 7
                              Select <Item>
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>
                                         <%= el.<Key> %>
                                     </Item>
                          %>
                      </Root>

        Console.WriteLine(xmlTree)
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

 <span data-ttu-id="c94c5-131">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c94c5-131">This code produces the following output:</span></span>

```xml
<Root>
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
</Root>
```
