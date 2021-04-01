---
title: C# で名前空間を持つドキュメントを作成する方法 - LINQ to XML
description: C# で XNamespace オブジェクトを使用して、既定の名前空間またはプレフィックスが付いた名前空間を持つドキュメントを作成します。
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 3ec9624bcc599a73a6872e5c4c79504a1a4b4380
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412052"
---
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a><span data-ttu-id="97bcc-103">C# で名前空間を持つドキュメントを作成する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="97bcc-103">How to create a document with namespaces in C# (LINQ to XML)</span></span>

<span data-ttu-id="97bcc-104">この記事では、C# で名前空間を持つドキュメントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-104">This article shows how to create documents in C# that have namespaces.</span></span>

## <a name="example-declare-and-initialize-a-default-namespace"></a><span data-ttu-id="97bcc-105">例: 既定の名前空間を宣言して初期化する</span><span class="sxs-lookup"><span data-stu-id="97bcc-105">Example: Declare and initialize a default namespace</span></span>

<span data-ttu-id="97bcc-106">名前空間にある要素や属性を作成するには、最初に <xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して初期化します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-106">To create an element or an attribute that's in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="97bcc-107">次に、加算演算子オーバーロードを使用して名前空間をローカル名に連結し、文字列として表します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>

<span data-ttu-id="97bcc-108">次の例では、1 つの名前空間を持つドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="97bcc-109">既定では、LINQ to XML によって、このドキュメントが既定の名前空間でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-109">By default, LINQ to XML serializes this document with a default namespace.</span></span>

```csharp
// Create an XML tree in a namespace.
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="97bcc-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-110">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child>child content</Child>
</Root>
```

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a><span data-ttu-id="97bcc-111">例: 名前空間と属性を持つドキュメントを作成する</span><span class="sxs-lookup"><span data-stu-id="97bcc-111">Example: Create a document that has a namespace and an attribute</span></span>

<span data-ttu-id="97bcc-112">次の例では、1 つの名前空間を持つドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="97bcc-113">名前空間プレフィックスを持つ名前空間を宣言する属性も作成します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="97bcc-114">プレフィックス付きの名前空間を宣言する属性を作成するには、属性名が名前空間プレフィックスで、この名前が <xref:System.Xml.Linq.XNamespace.Xmlns%2A> 名前空間にある属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="97bcc-115">この属性の値は名前空間の URI です。</span><span class="sxs-lookup"><span data-stu-id="97bcc-115">The value of this attribute is the URI of the namespace.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="97bcc-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-116">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="97bcc-117">例: 2 つの名前空間を持つドキュメントを作成し、1 つにプレフィックスを付ける</span><span class="sxs-lookup"><span data-stu-id="97bcc-117">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="97bcc-118">次の例では、2 つの名前空間が含まれるドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="97bcc-119">1 つは既定の名前空間で、もう 1 つはプレフィックスが付いた名前空間です。</span><span class="sxs-lookup"><span data-stu-id="97bcc-119">One is the default namespace, the other is a namespace with a prefix.</span></span>

<span data-ttu-id="97bcc-120">ルート要素に名前空間属性を含めることによって名前空間がシリアル化され、`http://www.adventure-works.com` が既定の名前空間となり、`www.fourthcoffee.com` は `fc` のプレフィックスでシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of `fc`.</span></span> <span data-ttu-id="97bcc-121">既定の名前空間を宣言する属性を作成するには、`xmlns` という名前の属性を、名前空間を指定せずに作成します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-121">To create an attribute that declares a default namespace, you create an attribute with the name `xmlns`, without a namespace.</span></span> <span data-ttu-id="97bcc-122">属性の値は、既定の名前空間 URI です。</span><span class="sxs-lookup"><span data-stu-id="97bcc-122">The value of the attribute is the default namespace URI.</span></span>

```csharp
// The http://www.adventure-works.com namespace is forced to be the default namespace.
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute("xmlns", "http://www.adventure-works.com"),
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

<span data-ttu-id="97bcc-123">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-123">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <DifferentChild>other content</DifferentChild>
  </fc:Child>
  <Child2>c2 content</Child2>
  <fc:Child3>c3 content</fc:Child3>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="97bcc-124">例: 2 つの名前空間を持つドキュメントを作成し、両方にプレフィックスを付ける</span><span class="sxs-lookup"><span data-stu-id="97bcc-124">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="97bcc-125">次の例では、名前空間プレフィックスのある名前空間を 2 つ含むドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),
    new XElement(fc + "Child",
        new XElement(aw + "DifferentChild", "other content")
    ),
    new XElement(aw + "Child2", "c2 content"),
    new XElement(fc + "Child3", "c3 content")
);
Console.WriteLine(root);
```

<span data-ttu-id="97bcc-126">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-126">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="example-create-a-namespace-using-expanded-names"></a><span data-ttu-id="97bcc-127">例: 展開名を使用して名前空間を作成する</span><span class="sxs-lookup"><span data-stu-id="97bcc-127">Example: Create a namespace using expanded names</span></span>

<span data-ttu-id="97bcc-128"><xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して作成する代わりに、展開名を使用しても同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>

<span data-ttu-id="97bcc-129">ただし、この方法はパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-129">This approach has performance implications.</span></span> <span data-ttu-id="97bcc-130">展開名が含まれた文字列を LINQ to XML に渡すたびに、LINQ to XML は名前を解析して、アトミック化された名前空間を検索し、アトミック化された名前を見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="97bcc-130">Each time you pass a string that contains an expanded name to LINQ to XML, LINQ to XML must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="97bcc-131">この処理は CPU 時間を消費します。</span><span class="sxs-lookup"><span data-stu-id="97bcc-131">This process takes CPU time.</span></span> <span data-ttu-id="97bcc-132">パフォーマンスが重要な場合には、<xref:System.Xml.Linq.XNamespace> オブジェクトを明示的に宣言して使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="97bcc-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>

<span data-ttu-id="97bcc-133">パフォーマンスが重要な場合、詳細については、「[XName オブジェクトの事前アトミック化](pre-atomization-xname-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97bcc-133">If performance is an important issue, see [Pre-Atomization of XName Objects](pre-atomization-xname-objects.md) for more information.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XElement root = new XElement("{http://www.adventure-works.com}Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement("{http://www.adventure-works.com}Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="97bcc-134">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="97bcc-134">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="97bcc-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="97bcc-135">See also</span></span>

- [<span data-ttu-id="97bcc-136">名前空間の概要</span><span class="sxs-lookup"><span data-stu-id="97bcc-136">Namespaces overview</span></span>](namespaces-overview.md)
