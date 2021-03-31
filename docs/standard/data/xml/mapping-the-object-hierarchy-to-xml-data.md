---
description: '詳細情報: オブジェクト階層の XML データへのマップ'
title: オブジェクト階層の XML データへのマップ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 450e350b-6a68-4634-a2a5-33f4dc33baf0
ms.openlocfilehash: 1be34c43bc9656288e886c309e665b15cb332524
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732099"
---
# <a name="mapping-the-object-hierarchy-to-xml-data"></a><span data-ttu-id="ab25b-103">オブジェクト階層の XML データへのマップ</span><span class="sxs-lookup"><span data-stu-id="ab25b-103">Mapping the Object Hierarchy to XML Data</span></span>

<span data-ttu-id="ab25b-104">メモリに読み込まれた XML ドキュメントは、ツリーという概念で表現されます。</span><span class="sxs-lookup"><span data-stu-id="ab25b-104">When an XML document is in memory, the conceptual representation is a tree.</span></span> <span data-ttu-id="ab25b-105">プログラミングでは、オブジェクト階層を利用してツリーのノードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ab25b-105">For programming, you have an object hierarchy to access the nodes of the tree.</span></span> <span data-ttu-id="ab25b-106">XML コンテンツがどのようにノードに変換されるかを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ab25b-106">The following example shows you how the XML content becomes nodes.</span></span>  
  
 <span data-ttu-id="ab25b-107">XML が XML ドキュメント オブジェクト モデル (DOM) に読み込まれると、各部がノードに変換されます。これらのノードは、ノード型や値など、ノード自身に関する付加的なメタデータを保持しています。</span><span class="sxs-lookup"><span data-stu-id="ab25b-107">As the XML is read into the XML Document Object Model (DOM), the pieces are translated into nodes, and these nodes retain additional metadata about themselves, such as their node type and values.</span></span> <span data-ttu-id="ab25b-108">ノード型はノードのオブジェクトであり、ノード型によって実行可能なアクションおよび設定や取得が可能なプロパティが決まります。</span><span class="sxs-lookup"><span data-stu-id="ab25b-108">The node type is its object and is what determines what actions can be performed and what properties can be set or retrieved.</span></span>  
  
 <span data-ttu-id="ab25b-109">次のような簡単な XML があるとします。</span><span class="sxs-lookup"><span data-stu-id="ab25b-109">If you have the following simple XML:</span></span>  
  
 <span data-ttu-id="ab25b-110">**入力**</span><span class="sxs-lookup"><span data-stu-id="ab25b-110">**Input**</span></span>  
  
```xml  
<book>  
    <title>The Handmaid's Tale</title>  
</book>  
```  
  
 <span data-ttu-id="ab25b-111">この入力は、メモリ上で次のようなノード ツリーとして表現され、ノード型プロパティが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ab25b-111">The input is represented in memory as the following node tree with the assigned node type property:</span></span>  
  
 <span data-ttu-id="ab25b-112">![サンプル ノード ツリー](media/simple-xml.gif "Simple_XML")</span><span class="sxs-lookup"><span data-stu-id="ab25b-112">![example node tree](media/simple-xml.gif "Simple_XML")</span></span>  
<span data-ttu-id="ab25b-113">book と title のノード ツリー表現</span><span class="sxs-lookup"><span data-stu-id="ab25b-113">Book and title node tree representation</span></span>  
  
 <span data-ttu-id="ab25b-114">`book` 要素は **XmlElement** オブジェクトになり、次の要素の `title` も **XmlElement** になりますが、要素コンテンツは **XmlText** オブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="ab25b-114">The `book` element becomes an **XmlElement** object, the next element, `title`, also becomes an **XmlElement**, while the element content becomes an **XmlText** object.</span></span> <span data-ttu-id="ab25b-115">**XmlElement** のメソッドとプロパティは、**XmlText** オブジェクトで使用できるメソッドとプロパティとは異なります。</span><span class="sxs-lookup"><span data-stu-id="ab25b-115">In looking at the **XmlElement** methods and properties, the methods and properties are different than the methods and properties available on an **XmlText** object.</span></span> <span data-ttu-id="ab25b-116">実行可能なアクションはノード型によって決定されるため、XML マークアップがどのノード型になるかを理解することがきわめて重要です。</span><span class="sxs-lookup"><span data-stu-id="ab25b-116">So knowing what node type the XML markup becomes is vital, as its node type determines the actions that can be performed.</span></span>  
  
 <span data-ttu-id="ab25b-117">XML データを読み込み、ノード型に応じて異なるテキストを書き出す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ab25b-117">The following example reads in XML data and writes out different text, depending on the node type.</span></span> <span data-ttu-id="ab25b-118">入力として、次の **items.xml** という XML データ ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ab25b-118">Using the following XML data file as input, **items.xml**:</span></span>  
  
 <span data-ttu-id="ab25b-119">**入力**</span><span class="sxs-lookup"><span data-stu-id="ab25b-119">**Input**</span></span>  
  
```xml  
<?xml version="1.0"?>  
<!-- This is a sample XML document -->  
<!DOCTYPE Items [<!ENTITY number "123">]>  
<Items>  
  <Item>Test with an entity: &number;</Item>  
  <Item>test with a child element <more/> stuff</Item>  
  <Item>test with a CDATA section <![CDATA[<456>]]> def</Item>  
  <Item>Test with a char entity: A</Item>  
  <!-- Fourteen chars in this element.-->  
  <Item>1234567890ABCD</Item>  
</Items>  
```  
  
 <span data-ttu-id="ab25b-120">**items.xml** ファイルを読み込み、それぞれのノード型の情報を表示するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ab25b-120">The following code example reads the **items.xml** file and displays information for each node type.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
    Private Const filename As String = "items.xml"  
  
    Public Shared Sub Main()  
  
        Dim reader As XmlTextReader = Nothing  
  
        Try  
            ' Load the reader with the data file and
            'ignore all white space nodes.
            reader = New XmlTextReader(filename)  
            reader.WhitespaceHandling = WhitespaceHandling.None  
  
            ' Parse the file and display each of the nodes.  
            While reader.Read()  
                Select Case reader.NodeType  
                    Case XmlNodeType.Element  
                        Console.Write("<{0}>", reader.Name)  
                    Case XmlNodeType.Text  
                        Console.Write(reader.Value)  
                    Case XmlNodeType.CDATA  
                        Console.Write("<![CDATA[{0}]]>", reader.Value)  
                    Case XmlNodeType.ProcessingInstruction  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value)  
                    Case XmlNodeType.Comment  
                        Console.Write("<!--{0}-->", reader.Value)  
                    Case XmlNodeType.XmlDeclaration  
                        Console.Write("<?xml version='1.0'?>")  
                    Case XmlNodeType.Document  
                    Case XmlNodeType.DocumentType  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value)  
                    Case XmlNodeType.EntityReference  
                        Console.Write(reader.Name)  
                    Case XmlNodeType.EndElement  
                        Console.Write("</{0}>", reader.Name)  
                End Select  
            End While  
  
        Finally  
            If Not (reader Is Nothing) Then  
                reader.Close()  
            End If  
        End Try  
    End Sub 'Main ' End class  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    private const String filename = "items.xml";  
  
    public static void Main()  
    {  
        XmlTextReader reader = null;  
  
        try  
        {  
            // Load the reader with the data file and ignore
            // all white space nodes.  
            reader = new XmlTextReader(filename);  
            reader.WhitespaceHandling = WhitespaceHandling.None;  
  
            // Parse the file and display each of the nodes.  
            while (reader.Read())  
            {  
                switch (reader.NodeType)  
                {  
                    case XmlNodeType.Element:  
                        Console.Write("<{0}>", reader.Name);  
                        break;  
                    case XmlNodeType.Text:  
                        Console.Write(reader.Value);  
                        break;  
                    case XmlNodeType.CDATA:  
                        Console.Write("<![CDATA[{0}]]>", reader.Value);  
                        break;  
                    case XmlNodeType.ProcessingInstruction:  
                        Console.Write("<?{0} {1}?>", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.Comment:  
                        Console.Write("<!--{0}-->", reader.Value);  
                        break;  
                    case XmlNodeType.XmlDeclaration:  
                        Console.Write("<?xml version='1.0'?>");  
                        break;  
                    case XmlNodeType.Document:  
                        break;  
                    case XmlNodeType.DocumentType:  
                        Console.Write("<!DOCTYPE {0} [{1}]", reader.Name, reader.Value);  
                        break;  
                    case XmlNodeType.EntityReference:  
                        Console.Write(reader.Name);  
                        break;  
                    case XmlNodeType.EndElement:  
                        Console.Write("</{0}>", reader.Name);  
                        break;  
                }  
            }  
        }  
  
        finally  
        {  
            if (reader != null)  
                reader.Close();  
        }  
    }  
} // End class  
```  
  
 <span data-ttu-id="ab25b-121">この例の出力を確認すると、データからノード型へのマップがわかります。</span><span class="sxs-lookup"><span data-stu-id="ab25b-121">The output from the example reveals the mapping of the data to the node types.</span></span>  
  
 <span data-ttu-id="ab25b-122">**出力**</span><span class="sxs-lookup"><span data-stu-id="ab25b-122">**Output**</span></span>  
  
```xml  
<?xml version='1.0'?><!--This is a sample XML document --><!DOCTYPE Items [<!ENTITY number "123">]<Items><Item>Test with an entity: 123</Item><Item>test with a child element <more> stuff</Item><Item>test with a CDATA section <![CDATA[<456>]]> def</Item><Item>Test with a char entity: A</Item><--Fourteen chars in this element.--><Item>1234567890ABCD</Item></Items>
```  
  
 <span data-ttu-id="ab25b-123">入力と、コードから生成された出力を 1 行ずつ対比させた以下の表を見れば、どのノード テストによってどの出力行が生成されたのかを分析でき、どの XML データがどのノード型になったかがわかります。</span><span class="sxs-lookup"><span data-stu-id="ab25b-123">Taking the input one line at a time and using the output generated from the code, you can use the following table to analyze what node test generated which lines of output, thereby understanding what XML data became what kind of node type.</span></span>  
  
|<span data-ttu-id="ab25b-124">入力</span><span class="sxs-lookup"><span data-stu-id="ab25b-124">Input</span></span>|<span data-ttu-id="ab25b-125">Output</span><span class="sxs-lookup"><span data-stu-id="ab25b-125">Output</span></span>|<span data-ttu-id="ab25b-126">ノード型のテスト</span><span class="sxs-lookup"><span data-stu-id="ab25b-126">Node Type Test</span></span>|  
|-----------|------------|--------------------|  
|\<?xml version="1.0"?>|\<?xml version='1.0'?>|<span data-ttu-id="ab25b-127">XmlNodeType.XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="ab25b-127">XmlNodeType.XmlDeclaration</span></span>|  
|\<!-- This is a sample XML document -->|\<!--This is a sample XML document -->|<span data-ttu-id="ab25b-128">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="ab25b-128">XmlNodeType.Comment</span></span>|  
|<span data-ttu-id="ab25b-129">\<!DOCTYPE Items [\<!ENTITY number "123">]></span><span class="sxs-lookup"><span data-stu-id="ab25b-129">\<!DOCTYPE Items [\<!ENTITY number "123">]></span></span>|<span data-ttu-id="ab25b-130">\<!DOCTYPE Items [\<!ENTITY number "123">]</span><span class="sxs-lookup"><span data-stu-id="ab25b-130">\<!DOCTYPE Items [\<!ENTITY number "123">]</span></span>|<span data-ttu-id="ab25b-131">XmlNodeType.DocumentType</span><span class="sxs-lookup"><span data-stu-id="ab25b-131">XmlNodeType.DocumentType</span></span>|  
|\<Items>|\<Items>|<span data-ttu-id="ab25b-132">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="ab25b-132">XmlNodeType.Element</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="ab25b-133">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="ab25b-133">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ab25b-134">Test with an entity: &number;</span><span class="sxs-lookup"><span data-stu-id="ab25b-134">Test with an entity: &number;</span></span>|<span data-ttu-id="ab25b-135">Test with an entity:123</span><span class="sxs-lookup"><span data-stu-id="ab25b-135">Test with an entity: 123</span></span>|<span data-ttu-id="ab25b-136">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="ab25b-136">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="ab25b-137">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="ab25b-137">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="ab25b-138">XmNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="ab25b-138">XmNodeType.Element</span></span>|  
|<span data-ttu-id="ab25b-139">test with a child element</span><span class="sxs-lookup"><span data-stu-id="ab25b-139">test with a child element</span></span>|<span data-ttu-id="ab25b-140">test with a child element</span><span class="sxs-lookup"><span data-stu-id="ab25b-140">test with a child element</span></span>|<span data-ttu-id="ab25b-141">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="ab25b-141">XmlNodeType.Text</span></span>|  
|\<more>|\<more>|<span data-ttu-id="ab25b-142">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="ab25b-142">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ab25b-143">stuff</span><span class="sxs-lookup"><span data-stu-id="ab25b-143">stuff</span></span>|<span data-ttu-id="ab25b-144">stuff</span><span class="sxs-lookup"><span data-stu-id="ab25b-144">stuff</span></span>|<span data-ttu-id="ab25b-145">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="ab25b-145">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="ab25b-146">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="ab25b-146">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="ab25b-147">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="ab25b-147">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ab25b-148">test with a CDATA section</span><span class="sxs-lookup"><span data-stu-id="ab25b-148">test with a CDATA section</span></span>|<span data-ttu-id="ab25b-149">test with a CDATA section</span><span class="sxs-lookup"><span data-stu-id="ab25b-149">test with a CDATA section</span></span>|<span data-ttu-id="ab25b-150">XmlTest.Text</span><span class="sxs-lookup"><span data-stu-id="ab25b-150">XmlTest.Text</span></span>|  
|<span data-ttu-id="ab25b-151"><![CDATA[\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="ab25b-151"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="ab25b-152"><![CDATA[\<456>]]\></span><span class="sxs-lookup"><span data-stu-id="ab25b-152"><![CDATA[\<456>]]\></span></span>|<span data-ttu-id="ab25b-153">XmlTest.CDATA</span><span class="sxs-lookup"><span data-stu-id="ab25b-153">XmlTest.CDATA</span></span>|  
|<span data-ttu-id="ab25b-154">def</span><span class="sxs-lookup"><span data-stu-id="ab25b-154">def</span></span>|<span data-ttu-id="ab25b-155">def</span><span class="sxs-lookup"><span data-stu-id="ab25b-155">def</span></span>|<span data-ttu-id="ab25b-156">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="ab25b-156">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="ab25b-157">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="ab25b-157">XmlNodeType.EndElement</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="ab25b-158">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="ab25b-158">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ab25b-159">Test with a char entity: &\#65;</span><span class="sxs-lookup"><span data-stu-id="ab25b-159">Test with a char entity: &\#65;</span></span>|<span data-ttu-id="ab25b-160">Test with a char entity:A</span><span class="sxs-lookup"><span data-stu-id="ab25b-160">Test with a char entity: A</span></span>|<span data-ttu-id="ab25b-161">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="ab25b-161">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="ab25b-162">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="ab25b-162">XmlNodeType.EndElement</span></span>|  
|\<!-- Fourteen chars in this element.-->|\<--Fourteen chars in this element.-->|<span data-ttu-id="ab25b-163">XmlNodeType.Comment</span><span class="sxs-lookup"><span data-stu-id="ab25b-163">XmlNodeType.Comment</span></span>|  
|\<Item>|\<Item>|<span data-ttu-id="ab25b-164">XmlNodeType.Element</span><span class="sxs-lookup"><span data-stu-id="ab25b-164">XmlNodeType.Element</span></span>|  
|<span data-ttu-id="ab25b-165">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="ab25b-165">1234567890ABCD</span></span>|<span data-ttu-id="ab25b-166">1234567890ABCD</span><span class="sxs-lookup"><span data-stu-id="ab25b-166">1234567890ABCD</span></span>|<span data-ttu-id="ab25b-167">XmlNodeType.Text</span><span class="sxs-lookup"><span data-stu-id="ab25b-167">XmlNodeType.Text</span></span>|  
|\</Item>|\</Item>|<span data-ttu-id="ab25b-168">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="ab25b-168">XmlNodeType.EndElement</span></span>|  
|\</Items>|\</Items>|<span data-ttu-id="ab25b-169">XmlNodeType.EndElement</span><span class="sxs-lookup"><span data-stu-id="ab25b-169">XmlNodeType.EndElement</span></span>|  
  
 <span data-ttu-id="ab25b-170">有効なアクションの種類と設定および取得できるプロパティの種類はノード型によって決まるため、割り当てられているノード型を知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab25b-170">You must know what node type is assigned, as the node type controls what kinds of actions are valid and what kind of properties you can set and retrieve.</span></span>  
  
 <span data-ttu-id="ab25b-171">空白ノードの作成は、データが DOM に読み込まれるときに **PreserveWhitespace** フラグによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="ab25b-171">Node creation for white space is controlled when the data is loaded into the DOM by the **PreserveWhitespace** flag.</span></span> <span data-ttu-id="ab25b-172">詳細については、「[DOM を読み込むときの空白および有意の空白の処理](white-space-and-significant-white-space-handling-when-loading-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab25b-172">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>  
  
 <span data-ttu-id="ab25b-173">DOM に新しいノードを追加するには、「[XML ドキュメントへのノードの挿入](inserting-nodes-into-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab25b-173">To add new nodes to the DOM, see [Inserting Nodes into an XML Document](inserting-nodes-into-an-xml-document.md).</span></span> <span data-ttu-id="ab25b-174">DOM からノードを削除するには、「[XML ドキュメントからのノード、コンテンツ、値の削除](removing-nodes-content-and-values-from-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab25b-174">To remove nodes from the DOM, see [Removing Nodes, Content, and Values from an XML Document](removing-nodes-content-and-values-from-an-xml-document.md).</span></span> <span data-ttu-id="ab25b-175">DOM のノードのコンテンツを編集するには、「[XML ドキュメントのノード、コンテンツ、値の変更](modifying-nodes-content-and-values-in-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab25b-175">To modify the content of nodes in the DOM, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab25b-176">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab25b-176">See also</span></span>

- [<span data-ttu-id="ab25b-177">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="ab25b-177">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
