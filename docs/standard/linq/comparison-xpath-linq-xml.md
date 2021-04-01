---
title: XPath と LINQ to XML の比較 - LINQ to XML
description: XPath と LINQ to XML のクエリはどちらも XML ツリーに対してクエリを実行できます。 この記事では、2 つのオプションを比較し、全体として LINQ to XML クエリの方が、より強力で、汎用性が高く、高速で、安全性が高く、より便利な選択肢であることを確認します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412034"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>XPath と LINQ to XML の比較

XPath と LINQ to XML は、いくつかの点で似ています。 どちらも XML ツリーに対してクエリを実行するために使用され、結果として、要素のコレクション、属性のコレクション、ノードのコレクション、要素や属性の値などを返します。 ただし、この 2 つのオプションには、大きな違いがあります。

## <a name="differences-between-xpath-and-linq-to-xml"></a>XPath と LINQ to XML の違い

XPath では、新しい型を射影できません。 XPath では、ツリーからノードのコレクションが返されるだけですが、LINQ to XML では、クエリを実行し、オブジェクト グラフまたは XML ツリーを新しい構造に射影できます。 LINQ to XML クエリは、XPath 式よりもはるかに多くのことができます。

XPath 式は、文字列内に独立して存在します。 C# コンパイラは、コンパイル時に XPath 式を解析できません。 一方 LINQ to XML クエリは、C# コンパイラによって解析され、コンパイルされます。 コンパイラによって、多くのクエリ エラーをキャッチできます。

XPath の結果は厳密に型指定されません。 多くの場合、XPath 式を評価した結果はオブジェクトであり、開発者が適切な型を決定し、必要に応じて結果をキャストする必要があります。 一方、LINQ to XML クエリからの射影は厳密に型指定されます。

## <a name="result-ordering"></a>結果の順序付け

XPath 1.0 勧告には、XPath 式の評価結果であるコレクションは順序付けされないことが記載されています。

ただし、LINQ to XML の XPath 軸メソッドから返されるコレクションを反復処理すると、コレクション内のノードがドキュメント順に返されます。 これは、ドキュメントの逆順として述語が表現されている `preceding` や `preceding-sibling` などの XPath 軸にアクセスする場合でも同様です。

これに対し、LINQ to XML 軸のほとんどは、ドキュメント順にコレクションを返します。 ただし、これらのうち 2 つ (<xref:System.Xml.Linq.XNode.Ancestors%2A> と <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>) は、ドキュメントの逆順でコレクションを返します。 次の表では、軸を列挙し、それぞれのコレクションの順序を示します。

|LINQ to XML 軸|並べ替え|
|----------------------|--------------|
|XContainer.DescendantNodes|ドキュメント順|
|XContainer.Descendants|ドキュメント順|
|XContainer.Elements|ドキュメント順|
|XContainer.Nodes|ドキュメント順|
|XContainer.NodesAfterSelf|ドキュメント順|
|XContainer.NodesBeforeSelf|ドキュメント順|
|XElement.AncestorsAndSelf|ドキュメントの逆順|
|XElement.Attributes|ドキュメント順|
|XElement.DescendantNodesAndSelf|ドキュメント順|
|XElement.DescendantsAndSelf|ドキュメント順|
|XNode.Ancestors|ドキュメントの逆順|
|XNode.ElementsAfterSelf|ドキュメント順|
|XNode.ElementsBeforeSelf|ドキュメント順|
|XNode.NodesAfterSelf|ドキュメント順|
|XNode.NodesBeforeSelf|ドキュメント順|

## <a name="positional-predicates"></a>位置述語

XPath 式では、多くの軸で位置述語がドキュメント順として表現されますが、逆方向軸の場合は、ドキュメントの逆順で表現されます。 逆方向軸は、`preceding`、`preceding-sibling`、`ancestor`、`ancestor-or-self` です。 たとえば、XPath 式 `preceding-sibling::*[1]` は、直前の兄弟を返します。 これは、最終的な結果セットがドキュメント順で表される場合も同様です。

一方、LINQ to XML の位置述語は、常に軸の順序として表現されます。 たとえば、`anElement.ElementsBeforeSelf().ElementAt(0)` は、直前の兄弟ではなく、クエリされる要素の親の最初の子要素を返します。 別の例として、`anElement.Ancestors().ElementAt(0)` は親要素を返します。

LINQ to XML で直前の要素を検索する場合は、次の式を記述します。

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a>パフォーマンスの違い

LINQ to XML 内の XPath 機能を使用する XPath クエリは、LINQ to XML クエリよりも遅くなります。

## <a name="comparison-of-composition"></a>構成の比較

LINQ to XML クエリの構成は、XPath 式の構成に似ていますが、構文は大きく異なります。

たとえば、`customers` という変数に要素があり、`Customer` というすべての子要素の下で `CompanyName` という孫要素を検索する場合は、次のようにこの XPath 式を記述します。

```csharp
customers.XPathSelectElements("./Customer/CompanyName")
```

```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

同等の LINQ to XML クエリは次のとおりです。

```csharp
customers.Elements("Customer").Elements("CompanyName")
```

```vb
customers.Elements("Customer").Elements("CompanyName")
```

同様の対応関係が XPath 軸ごとに存在します。

|XPath 軸|LINQ to XML 軸|
|----------------|----------------------|
|child (既定の軸)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|
|Parent (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|
|attribute 軸 (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|ancestor 軸|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|ancestor-or-self 軸|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|descendant 軸 (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> 、または<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> 、または<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|following-sibling|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> 、または<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|preceding-sibling|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|following|同等の軸はありません。|
|preceding|同等の軸はありません。|
