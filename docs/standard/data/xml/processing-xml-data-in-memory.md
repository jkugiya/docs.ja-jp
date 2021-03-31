---
description: '詳細情報: メモリ内の XML データの処理'
title: メモリ内の XML データの処理
ms.date: 03/30/2017
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 2990a922fa864849e0f46bcfc5d9da017e28495d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783197"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="8ab94-103">メモリ内の XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8ab94-103">Processing XML Data In-Memory</span></span>

<span data-ttu-id="8ab94-104">Microsoft .NET Framework には、XML データを処理するための 3 つのモデルである <xref:System.Xml.XmlDocument> クラス、<xref:System.Xml.XPath.XPathDocument> クラス、および [LINQ to XML (C#)](../../linq/linq-xml-overview.md) と [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8ab94-104">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span>  
  
 <span data-ttu-id="8ab94-105"><xref:System.Xml.XmlDocument> クラスは、W3C ドキュメント オブジェクト モデル (DOM) 勧告の DOM Level 1 Core および DOM Level 2 Core を実装しています。</span><span class="sxs-lookup"><span data-stu-id="8ab94-105">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="8ab94-106">DOM は XML ドキュメントのメモリ内 (キャッシュ) ツリー表現です。</span><span class="sxs-lookup"><span data-stu-id="8ab94-106">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="8ab94-107"><xref:System.Xml.XmlDocument> およびその関連クラスを使用すると、XML ドキュメントの作成、データの読み込みとアクセス、データの変更、および変更の保存が可能です。</span><span class="sxs-lookup"><span data-stu-id="8ab94-107">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="8ab94-108"><xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルに基づく、読み取り専用のメモリ内データ ストアです。</span><span class="sxs-lookup"><span data-stu-id="8ab94-108">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="8ab94-109"><xref:System.Xml.XPath.XPathNavigator> クラスは、読み取り専用の <xref:System.Xml.XPath.XPathDocument> クラスと <xref:System.Xml.XmlDocument> クラス内の XML ドキュメント全体にカーソル モデルを使用して、いくつかの編集オプションとナビゲーション機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="8ab94-109">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="8ab94-110">[LINQ to XML](../../linq/linq-xml-overview.md) は、XML データの処理を目的として .NET Framework バージョン 3.5 で導入されたモデルです。</span><span class="sxs-lookup"><span data-stu-id="8ab94-110">[LINQ to XML](../../linq/linq-xml-overview.md) is a model introduced in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="8ab94-111">[統合言語クエリ (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md) を活用するメモリ内モデルです。</span><span class="sxs-lookup"><span data-stu-id="8ab94-111">It's an in-memory model that leverages [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span></span> <span data-ttu-id="8ab94-112">LINQ では C# および Visual Basic の言語構文を拡張することで、新しいクエリ機能を実現しています。</span><span class="sxs-lookup"><span data-stu-id="8ab94-112">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ab94-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8ab94-113">In This Section</span></span>  

 [<span data-ttu-id="8ab94-114">DOM モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8ab94-114">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="8ab94-115"><xref:System.Xml.XmlDocument> とその関連クラスを使用した XML データの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ab94-115">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="8ab94-116">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8ab94-116">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="8ab94-117"><xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument>、および <xref:System.Xml.XPath.XPathNavigator> クラスを使用した XML データの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ab94-117">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="8ab94-118">LINQ to XML を使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8ab94-118">Process XML Data Using LINQ to XML</span></span>](process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="8ab94-119">LINQ to XML の概要を簡単に説明し、LINQ to XML に関する参照先のリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="8ab94-119">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8ab94-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ab94-120">Related Sections</span></span>  

 [<span data-ttu-id="8ab94-121">XML ドキュメントと XML データ</span><span class="sxs-lookup"><span data-stu-id="8ab94-121">XML Documents and Data</span></span>](index.md)
