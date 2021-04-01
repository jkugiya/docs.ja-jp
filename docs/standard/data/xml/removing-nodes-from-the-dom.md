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
# <a name="removing-nodes-from-the-dom"></a>DOM からのノードの削除

XML ドキュメント オブジェクト モデル (DOM) からノードを削除するには、<xref:System.Xml.XmlNode.RemoveChild%2A> メソッドを使用して特定のノードを削除します。 ノードを削除すると、削除しようとしたノードがリーフ ノードでない場合は、そのノードに含まれるサブツリーも削除されます。  
  
 DOM から複数のノードを削除するには、<xref:System.Xml.XmlNode.RemoveAll%2A> メソッドを使用します。現在のノードに子や属性があれば、それらがすべて削除されます。  
  
 <xref:System.Xml.XmlNamedNodeMap> を使用している場合は、<xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> メソッドを使用してノードを削除できます。  
  
 属性を削除するには、「[DOM の要素ノードからの属性の削除](removing-attributes-from-an-element-node-in-the-dom.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XML ドキュメント オブジェクト モデル (DOM)](xml-document-object-model-dom.md)
