---
description: '詳細情報: DOM への新しいノードの作成'
title: DOM への新しいノードの作成
ms.date: 03/30/2017
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
ms.openlocfilehash: fdc2eb20a71450285e47a5f8b6766ba77151a7f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783418"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="94b85-103">DOM への新しいノードの作成</span><span class="sxs-lookup"><span data-stu-id="94b85-103">Create New Nodes in the DOM</span></span>

<span data-ttu-id="94b85-104"><xref:System.Xml.XmlDocument> には、すべてのノード型に対応する Create メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="94b85-104">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="94b85-105">このメソッドに、名前が必要な場合は名前を渡し、コンテンツを持つノードではコンテンツやその他のパラメーターを指定すると、そのノードが作成されます。コンテンツを持つノードには、たとえばテキスト ノードがあります。</span><span class="sxs-lookup"><span data-stu-id="94b85-105">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="94b85-106">次のメソッドは、ノードを適切に作成するために、名前といくつかのパラメーターの指定が必要なメソッドです。</span><span class="sxs-lookup"><span data-stu-id="94b85-106">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
- <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
- <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
- <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
- <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
- <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 <span data-ttu-id="94b85-107">その他のノード型では、パラメーターにデータを与えるだけでなく、他の要件を満たす必要もあります。</span><span class="sxs-lookup"><span data-stu-id="94b85-107">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="94b85-108">属性の詳細については、「[DOM の要素に対する新しい属性の作成](creating-new-attributes-for-elements-in-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-108">For information on attributes, see [Creating New Attributes for Elements in the DOM](creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="94b85-109">要素名と属性名の検証については、「[新しいノードの作成時における XML 要素名および属性名の検証](xml-element-and-attribute-name-verification-when-creating-new-nodes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-109">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="94b85-110">エンティティ参照の作成については、「[新しいエンティティ参照の作成](creating-new-entity-references.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-110">For creating entity references, see [Creating New Entity References](creating-new-entity-references.md).</span></span> <span data-ttu-id="94b85-111">エンティティ参照の展開における名前空間の影響については、「[要素と属性を含む新しいノードでのエンティティ参照の展開に対する名前空間の影響](namespace-affect-on-entity-ref-expansion-for-new-nodes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-111">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="94b85-112">新しく作成したノードをツリーに挿入するには、いくつかのメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="94b85-112">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="94b85-113">使用できるメソッドと、そのメソッドによって DOM のどこに新しいノードが作成されるかの説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="94b85-113">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="94b85-114">メソッド</span><span class="sxs-lookup"><span data-stu-id="94b85-114">Method</span></span>|<span data-ttu-id="94b85-115">ノードの位置</span><span class="sxs-lookup"><span data-stu-id="94b85-115">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="94b85-116">参照ノードの前に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="94b85-116">Inserted before the reference node.</span></span> <span data-ttu-id="94b85-117">たとえば、5 番目の位置に新しいノードを挿入するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="94b85-117">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="94b85-118">詳細については、<xref:System.Xml.XmlNode.InsertBefore%2A> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-118">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="94b85-119">参照ノードの後に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="94b85-119">Inserted after the reference node.</span></span> <span data-ttu-id="94b85-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="94b85-120">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="94b85-121">詳細については、<xref:System.Xml.XmlNode.InsertAfter%2A> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-121">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="94b85-122">当該ノードの子ノードのリストの末尾にノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="94b85-122">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="94b85-123">追加するノードが <xref:System.Xml.XmlDocumentFragment> の場合は、ドキュメント フラグメントの内容全体がこのノードの子リストに移動されます。</span><span class="sxs-lookup"><span data-stu-id="94b85-123">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="94b85-124">詳細については、<xref:System.Xml.XmlNode.AppendChild%2A> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-124">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="94b85-125">当該ノードの子ノードのリストの先頭にノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="94b85-125">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="94b85-126">追加するノードが <xref:System.Xml.XmlDocumentFragment> の場合は、ドキュメント フラグメントの内容全体がこのノードの子リストに移動されます。</span><span class="sxs-lookup"><span data-stu-id="94b85-126">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="94b85-127">詳細については、<xref:System.Xml.XmlNode.PrependChild%2A> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-127">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="94b85-128">要素に関連付けられている属性コレクションの末尾に <xref:System.Xml.XmlAttribute> ノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="94b85-128">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="94b85-129">詳細については、<xref:System.Xml.XmlAttributeCollection.Append%2A> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="94b85-129">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94b85-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="94b85-130">See also</span></span>

- [<span data-ttu-id="94b85-131">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="94b85-131">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
