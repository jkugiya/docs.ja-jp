---
title: 特定の属性を持つ要素を検索する方法 - LINQ to XML
description: 属性に特定の値が含まれる要素を検索する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: a1569f8a91e980f12ecc1801e00d6414711833d0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412120"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-linq-to-xml"></a><span data-ttu-id="8475a-103">特定の属性を持つ要素を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8475a-103">How to find an element with a specific attribute (LINQ to XML)</span></span>

<span data-ttu-id="8475a-104">この記事では、属性に特定の値が含まれる要素を検索する方法の例を提供します。</span><span class="sxs-lookup"><span data-stu-id="8475a-104">This article provides examples of how to find an element whose attribute has a specific value.</span></span>

## <a name="example-find-an-element-whose-attribute-has-a-specific-value"></a><span data-ttu-id="8475a-105">例: 属性に特定の値が含まれる要素を検索する</span><span class="sxs-lookup"><span data-stu-id="8475a-105">Example: Find an element whose attribute has a specific value</span></span>

<span data-ttu-id="8475a-106">次の例では、"Billing" の値を含む `Type` 属性を持つ `Address` 要素を検索する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8475a-106">The following example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span> <span data-ttu-id="8475a-107">この例では、XML ドキュメント「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」を使用します。</span><span class="sxs-lookup"><span data-stu-id="8475a-107">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> address =
    from el in root.Elements("Address")
    where (string)el.Attribute("Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("PurchaseOrder.xml")
Dim address As IEnumerable(Of XElement) = _
    From el In root.<Address> _
    Where el.@Type = "Billing" _
    Select el
For Each el As XElement In address
    Console.WriteLine(el)
Next
```

<span data-ttu-id="8475a-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8475a-108">This example produces the following output:</span></span>

```xml
<Address Type="Billing">
  <Name>Tai Yee</Name>
  <Street>8 Oak Avenue</Street>
  <City>Old Town</City>
  <State>PA</State>
  <Zip>95819</Zip>
  <Country>USA</Country>
</Address>
```

## <a name="example-find-an-element-in-xml-thats-in-a-namespace"></a><span data-ttu-id="8475a-109">例: ある名前空間にある XML 内の要素を検索する</span><span class="sxs-lookup"><span data-stu-id="8475a-109">Example: Find an element in XML that's in a namespace</span></span>

<span data-ttu-id="8475a-110">次の例では同じクエリを確認できますが、ある名前空間にある XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="8475a-110">The following example shows the same query, but for XML that's in a namespace.</span></span> <span data-ttu-id="8475a-111">XML ドキュメント「[サンプル XML ファイル: 名前空間内の一般的な購買発注書](sample-xml-file-typical-purchase-order-namespace.md)」が使用されています。</span><span class="sxs-lookup"><span data-stu-id="8475a-111">It uses XML document [Sample XML file: typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span>

<span data-ttu-id="8475a-112">名前空間の詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8475a-112">For more information about namespaces, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> address =
    from el in root.Elements(aw + "Address")
    where (string)el.Attribute(aw + "Type") == "Billing"
    select el;
foreach (XElement el in address)
    Console.WriteLine(el);
```

```vb
Imports <xmlns:aw='http://www.adventure-works.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim address As IEnumerable(Of XElement) = _
            From el In root.<aw:Address> _
            Where el.@aw:Type = "Billing" _
            Select el
        For Each el As XElement In address
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

<span data-ttu-id="8475a-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8475a-113">This example produces the following output::</span></span>

```xml
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">
  <aw:Name>Tai Yee</aw:Name>
  <aw:Street>8 Oak Avenue</aw:Street>
  <aw:City>Old Town</aw:City>
  <aw:State>PA</aw:State>
  <aw:Zip>95819</aw:Zip>
  <aw:Country>USA</aw:Country>
</aw:Address>
```

## <a name="see-also"></a><span data-ttu-id="8475a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8475a-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="8475a-115">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="8475a-115">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8475a-116">射影操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="8475a-116">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="8475a-117">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8475a-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)
- [<span data-ttu-id="8475a-118">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8475a-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8475a-119">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8475a-119">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
