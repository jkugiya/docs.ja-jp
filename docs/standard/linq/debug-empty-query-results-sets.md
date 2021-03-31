---
title: 空のクエリ結果セットをデバッグする方法 - LINQ to XML
description: 既定の名前空間で XML ツリーにクエリを実行するときは、その XML が名前空間にないかのようにクエリを実行するというよくある間違いを避けてください。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 8fc6b1a80b183f8e2b0f80fc554a12c2657dcb55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "103366030"
---
# <a name="how-to-debug-empty-query-results-sets-linq-to-xml"></a><span data-ttu-id="baf5c-103">空のクエリ結果セットをデバッグする方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="baf5c-103">How to debug empty query results sets (LINQ to XML)</span></span>

<span data-ttu-id="baf5c-104">XML ツリーのクエリにおける最も一般的な問題の 1 つは、XML ツリーに既定の名前空間がある場合に、XML が名前空間に含まれていないものとして開発者がクエリを記述してしまうことです。</span><span class="sxs-lookup"><span data-stu-id="baf5c-104">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="baf5c-105">この記事の最初に示す一連の例では、既定の名前空間内の XML が読み込まれ、クエリが不適切に実行される典型的な例を示しています。</span><span class="sxs-lookup"><span data-stu-id="baf5c-105">The first set of examples in this article shows a typical way that XML in a default namespace is loaded, and then queried improperly.</span></span>

<span data-ttu-id="baf5c-106">2 番目に示す一連の例では、名前空間内の XML に対してクエリを実行できるようにするために必要な修正を示しています。</span><span class="sxs-lookup"><span data-stu-id="baf5c-106">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="baf5c-107">詳細については、[名前空間の概要](namespaces-overview.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="baf5c-107">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

## <a name="example-an-improper-query-on-xml-in-a-namespace"></a><span data-ttu-id="baf5c-108">例: 名前空間の XML に対する不適切なクエリ</span><span class="sxs-lookup"><span data-stu-id="baf5c-108">Example: An improper query on XML in a namespace</span></span>

<span data-ttu-id="baf5c-109">この例では、名前空間内にある XML の作成、および空の結果セットを返すクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="baf5c-109">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

<span data-ttu-id="baf5c-110">この例では、次の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="baf5c-110">The example produces this result:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example-a-proper-query-on-xml-in-a-namespace"></a><span data-ttu-id="baf5c-111">例: 名前空間の XML に対する適切なクエリ</span><span class="sxs-lookup"><span data-stu-id="baf5c-111">Example: A proper query on XML in a namespace</span></span>

<span data-ttu-id="baf5c-112">この例では、名前空間内にある XML の作成と、適切に記述されたクエリを示します。</span><span class="sxs-lookup"><span data-stu-id="baf5c-112">This example shows creation of XML in a namespace, and a query that's  coded properly.</span></span>

<span data-ttu-id="baf5c-113">解決方法は、<xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して初期化し、そのオブジェクトを <xref:System.Xml.Linq.XName> オブジェクトの指定時に使用することです。</span><span class="sxs-lookup"><span data-stu-id="baf5c-113">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="baf5c-114">この場合、<xref:System.Xml.Linq.XContainer.Elements%2A> メソッドの引数は <xref:System.Xml.Linq.XName> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="baf5c-114">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="baf5c-115">この例では、次の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="baf5c-115">The example produces this result:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="baf5c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="baf5c-116">See also</span></span>

- [<span data-ttu-id="baf5c-117">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="baf5c-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](./find-element-specific-attribute.md)
