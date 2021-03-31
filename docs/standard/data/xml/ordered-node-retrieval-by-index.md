---
description: '詳細情報: インデックスによる順序付けされたノードの取得'
title: インデックスによる順序付けられたノードの取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: b6bf7491b4e237a0dcd21c1a75a90160425db922
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783288"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="86b1e-103">インデックスによる順序付けられたノードの取得</span><span class="sxs-lookup"><span data-stu-id="86b1e-103">Ordered Node Retrieval by Index</span></span>

<span data-ttu-id="86b1e-104">W3C (World Wide Web Consortium) の XML ドキュメント オブジェクト モデル (DOM) では、**XmlNamedNodeMap** によって処理される順序付けられていないノード セットとは対照的に、順序付けられたノードのリストを処理する機能を持った NodeList も定義しています。</span><span class="sxs-lookup"><span data-stu-id="86b1e-104">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="86b1e-105">Microsoft .NET Framework の NodeList は **XmlNodeList** と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="86b1e-105">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="86b1e-106">**XmlNodeList** を返すメソッドとプロパティは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="86b1e-106">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="86b1e-107">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="86b1e-107">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="86b1e-108">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="86b1e-108">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="86b1e-109">XmlElement.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="86b1e-109">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="86b1e-110">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="86b1e-110">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="86b1e-111">**XmlNodeList** には **Count** プロパティがあり、次のコード サンプルに示すように、ループを記述して **XmlNodeList** のノードを反復処理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="86b1e-111">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}
```  
  
 <span data-ttu-id="86b1e-112">**Count** プロパティの他に、**XmlNodeList** 内のノード コレクションに対して `foreach` スタイルの反復処理を実行する **GetEnumerator** メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="86b1e-112">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="86b1e-113">`foreach` ステートメントの使用方法を次のコード サンプルに示します。</span><span class="sxs-lookup"><span data-stu-id="86b1e-113">The following code example shows the use of the `foreach` statement.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();
     // Loop over the XmlNodeList using the enumerator ienum
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 <span data-ttu-id="86b1e-114">**XmlNodeList** で利用可能なメソッドとプロパティの詳細については、「<xref:System.Xml.XmlNodeList>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86b1e-114">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b1e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="86b1e-115">See also</span></span>

- [<span data-ttu-id="86b1e-116">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="86b1e-116">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
