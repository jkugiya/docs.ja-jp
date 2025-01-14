---
description: '詳細情報: XPathNavigator によるノードの一致'
title: XPathNavigator によるノードの一致
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: d142490829473d0891c5b2f18b1c3ec9e7ace426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732008"
---
# <a name="matching-nodes-using-xpathnavigator"></a>XPathNavigator によるノードの一致

<xref:System.Xml.XPath.XPathNavigator> クラスは、ノードが XPath 式に一致するかどうかを調べる <xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドを提供します。 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは XPath 式を入力として取り、現在のノードが与えられた XPath 式またはコンパイル済み <xref:System.Boolean> オブジェクトと一致するかどうかを示す <xref:System.Xml.XPath.XPathExpression> を返します。  
  
## <a name="matching-nodes"></a>ノードの一致  

 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは、現在のノードが指定した XPath 式と一致すると `true` を返します。 たとえば次のコード サンプルで、<xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは、現在のノードが要素 `true` であり、要素 `b` が属性 `b` を持つ場合に `c` を返します。  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは <xref:System.Xml.XPath.XPathNavigator> の状態を変えません。  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath データ モデルを使用した XML データの処理](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator を使用した XML データの選択](select-xml-data-using-xpathnavigator.md)
- [XPathNavigator による XPath 式の評価](evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPath クエリで認識されるノード型](node-types-recognized-with-xpath-queries.md)
- [XPath クエリおよび名前空間](xpath-queries-and-namespaces.md)
- [コンパイルされた XPath 式](compiled-xpath-expressions.md)
