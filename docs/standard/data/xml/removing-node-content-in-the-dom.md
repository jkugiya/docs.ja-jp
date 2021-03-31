---
description: '詳細情報: DOM のノード コンテンツの削除'
title: DOM のノード コンテンツの削除
ms.date: 03/30/2017
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: 44f8e0ee63ae8317d6b19558829ff3b676867845
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783119"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="dffac-103">DOM のノード コンテンツの削除</span><span class="sxs-lookup"><span data-stu-id="dffac-103">Removing Node Content in the DOM</span></span>

<span data-ttu-id="dffac-104"><xref:System.Xml.XmlCharacterData> を継承するノード型、つまり <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace>、および <xref:System.Xml.XmlSignificantWhitespace> ノード型では、ノードから文字範囲を削除する <xref:System.Xml.XmlCharacterData.DeleteData%2A> メソッドを使用して文字を削除できます。</span><span class="sxs-lookup"><span data-stu-id="dffac-104">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="dffac-105">コンテンツを完全に削除するには、そのコンテンツが含まれているノードを削除します。</span><span class="sxs-lookup"><span data-stu-id="dffac-105">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="dffac-106">ノードを保持する必要があり、コンテンツが正しくない場合は、そのコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="dffac-106">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="dffac-107">ノードのコンテンツを変更する方法については、「[XML ドキュメントのノード、コンテンツ、値の変更](modifying-nodes-content-and-values-in-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dffac-107">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffac-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="dffac-108">See also</span></span>

- [<span data-ttu-id="dffac-109">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="dffac-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
