---
title: ルート要素を検索する方法 - LINQ to XML
description: C# および Visual Basic で XPath と LINQ to XML を使用して、XML ドキュメントのルート要素を検索する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 89247c19fc31add4e95f11742772cef1bdd2ce63
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "103412204"
---
# <a name="how-to-find-the-root-element-linq-to-xml"></a><span data-ttu-id="36995-103">ルート要素を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="36995-103">How to find the root element (LINQ to XML)</span></span>

<span data-ttu-id="36995-104">この記事では、C# および Visual Basic で XPath と LINQ to XML を使用して、XML ドキュメントのルート要素を検索する方法を示す例を提供します。</span><span class="sxs-lookup"><span data-stu-id="36995-104">This article provides an example that shows how to use XPath and LINQ to XML, in C# and Visual Basic, to find the root element of an XML document.</span></span>

## <a name="example-find-the-root-element"></a><span data-ttu-id="36995-105">例: ルート要素を検索する</span><span class="sxs-lookup"><span data-stu-id="36995-105">Example: Find the root element</span></span>

<span data-ttu-id="36995-106">この例では、LINQ to XML クエリと XPath を使用して、XML ドキュメントの「[サンプル XML ファイル: 複数の購買発注書](sample-xml-file-multiple-purchase-orders.md)」のルート要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="36995-106">This example uses LINQ to XML query and XPath to find the root element in XML document [Sample XML file: Multiple purchase orders](sample-xml-file-multiple-purchase-orders.md).</span></span> <span data-ttu-id="36995-107">XPath 式は `/PurchaseOrders` です。</span><span class="sxs-lookup"><span data-stu-id="36995-107">The XPath expression is `/PurchaseOrders`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

// LINQ to XML query
XElement el1 = po.Root;

// XPath expression
XElement el2 = po.XPathSelectElement("/PurchaseOrders");

if (el1 == el2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(el1.Name);
```

```vb
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")

' LINQ to XML query
Dim el1 As XElement = po.Root

' XPath expression
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")

If el1 Is el2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(el1.Name)
```

<span data-ttu-id="36995-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="36995-108">This example produces the following output:</span></span>

```output
Results are identical
PurchaseOrders
```

## <a name="see-also"></a><span data-ttu-id="36995-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="36995-109">See also</span></span>

- [<span data-ttu-id="36995-110">XPath と LINQ to XML の比較</span><span class="sxs-lookup"><span data-stu-id="36995-110">Comparison of XPath and LINQ to XML</span></span>](comparison-xpath-linq-xml.md)
