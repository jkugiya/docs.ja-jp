---
description: '詳細情報: XML ドキュメント オブジェクト モデル (DOM) の階層構造'
title: XML ドキュメント オブジェクト モデル (DOM) の階層構造
ms.date: 03/30/2017
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 66251169be0e386d3a0323c7d744804225ad6200
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782768"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="a23fe-103">XML ドキュメント オブジェクト モデル (DOM) の階層構造</span><span class="sxs-lookup"><span data-stu-id="a23fe-103">XML Document Object Model (DOM) Hierarchy</span></span>

<span data-ttu-id="a23fe-104">XML ドキュメント オブジェクト モデル (DOM) のクラスの階層構造を次の図に示します。クラス名に続くかっこ内の名前は、W3C (World Wide Web Consortium) 名です。</span><span class="sxs-lookup"><span data-stu-id="a23fe-104">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="a23fe-105">![XML ドキュメント オブジェクト モデル &#40;DOM&#41; の階層構造](media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="a23fe-105">![XML Document Object Model &#40;DOM&#41; hierarchy](media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="a23fe-106">XML ドキュメント オブジェクト モデル (DOM) の階層構造</span><span class="sxs-lookup"><span data-stu-id="a23fe-106">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="a23fe-107">次のクラスは **XmlNode** から継承したものではありません。</span><span class="sxs-lookup"><span data-stu-id="a23fe-107">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="a23fe-108">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="a23fe-108">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="a23fe-109">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="a23fe-109">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="a23fe-110">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="a23fe-110">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="a23fe-111">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="a23fe-111">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="a23fe-112">**XmlImplementation** クラスは、XML ドキュメントを作成するために使われます。</span><span class="sxs-lookup"><span data-stu-id="a23fe-112">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="a23fe-113">詳細については、「[XML ドキュメントの作成](xml-document-creation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a23fe-113">For more information, see [XML Document Creation](xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="a23fe-114">**XmlNamedNodeMap** クラスは、順序付けられていないノード セットを処理します。</span><span class="sxs-lookup"><span data-stu-id="a23fe-114">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="a23fe-115">詳細については、「[名前またはインデックスによる順序付けられていないノードの取得](unordered-node-retrieval-by-name-or-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a23fe-115">For more information, see [Unordered Node Retrieval by Name or Index](unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="a23fe-116">**XmlNodeList** クラスは、順序付けられたノード リストを処理します。</span><span class="sxs-lookup"><span data-stu-id="a23fe-116">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="a23fe-117">詳細については、「[インデックスによる順序付けられたノードの取得](ordered-node-retrieval-by-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a23fe-117">For more information, see [Ordered Node Retrieval by Index](ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="a23fe-118">**XmlNodeChangedEventArgs** クラスは、**XmlDocument** に登録されたイベント ハンドラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="a23fe-118">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="a23fe-119">詳細については、「[XmlNodeChangedEventArgs による XML ドキュメントのイベント処理](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a23fe-119">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="a23fe-120">**XmlLinkedNode** クラスは **XmlNode** から継承しています。</span><span class="sxs-lookup"><span data-stu-id="a23fe-120">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="a23fe-121">その目的は、**XmlNode** の **PreviousSibling** と **NextSibling** という 2 つのメソッドをオーバーライドすることです。</span><span class="sxs-lookup"><span data-stu-id="a23fe-121">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="a23fe-122">これらのオーバーライドされたメソッドは、前後に兄弟を持つ **XmlCharacterData**、**XmlDeclaration**、**XmlDocumentType**、**XmlElement**、**XmlEntityReference**、**XmlProcessingInstruction** クラスによって継承され、使用されます。</span><span class="sxs-lookup"><span data-stu-id="a23fe-122">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a23fe-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a23fe-123">See also</span></span>

- [<span data-ttu-id="a23fe-124">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="a23fe-124">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
