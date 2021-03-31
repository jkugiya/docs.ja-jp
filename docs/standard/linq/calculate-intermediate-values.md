---
title: 中間値を計算する方法 - LINQ to XML
description: 並べ替え、フィルタリング、選択で使用するために中間の値を計算します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: c37926b93e0dc11255fd27c312679f6286fa7e5d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412153"
---
# <a name="how-to-calculate-intermediate-values-linq-to-xml"></a><span data-ttu-id="1afc4-103">中間値を計算する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="1afc4-103">How to calculate intermediate values (LINQ to XML)</span></span>

<span data-ttu-id="1afc4-104">この記事では、C# と Visual Basic で並べ替え、フィルタリング、選択に使用する中間の値を計算する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="1afc4-104">This article shows how to calculate intermediate values for use in sorting, filtering, and selecting in C# and Visual Basic.</span></span>

## <a name="example-use-the-let-clause-to-calculate-based-on-element-data"></a><span data-ttu-id="1afc4-105">例: `let` 句を使用し、要素データに基づいて計算する</span><span class="sxs-lookup"><span data-stu-id="1afc4-105">Example: Use the `let` clause to calculate based on element data</span></span>

<span data-ttu-id="1afc4-106">次の例では、`let` 句を使用し、要素から数値の積を計算します。</span><span class="sxs-lookup"><span data-stu-id="1afc4-106">The following example uses the `let` clause to calculate products of numerical values from elements.</span></span> <span data-ttu-id="1afc4-107">XML ドキュメント「[サンプル XML ファイル: 数値データ](sample-xml-file-numerical-data.md)」が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1afc4-107">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> extensions =
    from el in root.Elements("Data")
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim extensions As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
    Where extension > 25 _
    Order By extension _
    Select extension
For Each ex As Decimal In extensions
    Console.WriteLine(ex)
Next
```

<span data-ttu-id="1afc4-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1afc4-108">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="example-calculate-from-xml-thats-in-a-namespace"></a><span data-ttu-id="1afc4-109">例: ある名前空間にある XML から計算する</span><span class="sxs-lookup"><span data-stu-id="1afc4-109">Example: Calculate from XML that's in a namespace</span></span>

<span data-ttu-id="1afc4-110">次の例のクエリは前のものと同じですが、ある名前空間にある XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="1afc4-110">The following example shows the same query as before, but for XML that's in a namespace.</span></span> <span data-ttu-id="1afc4-111">XML ドキュメント「[サンプル XML ファイル: 名前空間内の数値データ](sample-xml-file-numerical-data-namespace.md)」が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1afc4-111">It uses the XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="1afc4-112">詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1afc4-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace ad = "http://www.adatum.com";
IEnumerable<decimal> extensions =
    from el in root.Elements(ad + "Data")
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")
    where extension >= 25
    orderby extension
    select extension;
foreach (decimal ex in extensions)
    Console.WriteLine(ex);
```

```vb
Imports <xmlns="http://www.adatum.com">

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim extensions As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _
            Where extension > 25 _
            Order By extension _
            Select extension
        For Each ex As Decimal In extensions
            Console.WriteLine(ex)
        Next
    End Sub
End Module
```

<span data-ttu-id="1afc4-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1afc4-113">This example produces the following output:</span></span>

```output
55.92
73.50
89.99
198.00
435.00
```

## <a name="see-also"></a><span data-ttu-id="1afc4-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1afc4-114">See also</span></span>

- [<span data-ttu-id="1afc4-115">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1afc4-115">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
