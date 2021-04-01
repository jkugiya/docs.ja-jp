---
title: XAttribute クラスの概要
description: XAttribute クラスは、XML 属性を表します。 LINQ to XML での属性の操作は、要素の操作に似ています。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411959"
---
# <a name="xattribute-class-overview"></a><span data-ttu-id="fc12f-104">XAttribute クラスの概要</span><span class="sxs-lookup"><span data-stu-id="fc12f-104">XAttribute class overview</span></span>

<span data-ttu-id="fc12f-105">属性は、要素に関連付けられている名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="fc12f-105">Attributes are name-value pairs that are associated with an element.</span></span> <span data-ttu-id="fc12f-106"><xref:System.Xml.Linq.XAttribute> クラスは、XML 属性を表します。</span><span class="sxs-lookup"><span data-stu-id="fc12f-106">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>

<span data-ttu-id="fc12f-107">LINQ to XML での属性の操作は、要素の操作に似ています。</span><span class="sxs-lookup"><span data-stu-id="fc12f-107">Working with attributes in LINQ to XML is similar to working with elements.</span></span> <span data-ttu-id="fc12f-108">コンストラクターはほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="fc12f-108">Their constructors are similar.</span></span> <span data-ttu-id="fc12f-109">それぞれのコレクションの取得に使用するメソッドもほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="fc12f-109">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="fc12f-110">属性のコレクションの LINQ クエリ式は、要素のコレクションの LINQ クエリ式と似ています。</span><span class="sxs-lookup"><span data-stu-id="fc12f-110">A LINQ query expression for a collection of attributes looks similar to a LINQ query expression for a collection of elements.</span></span>

<span data-ttu-id="fc12f-111">属性が要素に追加された順序は保持されます。</span><span class="sxs-lookup"><span data-stu-id="fc12f-111">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="fc12f-112">つまり、属性を反復処理する場合、属性は追加された順序と同じ順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="fc12f-112">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>

## <a name="the-xattribute-constructor"></a><span data-ttu-id="fc12f-113">XAttribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="fc12f-113">The XAttribute constructor</span></span>

<span data-ttu-id="fc12f-114">最もよく使用する <xref:System.Xml.Linq.XAttribute> クラスのコンストラクターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="fc12f-114">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you'll most commonly use:</span></span>

|<span data-ttu-id="fc12f-115">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="fc12f-115">Constructor</span></span>|<span data-ttu-id="fc12f-116">説明</span><span class="sxs-lookup"><span data-stu-id="fc12f-116">Description</span></span>|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|<span data-ttu-id="fc12f-117"><xref:System.Xml.Linq.XAttribute> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="fc12f-117">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="fc12f-118">`name` 引数には属性の名前を指定し、`content` には属性のコンテンツを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc12f-118">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|

## <a name="example-create-an-element-with-an-attribute"></a><span data-ttu-id="fc12f-119">例: 属性を持つ要素を作成する</span><span class="sxs-lookup"><span data-stu-id="fc12f-119">Example: Create an element with an attribute</span></span>

<span data-ttu-id="fc12f-120">次の例は、属性を含む要素を作成する一般的なタスクを示しています。</span><span class="sxs-lookup"><span data-stu-id="fc12f-120">The following example shows the common task of creating an element that contains an attribute.</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

<span data-ttu-id="fc12f-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fc12f-121">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a><span data-ttu-id="fc12f-122">例: 属性の関数型構築</span><span class="sxs-lookup"><span data-stu-id="fc12f-122">Example: Functional construction of attributes</span></span>

<span data-ttu-id="fc12f-123"><xref:System.Xml.Linq.XAttribute> オブジェクトは、次の例に示すように、<xref:System.Xml.Linq.XElement> オブジェクトの構築と共にインラインで構築できます。</span><span class="sxs-lookup"><span data-stu-id="fc12f-123">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as shown in the following example:</span></span>

```csharp
XElement c = new XElement("Customers",
    new XElement("Customer",
        new XElement("Name", "John Doe"),
        new XElement("PhoneNumbers",
            new XElement("Phone",
                new XAttribute("type", "home"),
                "555-555-5555"),
            new XElement("Phone",
                new XAttribute("type", "work"),
                "666-666-6666")
        )
    )
);
Console.WriteLine(c);
```

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
```

<span data-ttu-id="fc12f-124">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fc12f-124">This example produces the following output:</span></span>

```xml
<Customers>
  <Customer>
    <Name>John Doe</Name>
    <PhoneNumbers>
      <Phone type="home">555-555-5555</Phone>
      <Phone type="work">666-666-6666</Phone>
    </PhoneNumbers>
  </Customer>
</Customers>
```

## <a name="attributes-arent-nodes"></a><span data-ttu-id="fc12f-125">属性はノードではない</span><span class="sxs-lookup"><span data-stu-id="fc12f-125">Attributes aren't nodes</span></span>

<span data-ttu-id="fc12f-126">属性と要素には、いくつかの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="fc12f-126">There are some differences between attributes and elements.</span></span> <span data-ttu-id="fc12f-127"><xref:System.Xml.Linq.XAttribute> オブジェクトは、XML ツリーのノードではありません。</span><span class="sxs-lookup"><span data-stu-id="fc12f-127"><xref:System.Xml.Linq.XAttribute> objects aren't nodes in the XML tree.</span></span> <span data-ttu-id="fc12f-128">属性は、XML 要素に関連付けられている名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="fc12f-128">They're name-value pairs associated with an XML element.</span></span> <span data-ttu-id="fc12f-129">ドキュメント オブジェクト モデル (DOM) とは異なり、XML の構造をより密接に反映します。</span><span class="sxs-lookup"><span data-stu-id="fc12f-129">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="fc12f-130"><xref:System.Xml.Linq.XAttribute> オブジェクトは実際には XML ツリーのノードではありませんが、<xref:System.Xml.Linq.XAttribute> オブジェクトの操作は <xref:System.Xml.Linq.XElement> オブジェクトの操作と似ています。</span><span class="sxs-lookup"><span data-stu-id="fc12f-130">Although <xref:System.Xml.Linq.XAttribute> objects aren't actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="fc12f-131">属性と要素の区別は主に、ノード レベルで XML ツリーを操作するコードを記述する開発者にとってのみ重要な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="fc12f-131">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="fc12f-132">多くの開発者は、この区別を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fc12f-132">Many developers won't be concerned with this distinction.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc12f-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc12f-133">See also</span></span>

- [<span data-ttu-id="fc12f-134">LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="fc12f-134">LINQ to XML overview</span></span>](linq-xml-overview.md)
