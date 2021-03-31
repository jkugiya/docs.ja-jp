---
title: グローバル名前空間の使用 (Visual Basic) - LINQ to XML
description: 名前空間が既定の名前空間の場合でも、名前空間にプレフィックスが付いている場合でも、Visual Basic で Imports ステートメントを使用して名前空間を宣言します。 この記事では、Import ステートメントと、名前空間使用のその他の面について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: f05fcab6788388e36e2b68a2d4f022ea63e74280
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412113"
---
# <a name="work-with-global-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="ce460-104">グローバル名前空間の使用 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ce460-104">Work with global namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="ce460-105">Visual Basic での XML リテラルの重要な機能の 1 つは、`Imports` ステートメントを使用して XML 名前空間を宣言できることです。</span><span class="sxs-lookup"><span data-stu-id="ce460-105">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="ce460-106">この機能を使用することで、プレフィックスを使用する XML 名前空間または既定の XML 名前空間を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ce460-106">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>

<span data-ttu-id="ce460-107">この機能は 2 つの状況で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ce460-107">This capability is useful in two situations:</span></span>

- <span data-ttu-id="ce460-108">XML リテラルで宣言された名前空間は、組み込み式に引き継がれません。</span><span class="sxs-lookup"><span data-stu-id="ce460-108">Namespaces declared in XML literals don't carry over into embedded expressions.</span></span> <span data-ttu-id="ce460-109">グローバル名前空間を宣言すると、名前空間を伴う組み込み式を使用しなければならない作業が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-109">Declaring global namespaces reduces the amount of work needed to use embedded expressions with namespaces.</span></span>
- <span data-ttu-id="ce460-110">名前空間と XML プロパティを併用するためには、グローバル名前空間を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce460-110">You must declare global namespaces in order to use namespaces with XML properties.</span></span>

<span data-ttu-id="ce460-111">グローバル名前空間はプロジェクト レベルで宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ce460-111">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="ce460-112">また、モジュール レベルでもグローバル名前空間を宣言できます。その場合、プロジェクト レベルのグローバル名前空間はオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="ce460-112">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="ce460-113">最終的に、グローバル名前空間は XML リテラルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="ce460-113">Finally, you can override global namespaces in an XML literal.</span></span>

<span data-ttu-id="ce460-114">グローバルに宣言された名前空間に含まれる XML リテラルまたは XML プロパティを使用する場合は、Visual Studio で XML リテラルまたはプロパティにカーソルを合わせることで、それらの展開名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-114">When using XML literals or XML properties that are in globally declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="ce460-115">拡張名はツールヒントに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-115">You will see the expanded name in a tooltip.</span></span>

<span data-ttu-id="ce460-116">グローバル名前空間に対応する <xref:System.Xml.Linq.XNamespace> オブジェクトを取得するには、`GetXmlNamespace` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ce460-116">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>

## <a name="example-use-imports-to-declare-a-global-namespace"></a><span data-ttu-id="ce460-117">例: `Imports` を使用してグローバル名前空間を宣言する</span><span class="sxs-lookup"><span data-stu-id="ce460-117">Example: Use `Imports` to declare a global namespace</span></span>

<span data-ttu-id="ce460-118">次の例では、`Imports` ステートメントを使用して既定のグローバル名前空間を宣言し、XML リテラルを使用してその名前空間内で <xref:System.Xml.Linq.XElement> オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="ce460-118">The following example declares a default global namespace with the `Imports` statement, and then initializes an <xref:System.Xml.Linq.XElement> object in that namespace with an XML literal:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="ce460-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-119">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" />
```

## <a name="example-declare-a-global-namespace-that-has-a-prefix"></a><span data-ttu-id="ce460-120">例: プレフィックスが付いたグローバル名前空間を宣言する</span><span class="sxs-lookup"><span data-stu-id="ce460-120">Example: Declare a global namespace that has a prefix</span></span>

<span data-ttu-id="ce460-121">次の例では、プレフィックスを付けてグローバル名前空間を宣言し、XML リテラルを使用して要素を初期化します。</span><span class="sxs-lookup"><span data-stu-id="ce460-121">The next example declares a global namespace with a prefix, and initializes an element with an XML literal:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="ce460-122">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-122">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" />
```

## <a name="example-declare-a-default-namespace-and-use-an-embedded-expression-for-the-child-element"></a><span data-ttu-id="ce460-123">例: 既定の名前空間を宣言し、`Child` 要素に埋め込み式を使用する</span><span class="sxs-lookup"><span data-stu-id="ce460-123">Example: Declare a default namespace and use an embedded expression for the `Child` element</span></span>

<span data-ttu-id="ce460-124">XML リテラルで宣言される名前空間は、組み込み式に引き継がれません。</span><span class="sxs-lookup"><span data-stu-id="ce460-124">Namespaces that are declared in XML literals don't carry over into embedded expressions.</span></span> <span data-ttu-id="ce460-125">次の例では、既定の名前空間を宣言し、`Child` 要素に埋め込み式を使用します。</span><span class="sxs-lookup"><span data-stu-id="ce460-125">The following example declares a default namespace, and then uses an embedded expression for the `Child` element.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child/> %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="ce460-126">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-126">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="" />
</Root>
```

<span data-ttu-id="ce460-127">結果的に生成される XML では、`Child` 要素がどの名前空間にも属さないように、既定の名前空間の宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ce460-127">The resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>

<span data-ttu-id="ce460-128">次のように、組み込み式で別の名前空間を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="ce460-128">You could declare a different namespace in the embedded expression, as follows:</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child xmlns="http://www.adventure-works.com"/> %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="ce460-129">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-129">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="http://www.adventure-works.com" />
</Root>
```

<span data-ttu-id="ce460-130">ただし、既定のグローバル名前空間を使用することで、名前空間を宣言せずに XML リテラルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce460-130">However, with the global default namespace you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="ce460-131">結果的に生成される XML は、この例のように、グローバルに宣言された既定の名前空間に属することになります。</span><span class="sxs-lookup"><span data-stu-id="ce460-131">The resulting XML will be in the globally-declared default namespace, as in this example:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root>
                                   <%= <Child/> %>
                               </Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="ce460-132">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-132">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child />
</Root>
```

## <a name="example-use-namespaces-with-xml-properties"></a><span data-ttu-id="ce460-133">例: 名前空間と XML プロパティを併用する</span><span class="sxs-lookup"><span data-stu-id="ce460-133">Example: Use namespaces with XML properties</span></span>

<span data-ttu-id="ce460-134">名前空間に含まれている XML ツリーを操作する場合に XML プロパティを使用するときは、XML プロパティが正しい名前空間に含まれるように、グローバル名前空間を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce460-134">If you're working with an XML tree that's in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="ce460-135">次の例では、名前空間で XML ツリーを宣言し、`Child` 要素の数を出力します。</span><span class="sxs-lookup"><span data-stu-id="ce460-135">The following example declares an XML tree in a namespace, and then prints the count of `Child` elements.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <Child>content</Child>
    </Root>
Console.WriteLine(root.<Child>.Count())
```

<span data-ttu-id="ce460-136">この例は `Child` 要素が存在しないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="ce460-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="ce460-137">次が出力されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-137">It produces this output:</span></span>

```output
0
```

<span data-ttu-id="ce460-138">ただし、既定のグローバル名前空間を宣言すると、XML リテラルと XML プロパティの両方が既定のグローバル名前空間に含まれます。</span><span class="sxs-lookup"><span data-stu-id="ce460-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>content</Child>
            </Root>
        Console.WriteLine(root.<Child>.Count())
    End Sub
End Module
```

<span data-ttu-id="ce460-139">この例は、`Child` 要素が 1 つ存在することを示しています。</span><span class="sxs-lookup"><span data-stu-id="ce460-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="ce460-140">次が出力されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-140">It produces this output:</span></span>

```output
1
```

<span data-ttu-id="ce460-141">プレフィックスを持つグローバル名前空間を宣言すると、そのプレフィックスを XML リテラルと XML プロパティの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce460-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>content</aw:Child>
            </aw:Root>
        Console.WriteLine(root.<aw:Child>.Count())
    End Sub
End Module
```

## <a name="example-use-getxmlnamespace-to-get-an-xnamespace"></a><span data-ttu-id="ce460-142">例: `GetXmlNamespace` を使用して `XNamespace` を取得する</span><span class="sxs-lookup"><span data-stu-id="ce460-142">Example: Use `GetXmlNamespace` to get an `XNamespace`</span></span>

<span data-ttu-id="ce460-143">`GetXmlNamespace` メソッドを使用して <xref:System.Xml.Linq.XNamespace> オブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="ce460-143">You can obtain an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Dim xn As XNamespace = GetXmlNamespace(aw)
        Console.WriteLine(xn)
    End Sub
End Module
```

<span data-ttu-id="ce460-144">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ce460-144">This example produces the following output:</span></span>

```output
http://www.adventure-works.com
```

## <a name="see-also"></a><span data-ttu-id="ce460-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce460-145">See also</span></span>

- [<span data-ttu-id="ce460-146">名前空間の概要</span><span class="sxs-lookup"><span data-stu-id="ce460-146">Namespaces overview</span></span>](namespaces-overview.md)
