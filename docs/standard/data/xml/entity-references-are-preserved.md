---
description: '詳細情報: 保持されるエンティティ参照'
title: 保持されるエンティティ参照
ms.date: 03/30/2017
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
ms.openlocfilehash: 189096d2dd87731a06fdb805ba5f041c041e26b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629631"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="65a95-103">保持されるエンティティ参照</span><span class="sxs-lookup"><span data-stu-id="65a95-103">Entity References are Preserved</span></span>

<span data-ttu-id="65a95-104">エンティティ参照を展開せずに保持する場合、XML ドキュメント オブジェクト モデル (DOM) は、エンティティ参照を検出すると **XmlEntityReference** ノードを構築します。</span><span class="sxs-lookup"><span data-stu-id="65a95-104">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="65a95-105">たとえば、次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="65a95-105">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="65a95-106">DOM は、`&publisher;` 参照を検出すると **XmlEntityReference** ノードを構築します。</span><span class="sxs-lookup"><span data-stu-id="65a95-106">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="65a95-107">**XmlEntityReference** には、エンティティ宣言のコンテンツからコピーされた子ノードが格納されます。</span><span class="sxs-lookup"><span data-stu-id="65a95-107">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="65a95-108">上記のコード サンプルでは、エンティティ宣言にテキストが含まれているため、エンティティ参照ノードの子ノードとして **XmlText** ノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="65a95-108">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="65a95-109">![保持されているエンティティ参照のツリー構造](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="65a95-109">![Tree structure for preserved entity references](media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="65a95-110">エンティティ参照が保持される場合のツリー構造</span><span class="sxs-lookup"><span data-stu-id="65a95-110">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="65a95-111">**XmlEntityReference** の子ノードは、エンティティ宣言が検出されたときに **XmlEntity** ノードから作成されたすべての子ノードのコピーです。</span><span class="sxs-lookup"><span data-stu-id="65a95-111">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65a95-112">**XmlEntity** からコピーされたノードは、エンティティ参照ノードの下に配置されると、必ずしも元のノードの完全なコピーにはなりません。</span><span class="sxs-lookup"><span data-stu-id="65a95-112">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="65a95-113">エンティティ参照ノードが現れた位置のスコープに名前空間が適用されていると、それが子ノードの最終的な構成に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="65a95-113">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="65a95-114">既定では、`&abc;` のような一般エンティティは保持され、常に **XmlEntityReference** ノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="65a95-114">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a95-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="65a95-115">See also</span></span>

- [<span data-ttu-id="65a95-116">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="65a95-116">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
