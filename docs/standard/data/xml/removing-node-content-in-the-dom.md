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
# <a name="removing-node-content-in-the-dom"></a>DOM のノード コンテンツの削除

<xref:System.Xml.XmlCharacterData> を継承するノード型、つまり <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace>、および <xref:System.Xml.XmlSignificantWhitespace> ノード型では、ノードから文字範囲を削除する <xref:System.Xml.XmlCharacterData.DeleteData%2A> メソッドを使用して文字を削除できます。 コンテンツを完全に削除するには、そのコンテンツが含まれているノードを削除します。 ノードを保持する必要があり、コンテンツが正しくない場合は、そのコンテンツを変更します。 ノードのコンテンツを変更する方法については、「[XML ドキュメントのノード、コンテンツ、値の変更](modifying-nodes-content-and-values-in-an-xml-document.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XML ドキュメント オブジェクト モデル (DOM)](xml-document-object-model-dom.md)
