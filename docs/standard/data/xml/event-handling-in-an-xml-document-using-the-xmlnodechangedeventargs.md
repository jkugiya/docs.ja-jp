---
description: '詳細情報: XmlNodeChangedEventArgs による XML ドキュメントのイベント処理'
title: XmlNodeChangedEventArgs による XML ドキュメントのイベント処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fe844e3-5b6f-4fe7-ad15-22459501738b
ms.openlocfilehash: 6d7a263e0931b8de58a3e7e4ec10e29f6c723b1c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783327"
---
# <a name="event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs"></a><span data-ttu-id="17164-103">XmlNodeChangedEventArgs による XML ドキュメントのイベント処理</span><span class="sxs-lookup"><span data-stu-id="17164-103">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>

<span data-ttu-id="17164-104">イベント処理のために **XmlDocument** オブジェクトに登録されたイベント ハンドラーでは、渡された引数が **XmlNodeChangedEventArgs** によってカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="17164-104">The **XmlNodeChangedEventArgs** encapsulates the arguments passed to the event handlers registered on the **XmlDocument** object for handling events.</span></span> <span data-ttu-id="17164-105">各イベントとその発生するタイミングを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="17164-105">The events and a description of when they are fired is given in the following table.</span></span>  
  
|<span data-ttu-id="17164-106">event</span><span class="sxs-lookup"><span data-stu-id="17164-106">Event</span></span>|<span data-ttu-id="17164-107">発生するタイミング</span><span class="sxs-lookup"><span data-stu-id="17164-107">Fired</span></span>|  
|-----------|-----------|  
|<xref:System.Xml.XmlDocument.NodeInserting>|<span data-ttu-id="17164-108">現在のドキュメントに属するノードが別のノードに挿入されるとき。</span><span class="sxs-lookup"><span data-stu-id="17164-108">When a node belonging to the current document is about to be inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeInserted>|<span data-ttu-id="17164-109">現在のドキュメントに属するノードが別のノードに挿入されたとき。</span><span class="sxs-lookup"><span data-stu-id="17164-109">When a node belonging to the current document has been inserted into another node.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoving>|<span data-ttu-id="17164-110">このドキュメントに属するノードがドキュメントから削除されるとき。</span><span class="sxs-lookup"><span data-stu-id="17164-110">When a node belonging to this document is about to be removed from the document.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeRemoved>|<span data-ttu-id="17164-111">このドキュメントに属するノードがその親から削除されたとき。</span><span class="sxs-lookup"><span data-stu-id="17164-111">When a node belonging to this document has been removed from its parent.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanging>|<span data-ttu-id="17164-112">ノードの値が変更されるとき。</span><span class="sxs-lookup"><span data-stu-id="17164-112">When the value of a node is about to be changed.</span></span>|  
|<xref:System.Xml.XmlDocument.NodeChanged>|<span data-ttu-id="17164-113">ノードの値が変更されたとき。</span><span class="sxs-lookup"><span data-stu-id="17164-113">When the value of a node has been changed.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="17164-114">**XmlDataDocument** のメモリの用途が **DataSet** ストレージの利用に完全に最適化されている場合は、基になる **DataSet** が変更された場合でも、**XmlDataDocument** では上に示したどのイベントも発生しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="17164-114">If the **XmlDataDocument** memory usage is fully optimized to use **DataSet** storage, the **XmlDataDocument** might not raise any of the events listed above when changes are made to the underlying **DataSet**.</span></span> <span data-ttu-id="17164-115">これらのイベントが必要な場合は、**XmlDocument** 全体を 1 回走査して、メモリ使用の最適化が完全でない状態にします。</span><span class="sxs-lookup"><span data-stu-id="17164-115">If you need these events, you must traverse the whole **XmlDocument** once to make the memory usage non-fully optimized.</span></span>  
  
 <span data-ttu-id="17164-116">イベント ハンドラーを定義する方法、およびイベント ハンドラーをイベントに追加する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="17164-116">The following code example shows how to define an event handler and how to add the event handler to an event.</span></span>  
  
```vb  
' Attach the event handler, NodeInsertedHandler, to the NodeInserted  
' event.  
Dim doc as XmlDocument = new XmlDocument()  
Dim XmlNodeChgEHdlr as XmlNodeChangedEventHandler = new XmlNodeChangedEventHandler(addressof MyNodeChangedEvent)
AddHandler doc.NodeInserted, XmlNodeChgEHdlr
  
Dim n as XmlNode = doc.CreateElement( "element" )  
Console.WriteLine( "Before Event Inserting" )
  
' This is the point where the new node is being inserted in the tree,  
' and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n )  
Console.WriteLine( "After Event Inserting" )
  
' Define the event handler that handles the NodeInserted event.  
sub NodeInsertedHandler(src as Object, args as XmlNodeChangedEventArgs)  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!")  
end sub  
```  
  
```csharp  
// Attach the event handler, NodeInsertedHandler, to the NodeInserted  
// event.  
XmlDocument doc = new XmlDocument();  
doc.NodeInserted += new XmlNodeChangedEventHandler(NodeInsertedHandler);  
XmlNode n = doc.CreateElement( "element" );  
Console.WriteLine( "Before Event Inserting" );  
  
// This is the point where the new node is being inserted in the tree,  
// and this is the point where the NodeInserted event is raised.  
doc.AppendChild( n );  
Console.WriteLine( "After Event Inserting" );
  
// Define the event handler that handles the NodeInserted event.  
void NodeInsertedHandler(Object src, XmlNodeChangedEventArgs args)  
{  
    Console.WriteLine("Node " + args.Node.Name + " inserted!!");  
}  
```  
  
 <span data-ttu-id="17164-117">XML ドキュメント オブジェクト モデル (DOM) の操作の中には、複数のイベントが発生する複合操作があります。</span><span class="sxs-lookup"><span data-stu-id="17164-117">Some XML Document Object Model (DOM) operations are compound operations that can result in multiple events being fired.</span></span> <span data-ttu-id="17164-118">たとえば **AppendChild** では、追加されるノードを以前の親から削除する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="17164-118">For example, **AppendChild** may also have to remove the node being appended from its previous parent.</span></span> <span data-ttu-id="17164-119">この場合は、最初に **NodeRemoved** イベントが発生し、次に **NodeInserted** イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="17164-119">In this case, you see a **NodeRemoved** event fired first, followed by a **NodeInserted** event.</span></span> <span data-ttu-id="17164-120">**InnerXml** を設定する操作なども、複数のイベントが発生する結果になります。</span><span class="sxs-lookup"><span data-stu-id="17164-120">Operations like setting **InnerXml** could result in multiple events.</span></span>  
  
 <span data-ttu-id="17164-121">イベント ハンドラーを作成する方法および **NodeInserted** イベントを処理する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="17164-121">The following code example shows the creation of the event handler and the handling of the **NodeInserted** event.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports Microsoft.VisualBasic  
  
Public Class Sample  
  
    Private Const filename As String = "books.xml"  
  
    Shared Sub Main()  
        Dim mySample As Sample = New Sample()  
        mySample.Run(filename)  
    End Sub  
  
    Public Sub Run(ByVal args As String)  
        ' Create and load the XML document.  
        Console.WriteLine("Loading file 0 ...", args)  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.Load(args)  
  
        ' Create the event handlers.  
        Dim XmlNodeChgEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeChangedEvent)  
        Dim XmlNodeInsrtEHdlr As XmlNodeChangedEventHandler = New XmlNodeChangedEventHandler(AddressOf MyNodeInsertedEvent)  
        AddHandler doc.NodeChanged, XmlNodeChgEHdlr  
        AddHandler doc.NodeInserted, XmlNodeInsrtEHdlr  
  
        ' Change the book price.  
        doc.DocumentElement.LastChild.InnerText = "5.95"  
  
        ' Add a new element.  
        Dim newElem As XmlElement = doc.CreateElement("style")  
        newElem.InnerText = "hardcover"  
        doc.DocumentElement.AppendChild(newElem)  
  
        Console.WriteLine(Chr(13) + Chr(10) + "Display the modified XML...")  
        Console.WriteLine(doc.OuterXml)  
    End Sub  
  
    ' Handle the NodeChanged event.  
    Public Sub MyNodeChangedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Changed Event: <0> changed", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value  0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
    ' Handle the NodeInserted event.  
    Public Sub MyNodeInsertedEvent(ByVal src As Object, ByVal args As XmlNodeChangedEventArgs)  
        Console.Write("Node Inserted Event: <0> inserted", args.Node.Name)  
        If Not (args.Node.Value Is Nothing) Then  
            Console.WriteLine(" with value 0", args.Node.Value)  
        Else  
            Console.WriteLine("")  
        End If  
    End Sub  
  
End Class        ' End class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  private const String filename = "books.xml";  
  
  public static void Main()  
  {  
     Sample mySample = new Sample();  
     mySample.Run(filename);  
  }  
  
  public void Run(String args)  
  {  
  
     // Create and load the XML document.  
     Console.WriteLine ("Loading file {0} ...", args);  
     XmlDocument doc = new XmlDocument();  
     doc.Load (args);  
  
     // Create the event handlers.  
     doc.NodeChanged += new XmlNodeChangedEventHandler(this.MyNodeChangedEvent);  
     doc.NodeInserted += new XmlNodeChangedEventHandler(this.MyNodeInsertedEvent);  
  
     // Change the book price.  
     doc.DocumentElement.LastChild.InnerText = "5.95";  
  
     // Add a new element.  
     XmlElement newElem = doc.CreateElement("style");  
     newElem.InnerText = "hardcover";  
     doc.DocumentElement.AppendChild(newElem);  
  
     Console.WriteLine("\r\nDisplay the modified XML...");  
     Console.WriteLine(doc.OuterXml);
  
  }  
  
  // Handle the NodeChanged event.  
  public void MyNodeChangedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Changed Event: <{0}> changed", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value  {0}", args.Node.Value);  
     }  
     else  
       Console.WriteLine("");  
  }  
  
  // Handle the NodeInserted event.  
  public void MyNodeInsertedEvent(Object src, XmlNodeChangedEventArgs args)  
  {  
     Console.Write("Node Inserted Event: <{0}> inserted", args.Node.Name);  
     if (args.Node.Value != null)  
     {  
        Console.WriteLine(" with value {0}", args.Node.Value);  
     }  
     else  
        Console.WriteLine("");  
  }  
  
} // End class
```  
  
 <span data-ttu-id="17164-122">詳細については、次のトピックを参照してください。 <xref:System.Xml.XmlNodeChangedEventArgs> および <xref:System.Xml.XmlNodeChangedEventHandler></span><span class="sxs-lookup"><span data-stu-id="17164-122">For more information, see <xref:System.Xml.XmlNodeChangedEventArgs> and <xref:System.Xml.XmlNodeChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17164-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="17164-123">See also</span></span>

- [<span data-ttu-id="17164-124">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="17164-124">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
