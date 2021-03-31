---
title: 要素のコレクションを取得する方法 - LINQ to XML
description: XContainer.Elements メソッドを使用し、要素の子要素のコレクションを取得する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: e73f608cff13f75f769f77372dc1c09949e00b0e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411963"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml"></a><span data-ttu-id="157ee-103">要素のコレクションを取得する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="157ee-103">How to retrieve a collection of elements (LINQ to XML)</span></span>

<span data-ttu-id="157ee-104">この記事では、要素の子要素のコレクションを取得する <xref:System.Xml.Linq.XContainer.Elements%2A> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="157ee-104">This article demonstrates the <xref:System.Xml.Linq.XContainer.Elements%2A> method, which retrieves a collection of the child elements of an element.</span></span>

## <a name="example-iterate-through-the-child-elements-of-an-element"></a><span data-ttu-id="157ee-105">例: 要素の子要素を反復処理する</span><span class="sxs-lookup"><span data-stu-id="157ee-105">Example: Iterate through the child elements of an element</span></span>

<span data-ttu-id="157ee-106">この例では、`purchaseOrder` 要素の子要素を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="157ee-106">This example iterates through the child elements of the `purchaseOrder` element.</span></span> <span data-ttu-id="157ee-107">XML ドキュメント「[サンプル XML ファイル: 一般的な購買発注書](sample-xml-file-typical-purchase-order.md)」が使用されます。</span><span class="sxs-lookup"><span data-stu-id="157ee-107">It uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
XElement po = XElement.Load("PurchaseOrder.xml");
IEnumerable<XElement> childElements =
    from el in po.Elements()
    select el;
foreach (XElement el in childElements)
    Console.WriteLine("Name: " + el.Name);
```

```vb
Dim po As XElement = XElement.Load("PurchaseOrder.xml")
Dim childElements As IEnumerable(Of XElement)
childElements = _
    From el In po.Elements() _
    Select el
For Each el As XElement In childElements
    Console.WriteLine("Name: " & el.Name.ToString())
Next
```

<span data-ttu-id="157ee-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="157ee-108">This example produces the following output:</span></span>

```output
Name: Address
Name: Address
Name: DeliveryNotes
Name: Items
```

## <a name="see-also"></a><span data-ttu-id="157ee-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="157ee-109">See also</span></span>

- [<span data-ttu-id="157ee-110">LINQ to XML 軸の概要</span><span class="sxs-lookup"><span data-stu-id="157ee-110">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
