---
description: '詳細情報: 新しいノードの作成時における XML 要素名および属性名の検証'
title: 新しいノードの作成時における XML 要素名および属性名の検証
ms.date: 03/30/2017
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 07b878424df57c34c5dc2b614fdff9a5dcef26bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782716"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a>新しいノードの作成時における XML 要素名および属性名の検証

XML ドキュメント オブジェクト モデル (DOM) は、新しい要素ノードまたは属性ノードを作成するときに名前の有効性を確認します。 名前に無効な文字が含まれていると、例外がスローされます。 名前が正しくエンコードされ、有効であることを保証するには、**XmlConvert** クラスを使用して名前をエンコードし、アプリケーション レベルで名前をデコードする必要があります。 **XmlWriter** には、整形式の XML を生成するための追加の処理を行うメソッドが用意されています。  
  
## <a name="see-also"></a>関連項目

- [XML ドキュメント オブジェクト モデル (DOM)](xml-document-object-model-dom.md)
