---
description: '詳細情報: NodeLists および NamedNodeMaps の動的更新'
title: NodeLists および NamedNodeMaps の動的更新
ms.date: 03/30/2017
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 4e4b88d0e084e32fdb27f3d5762e305a4e900f1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783379"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a>NodeLists および NamedNodeMaps の動的更新

**XmlNodeList** と **XmlNamedNodeMap** にはノード セットが格納されますが、XML ドキュメントはメモリに読み込まれ、変更されるため、W3C (World Wide Web Consortium) では、ノード セットが格納されるこれらのオブジェクトは動的でなければならないと規定しています。 つまり、基になっているドキュメントが変更されたら、これら 2 つのオブジェクトも変更される必要があります。 したがって、特定の要素 (たとえば要素 X) のすべての子要素が **XmlNodeList** に格納されている場合、別の要素である要素 Q は、要素 X の下のドキュメントに追加されます。**XmlNodeList** のコレクションにも、その新しい要素 Q を追加する必要があります。 逆の場合も同様です。 **XmlNodeList** にノードが追加された場合は、基になっているドキュメントも同様に更新されます。  
  
## <a name="see-also"></a>関連項目

- [XML ドキュメント オブジェクト モデル (DOM)](xml-document-object-model-dom.md)
