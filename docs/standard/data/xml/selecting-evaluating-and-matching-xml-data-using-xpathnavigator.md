---
description: '詳細情報: XPathNavigator を使用した XML データの選択、評価、および照合'
title: XPathNavigator を使用した XML データの選択、評価、および照合
ms.date: 03/30/2017
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
ms.openlocfilehash: 2efec77904e458bfc0d6c4db46059d89ffd3a97d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782950"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="00670-103">XPathNavigator を使用した XML データの選択、評価、および照合</span><span class="sxs-lookup"><span data-stu-id="00670-103">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>

<span data-ttu-id="00670-104"><xref:System.Xml.XPath.XPathNavigator> クラスは、XPath クエリによる <xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクト内のノードの選択、XPath 式の結果の評価と検査、および <xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクト内のノードが指定された XPath 式に一致するかどうかの判定のためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="00670-104">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="00670-105">以下のトピックでは、これらの概念および <xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクト内のノードの選択、評価、および照合に関連する他の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="00670-105">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00670-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="00670-106">In This Section</span></span>  

 [<span data-ttu-id="00670-107">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="00670-107">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="00670-108"><xref:System.Xml.XPath.XPathNavigator> オブジェクトまたは <xref:System.Xml.XPath.XPathDocument> オブジェクト内で XPath 式を使用してノード セットを選択するために使用される <xref:System.Xml.XmlDocument> クラスの一連のメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="00670-108">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="00670-109">XPathNavigator による XPath 式の評価</span><span class="sxs-lookup"><span data-stu-id="00670-109">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="00670-110">XPath 式の評価に使用される <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="00670-110">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="00670-111">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="00670-111">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="00670-112">ノードが XPath 式に一致するかどうかを判定するために使用される <xref:System.Xml.XPath.XPathNavigator.Matches%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="00670-112">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="00670-113">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="00670-113">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="00670-114">XPath クエリで認識されるノードの型について説明します。</span><span class="sxs-lookup"><span data-stu-id="00670-114">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="00670-115">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="00670-115">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)  
 <span data-ttu-id="00670-116">XPath クエリでの名前空間の使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="00670-116">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="00670-117">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="00670-117">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)  
 <span data-ttu-id="00670-118">コンパイル済みの XPath クエリを表す <xref:System.Xml.XPath.XPathExpression> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="00670-118">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00670-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="00670-119">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="00670-120">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="00670-120">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="00670-121">XPathDocument および XmlDocument を使用した XML データの読み取り</span><span class="sxs-lookup"><span data-stu-id="00670-121">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="00670-122">XPathNavigator による XML データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="00670-122">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="00670-123">XPathNavigator による XML データの編集</span><span class="sxs-lookup"><span data-stu-id="00670-123">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="00670-124">XPathNavigator を使用したスキーマ検証</span><span class="sxs-lookup"><span data-stu-id="00670-124">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)
