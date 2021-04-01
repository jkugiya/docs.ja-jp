---
description: '詳細情報: XPathNavigator によるノードの一致'
title: XPathNavigator によるノードの一致
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: d142490829473d0891c5b2f18b1c3ec9e7ace426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732008"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="90a77-103">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="90a77-103">Matching Nodes using XPathNavigator</span></span>

<span data-ttu-id="90a77-104"><xref:System.Xml.XPath.XPathNavigator> クラスは、ノードが XPath 式に一致するかどうかを調べる <xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="90a77-104">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="90a77-105"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは XPath 式を入力として取り、現在のノードが与えられた XPath 式またはコンパイル済み <xref:System.Boolean> オブジェクトと一致するかどうかを示す <xref:System.Xml.XPath.XPathExpression> を返します。</span><span class="sxs-lookup"><span data-stu-id="90a77-105">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="90a77-106">ノードの一致</span><span class="sxs-lookup"><span data-stu-id="90a77-106">Matching Nodes</span></span>  

 <span data-ttu-id="90a77-107"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは、現在のノードが指定した XPath 式と一致すると `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="90a77-107">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="90a77-108">たとえば次のコード サンプルで、<xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは、現在のノードが要素 `true` であり、要素 `b` が属性 `b` を持つ場合に `c` を返します。</span><span class="sxs-lookup"><span data-stu-id="90a77-108">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90a77-109"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは <xref:System.Xml.XPath.XPathNavigator> の状態を変えません。</span><span class="sxs-lookup"><span data-stu-id="90a77-109">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="90a77-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="90a77-110">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="90a77-111">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="90a77-111">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="90a77-112">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="90a77-112">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="90a77-113">XPathNavigator による XPath 式の評価</span><span class="sxs-lookup"><span data-stu-id="90a77-113">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="90a77-114">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="90a77-114">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="90a77-115">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="90a77-115">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="90a77-116">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="90a77-116">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
