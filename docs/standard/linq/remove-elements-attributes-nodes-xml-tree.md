---
title: XML ツリーから要素、属性、ノードを削除する - LINQ to XML
description: XML ツリーから要素、属性、およびその他の種類のノードを削除する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 1a7c10892ccf1baaab7dde700266a134abe727de
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412078"
---
# <a name="remove-elements-attributes-and-nodes-from-an-xml-tree-linq-to-xml"></a><span data-ttu-id="a73a4-103">XML ツリーから要素、属性、ノードを削除する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a73a4-103">Remove elements, attributes, and nodes from an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="a73a4-104">要素、属性、およびその他の種類のノードを削除して、XML ツリーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="a73a4-104">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="a73a4-105">1 つの要素または 1 つの属性は XML ドキュメントから簡単に削除できます。</span><span class="sxs-lookup"><span data-stu-id="a73a4-105">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="a73a4-106">一方、要素または属性のコレクションを削除する場合は、まずコレクションをリストに具体化し、そのリストから要素または属性を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a73a4-106">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="a73a4-107">最適な方法は、<xref:System.Xml.Linq.Extensions.Remove%2A> 拡張メソッドを使用してこれを行うことです。</span><span class="sxs-lookup"><span data-stu-id="a73a4-107">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method to do this.</span></span>

<span data-ttu-id="a73a4-108">この方法を使用する主な理由は、XML ツリーから取得するコレクションのほとんどが遅延実行を使用して生成されるからです。</span><span class="sxs-lookup"><span data-stu-id="a73a4-108">The main reason to use this approach is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="a73a4-109">最初にコレクションをリストに具体化せず、拡張メソッドも使用しない場合、特定の種類のバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a73a4-109">If you don't first materialize them into a list, or if you don't use the extension methods, you may encounter a certain class of bugs.</span></span> <span data-ttu-id="a73a4-110">詳細については、「[宣言型コードと命令型コードの混在バグ](mixed-declarative-imperative-code-bugs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a73a4-110">For more information, see [Mixed declarative/imperative code bugs](mixed-declarative-imperative-code-bugs.md).</span></span>

<span data-ttu-id="a73a4-111">ノードおよび属性を XML ツリーから削除するメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-111">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="a73a4-112">メソッド</span><span class="sxs-lookup"><span data-stu-id="a73a4-112">Method</span></span>|<span data-ttu-id="a73a4-113">説明</span><span class="sxs-lookup"><span data-stu-id="a73a4-113">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a73a4-114"><xref:System.Xml.Linq.XAttribute> をその親から削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-114">Remove an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="a73a4-115">子ノードを <xref:System.Xml.Linq.XContainer> から削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-115">Remove the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="a73a4-116">コンテンツおよび属性を <xref:System.Xml.Linq.XElement> から削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-116">Remove content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="a73a4-117"><xref:System.Xml.Linq.XElement> の属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-117">Remove the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a73a4-118">値 `null` を渡す場合は、属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-118">Remove the attribute if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="a73a4-119">値 `null` を渡す場合は、子要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-119">Remove the child element if you pass the value `null`.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a73a4-120"><xref:System.Xml.Linq.XNode> をその親から削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-120">Remove an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="a73a4-121">ソース コレクション内のすべての属性または要素をその親要素から削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-121">Remove every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example-remove-a-single-element-and-remove-a-collection-of-elements-in-two-ways"></a><span data-ttu-id="a73a4-122">例: 1 つの要素を削除し、要素のコレクションを 2 つの方法で削除する</span><span class="sxs-lookup"><span data-stu-id="a73a4-122">Example: Remove a single element, and remove a collection of elements in two ways</span></span>

<span data-ttu-id="a73a4-123">この例では、要素を削除する 3 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="a73a4-124">まず、1 つの要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-124">First, it removes a single element.</span></span> <span data-ttu-id="a73a4-125">次に、要素のコレクションを取得し、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 演算子を使用して要素を具体化してから、コレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and then removes the collection.</span></span> <span data-ttu-id="a73a4-126">最後に、要素のコレクションを取得し、<xref:System.Xml.Linq.Extensions.Remove%2A> 拡張メソッドを使用して要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="a73a4-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="a73a4-127"><xref:System.Linq.Enumerable.ToList%2A> 演算子の詳細については、「[データ型の変換 (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md)」と「[データ型の変換 (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a73a4-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](../../csharp/programming-guide/concepts/linq/converting-data-types.md) and [Converting Data Types (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
    <Child1>
        <GrandChild1/>
        <GrandChild2/>
        <GrandChild3/>
    </Child1>
    <Child2>
        <GrandChild4/>
        <GrandChild5/>
        <GrandChild6/>
    </Child2>
    <Child3>
        <GrandChild7/>
        <GrandChild8/>
        <GrandChild9/>
    </Child3>
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>
            <GrandChild1/>
            <GrandChild2/>
            <GrandChild3/>
        </Child1>
        <Child2>
            <GrandChild4/>
            <GrandChild5/>
            <GrandChild6/>
        </Child2>
        <Child3>
            <GrandChild7/>
            <GrandChild8/>
            <GrandChild9/>
        </Child3>
    </Root>
root.<Child1>.<GrandChild1>.Remove()
root.<Child2>.Elements().ToList().Remove()
root.<Child3>.Elements().Remove()
Console.WriteLine(root)
```

<span data-ttu-id="a73a4-128">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a73a4-128">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>
    <GrandChild2 />
    <GrandChild3 />
  </Child1>
  <Child2 />
  <Child3 />
</Root>
```

<span data-ttu-id="a73a4-129">最初の孫要素が `Child1` から削除され、すべての孫要素が `Child2` と `Child3` から削除されました。</span><span class="sxs-lookup"><span data-stu-id="a73a4-129">The first grandchild element was removed from `Child1`, and all grandchildren elements were removed from `Child2` and from `Child3`.</span></span>
