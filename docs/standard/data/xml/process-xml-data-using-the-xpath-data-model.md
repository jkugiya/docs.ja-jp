---
description: '詳細情報: XPath データ モデルを使用した XML データの処理'
title: XPath データ モデルを使用した XML データの処理
ms.date: 03/30/2017
ms.assetid: 536c6fce-1453-4654-9c72-bca54d47e081
ms.openlocfilehash: c01d2313d3045e1516b8bfc59dfdb3180109f560
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783210"
---
# <a name="process-xml-data-using-the-xpath-data-model"></a><span data-ttu-id="28782-103">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="28782-103">Process XML Data Using the XPath Data Model</span></span>

<span data-ttu-id="28782-104"><xref:System.Xml?displayProperty=nameWithType> 名前空間は、<xref:System.Xml.XmlDocument> または <xref:System.Xml.XPath.XPathDocument> クラスを使用して、メモリ内の XML ドキュメント、フラグメント、ノード、またはノードセットのプログラム表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="28782-104">The <xref:System.Xml?displayProperty=nameWithType> namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets in-memory, using the <xref:System.Xml.XmlDocument> or <xref:System.Xml.XPath.XPathDocument> classes.</span></span>  
  
 <span data-ttu-id="28782-105"><xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルによる XML ドキュメントの高速、読み取り専用のメモリ内表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="28782-105">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="28782-106"><xref:System.Xml.XmlDocument> クラスは、W3C ドキュメント オブジェクト モデル (DOM) の DOM Level 1 Core および DOM Level 2 Core を実装する XML ドキュメントの編集可能なメモリ内表現です。</span><span class="sxs-lookup"><span data-stu-id="28782-106">The <xref:System.Xml.XmlDocument> class provides an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="28782-107">どちらのクラスも <xref:System.Xml.XPath.IXPathNavigable> インターフェイスを実装し、基になる XML データの選択、評価、移動、および (場合によっては) 編集に使用される <xref:System.Xml.XPath.XPathNavigator> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="28782-107">Both classes implement the <xref:System.Xml.XPath.IXPathNavigable> interface and return an <xref:System.Xml.XPath.XPathNavigator> object used to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="28782-108">以下では、<xref:System.Xml.XPath.XPathNavigator> クラスの機能を、それを返すクラスに基づいて説明します。</span><span class="sxs-lookup"><span data-stu-id="28782-108">The following sections describe the functionality of the <xref:System.Xml.XPath.XPathNavigator> class based on the class that returns it.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28782-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="28782-109">In This Section</span></span>  

 [<span data-ttu-id="28782-110">XPathDocument および XmlDocument を使用した XML データの読み取り</span><span class="sxs-lookup"><span data-stu-id="28782-110">Reading XML Data using XPathDocument and XmlDocument</span></span>](reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 <span data-ttu-id="28782-111">XML ドキュメントを読むために読み取り専用の <xref:System.Xml.XPath.XPathDocument> クラス オブジェクトを作成する方法、および XML ドキュメントを読み込んで編集するために編集可能な <xref:System.Xml.XmlDocument> クラス オブジェクトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28782-111">Describes how to create a read-only <xref:System.Xml.XPath.XPathDocument> class object to read an XML document and how to create an editable <xref:System.Xml.XmlDocument> class object to read and edit an XML document.</span></span> <span data-ttu-id="28782-112">このトピックでは、各クラスから <xref:System.Xml.XPath.XPathNavigator> オブジェクトを返して、XML ドキュメント内を移動して編集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28782-112">This topic also describes how return an <xref:System.Xml.XPath.XPathNavigator> object from each class to navigate and edit an XML document.</span></span>  
  
 [<span data-ttu-id="28782-113">XPathNavigator を使用した XML データの選択、評価、および照合</span><span class="sxs-lookup"><span data-stu-id="28782-113">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="28782-114">XPath クエリによる <xref:System.Xml.XPath.XPathNavigator> または <xref:System.Xml.XPath.XPathDocument> オブジェクト内のノードの選択、XPath 式の結果の評価と検査、および XML ドキュメントのノードが指定された XPath 式に一致するかどうかの判定に使用される <xref:System.Xml.XmlDocument> クラスのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28782-114">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an XML document matches a given XPath expression.</span></span>  
  
 [<span data-ttu-id="28782-115">XPathNavigator による XML データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="28782-115">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="28782-116"><xref:System.Xml.XPath.XPathNavigator> オブジェクトまたは <xref:System.Xml.XPath.XPathDocument> オブジェクト内で、ノード間の移動、XML データの抽出、および厳密に型指定された XML データへのアクセスに使用される <xref:System.Xml.XmlDocument> クラスのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28782-116">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="28782-117">XPathNavigator による XML データの編集</span><span class="sxs-lookup"><span data-stu-id="28782-117">Editing XML Data using XPathNavigator</span></span>](editing-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="28782-118"><xref:System.Xml.XPath.XPathNavigator> オブジェクトに含まれる XML ドキュメントでノードと値の挿入、変更、および削除に使用される <xref:System.Xml.XmlDocument> クラスのメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28782-118">Describes the methods of the <xref:System.Xml.XPath.XPathNavigator> class used to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="28782-119">XPathNavigator を使用したスキーマ検証</span><span class="sxs-lookup"><span data-stu-id="28782-119">Schema Validation using XPathNavigator</span></span>](schema-validation-using-xpathnavigator.md)  
 <span data-ttu-id="28782-120"><xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクトに含まれる XML コンテンツの検証方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28782-120">Describes the ways to validate the XML content contained in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28782-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="28782-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="28782-122">DOM モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="28782-122">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)
