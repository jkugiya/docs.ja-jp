---
description: '詳細情報: 名前またはインデックスによる順序付けられていないノードの取得'
title: 名前またはインデックスによる順序付けられていないノードの取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 805f61233a27812f032b83fede2dd8db3d196ba5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782872"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="1dbd7-103">名前またはインデックスによる順序付けられていないノードの取得</span><span class="sxs-lookup"><span data-stu-id="1dbd7-103">Unordered Node Retrieval by Name or Index</span></span>

<span data-ttu-id="1dbd7-104">W3C (World Wide Web Consortium) 仕様で NamedNodeMap として定義されている **XmlNamedNodeMap** は、名前またはインデックスでノードを参照する機能を持っており、順序付けられていないノード セットを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-104">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="1dbd7-105">**XmlNamedNodeMap** にアクセスできるのは、メソッドまたはプロパティから **XmlNamedNodeMap** が返されたときだけです。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-105">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="1dbd7-106">**XmlNamedNodeMap** を返すメソッドやプロパティには、次の 3 つがあります。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-106">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
- <span data-ttu-id="1dbd7-107">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="1dbd7-107">XmlElement.Attributes</span></span>  
  
- <span data-ttu-id="1dbd7-108">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="1dbd7-108">XmlDocumentType.Entities</span></span>  
  
- <span data-ttu-id="1dbd7-109">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="1dbd7-109">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="1dbd7-110">たとえば、**XmlDocumentType.Entities** プロパティは、ドキュメント型宣言で宣言された **XmlEntity** ノードのコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-110">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="1dbd7-111">このコレクションは **XmlNamedNodeMap** として返され、**Count** プロパティを使用してコレクションを反復処理し、エンティティ情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-111">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="1dbd7-112">**XmlNamedNodeMap** の反復処理の例については、「<xref:System.Xml.XmlDocumentType.Entities%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-112">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="1dbd7-113">**XmlAttributeCollection** は **XmlNamedNodeMap** から派生しており、属性だけは変更できますが、記法とエンティティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-113">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="1dbd7-114">属性に対して **XmlNamedNodeMap** を使用すると、XML 名に基づいて属性のノードを取得できます。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-114">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="1dbd7-115">これは、要素ノードの属性コレクションを操作する簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-115">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="1dbd7-116">**XmlNodeList** にも **IEnumerable** インターフェイスが実装されていますが、文字列ではなくインデックス アクセサーを使用するという点で異なります。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-116">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="1dbd7-117">**RemoveNamedItem** メソッドと **SetNamedItem** メソッドは **XmlAttributeCollection** に対してだけ使用します。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-117">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="1dbd7-118">属性コレクションに追加したり、属性コレクションから削除すると、**AttributeCollection** または **XmlNamedNodeMap** のどちらの実装を使用した場合でも、要素の属性コレクションが変更されます。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-118">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="1dbd7-119">属性を移動する方法と新しい属性を作成する方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-119">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );
  
    }  
}  
```  
  
 <span data-ttu-id="1dbd7-120">**AttributeCollection** から属性を削除するコード サンプルについては、「[XmlNamedNodeMap.RemoveNamedItem メソッド](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-120">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span></span> <span data-ttu-id="1dbd7-121">メソッドとプロパティの詳細については、「[XmlNamedNodeMap メンバー](xref:System.Xml.XmlNamedNodeMap)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dbd7-121">For more information on the methods and properties, see [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbd7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1dbd7-122">See also</span></span>

- [<span data-ttu-id="1dbd7-123">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="1dbd7-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
