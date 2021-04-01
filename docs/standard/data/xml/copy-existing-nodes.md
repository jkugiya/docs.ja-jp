---
description: '詳細情報: 既存のノードのコピー'
title: 既存のノードのコピー
ms.date: 03/30/2017
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 48bc1fd4f0eeb16691d6f9c0631998db9a54bba1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783431"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="df8b7-103">既存のノードのコピー</span><span class="sxs-lookup"><span data-stu-id="df8b7-103">Copy Existing Nodes</span></span>

<span data-ttu-id="df8b7-104">XML ドキュメント オブジェクト モデル (DOM) には、**SelectSingleNode**、**ChildNodes[int i]** 、**Attributes[int i]** など、ノードの選択に使用できるメソッドとプロパティが多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="df8b7-104">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="df8b7-105">ノードを選択すると、その特定のノード型で利用できる挿入メソッドを使用してツリーに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="df8b7-105">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="df8b7-106">ノードをツリーに挿入するときの唯一の制約は、ノードを挿入した後もドキュメントが整形式になっていなければならないことです。</span><span class="sxs-lookup"><span data-stu-id="df8b7-106">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="df8b7-107">既存のノードを DOM ツリーに挿入すると、そのノードは元の位置から削除され、挿入先の位置に追加されます。</span><span class="sxs-lookup"><span data-stu-id="df8b7-107">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df8b7-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="df8b7-108">See also</span></span>

- [<span data-ttu-id="df8b7-109">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="df8b7-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
