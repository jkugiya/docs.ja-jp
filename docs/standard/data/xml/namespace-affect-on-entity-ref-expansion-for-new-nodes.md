---
description: '詳細情報: 要素と属性を含む新しいノードでのエンティティ参照の展開に対する名前空間の影響'
title: 要素と属性を含む新しいノードでのエンティティ参照の展開に対する名前空間の影響
ms.date: 03/30/2017
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 48345d75f9cf77f8e70655c8f166978cafbf06c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713482"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>要素と属性を含む新しいノードでのエンティティ参照の展開に対する名前空間の影響

エンティティ宣言には、原則として任意のコンテンツを含めることができるため、`<!ENTITY aname "<elem>test</elem>">` のような要素が含まれている可能性もあります。  
  
 `&aname;` の置換コンテンツへの展開は、XML の解析時に行われるのではありません。 ノードがドキュメントに配置されるまでは、要素に対する名前空間を解決できないため、XML の展開は実行されません。 スコープ内の名前空間が判明するのは、ノードが配置された後になります。 ノードがドキュメントに配置されると、名前空間の解決が行われ、結果として得られたエンティティ コンテンツが適切なノードに解析されます。  
  
> [!NOTE]
> 新しく作成されたエンティティ参照ノードがいったん展開された後、再び展開されることはありません。 したがって、要素の置換テキストで使われる名前空間は、親ノードの設定時にバインドされます。 ただし、既存のエンティティ参照ノードを削除して別の場所に挿入すると、そのノードに対する名前空間が変更される可能性があります。また、**CloneNode** メソッドで複製されたエンティティ参照ノードにおいても、名前空間が変わる可能性があります。  
  
## <a name="see-also"></a>関連項目

- [XML ドキュメント オブジェクト モデル (DOM)](xml-document-object-model-dom.md)
