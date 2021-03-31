---
title: 要素の浅い値を取得する方法 - LINQ to XML
description: 要素の浅い値を取得するには、`ShallowValue` 拡張メソッドを使用します。 浅い値は、その要素の値のみです。つまり、子孫要素の値は含まれません。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 761ffc07b13ebdc652b75bf96ba5b121c7912fd7
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412074"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-linq-to-xml"></a><span data-ttu-id="9ae6a-104">要素の浅い値を取得する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9ae6a-104">How to retrieve the shallow value of an element (LINQ to XML)</span></span>

<span data-ttu-id="9ae6a-105">この記事では、要素の浅い値を取得する方法について説明します。これは要素の値のみで、子孫要素の値は含まれません。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-105">This article shows how to retrieve the shallow value of an element, which is the value of that element only, not including values of descendent elements.</span></span> <span data-ttu-id="9ae6a-106">浅い値を取得することは、要素をその内容に基づいて選択する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-106">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="9ae6a-107">キャストまたは <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> プロパティを使用して要素の値を取得すると、その子孫が値に含まれます。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-107">When you use casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property to retrieve an element value, the value includes the descendants.</span></span> <span data-ttu-id="9ae6a-108">浅い値を取得するには、次の例のように `ShallowValue` 拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-108">To retrieve the shallow value you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="9ae6a-109">この例では、要素の浅い値を取得する拡張メソッドを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-109">The example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="9ae6a-110">次に、この拡張メソッドをクエリの中で使用して、計算値を含んだすべての要素をリストします。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-110">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example-use-the-shallowvalue-extension-method-to-retrieve-the-shallow-value-of-an-element"></a><span data-ttu-id="9ae6a-111">例: `ShallowValue` 拡張メソッドを使用して要素の浅い値を取得する</span><span class="sxs-lookup"><span data-stu-id="9ae6a-111">Example: Use the `ShallowValue` extension method to retrieve the shallow value of an element</span></span>

<span data-ttu-id="9ae6a-112">この例では、次を含むテキスト ファイル Report.xml を使用します。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-112">The examples uses the text file Report.xml that contains the following:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Report>
  <Section>
    <Heading>
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>
      <Column Name="Name">=Customer.Name.Heading</Column>
    </Heading>
    <Detail>
      <Column Name="CustomerId">=Customer.CustomerId</Column>
      <Column Name="Name">=Customer.Name</Column>
    </Detail>
  </Section>
</Report>
```

<span data-ttu-id="9ae6a-113">この例のコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-113">Here is the code for the example:</span></span>

```csharp
public static class MyExtensions
{
    public static string ShallowValue(this XElement xe)
    {
        return xe
               .Nodes()
               .OfType<XText>()
               .Aggregate(new StringBuilder(),
                          (s, c) => s.Append(c),
                          s => s.ToString());
    }
}

class Program
{
    static void Main(string[] args)
    {
        XElement root = XElement.Load("Report.xml");

        IEnumerable<XElement> query = from el in root.Descendants()
                                      where el.ShallowValue().StartsWith("=")
                                      select el;

        foreach (var q in query)
        {
            Console.WriteLine("{0}{1}{2}",
                q.Name.ToString().PadRight(8),
                q.Attribute("Name").ToString().PadRight(20),
                q.ShallowValue());
        }
    }
}
```

```vb
Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function ShallowValue(ByVal xe As XElement)
        Return xe _
               .Nodes() _
               .OfType(Of XText)() _
               .Aggregate(New StringBuilder(), _
                              Function(s, c) s.Append(c), _
                              Function(s) s.ToString())
    End Function

    Sub Main()
        Dim root As XElement = XElement.Load("Report.xml")

        Dim query As IEnumerable(Of XElement) = _
            From el In root.Descendants() _
            Where (el.ShallowValue().StartsWith("=")) _
            Select el

        For Each q As XElement In query
            Console.WriteLine("{0}{1}{2}", _
                q.Name.ToString().PadRight(8), _
                q.Attribute("Name").ToString().PadRight(20), _
                q.ShallowValue())
        Next
    End Sub
End Module
```

<span data-ttu-id="9ae6a-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9ae6a-114">This example produces the following output:</span></span>

```output
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="9ae6a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ae6a-115">See also</span></span>

- [<span data-ttu-id="9ae6a-116">LINQ to XML 軸の概要</span><span class="sxs-lookup"><span data-stu-id="9ae6a-116">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
