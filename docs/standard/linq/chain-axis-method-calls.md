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
# <a name="how-to-chain-axis-method-calls-linq-to-xml"></a><span data-ttu-id="ff1f3-103">軸メソッドの呼び出しを連結する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ff1f3-103">How to chain axis method calls (LINQ to XML)</span></span>

<span data-ttu-id="ff1f3-104">コードで使用する一般的なパターンでは、軸メソッドを呼び出してから、拡張メソッド軸のいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-104">A common pattern that you will use in your code is to call an axis method, then call one of the extension method axes.</span></span>

<span data-ttu-id="ff1f3-105">要素のコレクションを返す `Elements` という名前の軸には、<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> メソッドと <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> メソッドの 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-105">There are two axes with the name of `Elements` that return a collection of elements: the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method and the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ff1f3-106">この 2 つの軸を組み合わせて、ツリー内の指定した深さで指定した名前を持つ要素をすべて検索できます。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-106">You can combine these two axes to find all elements of a specified name at a given depth in the tree.</span></span>

## <a name="example-retrieve-all-name-elements"></a><span data-ttu-id="ff1f3-107">例: すべての name 要素を取得する</span><span class="sxs-lookup"><span data-stu-id="ff1f3-107">Example: Retrieve all name elements</span></span>

<span data-ttu-id="ff1f3-108">この例では、<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> および <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> を使用して、すべての `PurchaseOrder` 要素内にあるすべての `Address` 要素内で `Name` 要素をすべて取得します。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-108">This example uses <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> and <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> to retrieve all `Name` elements in all `Address` elements in all `PurchaseOrder` elements.</span></span>

<span data-ttu-id="ff1f3-109">この例では、「[サンプル XML ファイル: 複数の購買発注書](sample-xml-file-multiple-purchase-orders.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-109">This example uses XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span>

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

<span data-ttu-id="ff1f3-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-110">This example produces the following output:</span></span>

```xml
<Name>Ellen Adams</Name>
<Name>Tai Yee</Name>
<Name>Cristian Osorio</Name>
<Name>Cristian Osorio</Name>
<Name>Jessica Arnold</Name>
<Name>Jessica Arnold</Name>
```

<span data-ttu-id="ff1f3-111">このように出力されるのは、`Elements` 軸の実装の 1 つが、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XContainer> に対する拡張メソッドとして存在しているためです。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-111">This works because one of the implementations of the `Elements` axis is as an extension method on <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="ff1f3-112"><xref:System.Xml.Linq.XElement> は <xref:System.Xml.Linq.XContainer> から派生するため、<xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> メソッドを呼び出した結果に対して <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-112"><xref:System.Xml.Linq.XElement> derives from <xref:System.Xml.Linq.XContainer>, so you can call the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> method on the results of a call to the <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType> method.</span></span>

## <a name="example-retrieve-all-elements-at-a-particular-depth"></a><span data-ttu-id="ff1f3-113">例: 特定の深さにあるすべての要素を取得する</span><span class="sxs-lookup"><span data-stu-id="ff1f3-113">Example: Retrieve all elements at a particular depth</span></span>

<span data-ttu-id="ff1f3-114">祖先が介在しない可能性がある場合に、特定の要素の深さにあるすべての要素を取得しなければならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-114">Sometimes you want to retrieve all elements at a particular element depth when there may not be intervening ancestors.</span></span> <span data-ttu-id="ff1f3-115">たとえば、次のドキュメントで、`Customer` 要素の子である `ConfigParameter` 要素はすべて取得し、`Root` 要素の子である `ConfigParameter` は取得しないとします。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-115">For example, in the following document, you might want to retrieve all the `ConfigParameter` elements that are children of the `Customer` element, but not the `ConfigParameter` that's a child of the `Root` element.</span></span>

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

 <span data-ttu-id="ff1f3-116">この操作を行うには、次のように <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> 軸を使用します。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-116">To do this, you can use the <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType> axis, as follows:</span></span>

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

<span data-ttu-id="ff1f3-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-117">This example produces the following output:</span></span>

```xml
<ConfigParameter>FirstConfigParameter</ConfigParameter>
<ConfigParameter>SecondConfigParameter</ConfigParameter>
```

## <a name="example-retrieve-elements-for-xml-thats-in-a-namespace"></a><span data-ttu-id="ff1f3-118">例: 名前空間に含まれている XML の要素を取得する</span><span class="sxs-lookup"><span data-stu-id="ff1f3-118">Example: Retrieve elements for XML that's in a namespace</span></span>

<span data-ttu-id="ff1f3-119">次の例は名前空間に含まれている XML 用の手法です。これらの手法は上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-119">The following example shows the same technique for XML that's in a namespace.</span></span> <span data-ttu-id="ff1f3-120">詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-120">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="ff1f3-121">この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](sample-xml-file-multiple-purchase-orders-namespace.md)」の XML ドキュメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-121">This example uses XML document [Sample XML file: Multiple purchase orders in a namespace](sample-xml-file-multiple-purchase-orders-namespace.md).</span></span>

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

<span data-ttu-id="ff1f3-122">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ff1f3-122">This example produces the following output:</span></span>

```xml
<aw:Name xmlns:aw="http://www.adventure-works.com">Ellen Adams</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Tai Yee</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Cristian Osorio</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
<aw:Name xmlns:aw="http://www.adventure-works.com">Jessica Arnold</aw:Name>
```

## <a name="see-also"></a><span data-ttu-id="ff1f3-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff1f3-123">See also</span></span>

- [<span data-ttu-id="ff1f3-124">LINQ to XML 軸の概要</span><span class="sxs-lookup"><span data-stu-id="ff1f3-124">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
