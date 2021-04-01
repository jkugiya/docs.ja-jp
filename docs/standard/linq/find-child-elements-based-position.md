---
title: 位置に基づいて子要素を検索する方法 - LINQ to XML
description: 要素の位置に基づいて要素を検索する方法について説明します。 3 つの方法を紹介します。そのうちの 1 つでは XPathEvaluate を使用し、そのうちの 2 つでは LINQ to XML クエリを使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 889e3dbac3acf229fd49422285d650fc13792521
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412146"
---
# <a name="how-to-find-child-elements-based-on-position-linq-to-xml"></a><span data-ttu-id="f1726-104">位置に基づいて子要素を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f1726-104">How to find child elements based on position (LINQ to XML)</span></span>

<span data-ttu-id="f1726-105">この記事では、<xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> を使用し、要素の位置に基づいて要素を検索する方法を紹介します。たとえば、2 番目の要素を検索したり、3 番目から 5 番目までを検索したりします。</span><span class="sxs-lookup"><span data-stu-id="f1726-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to find elements based on element position – for example, to find the second element, or the third through the fifth.</span></span> <span data-ttu-id="f1726-106">また、LINQ to XML クエリを使用して同じことを行う方法を 2 つ紹介します。</span><span class="sxs-lookup"><span data-stu-id="f1726-106">It also shows two ways to use LINQ to XML query to do the same thing.</span></span>

<span data-ttu-id="f1726-107">レイジー方式でこの LINQ to XML クエリを記述する方法が 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="f1726-107">There are two approaches to writing this LINQ to XML query in a lazy way.</span></span> <span data-ttu-id="f1726-108">1 つは <xref:System.Linq.Enumerable.Skip%2A> 演算子と <xref:System.Linq.Enumerable.Take%2A> 演算子を使用する方法で、もう 1 つはインデックスを受け取る <xref:System.Linq.Enumerable.Where%2A> オーバーロードを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="f1726-108">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="f1726-109"><xref:System.Linq.Enumerable.Where%2A> オーバーロードを使用する場合は、2 つの引数を受け取るラムダ式を使用します。</span><span class="sxs-lookup"><span data-stu-id="f1726-109">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="f1726-110">次の例では、位置に基づいて選択する両方のメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="f1726-110">The following example shows both methods of selecting based on position.</span></span>

## <a name="example-find-the-second-through-the-fourth-test-elements"></a><span data-ttu-id="f1726-111">例: 2 番目から 4 番目の `Test` 要素を検索する</span><span class="sxs-lookup"><span data-stu-id="f1726-111">Example: Find the second through the fourth `Test` elements</span></span>

<span data-ttu-id="f1726-112">この例では、「[サンプル XML ファイル: テスト構成](sample-xml-file-test-configuration.md)」で 2 番目から 4 番目までの `Test` 要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="f1726-112">This example finds the second through the fourth `Test` element in the [Sample XML file: Test configuration](sample-xml-file-test-configuration.md).</span></span> <span data-ttu-id="f1726-113">結果は要素のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="f1726-113">The result is a collection of elements.</span></span>

<span data-ttu-id="f1726-114">XPath 式は `Test[position() >= 2 and position() <= 4]` です。</span><span class="sxs-lookup"><span data-stu-id="f1726-114">The XPath expression is `Test[position() >= 2 and position() <= 4]`.</span></span>

```csharp
XElement testCfg = XElement.Load("TestConfig.xml");

// LINQ to XML query
IEnumerable<XElement> list1 =
    testCfg
    .Elements("Test")
    .Skip(1)
    .Take(3);

// LINQ to XML query
IEnumerable<XElement> list2 =
    testCfg
    .Elements("Test")
    .Where((el, idx) => idx >= 1 && idx <= 3);

// XPath expression
IEnumerable<XElement> list3 =
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");

if (list1.Count() == list2.Count() &&
    list1.Count() == list3.Count() &&
    list1.Intersect(list2).Count() == list1.Count() &&
    list1.Intersect(list3).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim testCfg As XElement = XElement.Load("TestConfig.xml")

' LINQ to XML query
Dim list1 As IEnumerable(Of XElement) = _
    testCfg.Elements("Test").Skip(1).Take(3)

'LINQ to XML query
Dim list2 As IEnumerable(Of XElement) = _
    testCfg.Elements("Test"). _
    Where(Function(ByVal el, ByVal idx) idx >= 1 And idx <= 3)

' XPath expression
Dim list3 As IEnumerable(Of XElement) = _
    testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]")

If list1.Count() = list2.Count() And _
       list1.Count() = list3.Count() And _
       list1.Intersect(list2).Count() = list1.Count() And _
       list1.Intersect(list3).Count() = list1.Count() Then

    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If

For Each el As XElement In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f1726-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f1726-115">This example produces the following output:</span></span>

```output
Results are identical
<Test TestId="0002" TestType="CMD">
  <Name>Find succeeding characters</Name>
  <CommandLine>Examp2.EXE</CommandLine>
  <Input>abc</Input>
  <Output>def</Output>
</Test>
<Test TestId="0003" TestType="GUI">
  <Name>Convert multiple numbers to strings</Name>
  <CommandLine>Examp2.EXE /Verbose</CommandLine>
  <Input>123</Input>
  <Output>One Two Three</Output>
</Test>
<Test TestId="0004" TestType="GUI">
  <Name>Find correlated key</Name>
  <CommandLine>Examp3.EXE</CommandLine>
  <Input>a1</Input>
  <Output>b1</Output>
</Test>
```

## <a name="see-also"></a><span data-ttu-id="f1726-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1726-116">See also</span></span>

- [<span data-ttu-id="f1726-117">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1726-117">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
