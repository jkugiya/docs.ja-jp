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
# <a name="copy-existing-nodes"></a>既存のノードのコピー

XML ドキュメント オブジェクト モデル (DOM) には、**SelectSingleNode**、**ChildNodes[int i]** 、**Attributes[int i]** など、ノードの選択に使用できるメソッドとプロパティが多数用意されています。 ノードを選択すると、その特定のノード型で利用できる挿入メソッドを使用してツリーに挿入できます。 ノードをツリーに挿入するときの唯一の制約は、ノードを挿入した後もドキュメントが整形式になっていなければならないことです。 既存のノードを DOM ツリーに挿入すると、そのノードは元の位置から削除され、挿入先の位置に追加されます。  
  
## <a name="see-also"></a>関連項目

- [XML ドキュメント オブジェクト モデル (DOM)](xml-document-object-model-dom.md)
