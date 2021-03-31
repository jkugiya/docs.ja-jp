---
description: '詳細情報: XPathNavigator による XPath 式の評価'
title: XPathNavigator による Xpath 式の評価
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 847f83eb9a41cdd28763c5b1516bee89c04517fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629618"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="3f614-103">XPathNavigator による Xpath 式の評価</span><span class="sxs-lookup"><span data-stu-id="3f614-103">Evaluate XPath Expressions using XPathNavigator</span></span>

<span data-ttu-id="3f614-104"><xref:System.Xml.XPath.XPathNavigator> クラスは、XPath 式を評価する <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3f614-104">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="3f614-105"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドは XPath 式を受け取って評価し、XPath 式の結果に基づいて W3C XPath 型のブール値、数字、文字列、またはノード セットを返します。</span><span class="sxs-lookup"><span data-stu-id="3f614-105">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="3f614-106">Evaluate メソッド</span><span class="sxs-lookup"><span data-stu-id="3f614-106">The Evaluate Method</span></span>  

 <span data-ttu-id="3f614-107"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドは XPath 式を受け取って評価し、XPath 式の結果に基づいて W3C XPath 型のブール値 (<xref:System.Boolean>)、数字 (<xref:System.Double>)、文字列 (<xref:System.String>)、またはノード セット (<xref:System.Xml.XPath.XPathNodeIterator>) を返します。</span><span class="sxs-lookup"><span data-stu-id="3f614-107">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="3f614-108">たとえば、<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドは数値演算メソッドで使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f614-108">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="3f614-109">次のサンプル コードは、`books.xml` ファイル内の本すべての総額を計算します。</span><span class="sxs-lookup"><span data-stu-id="3f614-109">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="3f614-110">この例は、`books.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="3f614-110">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="3f614-111">position 関数と last 関数</span><span class="sxs-lookup"><span data-stu-id="3f614-111">position and last Functions</span></span>  

 <span data-ttu-id="3f614-112"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドはオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="3f614-112">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="3f614-113"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドの 1 つは、パラメーターとして <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3f614-113">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="3f614-114">この特定の <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> メソッドは、現在の評価対象コンテキストを指定するノード セット引数を許可することを除き、パラメーターとして <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> オブジェクトだけを受け取る <xref:System.Xml.XPath.XPathExpression> メソッドと同じです。</span><span class="sxs-lookup"><span data-stu-id="3f614-114">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="3f614-115">XPath の `position()` 関数および `last()` 関数は現在のコンテキスト ノードに相対的であるため、これらの関数ではコンテキストが必須です。</span><span class="sxs-lookup"><span data-stu-id="3f614-115">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="3f614-116">ロケーション ステップで述語として使用される場合を除き、XPath の `position()` 関数および `last()` 関数では、ノード セットへの参照が評価のために必須です。ノード セットへの参照がない場合、`position` 関数および `last` 関数は `0` を返します。</span><span class="sxs-lookup"><span data-stu-id="3f614-116">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f614-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f614-117">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="3f614-118">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="3f614-118">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="3f614-119">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="3f614-119">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3f614-120">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="3f614-120">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="3f614-121">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="3f614-121">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="3f614-122">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="3f614-122">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="3f614-123">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="3f614-123">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
