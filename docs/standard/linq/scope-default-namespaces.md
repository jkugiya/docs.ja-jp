---
title: 既定の名前空間のスコープ - LINQ to XML
description: XML ツリーで表される既定の名前空間は、クエリのスコープ内にありません。 クエリの実行方法として適切な方法と不適切な方法を次に示します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103366019"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a><span data-ttu-id="be51f-104">既定の名前空間のスコープ (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="be51f-104">Scope of default namespaces (LINQ to XML)</span></span>

<span data-ttu-id="be51f-105">XML ツリーで表される既定の名前空間は、クエリのスコープ内にありません。</span><span class="sxs-lookup"><span data-stu-id="be51f-105">Default namespaces as represented in the XML tree aren't in scope for queries.</span></span> <span data-ttu-id="be51f-106">XML が既定の名前空間に属する場合、名前空間とローカル名を組み合わせ、クエリで使用する修飾名を作る必要があります。</span><span class="sxs-lookup"><span data-stu-id="be51f-106">If you have XML that's in a default namespace, you must combine a namespace with the local name to make a qualified name to be used in the query.</span></span>

<span data-ttu-id="be51f-107">既定の名前空間を持つ XML ツリーにクエリを実行するときによくある間違いは、その XML が名前空間に属していないかのようにクエリを作成することです。</span><span class="sxs-lookup"><span data-stu-id="be51f-107">A common mistake in querying an XML tree that has a default namespace is to write the query as if the XML weren't in a namespace.</span></span> <span data-ttu-id="be51f-108">最初の例で確認できる既定の名前空間のクエリは、不適切なクエリとして典型的なものです。</span><span class="sxs-lookup"><span data-stu-id="be51f-108">The first example shows a typical improper query of a default namespace.</span></span> <span data-ttu-id="be51f-109">2 つ目からは適切なクエリを確認できます。</span><span class="sxs-lookup"><span data-stu-id="be51f-109">The second shows a proper query.</span></span>

## <a name="example-improper-query-of-xml-in-a-namespace"></a><span data-ttu-id="be51f-110">例: 名前空間における XML の不適切なクエリ</span><span class="sxs-lookup"><span data-stu-id="be51f-110">Example: Improper query of XML in a namespace</span></span>

<span data-ttu-id="be51f-111">この例では、名前空間で XML が作成されており、不適切なクエリから空の結果セットが返されています。</span><span class="sxs-lookup"><span data-stu-id="be51f-111">This example shows the creation of XML in a namespace, and an improper query that returns an empty result set.</span></span>

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

<span data-ttu-id="be51f-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be51f-112">This example produces the following output:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a><span data-ttu-id="be51f-113">例: 名前空間における XML の適切なクエリ</span><span class="sxs-lookup"><span data-stu-id="be51f-113">Example:  Proper query of XML in a namespace</span></span>

<span data-ttu-id="be51f-114">この例では、名前空間で XML が作成されており、クリエは適切です。</span><span class="sxs-lookup"><span data-stu-id="be51f-114">This example shows the creation of XML in a namespace, and a proper query.</span></span>

<span data-ttu-id="be51f-115">C# の場合、正しいアプローチは、<xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して初期化し、そのオブジェクトを <xref:System.Xml.Linq.XName> オブジェクトの指定時に使用することです。</span><span class="sxs-lookup"><span data-stu-id="be51f-115">In C#, the correct approach is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="be51f-116">この場合、<xref:System.Xml.Linq.XContainer.Elements%2A> メソッドの引数は <xref:System.Xml.Linq.XName> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="be51f-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="be51f-117">Visual Basic を使用する場合は、グローバルな既定の名前空間を宣言して初期化するのが正しい方法です。</span><span class="sxs-lookup"><span data-stu-id="be51f-117">The correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="be51f-118">これにより、すべての XML プロパティが既定の名前空間に配置されます。</span><span class="sxs-lookup"><span data-stu-id="be51f-118">This places all XML properties in the default namespace.</span></span>

<span data-ttu-id="be51f-119">次にコードを示します。</span><span class="sxs-lookup"><span data-stu-id="be51f-119">Here is the code:</span></span>

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
            Console.WriteLine(el.Value)
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="be51f-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="be51f-120">This example produces the following output:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="be51f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="be51f-121">See also</span></span>

- [<span data-ttu-id="be51f-122">名前空間の概要</span><span class="sxs-lookup"><span data-stu-id="be51f-122">Namespaces overview</span></span>](namespaces-overview.md)
