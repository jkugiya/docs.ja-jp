---
title: 子要素の子孫を検索する方法 - LINQ to XML
description: 子要素または一連の子要素の子孫を検索する方法について説明します。 2 つの方法を紹介します。1 つは XPathEvaluate を使用し、もう 1 つは LINQ to XML クエリを使用します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: 2ac023ddc797f27f5f00eaf86ff6357096f333c8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103412156"
---
# <a name="how-to-find-descendants-of-a-child-element-linq-to-xml"></a><span data-ttu-id="cb604-104">子要素の子孫を検索する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cb604-104">How to find descendants of a child element (LINQ to XML)</span></span>

<span data-ttu-id="cb604-105">この記事では、<xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> を使用し、一連の子要素の子孫要素を検索する方法と、LINQ to XML クエリを使用して同じことをする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="cb604-105">This article shows how to use <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> to find the descendant elements of a sequence of child elements, and how to use LINQ to XML query to find the same elements.</span></span>

## <a name="example-find-all-the-text-descendant-elements-of-all-the-paragraph-elements"></a><span data-ttu-id="cb604-106">例: すべての `Paragraph` 要素の `Text` 子孫要素をすべて検索する</span><span class="sxs-lookup"><span data-stu-id="cb604-106">Example: Find all the `Text` descendant elements of all the `Paragraph` elements</span></span>

<span data-ttu-id="cb604-107">この例では、XML で表現された簡単なワープロ文書からテキストを抽出します。</span><span class="sxs-lookup"><span data-stu-id="cb604-107">This example extracts text from an XML representation of a simple word processing document.</span></span> <span data-ttu-id="cb604-108">最初に `Comment` 要素を無視してすべての `Paragraph` 要素を選択します。次に、各 `Paragraph` 要素の `Text` 子孫要素をすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="cb604-108">It first selects all `Paragraph` elements, ignoring the `Comment` element, and then it selects all the `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="cb604-109">この作業は 2 つの方法で行われます。<xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> を使用する方法と、LINQ to XML クエリを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="cb604-109">It does this task in two ways: with <xref:System.Xml.XPath.Extensions.XPathEvaluate%2A> and with LINQ to XML query.</span></span> <span data-ttu-id="cb604-110">その後、結果を比較し、同じであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cb604-110">It then compares the results and finds them identical.</span></span>

<span data-ttu-id="cb604-111">XPath 式は `./Paragraph//Text/text()` です。</span><span class="sxs-lookup"><span data-stu-id="cb604-111">The XPath expression is  `./Paragraph//Text/text()`.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root>
  <Paragraph>
    <Text>This is the start of</Text>
  </Paragraph>
  <Comment>
    <Text>This comment isn't part of the paragraph text.</Text>
  </Comment>
  <Paragraph>
    <Annotation Emphasis='true'>
      <Text> a sentence.</Text>
    </Annotation>
  </Paragraph>
  <Paragraph>
    <Text>  This is the second sentence.</Text>
  </Paragraph>
</Root>");

// LINQ to XML query
string str1 =
    root
    .Elements("Paragraph")
    .Descendants("Text")
    .Select(s => s.Value)
    .Aggregate(
        new StringBuilder(),
        (s, i) => s.Append(i),
        s => s.ToString()
    );

// XPath expression
string str2 =
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))
    .Cast<XText>()
    .Select(s => s.Value)
    .Aggregate(
        new StringBuilder(),
        (s, i) => s.Append(i),
        s => s.ToString()
    );

if (str1 == str2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(str2);
```

```vb
Dim root As XElement = _
    <Root>
        <Paragraph>
            <Text>This is the start of</Text>
        </Paragraph>
        <Comment>
            <Text>This comment isn't part of the paragraph text.</Text>
        </Comment>
        <Paragraph>
            <Annotation Emphasis='true'>
                <Text> a sentence.</Text>
            </Annotation>
        </Paragraph>
        <Paragraph>
            <Text>This is the second sentence.</Text>
        </Paragraph>
    </Root>

' LINQ to XML query
Dim str1 As String = _
    root.<Paragraph>...<Text>.Select(Function(ByVal s) s.Value). _
    Aggregate( _
        New StringBuilder(), _
        Function(ByVal s, ByVal i) s.Append(i), _
        Function(ByVal s) s.ToString())

' XPath expression
Dim str2 As String = DirectCast(root.XPathEvaluate("./Paragraph//Text/text()"), IEnumerable) _
    .Cast(Of XText)().Select(Function(ByVal s) s.Value) _
    .Aggregate( _
        New StringBuilder(), _
        Function(ByVal s, ByVal i) s.Append(i), _
        Function(ByVal s) s.ToString())

If str1 = str2 Then
    Console.WriteLine("Results are identical")
Else
    Console.WriteLine("Results differ")
End If
Console.WriteLine(str2)
```

<span data-ttu-id="cb604-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cb604-112">This example produces the following output:</span></span>

```output
Results are identical
This is the start of a sentence.  This is the second sentence.
```

## <a name="see-also"></a><span data-ttu-id="cb604-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb604-113">See also</span></span>

- [<span data-ttu-id="cb604-114">XPath ユーザー向けの LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb604-114">LINQ to XML for XPath Users (Visual Basic)</span></span>](./comparison-xpath-linq-xml.md)
