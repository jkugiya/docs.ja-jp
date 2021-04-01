---
description: '詳細情報: DOM からのノードの削除'
title: DOM からのノードの削除
ms.date: 03/30/2017
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
ms.openlocfilehash: b5e85157c194b034289a46140a44d2a9d1109061
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783093"
---
# <a name="removing-nodes-from-the-dom"></a><span data-ttu-id="0b2bf-103">DOM からのノードの削除</span><span class="sxs-lookup"><span data-stu-id="0b2bf-103">Removing Nodes from the DOM</span></span>

<span data-ttu-id="0b2bf-104">XML ドキュメント オブジェクト モデル (DOM) からノードを削除するには、<xref:System.Xml.XmlNode.RemoveChild%2A> メソッドを使用して特定のノードを削除します。</span><span class="sxs-lookup"><span data-stu-id="0b2bf-104">To remove a node from the XML Document Object Model (DOM), use the <xref:System.Xml.XmlNode.RemoveChild%2A> method to remove a specific node.</span></span> <span data-ttu-id="0b2bf-105">ノードを削除すると、削除しようとしたノードがリーフ ノードでない場合は、そのノードに含まれるサブツリーも削除されます。</span><span class="sxs-lookup"><span data-stu-id="0b2bf-105">When you remove a node, the method removes the subtree belonging to the node being removed; that is, if it is not a leaf node.</span></span>  
  
 <span data-ttu-id="0b2bf-106">DOM から複数のノードを削除するには、<xref:System.Xml.XmlNode.RemoveAll%2A> メソッドを使用します。現在のノードに子や属性があれば、それらがすべて削除されます。</span><span class="sxs-lookup"><span data-stu-id="0b2bf-106">To remove multiple nodes from the DOM, use the <xref:System.Xml.XmlNode.RemoveAll%2A> method to remove all the children and attributes, if applicable, of the current node.</span></span>  
  
 <span data-ttu-id="0b2bf-107"><xref:System.Xml.XmlNamedNodeMap> を使用している場合は、<xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> メソッドを使用してノードを削除できます。</span><span class="sxs-lookup"><span data-stu-id="0b2bf-107">If you are working with an <xref:System.Xml.XmlNamedNodeMap>, you can remove a node using the <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> method.</span></span>  
  
 <span data-ttu-id="0b2bf-108">属性を削除するには、「[DOM の要素ノードからの属性の削除](removing-attributes-from-an-element-node-in-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b2bf-108">To remove attributes, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b2bf-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b2bf-109">See also</span></span>

- [<span data-ttu-id="0b2bf-110">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="0b2bf-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
