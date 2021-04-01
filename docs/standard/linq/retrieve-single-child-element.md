---
title: 単一の子要素を取得する方法 - LINQ to XML
description: 指定された名前を持つ最初の子要素を取得します。 C# では XContainer.Element を使用し、Visual Basic では配列インデクサー表記を使用できます。
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: e557e82e4e5891d6890a0efb4973796050b75349
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412196"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml"></a><span data-ttu-id="6adc6-104">単一の子要素を取得する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6adc6-104">How to retrieve a single child element (LINQ to XML)</span></span>

<span data-ttu-id="6adc6-105">この記事では、指定された名前を持つ最初の子要素である単一の子要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6adc6-105">This article explains how to retrieve a single child element, the first child element that has a specified name.</span></span> <span data-ttu-id="6adc6-106">C# では、<xref:System.Xml.Linq.XContainer.Element%2A> メソッドを使用してこれを行います。</span><span class="sxs-lookup"><span data-stu-id="6adc6-106">In C# you do this with the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span> <span data-ttu-id="6adc6-107">Visual Basic は、配列インデクサー表記を使用してこれを行います。</span><span class="sxs-lookup"><span data-stu-id="6adc6-107">In Visual Basic you do it with array indexer notation.</span></span>

## <a name="example-retrieve-the-first-element-that-has-a-specified-name"></a><span data-ttu-id="6adc6-108">例: 指定された名前を持つ最初の要素を取得する</span><span class="sxs-lookup"><span data-stu-id="6adc6-108">Example: Retrieve the first element that has a specified name</span></span>

<span data-ttu-id="6adc6-109">次の例では、「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」の XML ドキュメントから最初の `DeliveryNotes` 要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="6adc6-109">The following example retrieves the first `DeliveryNotes` element from the XML document in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
XElement e = po.Element("DeliveryNotes");
Console.WriteLine(e);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim e As XElement = po.<DeliveryNotes>(0)
Console.WriteLine(e)
```

<span data-ttu-id="6adc6-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6adc6-110">This example produces the following output:</span></span>

```xml
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>
```

## <a name="example-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="6adc6-111">例: 名前空間にある XML から取得する</span><span class="sxs-lookup"><span data-stu-id="6adc6-111">Example: Retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="6adc6-112">次の例は、1 つ上と同じ内容を行いますが、名前空間にある XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="6adc6-112">The following example does the same thing as the one above, but for XML that's in a namespace.</span></span> <span data-ttu-id="6adc6-113">XML ドキュメントの[サンプル XML ファイル: 名前空間内の一般的な購買発注書](sample-xml-file-typical-purchase-order-namespace.md)が使用されています。</span><span class="sxs-lookup"><span data-stu-id="6adc6-113">It uses the XML document [Sample XML file: Typical purchase order in a namespace](sample-xml-file-typical-purchase-order-namespace.md).</span></span> <span data-ttu-id="6adc6-114">名前空間の詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6adc6-114">For more information about namespaces, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");
XNamespace aw = "http://www.adventure-works.com";
XElement e = po.Element(aw + "DeliveryNotes");
Console.WriteLine(e);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")
        Dim e As XElement = po.<aw:DeliveryNotes>(0)
        Console.WriteLine(e)
    End Sub
End Module
```

<span data-ttu-id="6adc6-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6adc6-115">This example produces the following output:</span></span>

```xml
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>
```

## <a name="see-also"></a><span data-ttu-id="6adc6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6adc6-116">See also</span></span>

- [<span data-ttu-id="6adc6-117">LINQ to XML 軸の概要</span><span class="sxs-lookup"><span data-stu-id="6adc6-117">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
