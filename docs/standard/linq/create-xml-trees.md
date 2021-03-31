---
title: C# で XML ツリーを作成する - LINQ to XML
description: LINQ to XML の XElement および XAttribute コンストラクターを使用して C# で XML ツリーを作成し、コードを基になる XML の構造に似せることができます。
ms.date: 08/31/2018
ms.assetid: cc74234a-0bac-4327-9c8c-5a2ead15b595
ms.openlocfilehash: 97bf40d84f40eabf6fa84f10bf4febb7697b10f5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412097"
---
# <a name="create-xml-trees-in-c-linq-to-xml"></a><span data-ttu-id="b68e2-103">C# で XML ツリーを作成する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b68e2-103">Create XML trees in C# (LINQ to XML)</span></span>

<span data-ttu-id="b68e2-104">この記事では、C# での XML ツリーの作成に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-104">This article provides information about creating XML trees in C#.</span></span>

<span data-ttu-id="b68e2-105">LINQ クエリの結果を <xref:System.Xml.Linq.XElement> のコンテンツとして使用する方法については、「[関数型構築](functional-construction.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b68e2-105">For information about using the results of LINQ queries as the content for an <xref:System.Xml.Linq.XElement>, see [Functional construction](functional-construction.md).</span></span>

## <a name="construct-elements"></a><span data-ttu-id="b68e2-106">要素の構築</span><span class="sxs-lookup"><span data-stu-id="b68e2-106">Construct elements</span></span>

<span data-ttu-id="b68e2-107"><xref:System.Xml.Linq.XElement> コンストラクターと <xref:System.Xml.Linq.XAttribute> コンストラクターのシグネチャを使用すると、要素または属性のコンテンツを引数としてコンストラクターに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-107">The signatures of the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors let you pass the contents of the element or attribute as arguments to the constructor.</span></span> <span data-ttu-id="b68e2-108">いずれかのコンストラクターは任意の数の引数を受け取るため、任意の数の子要素を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-108">Because one of the constructors takes a variable number of arguments, you can pass any number of child elements.</span></span> <span data-ttu-id="b68e2-109">もちろん、それらの子要素のそれぞれに、さらに子要素を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-109">Of course, each of those child elements can contain their own child elements.</span></span> <span data-ttu-id="b68e2-110">いずれの要素にも、任意の数の属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-110">For any element, you can add any number of attributes.</span></span>

<span data-ttu-id="b68e2-111"><xref:System.Xml.Linq.XNode> オブジェクト (<xref:System.Xml.Linq.XElement> を含む) や <xref:System.Xml.Linq.XAttribute> オブジェクトの追加時に、新しいコンテンツに親がない場合、単にオブジェクトが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-111">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="b68e2-112">新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製され、新しく複製されたコンテンツが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-112">If the new content already is parented, and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span> <span data-ttu-id="b68e2-113">この記事の最後の例では、この動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-113">The last example in this article demonstrates this.</span></span>

<span data-ttu-id="b68e2-114">`contacts`<xref:System.Xml.Linq.XElement> を作成するには、次のコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-114">To create a `contacts` <xref:System.Xml.Linq.XElement>, you could use the following code:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

<span data-ttu-id="b68e2-115">適切にインデントされていれば、<xref:System.Xml.Linq.XElement> オブジェクトを構築するコードは、基になる XML の構造によく似ています。</span><span class="sxs-lookup"><span data-stu-id="b68e2-115">If indented properly, the code to construct <xref:System.Xml.Linq.XElement> objects closely resembles the structure of the underlying XML.</span></span>

## <a name="xelement-constructors"></a><span data-ttu-id="b68e2-116">XElement コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b68e2-116">XElement constructors</span></span>

<span data-ttu-id="b68e2-117"><xref:System.Xml.Linq.XElement> クラスは、関数型構築で次のコンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-117">The <xref:System.Xml.Linq.XElement> class uses the following constructors for functional construction.</span></span> <span data-ttu-id="b68e2-118"><xref:System.Xml.Linq.XElement> のコンストラクターはこれ以外にも存在しますが、関数型構築に使用されないものはこの一覧に示していません。</span><span class="sxs-lookup"><span data-stu-id="b68e2-118">Note that there are some other constructors for <xref:System.Xml.Linq.XElement>, but because they're not used for functional construction they're not listed here.</span></span>

|<span data-ttu-id="b68e2-119">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b68e2-119">Constructor</span></span>|<span data-ttu-id="b68e2-120">説明</span><span class="sxs-lookup"><span data-stu-id="b68e2-120">Description</span></span>|
|-----------------|-----------------|
|`XElement(XName name, object content)`|<span data-ttu-id="b68e2-121"><xref:System.Xml.Linq.XElement> を作成します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-121">Creates an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b68e2-122">`name` パラメーターには要素の名前を指定し、`content` には要素のコンテンツを指定します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-122">The `name` parameter specifies the name of the element; `content` specifies the content of the element.</span></span>|
|`XElement(XName name)`|<span data-ttu-id="b68e2-123">指定した名前で <xref:System.Xml.Linq.XElement> を初期化して、<xref:System.Xml.Linq.XName> を作成します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-123">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span>|
|`XElement(XName name, params object[] content)`|<span data-ttu-id="b68e2-124">指定した名前で <xref:System.Xml.Linq.XElement> を初期化して、<xref:System.Xml.Linq.XName> を作成します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-124">Creates an <xref:System.Xml.Linq.XElement> with its <xref:System.Xml.Linq.XName> initialized to the specified name.</span></span> <span data-ttu-id="b68e2-125">属性や子要素が、パラメーター リストのコンテンツから作成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-125">The attributes and/or child elements are created from the contents of the parameter list.</span></span>|

<span data-ttu-id="b68e2-126">`content` パラメーターは非常に柔軟です。</span><span class="sxs-lookup"><span data-stu-id="b68e2-126">The `content` parameter is extremely flexible.</span></span> <span data-ttu-id="b68e2-127"><xref:System.Xml.Linq.XElement> の有効な子オブジェクトの型すべてがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b68e2-127">It supports any type of object that's a valid child of an <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="b68e2-128">このパラメーターで渡されるさまざまな型のオブジェクトには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-128">The following rules apply to different types of objects passed in this parameter:</span></span>

- <span data-ttu-id="b68e2-129">文字列はテキスト コンテンツとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-129">A string is added as text content.</span></span>
- <span data-ttu-id="b68e2-130"><xref:System.Xml.Linq.XElement> は子要素として追加されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-130">An <xref:System.Xml.Linq.XElement> is added as a child element.</span></span>
- <span data-ttu-id="b68e2-131"><xref:System.Xml.Linq.XAttribute> は属性として追加されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-131">An <xref:System.Xml.Linq.XAttribute> is added as an attribute.</span></span>
- <span data-ttu-id="b68e2-132"><xref:System.Xml.Linq.XProcessingInstruction>、<xref:System.Xml.Linq.XComment>、または <xref:System.Xml.Linq.XText> は、子コンテンツとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-132">An <xref:System.Xml.Linq.XProcessingInstruction>, <xref:System.Xml.Linq.XComment>, or <xref:System.Xml.Linq.XText> is added as child content.</span></span>
- <span data-ttu-id="b68e2-133"><xref:System.Collections.IEnumerable> は列挙され、その結果にこれらの規則が再帰的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-133">An <xref:System.Collections.IEnumerable> is enumerated, and these rules are applied recursively to the results.</span></span>
- <span data-ttu-id="b68e2-134">その他の型に対しては `ToString` メソッドが呼び出され、その結果がテキスト コンテンツとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-134">For any other type, its `ToString` method is called and the result is added as text content.</span></span>

## <a name="example-create-an-xelement-with-content"></a><span data-ttu-id="b68e2-135">例: コンテンツを含む XElement を作成する</span><span class="sxs-lookup"><span data-stu-id="b68e2-135">Example: Create an XElement with content</span></span>

<span data-ttu-id="b68e2-136">単純コンテンツが含まれる <xref:System.Xml.Linq.XElement> は、1 回のメソッド呼び出しで作成できます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-136">You can create an <xref:System.Xml.Linq.XElement> that contains simple content with a single method call.</span></span> <span data-ttu-id="b68e2-137">そのためには、次のように、コンテンツを 2 番目のパラメーターとして指定します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-137">To do this, specify the content as the second parameter, as follows:</span></span>

```csharp
XElement n = new XElement("Customer", "Adventure Works");
Console.WriteLine(n);
```

<span data-ttu-id="b68e2-138">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-138">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

<span data-ttu-id="b68e2-139">任意の型のオブジェクトをコンテンツとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-139">You can pass any type of object as the content.</span></span> <span data-ttu-id="b68e2-140">たとえば、次のコードでは、浮動小数点数がコンテンツとして含まれる要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-140">For example, the following code creates an element that contains a floating point number as content:</span></span>

```csharp
XElement n = new XElement("Cost", 324.50);
Console.WriteLine(n);
```

<span data-ttu-id="b68e2-141">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-141">This example produces the following output:</span></span>

```xml
<Cost>324.5</Cost>
```

<span data-ttu-id="b68e2-142">浮動小数点数はボックス化されてコンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-142">The floating point number is boxed and passed in to the constructor.</span></span> <span data-ttu-id="b68e2-143">ボックス化された数は文字列に変換され、要素のコンテンツとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-143">The boxed number is converted to a string and used as the content of the element.</span></span>

## <a name="example-create-an-xelement-with-a-child-element"></a><span data-ttu-id="b68e2-144">例: 子要素を持つ XElement を作成する</span><span class="sxs-lookup"><span data-stu-id="b68e2-144">Example: Create an XElement with a child element</span></span>

<span data-ttu-id="b68e2-145"><xref:System.Xml.Linq.XElement> クラスのインスタンスをコンテンツ引数として渡すと、コンストラクターによって、子要素を持つ要素が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-145">If you pass an instance of the <xref:System.Xml.Linq.XElement> class for the content argument, the constructor creates an element with a child element:</span></span>

```csharp
XElement shippingUnit = new XElement("ShippingUnit",
    new XElement("Cost", 324.50)
);
Console.WriteLine(shippingUnit);
```

<span data-ttu-id="b68e2-146">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-146">This example produces the following output:</span></span>

```xml
<ShippingUnit>
  <Cost>324.5</Cost>
</ShippingUnit>
```

## <a name="example-create-an-xelement-with-multiple-child-elements"></a><span data-ttu-id="b68e2-147">例: 複数の子要素を持つ XElement を作成する</span><span class="sxs-lookup"><span data-stu-id="b68e2-147">Example: Create an XElement with multiple child elements</span></span>

<span data-ttu-id="b68e2-148">複数の <xref:System.Xml.Linq.XElement> オブジェクトをコンテンツとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-148">You can pass in a number of <xref:System.Xml.Linq.XElement> objects for the content.</span></span> <span data-ttu-id="b68e2-149">各 <xref:System.Xml.Linq.XElement> オブジェクトは、子要素として格納されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-149">Each of the <xref:System.Xml.Linq.XElement> objects is included as a child element.</span></span>

```csharp
XElement address = new XElement("Address",
    new XElement("Street1", "123 Main St"),
    new XElement("City", "Mercer Island"),
    new XElement("State", "WA"),
    new XElement("Postal", "68042")
);
Console.WriteLine(address);
```

<span data-ttu-id="b68e2-150">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-150">This example produces the following output:</span></span>

```xml
<Address>
  <Street1>123 Main St</Street1>
  <City>Mercer Island</City>
  <State>WA</State>
  <Postal>68042</Postal>
</Address>
```

<span data-ttu-id="b68e2-151">上の例を次のように拡張すると、完全な XML ツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-151">By extending the previous example, you can create an entire XML tree, as follows:</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
Console.WriteLine(contacts);
```

<span data-ttu-id="b68e2-152">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-152">This example produces the following output:</span></span>

```xml
<Contacts>
  <Contact>
    <Name>Patrick Hines</Name>
    <Phone>206-555-0144</Phone>
    <Address>
      <Street1>123 Main St</Street1>
      <City>Mercer Island</City>
      <State>WA</State>
      <Postal>68042</Postal>
    </Address>
  </Contact>
</Contacts>
```

## <a name="example-create-an-xelement-with-an-xattribute"></a><span data-ttu-id="b68e2-153">例: XAttribute を持つ XElement を作成する</span><span class="sxs-lookup"><span data-stu-id="b68e2-153">Example: Create an XElement with an XAttribute</span></span>

<span data-ttu-id="b68e2-154"><xref:System.Xml.Linq.XAttribute> クラスのインスタンスをコンテンツ引数として渡すと、コンストラクターによって、属性がある要素が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-154">If you pass an instance of the <xref:System.Xml.Linq.XAttribute> class for the content argument, the constructor creates an element with an attribute:</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

<span data-ttu-id="b68e2-155">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-155">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-create-an-empty-element"></a><span data-ttu-id="b68e2-156">例: 空の要素を作成する</span><span class="sxs-lookup"><span data-stu-id="b68e2-156">Example: Create an empty element</span></span>

<span data-ttu-id="b68e2-157">空の <xref:System.Xml.Linq.XElement> を作成するには、コンストラクターにコンテンツを渡さないでください。</span><span class="sxs-lookup"><span data-stu-id="b68e2-157">To create an empty <xref:System.Xml.Linq.XElement>, don't pass any content to the constructor.</span></span> <span data-ttu-id="b68e2-158">次の例では、空要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-158">The following example creates an empty element:</span></span>

```csharp
XElement n = new XElement("Customer");
Console.WriteLine(n);
```

<span data-ttu-id="b68e2-159">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-159">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="example-attach-vs-clone"></a><span data-ttu-id="b68e2-160">例: アタッチと複製</span><span class="sxs-lookup"><span data-stu-id="b68e2-160">Example: Attach vs. clone</span></span>

<span data-ttu-id="b68e2-161">既に説明したように、<xref:System.Xml.Linq.XNode> オブジェクト (<xref:System.Xml.Linq.XElement> を含む) や <xref:System.Xml.Linq.XAttribute> オブジェクトの追加時に、新しいコンテンツに親がない場合、単にオブジェクトが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-161">As mentioned previously, when adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="b68e2-162">新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製され、新しく複製されたコンテンツが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="b68e2-162">If the new content already is parented and is part of another XML tree, the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>

<span data-ttu-id="b68e2-163">次の例では、親を持つ要素をツリーに追加する場合と親を持たない要素をツリーに追加する場合の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="b68e2-163">The following example demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree:</span></span>

```csharp
// Create a tree with a child element.
XElement xmlTree1 = new XElement("Root",
    new XElement("Child1", 1)
);

// Create an element that's not parented.
XElement child2 = new XElement("Child2", 2);

// Create a tree and add Child1 and Child2 to it.
XElement xmlTree2 = new XElement("Root",
    xmlTree1.Element("Child1"),
    child2
);

// Compare Child1 identity.
Console.WriteLine("Child1 was {0}",
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?
    "attached" : "cloned");

// Compare Child2 identity.
Console.WriteLine("Child2 was {0}",
    child2 == xmlTree2.Element("Child2") ?
    "attached" : "cloned");

// This example produces the following output:
//    Child1 was cloned
//    Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="b68e2-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="b68e2-164">See also</span></span>

- [<span data-ttu-id="b68e2-165">関数型構築</span><span class="sxs-lookup"><span data-stu-id="b68e2-165">Functional construction</span></span>](functional-construction.md)
