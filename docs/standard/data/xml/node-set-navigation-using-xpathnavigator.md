---
description: '詳細情報: XPathNavigator を使用するノード セットのナビゲーション'
title: XPathNavigator を使用するノード セットのナビゲーション
ms.date: 03/30/2017
ms.assetid: 1a954b41-7173-40bc-8544-d430f209b1e5
ms.openlocfilehash: d4e902cbe8cf93fe753c9cbdd01d6a369152c092
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675963"
---
# <a name="node-set-navigation-using-xpathnavigator"></a><span data-ttu-id="9ec09-103">XPathNavigator を使用するノード セットのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="9ec09-103">Node Set Navigation Using XPathNavigator</span></span>

<span data-ttu-id="9ec09-104"><xref:System.Xml.XPath.XPathDocument> クラスのノード セット ナビゲーション メソッドを使用して、<xref:System.Xml.XmlDocument> または <xref:System.Xml.XPath.XPathNavigator> オブジェクト内のノード間を移動できます。</span><span class="sxs-lookup"><span data-stu-id="9ec09-104">You can navigate over nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="9ec09-105">すべてのノード間の移動、または <xref:System.Xml.XPath.XPathNavigator> クラスの選択メソッドによって返される選択されたノード セット間を移動できます。</span><span class="sxs-lookup"><span data-stu-id="9ec09-105">You can navigate over all the nodes or over a selected set of nodes returned by one of the selection methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="element-node-set-navigation"></a><span data-ttu-id="9ec09-106">要素ノード セットのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="9ec09-106">Element Node Set Navigation</span></span>  

 <span data-ttu-id="9ec09-107"><xref:System.Xml.XPath.XPathNavigator> クラスは、要素ノードの移動に使用されるいくつかのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-107">The <xref:System.Xml.XPath.XPathNavigator> class provides several methods used to navigate element nodes.</span></span> <span data-ttu-id="9ec09-108">利用可能なナビゲーション メソッドおよびその移動方法を次の表に示します。これには、属性および名前空間のノードのナビゲートに使用されるメソッドは含まれません。</span><span class="sxs-lookup"><span data-stu-id="9ec09-108">The following table shows the navigation methods available and a description of how they move; this does not include methods used to navigate attribute and namespace nodes.</span></span>  
  
 <span data-ttu-id="9ec09-109"><xref:System.Xml.XPath.XPathNavigator> オブジェクトでノードを選択する方法については、「[XPathNavigator を使用した XML データの選択、評価、および照合](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ec09-109">For more information about selecting nodes in an <xref:System.Xml.XPath.XPathNavigator> object, see [Selecting, Evaluating and Matching XML Data using XPathNavigator](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md).</span></span> <span data-ttu-id="9ec09-110">属性ノードと名前空間ノードをナビゲートする方法については、「[XPathNavigator を使用する属性と名前空間のナビゲーション](attribute-and-namespace-node-navigation-using-xpathnavigator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ec09-110">For more information about navigating attribute and namespace nodes, see [Attribute and Namespace Node Navigation Using XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md).</span></span>  
  
|<span data-ttu-id="9ec09-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="9ec09-111">Method</span></span>|<span data-ttu-id="9ec09-112">説明</span><span class="sxs-lookup"><span data-stu-id="9ec09-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>|<span data-ttu-id="9ec09-113"><xref:System.Xml.XPath.XPathNavigator> を指定された <xref:System.Xml.XPath.XPathNavigator> と同じ位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-113">Moves the <xref:System.Xml.XPath.XPathNavigator> to the same position of the <xref:System.Xml.XPath.XPathNavigator> specified.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>|<span data-ttu-id="9ec09-114"><xref:System.Xml.XPath.XPathNavigator> を現在のノードの子ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-114">Moves the <xref:System.Xml.XPath.XPathNavigator> to a child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>|<span data-ttu-id="9ec09-115"><xref:System.Xml.XPath.XPathNavigator> を現在のノードの最初の兄弟ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-115">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>|<span data-ttu-id="9ec09-116"><xref:System.Xml.XPath.XPathNavigator> を現在のノードの最初の子ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-116">Moves the <xref:System.Xml.XPath.XPathNavigator> to the first child node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToFollowing%2A>|<span data-ttu-id="9ec09-117"><xref:System.Xml.XPath.XPathNavigator> をドキュメント順で指定された要素に移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-117">Moves the <xref:System.Xml.XPath.XPathNavigator> to the specified element in document order.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>|<span data-ttu-id="9ec09-118"><xref:System.Xml.XPath.XPathNavigator> を、与えられた `ID` に一致する値の <xref:System.String> 型の属性を持つノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-118">Moves the <xref:System.Xml.XPath.XPathNavigator> to the node that has an attribute of type `ID` with a value that matches the given <xref:System.String>.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>|<span data-ttu-id="9ec09-119"><xref:System.Xml.XPath.XPathNavigator> を現在のノードの次の兄弟ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-119">Moves the <xref:System.Xml.XPath.XPathNavigator> to the next sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>|<span data-ttu-id="9ec09-120"><xref:System.Xml.XPath.XPathNavigator> を現在のノードの親ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-120">Moves the <xref:System.Xml.XPath.XPathNavigator> to the parent node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>|<span data-ttu-id="9ec09-121"><xref:System.Xml.XPath.XPathNavigator> を現在のノードの前の兄弟ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-121">Moves the <xref:System.Xml.XPath.XPathNavigator> to the previous sibling node of the current node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.MoveToRoot%2A>|<span data-ttu-id="9ec09-122"><xref:System.Xml.XPath.XPathNavigator> を XML ドキュメントのルート ノードに移動します。</span><span class="sxs-lookup"><span data-stu-id="9ec09-122">Moves the <xref:System.Xml.XPath.XPathNavigator> to the root node of the XML document.</span></span>|  
  
## <a name="comments-and-processing-instruction-node-navigation"></a><span data-ttu-id="9ec09-123">コメントおよび処理命令ノードのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="9ec09-123">Comments and Processing Instruction Node Navigation</span></span>  

 <span data-ttu-id="9ec09-124">次の <xref:System.Xml.XPath.XPathNavigator> クラスのメソッドは XML ドキュメント内の他のノードからコメントまたは処理命令に移動するのに有効です。</span><span class="sxs-lookup"><span data-stu-id="9ec09-124">The following <xref:System.Xml.XPath.XPathNavigator> class methods are valid for moving to comments or processing instructions from other nodes in an XML document.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToNext%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToPrevious%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToFirstChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToParent%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.MoveToId%2A>  
  
## <a name="see-also"></a><span data-ttu-id="9ec09-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ec09-125">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="9ec09-126">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="9ec09-126">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="9ec09-127">XPathNavigator を使用する属性と名前空間のナビゲーション</span><span class="sxs-lookup"><span data-stu-id="9ec09-127">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="9ec09-128">XpathNavigator を使用した XML データの抽出</span><span class="sxs-lookup"><span data-stu-id="9ec09-128">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="9ec09-129">厳密に型指定された XML データへの XPathNavigator を使用したアクセス</span><span class="sxs-lookup"><span data-stu-id="9ec09-129">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
