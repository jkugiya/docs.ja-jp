---
title: 要素を並べ替える方法 - LINQ to XML
description: その結果を並べ替えるクエリを記述する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 0e93add12e39c71c7312036917d42dd53450b712
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412134"
---
# <a name="how-to-sort-elements-linq-to-xml"></a><span data-ttu-id="54fff-103">要素を並べ替える方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="54fff-103">How to sort elements (LINQ to XML)</span></span>

<span data-ttu-id="54fff-104">XML にクエリを実行するとき、結果を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="54fff-104">You can sort your results when you query XML.</span></span> <span data-ttu-id="54fff-105">この記事では、2 つの例を取り上げます。最初の例では、名前空間に "*属さない*" XML に対して結果を並べ替えます。2 番目も並べ替えは同じですが、ある名前空間に "*属する*" XML が対象になります。</span><span class="sxs-lookup"><span data-stu-id="54fff-105">This article provides two examples: the first sorts results for XML that *isn't* in a namespace, and the second does the same sort, but for XML that *is* in a namespace.</span></span>

## <a name="example-write-a-query-that-sorts-its-results"></a><span data-ttu-id="54fff-106">例: その結果を並べ替えるクエリを記述する</span><span class="sxs-lookup"><span data-stu-id="54fff-106">Example: Write a query that sorts its results</span></span>

<span data-ttu-id="54fff-107">この例では、結果を並べ替えるクエリの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="54fff-107">This example shows how to write a query that sorts its results.</span></span> <span data-ttu-id="54fff-108">XML ドキュメント「[サンプル XML ファイル: 数値データ](sample-xml-file-numerical-data.md)」が使用されます。</span><span class="sxs-lookup"><span data-stu-id="54fff-108">It uses XML document [Sample XML file: Numerical data](sample-xml-file-numerical-data.md).</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
IEnumerable<decimal> prices =
    from el in root.Elements("Data")
    let price = (decimal)el.Element("Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim prices As IEnumerable(Of Decimal) = _
    From el In root.<Data> _
    Let price = Convert.ToDecimal(el.<Price>.Value) _
    Order By (price) _
    Select price
For Each el As Decimal In prices
    Console.WriteLine(el)
Next
```

<span data-ttu-id="54fff-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="54fff-109">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="example-write-a-query-in-a-namespace-that-sorts-its-results"></a><span data-ttu-id="54fff-110">例: ある名前空間を対象とするクエリで、その結果を並べ替えるクエリを記述する</span><span class="sxs-lookup"><span data-stu-id="54fff-110">Example: Write a query in a namespace that sorts its results</span></span>

<span data-ttu-id="54fff-111">次の例では同じクエリを確認できますが、ある名前空間にある XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="54fff-111">The following example shows the same query for XML that's in a namespace.</span></span> <span data-ttu-id="54fff-112">XML ドキュメント「[サンプル XML ファイル: 名前空間内の数値データ](sample-xml-file-numerical-data-namespace.md)」が使用されます。</span><span class="sxs-lookup"><span data-stu-id="54fff-112">It uses XML document [Sample XML file: Numerical data in a namespace](sample-xml-file-numerical-data-namespace.md).</span></span>

<span data-ttu-id="54fff-113">詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54fff-113">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Load("DataInNamespace.xml");
XNamespace aw = "http://www.adatum.com";
IEnumerable<decimal> prices =
    from el in root.Elements(aw + "Data")
    let price = (decimal)el.Element(aw + "Price")
    orderby price
    select price;
foreach (decimal el in prices)
    Console.WriteLine(el);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = XElement.Load("DataInNamespace.xml")
        Dim prices As IEnumerable(Of Decimal) = _
            From el In root.<Data> _
            Let price = Convert.ToDecimal(el.<Price>.Value) _
            Order By (price) _
            Select price
        For Each el As Decimal In prices
            Console.WriteLine(el)
        Next
    End Sub
End Module
```

<span data-ttu-id="54fff-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="54fff-114">This example produces the following output:</span></span>

```output
0.99
4.95
6.99
24.50
29.00
66.00
89.99
```

## <a name="see-also"></a><span data-ttu-id="54fff-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="54fff-115">See also</span></span>

- [<span data-ttu-id="54fff-116">データの並べ替え (C#)</span><span class="sxs-lookup"><span data-stu-id="54fff-116">Sorting Data (C#)</span></span>](../../csharp/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="54fff-117">データの並べ替え (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54fff-117">Sorting Data (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/sorting-data.md)
- [<span data-ttu-id="54fff-118">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54fff-118">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
