---
title: 要素名をフィルター処理する方法 - LINQ to XML
description: XElement の IEnumerable を返すメソッドを呼び出すときに、要素名をフィルター処理する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1849fb03-f075-421f-863c-e8fb32773cdf
ms.openlocfilehash: 1f831fe0008c94b3956e93f3ced7176d8c0bf34e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411952"
---
# <a name="how-to-filter-on-element-names-linq-to-xml"></a><span data-ttu-id="8adf3-103">要素名をフィルター処理する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8adf3-103">How to filter on element names (LINQ to XML)</span></span>

<span data-ttu-id="8adf3-104"><xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement> を返すメソッドのいずれかを呼び出す際に、要素名をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="8adf3-104">When you call one of the methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, you can filter on the element name.</span></span>

## <a name="example-retrieve-descendants-filtered-to-a-specified-name"></a><span data-ttu-id="8adf3-105">例: 特定の名前でフィルタリングされた子孫を取得する</span><span class="sxs-lookup"><span data-stu-id="8adf3-105">Example: Retrieve descendants filtered to a specified name</span></span>

<span data-ttu-id="8adf3-106">この例では、指定した名前を持つ子孫だけが含まれるようにフィルター処理された子孫のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="8adf3-106">This example retrieves a collection of descendants that's filtered to contain only descendants with the specified name.</span></span>

<span data-ttu-id="8adf3-107">この例では、XML ドキュメント「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="8adf3-107">This example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> items =
    from el in po.Descendants("ProductName")
    select el;
foreach(XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string) prdName);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim items As IEnumerable(Of XElement) = _
    From el In po...<ProductName> _
    Select el
For Each prdName As XElement In items
    Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
Next
```

<span data-ttu-id="8adf3-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8adf3-108">This example produces the following output:</span></span>

```output
ProductName:Lawnmower
ProductName:Baby Monitor
```

<span data-ttu-id="8adf3-109"><xref:System.Collections.Generic.IEnumerable%601> コレクションの <xref:System.Xml.Linq.XElement> を返す他のメソッドは、同じパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="8adf3-109">The other methods that return <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> collections follow the same pattern.</span></span> <span data-ttu-id="8adf3-110">そのシグネチャは、<xref:System.Xml.Linq.XContainer.Elements%2A> および <xref:System.Xml.Linq.XContainer.Descendants%2A> と似ています。</span><span class="sxs-lookup"><span data-stu-id="8adf3-110">Their signatures are similar to <xref:System.Xml.Linq.XContainer.Elements%2A> and <xref:System.Xml.Linq.XContainer.Descendants%2A>.</span></span> <span data-ttu-id="8adf3-111">類似するシグネチャを持つメソッドの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8adf3-111">The following is the complete list of methods that have similar method signatures:</span></span>

- <xref:System.Xml.Linq.XNode.Ancestors%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>
- <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>
- <xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A>

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="8adf3-112">例: ある名前空間に属する XML から取得する</span><span class="sxs-lookup"><span data-stu-id="8adf3-112">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="8adf3-113">次の例では同じクエリを確認できますが、ある名前空間に属する XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="8adf3-113">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="8adf3-114">詳細については、[名前空間の概要](namespaces-overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8adf3-114">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

<span data-ttu-id="8adf3-115">この例では、XML ドキュメント「[サンプル XML ファイル: 名前空間内の一般的な購買発注書](sample-xml-file-typical-purchase-order-namespace.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="8adf3-115">The example uses XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
IEnumerable<XElement> items =
    from el in po.Descendants(aw + "ProductName")
    select el;
foreach (XElement prdName in items)
    Console.WriteLine(prdName.Name + ":" + (string)prdName);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim items As IEnumerable(Of XElement) = _
            From el In po...<aw:ProductName> _
            Select el
        For Each prdName As XElement In items
            Console.WriteLine(prdName.Name.ToString & ":" & prdName.Value)
        Next
    End Sub
End Module
```

<span data-ttu-id="8adf3-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8adf3-116">This example produces the following output:</span></span>

```output
{http://www.adventure-works.com}ProductName:Lawnmower
{http://www.adventure-works.com}ProductName:Baby Monitor
```

## <a name="see-also"></a><span data-ttu-id="8adf3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8adf3-117">See also</span></span>

- [<span data-ttu-id="8adf3-118">LINQ to XML 軸の概要</span><span class="sxs-lookup"><span data-stu-id="8adf3-118">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
