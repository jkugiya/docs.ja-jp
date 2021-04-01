---
title: Visual Basic で名前空間を持つドキュメントを作成する方法 - LINQ to XML
description: Visual Basic で XML リテラルを使用して、既定の名前空間またはプレフィックスが付いた名前空間を持つドキュメントを作成します。
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 48e2a1abf8f7a82df3db5cb2f580804d67776b15
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412050"
---
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="2ceb9-103">Visual Basic で名前空間を持つドキュメントを作成する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2ceb9-103">How to create a document with namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="2ceb9-104">この記事では、Visual Basic で名前空間を持つドキュメントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-104">This article shows how to create a document with namespaces in Visual Basic.</span></span>

<span data-ttu-id="2ceb9-105">Visual Basic で XML リテラルを使用している場合、ユーザーは 1 つのグローバルな既定の XML 名前空間を定義できます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-105">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="2ceb9-106">この名前空間は、XML リテラルと XML プロパティの両方の既定の名前空間です。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-106">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="2ceb9-107">既定の XML 名前空間は、プロジェクト レベルまたはファイル レベルで定義できます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-107">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="2ceb9-108">ファイル レベルで定義すると、プロジェクト レベルの既定の名前空間がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-108">If it's defined at the file level, it overrides the default namespace at the project level.</span></span>

<span data-ttu-id="2ceb9-109">他の名前空間を定義して、それらの名前空間のプレフィックスを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-109">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span> <span data-ttu-id="2ceb9-110">`Imports` キーワードを使用して、両方の名前空間の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-110">You use the `Imports` keyword to define both types of namespace.</span></span>

<span data-ttu-id="2ceb9-111">詳細については、「[Visual Basic の XML リテラル](xml-literals.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-111">For more information, see [XML literals in Visual Basic](xml-literals.md).</span></span>

<span data-ttu-id="2ceb9-112">既定の XML 名前空間は要素だけに適用され、属性には適用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-112">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="2ceb9-113">既定では、属性は既定の名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-113">Attributes are by default in the default namespace.</span></span> <span data-ttu-id="2ceb9-114">ただし、名前空間プレフィックスを使用して属性を名前空間に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-114">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>

## <a name="example-create-a-document-that-has-a-namespace"></a><span data-ttu-id="2ceb9-115">例: 名前空間を持つドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="2ceb9-115">Example: Create a document that has a namespace</span></span>

<span data-ttu-id="2ceb9-116">この例では、1 つの名前空間を含むドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-116">This example creates a document that contains a namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child aw:Att="attvalue"/>
            </aw:Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="2ceb9-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-117">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="2ceb9-118">例: 2 つの名前空間を持つドキュメントを作成し、1 つにプレフィックスを付ける</span><span class="sxs-lookup"><span data-stu-id="2ceb9-118">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="2ceb9-119">この例では、2 つの名前空間を含むドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-119">This example creates a document that contains two namespaces.</span></span> <span data-ttu-id="2ceb9-120">1 つは既定の名前空間で、もう 1 つはプレフィックスが付いています。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-120">One is the default namespace, the other has a prefix.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child Att="attvalue"/>
                <fc:Child2>child2 content</fc:Child2>
            </Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="2ceb9-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-121">This example produces the following output:</span></span>

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="2ceb9-122">例: 2 つの名前空間を持つドキュメントを作成し、両方にプレフィックスを付ける</span><span class="sxs-lookup"><span data-stu-id="2ceb9-122">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="2ceb9-123">次の例では、名前空間プレフィックスのある名前空間を 2 つ含むドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-123">The following example creates a document that contains two namespaces, both having namespace prefixes.</span></span>

<span data-ttu-id="2ceb9-124">XML ツリーをシリアル化するとき、各要素が指定された名前空間に含まれるように、LINQ to XML によって必要に応じて名前空間宣言が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-124">When serializing an XML tree, LINQ to XML emits namespace declarations as required so that each element is in its designated namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="2ceb9-125">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="2ceb9-125">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="2ceb9-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ceb9-126">See also</span></span>

- [<span data-ttu-id="2ceb9-127">名前空間の概要</span><span class="sxs-lookup"><span data-stu-id="2ceb9-127">Namespaces overview</span></span>](namespaces-overview.md)
