---
title: 名前空間内の XML に対するクエリを記述する方法 - LINQ to XML
description: 名前空間内の XML に対するクエリを記述するには、正しい名前空間を持つ XName オブジェクトを使用します。 これを C# と Visual Basic で行う方法と、クエリを作成する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7c54df81-15e4-4091-8c81-a87637029130
ms.openlocfilehash: 7d2c765c30409b019bf4723b9161c577e2074c04
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103365989"
---
# <a name="how-to-write-queries-on-xml-in-namespaces-linq-to-xml"></a><span data-ttu-id="5a2a5-104">名前空間内の XML に対するクエリを記述する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5a2a5-104">How to write queries on XML in namespaces (LINQ to XML)</span></span>

<span data-ttu-id="5a2a5-105">名前空間にある XML でクエリを記述するには、名前空間が正しい <xref:System.Xml.Linq.XName> オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-105">To write a query on XML that's in a namespace, you must use <xref:System.Xml.Linq.XName> objects that have the correct namespace.</span></span>

<span data-ttu-id="5a2a5-106">C# での最も一般的な方法は、URI を含んだ文字列を使用して <xref:System.Xml.Linq.XNamespace> を初期化し、加算演算子オーバーロードを使用して名前空間をローカル名に連結することです。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-106">For C#, the most common approach is to initialize an <xref:System.Xml.Linq.XNamespace> using a string that contains the URI, then use the addition operator overload to combine the namespace with the local name.</span></span>

<span data-ttu-id="5a2a5-107">Visual Basic の場合、最も一般的な方法は、グローバル名前空間を定義し、その名前空間を使用する XML リテラルおよび XML プロパティを使用することです。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-107">For Visual Basic, the most common approach is to define a global namespace, and then use XML literals and XML properties that use the global namespace.</span></span> <span data-ttu-id="5a2a5-108">既定のグローバル名前空間を定義できます。その場合、XML リテラルの要素は既定でこの名前空間に含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-108">You can define a global default namespace, in which case elements in the XML literals will be in the namespace by default.</span></span> <span data-ttu-id="5a2a5-109">または、プレフィックスを持つグローバル名前空間を定義し、そのプレフィックスを必要に応じて XML リテラルや XML プロパティで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-109">Alternatively, you can define a global namespace with a prefix, and then use the prefix as required in the XML literals and in XML properties.</span></span> <span data-ttu-id="5a2a5-110">XML のその他の形式と同様に、属性は既定でどの名前空間にも含まれません。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-110">As with other forms of XML, attributes are always in no namespace by default.</span></span>

<span data-ttu-id="5a2a5-111">この記事の最初の例では、既定の名前空間内に XML ツリーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-111">The first example in this article shows how to create an XML tree in a default namespace.</span></span> <span data-ttu-id="5a2a5-112">2 つ目の例では、プレフィックスを持つ名前空間で XML ツリーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-112">The second shows how to create an XML tree in a namespace with a prefix.</span></span>

## <a name="example-create-a-tree-in-a-default-namespace-and-retrieve-elements"></a><span data-ttu-id="5a2a5-113">例: 既定の名前空間でツリーを作成し、要素を取得する</span><span class="sxs-lookup"><span data-stu-id="5a2a5-113">Example: Create a tree in a default namespace and retrieve elements</span></span>

<span data-ttu-id="5a2a5-114">次の例では、既定の名前空間にある XML ツリーが作成され、その後、要素コレクションが取得されます。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-114">The following example creates an XML tree that's in a default namespace, and then retrieves a collection of elements.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
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
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
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
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
    End Sub
End Module
```

<span data-ttu-id="5a2a5-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-115">This example produces the following output:</span></span>

```output
1
2
3
```

## <a name="example-create-a-tree-in-a-namespace-with-a-prefix-and-retrieve-elements"></a><span data-ttu-id="5a2a5-116">例: プレフィックスのある名前空間でツリーを作成し、要素を取得する</span><span class="sxs-lookup"><span data-stu-id="5a2a5-116">Example: Create a tree in a namespace with a prefix and retrieve elements</span></span>

<span data-ttu-id="5a2a5-117">C# では、プレフィックスを持つ名前空間を使用する XML ツリーでも、既定の名前空間を持つ XML ツリーでも、クエリを記述する方法は同じです。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-117">In C#, you write queries in the same way regardless of whether you're writing queries on an XML tree that uses a namespace with a prefix or on an XML tree with a default namespace.</span></span>

<span data-ttu-id="5a2a5-118">次の例では、プレフィックスのある名前空間にある XML ツリーが作成され、要素コレクションが取得されます。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-118">The following example creates an XML tree that's in a namespace with a prefix, and then retrieves a collection of elements.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = XElement.Parse(
@"<aw:Root xmlns:aw='http://www.adventure-works.com'>
    <aw:Child>1</aw:Child>
    <aw:Child>2</aw:Child>
    <aw:Child>3</aw:Child>
    <aw:AnotherChild>4</aw:AnotherChild>
    <aw:AnotherChild>5</aw:AnotherChild>
    <aw:AnotherChild>6</aw:AnotherChild>
</aw:Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
foreach (XElement el in c1)
    Console.WriteLine((int)el);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>1</aw:Child>
                <aw:Child>2</aw:Child>
                <aw:Child>3</aw:Child>
                <aw:AnotherChild>4</aw:AnotherChild>
                <aw:AnotherChild>5</aw:AnotherChild>
                <aw:AnotherChild>6</aw:AnotherChild>
            </aw:Root>
        Dim c1 As IEnumerable(Of XElement) = _
            From el In root.<aw:Child> _
            Select el
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
    End Sub
End Module
```

<span data-ttu-id="5a2a5-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5a2a5-119">This example produces the following output:</span></span>

```output
1
2
3
```

## <a name="see-also"></a><span data-ttu-id="5a2a5-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a2a5-120">See also</span></span>

- [<span data-ttu-id="5a2a5-121">名前空間の概要</span><span class="sxs-lookup"><span data-stu-id="5a2a5-121">Namespaces overview</span></span>](namespaces-overview.md)
