---
title: 軸メソッドの呼び出しを連結する方法 - LINQ to XML
description: XContainer. Elements と Extensions. Elements のメソッドを使用して、ツリー内の指定した深さで指定した名前を持つ要素をすべて見つける方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 067e6da2-ee32-486d-803c-e611b328e39a
ms.openlocfilehash: 23d3b5a3dacbc56a570a92178cb8e28482907ca1
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412048"
---
# <a name="how-to-chain-axis-method-calls-linq-to-xml"></a>軸メソッドの呼び出しを連結する方法 (LINQ to XML)

コードで使用する一般的なパターンでは、軸メソッドを呼び出してから、拡張メソッド軸のいずれかを呼び出します。

要素のコレクションを返す `Elements` という名前の軸には、<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> メソッドと <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> メソッドの 2 つがあります。 この 2 つの軸を組み合わせて、ツリー内の指定した深さで指定した名前を持つ要素をすべて検索できます。

## <a name="example-retrieve-all-name-elements"></a>例: すべての name 要素を取得する

この例では、<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> および <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> を使用して、すべての `PurchaseOrder` 要素内にあるすべての `Address` 要素内で `Name` 要素をすべて取得します。

この例では、「[サンプル XML ファイル: 複数の購買発注書](sample-xml-file-multiple-purchase-orders.md)」の XML ドキュメントを使用します。

```csharp
XElement purchaseOrders = XElement.Load("PurchaseOrders.xml");
IEnumerable<XElement> names =
    from el in purchaseOrders
        .Elements("PurchaseOrder")
        .Elements("Address")
        .Elements("Name")
    select el;
foreach (XElement e in names)
    Console.WriteLine(e);
```

```vb
Dim purchaseOrders As XElement = XElement.Load("PurchaseOrders.xml")
Dim names As IEnumerable(Of XElement) = _
    From el In purchaseOrders.<PurchaseOrder>.<Address>.<Name> _
    Select el
For Each e As XElement In names
    Console.WriteLine(e)
Next
```

この例を実行すると、次の出力が生成されます。

```xml
<Name>Ellen Adams</Name>
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

このように出力されるのは、`Elements` 軸の実装の 1 つが、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XContainer> に対する拡張メソッドとして存在しているためです。 <xref:System.Xml.Linq.XElement> は <xref:System.Xml.Linq.XContainer> から派生するため、<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> メソッドを呼び出した結果に対して <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。

## <a name="example-retrieve-all-elements-at-a-particular-depth"></a>例: 特定の深さにあるすべての要素を取得する

祖先が介在しない可能性がある場合に、特定の要素の深さにあるすべての要素を取得しなければならないことがあります。 たとえば、次のドキュメントで、`Customer` 要素の子である `ConfigParameter` 要素はすべて取得し、`Root` 要素の子である `ConfigParameter` は取得しないとします。

```xml
<Root>
  <ConfigParameter>RootConfigParameter</ConfigParameter>
  <Customer>
    <Name>Frank</Name>
    <Config>
      <ConfigParameter>FirstConfigParameter</ConfigParameter>
    </Config>
  </Customer>
  <Customer>
    <Name>Bob</Name>
    <!--This customer doesn't have a Config element-->
  </Customer>
  <Customer>
    <Name>Bill</Name>
    <Config>
      <ConfigParameter>SecondConfigParameter</ConfigParameter>
    </Config>
  </Customer>
</Root>
```

 この操作を行うには、次のように <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 軸を使用します。

```csharp
XElement root = XElement.Load("Irregular.xml");
IEnumerable<XElement> configParameters =
    root.Elements("Customer").Elements("Config").
    Elements("ConfigParameter");
foreach (XElement cp in configParameters)
    Console.WriteLine(cp);
```

```vb
Dim root As XElement = XElement.Load("Irregular.xml")
Dim configParameters As IEnumerable(Of XElement) = _
    root.<Customer>.<Config>.<ConfigParameter>
For Each cp As XElement In configParameters
    Console.WriteLine(cp)
Next
```

この例を実行すると、次の出力が生成されます。

```xml
<ConfigParameter>FirstConfigParameter</ConfigParameter>
<ConfigParameter>SecondConfigParameter</ConfigParameter>
```

## <a name="example-retrieve-elements-for-xml-thats-in-a-namespace"></a>例: 名前空間に含まれている XML の要素を取得する

次の例は名前空間に含まれている XML 用の手法です。これらの手法は上の例と同じ機能を表しています。 詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。

この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](sample-xml-file-multiple-purchase-orders-namespace.md)」の XML ドキュメントを使用します。

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement purchaseOrders = XElement.Load("PurchaseOrdersInNamespace.xml");
IEnumerable<XElement> names =
    from el in purchaseOrders
        .Elements(aw + "PurchaseOrder")
        .Elements(aw + "Address")
        .Elements(aw + "Name")
    select el;
foreach (XElement e in names)
    Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim purchaseOrders As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")
        Dim names As IEnumerable(Of XElement) = _
            From el In purchaseOrders.<aw:PurchaseOrder>.<aw:Address>.<aw:Name> _
            Select el
        For Each e As XElement In names
            Console.WriteLine(e)
        Next
    End Sub
End Module
```

この例を実行すると、次の出力が生成されます。

```xml
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
```

## <a name="see-also"></a>関連項目

- [LINQ to XML 軸の概要](linq-xml-axes-overview.md)
