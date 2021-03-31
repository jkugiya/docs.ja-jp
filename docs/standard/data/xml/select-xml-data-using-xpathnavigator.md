---
description: '詳細情報: XPathNavigator を使用した XML データの選択'
title: XPathNavigator を使用した XML データの選択
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: d6a5e80ef751838e02e10a0bcec53749fdf7d3ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782963"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="14b7d-103">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="14b7d-103">Select XML Data Using XPathNavigator</span></span>

<span data-ttu-id="14b7d-104"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクト内で XPath 式を使用してノード セットを選択するための一連のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="14b7d-104">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="14b7d-105">選択した後、選択されたノード セットに対して反復して処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="14b7d-105">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="14b7d-106">XPathNavigator の選択メソッド</span><span class="sxs-lookup"><span data-stu-id="14b7d-106">XPathNavigator Selection Methods</span></span>  

 <span data-ttu-id="14b7d-107"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクト内で XPath 式を使用してノード セットを選択するための一連のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="14b7d-107">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="14b7d-108"><xref:System.Xml.XPath.XPathNavigator> クラスは、祖先、子、および子孫のノードを、XPath 式を使用するよりも高速に選択できる最適化された一連のメソッドも提供します。</span><span class="sxs-lookup"><span data-stu-id="14b7d-108">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="14b7d-109">選択されたノード セットは、<xref:System.Xml.XPath.XPathNodeIterator> オブジェクトまたは、選択されたノードが単一の場合は <xref:System.Xml.XPath.XPathNavigator> オブジェクトとして返されます。</span><span class="sxs-lookup"><span data-stu-id="14b7d-109">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="14b7d-110">XPath 式によるノードの選択</span><span class="sxs-lookup"><span data-stu-id="14b7d-110">Selecting Nodes Using XPath Expressions</span></span>  

 <span data-ttu-id="14b7d-111">XPath 式を使用して 1 つのノード セットを選択するには、次のいずれかの選択メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="14b7d-111">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="14b7d-112">呼び出されると、これらのメソッドは <xref:System.Xml.XPath.XPathNodeIterator> オブジェクト、または選択が単一ノードの場合は <xref:System.Xml.XPath.XPathNavigator> オブジェクトを使用して、自由に移動できる 1 つのノード セットを返します。</span><span class="sxs-lookup"><span data-stu-id="14b7d-112">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="14b7d-113"><xref:System.Xml.XPath.XPathNodeIterator> オブジェクトを使用して移動しても、その作成に使用された <xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置に影響ありません。</span><span class="sxs-lookup"><span data-stu-id="14b7d-113">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="14b7d-114"><xref:System.Xml.XPath.XPathNavigator> メソッドから返された <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> オブジェクトは、返された単一ノード上に位置し、この場合もその作成に使用された <xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置には影響しません。</span><span class="sxs-lookup"><span data-stu-id="14b7d-114">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="14b7d-115">次の例は、<xref:System.Xml.XPath.XPathNavigator> オブジェクトからの <xref:System.Xml.XPath.XPathDocument> オブジェクトの作成、<xref:System.Xml.XPath.XPathNavigator.Select%2A> メソッドを使用した <xref:System.Xml.XPath.XPathDocument> オブジェクト内のノードの選択、および <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトを使用した選択ノード上の繰り返し処理について示しています。</span><span class="sxs-lookup"><span data-stu-id="14b7d-115">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 <span data-ttu-id="14b7d-116">この例は、`books.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="14b7d-116">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="14b7d-117">最適化された選択メソッド</span><span class="sxs-lookup"><span data-stu-id="14b7d-117">Optimized Selection Methods</span></span>  

 <span data-ttu-id="14b7d-118"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A>、および <xref:System.Xml.XPath.XPathNavigator> メソッドは、子、子孫、および祖先のノードにアクセスする一般的な XPath 式に相当します。</span><span class="sxs-lookup"><span data-stu-id="14b7d-118">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="14b7d-119">これらのメソッドのパフォーマンスは最適化されており、対応する XPath 式よりも高速です。</span><span class="sxs-lookup"><span data-stu-id="14b7d-119">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="14b7d-120"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>、および <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> メソッドは、<xref:System.Xml.XPath.XPathNodeType> 値または選択するノードのローカル名と名前空間 URI を基にして祖先、子、および子孫のノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="14b7d-120">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="14b7d-121">選択された祖先、子、および子孫のノードは <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトとして返されます。</span><span class="sxs-lookup"><span data-stu-id="14b7d-121">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14b7d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="14b7d-122">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="14b7d-123">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="14b7d-123">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="14b7d-124">XPathNavigator による XPath 式の評価</span><span class="sxs-lookup"><span data-stu-id="14b7d-124">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="14b7d-125">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="14b7d-125">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="14b7d-126">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="14b7d-126">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="14b7d-127">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="14b7d-127">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="14b7d-128">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="14b7d-128">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
