---
title: 省略可能な要素をフィルター処理する方法 - LINQ to XML
description: 要素が存在しないとき、検索で例外をトリガーしないように子要素の検索を記述できます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: 0bf4a2f2c1db420492939351795e3b66b9e0b6b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412128"
---
# <a name="how-to-filter-on-an-optional-element-linq-to-xml"></a><span data-ttu-id="a7233-103">省略可能な要素をフィルター処理する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a7233-103">How to filter on an optional element (LINQ to XML)</span></span>

<span data-ttu-id="a7233-104">要素に対するフィルター処理が、その要素が XML ドキュメント内に存在しているかどうか明確でない場合でも必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="a7233-104">Sometimes you want to filter for an element even though you're not sure it exists in your XML document.</span></span> <span data-ttu-id="a7233-105">特定の要素に子要素がない場合でも、それに対するフィルター処理によって null 参照例外をトリガーしないように検索を記述できます。</span><span class="sxs-lookup"><span data-stu-id="a7233-105">You can write your search so that, even if the particular element doesn't have the child element, you don't trigger a null reference exception by filtering for it.</span></span>

## <a name="example-search-that-doesnt-trigger-an-exception-when-the-target-element-doesnt-exist"></a><span data-ttu-id="a7233-106">例: ターゲット要素が存在しないときに例外をトリガーしない検索</span><span class="sxs-lookup"><span data-stu-id="a7233-106">Example: Search that doesn't trigger an exception when the target element doesn't exist</span></span>

<span data-ttu-id="a7233-107">次の例では、`Child5` 要素には `Type` 子要素はありませんが、クエリは正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a7233-107">In the following example, the `Child5` element doesn't have a `Type` child element, but the query still executes correctly.</span></span> <span data-ttu-id="a7233-108">例では、<xref:System.Xml.Linq.Extensions.Elements%2A> 拡張メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="a7233-108">The example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
var cList =
    from typeElement in root.Elements().Elements("Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element("Text");
foreach(string str in cList)
    Console.WriteLine(str);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <Text>Child One Text</Text>
            <Type Value="Yes"/>
        </Child1>
        <Child2>
            <Text>Child Two Text</Text>
            <Type Value="Yes"/>
        </Child2>
        <Child3>
            <Text>Child Three Text</Text>
            <Type Value="No"/>
        </Child3>
        <Child4>
            <Text>Child Four Text</Text>
            <Type Value="Yes"/>
        </Child4>
        <Child5>
            <Text>Child Five Text</Text>
        </Child5>
    </Root>
Dim cList As IEnumerable(Of String) = _
    From typeElement In root.Elements().<Type> _
    Where typeElement.@Value = "Yes" _
    Select typeElement.Parent.<Text>.Value
Dim str As String
For Each str In cList
    Console.WriteLine(str)
Next
```

<span data-ttu-id="a7233-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a7233-109">This example produces the following output:</span></span>

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="example-same-search-but-for-xml-in-a-namespace"></a><span data-ttu-id="a7233-110">例: 同じ検索であるが、ある名前空間に属する XML を対象とする</span><span class="sxs-lookup"><span data-stu-id="a7233-110">Example: Same search but for XML in a namespace</span></span>

<span data-ttu-id="a7233-111">次の例では同じクエリを確認できますが、ある名前空間にある XML が対象になっています。</span><span class="sxs-lookup"><span data-stu-id="a7233-111">The following example is the same query but for XML that's in a namespace.</span></span> <span data-ttu-id="a7233-112">詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a7233-112">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>
  <Child1>
    <Text>Child One Text</Text>
    <Type Value=""Yes""/>
  </Child1>
  <Child2>
    <Text>Child Two Text</Text>
    <Type Value=""Yes""/>
  </Child2>
  <Child3>
    <Text>Child Three Text</Text>
    <Type Value=""No""/>
  </Child3>
  <Child4>
    <Text>Child Four Text</Text>
    <Type Value=""Yes""/>
  </Child4>
  <Child5>
    <Text>Child Five Text</Text>
  </Child5>
</Root>");
XNamespace ad = "http://www.adatum.com";
var cList =
    from typeElement in root.Elements().Elements(ad + "Type")
    where (string)typeElement.Attribute("Value") == "Yes"
    select (string)typeElement.Parent.Element(ad + "Text");
foreach (string str in cList)
    Console.WriteLine(str);
```

```vb
Imports <xmlns='http://www.adatum.com'>

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child1>
                    <Text>Child One Text</Text>
                    <Type Value="Yes"/>
                </Child1>
                <Child2>
                    <Text>Child Two Text</Text>
                    <Type Value="Yes"/>
                </Child2>
                <Child3>
                    <Text>Child Three Text</Text>
                    <Type Value="No"/>
                </Child3>
                <Child4>
                    <Text>Child Four Text</Text>
                    <Type Value="Yes"/>
                </Child4>
                <Child5>
                    <Text>Child Five Text</Text>
                </Child5>
            </Root>
        Dim cList As IEnumerable(Of String) = _
            From typeElement In root.Elements().<Type> _
            Where typeElement.@Value = "Yes" _
            Select typeElement.Parent.<Text>.Value
        Dim str As String
        For Each str In cList
            Console.WriteLine(str)
        Next
    End Sub
End Module
```

<span data-ttu-id="a7233-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a7233-113">This example produces the following output:</span></span>

```output
Child One Text
Child Two Text
Child Four Text
```

## <a name="see-also"></a><span data-ttu-id="a7233-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7233-114">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a7233-115">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="a7233-115">Standard Query Operators Overview (C#)</span></span>](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a7233-116">射影操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="a7233-116">Projection Operations (C#)</span></span>](../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="a7233-117">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7233-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
- [<span data-ttu-id="a7233-118">XML 子軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7233-118">XML Child Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="a7233-119">XML 属性軸プロパティ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7233-119">XML Attribute Axis Property (Visual Basic)</span></span>](../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="a7233-120">XML Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="a7233-120">XML Value Property</span></span>](../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="a7233-121">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7233-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a7233-122">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7233-122">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
