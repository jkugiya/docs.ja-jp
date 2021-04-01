---
title: 名前と値のペアを維持する - LINQ to XML
description: LINQ to XML メソッドを使用し、名前と値のペアのセットを維持する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7b04b0f1-af64-42eb-8737-83f8861b5915
ms.openlocfilehash: 681df91d42f8bdb403dcf6f735104301c4a0c9ba
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412012"
---
# <a name="maintain-name-value-pairs-linq-to-xml"></a><span data-ttu-id="a4b48-103">名前と値のペアを維持する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="a4b48-103">Maintain name-value pairs (LINQ to XML)</span></span>

<span data-ttu-id="a4b48-104">多くのアプリケーションでは、情報を名前と値のペアとして保持するのが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="a4b48-104">Many applications have to maintain information that is best kept as name-value pairs.</span></span> <span data-ttu-id="a4b48-105">このような情報には、構成情報やグローバル設定などがあります。</span><span class="sxs-lookup"><span data-stu-id="a4b48-105">This information might be configuration information or global settings.</span></span> <span data-ttu-id="a4b48-106">LINQ to XML には、名前と値のペアのセットを簡単に保持できるようにするメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="a4b48-106">LINQ to XML contains methods that make it easy to maintain a set of name-value pairs.</span></span> <span data-ttu-id="a4b48-107">情報を属性として保持することも、子要素のセットとして保持することもできます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-107">You can either keep the information as attributes or as a set of child elements.</span></span>

<span data-ttu-id="a4b48-108">情報を属性として保持する場合と子要素として保持する場合の違いの 1 つは、要素の特定の名前を持つ属性は 1 つしか存在できないという制約が属性にはあることです。</span><span class="sxs-lookup"><span data-stu-id="a4b48-108">One difference between keeping the information as attributes or as child elements is that attributes have the constraint that there can be only one attribute with a particular name for an element.</span></span> <span data-ttu-id="a4b48-109">この制限は子要素には適用されません。</span><span class="sxs-lookup"><span data-stu-id="a4b48-109">This limitation doesn't apply to child elements.</span></span>

## <a name="setattributevalue-and-setelementvalue"></a><span data-ttu-id="a4b48-110">SetAttributeValue と SetElementValue</span><span class="sxs-lookup"><span data-stu-id="a4b48-110">SetAttributeValue and SetElementValue</span></span>

<span data-ttu-id="a4b48-111">名前と値のペアの保持を容易にする 2 つのメソッドは、<xref:System.Xml.Linq.XElement.SetAttributeValue%2A> と <xref:System.Xml.Linq.XElement.SetElementValue%2A> です。</span><span class="sxs-lookup"><span data-stu-id="a4b48-111">The two methods that facilitate keeping name-value pairs are <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> and <xref:System.Xml.Linq.XElement.SetElementValue%2A>.</span></span> <span data-ttu-id="a4b48-112">これらの 2 つのメソッドは、よく似たセマンティクスを持っています。</span><span class="sxs-lookup"><span data-stu-id="a4b48-112">These two methods have similar semantics.</span></span>

<span data-ttu-id="a4b48-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> では、要素の属性を追加、変更、削除できます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-113"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A> can add, modify, and remove attributes of an element.</span></span>

- <span data-ttu-id="a4b48-114">存在しない属性の名前を指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出すと、新しい属性が作成され、その属性が指定した要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-114">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an attribute that doesn't exist, the method creates a new attribute and adds it to the specified element.</span></span>
- <span data-ttu-id="a4b48-115">既存の属性の名前およびコンテンツを指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出すと、その属性のコンテンツが指定したコンテンツに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-115">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute and with some specified content, the contents of the attribute are replaced with the specified content.</span></span>
- <span data-ttu-id="a4b48-116">既存の属性の名前を指定して <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> を呼び出し、コンテンツに `null` を指定すると、その属性が親から削除されます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-116">If you call <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> with a name of an existing attribute, and specify `null` for the content, the attribute is removed from its parent.</span></span>

<span data-ttu-id="a4b48-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> では、要素の子要素を追加、変更、削除できます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-117"><xref:System.Xml.Linq.XElement.SetElementValue%2A> can add, modify, and remove child elements of an element.</span></span>

- <span data-ttu-id="a4b48-118">存在しない子要素の名前を指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出すと、新しい要素が作成され、その要素が指定した要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-118">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of a child element that doesn't exist, the method creates a new element and adds it to the specified element.</span></span>
- <span data-ttu-id="a4b48-119">既存の要素の名前およびコンテンツを指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出すと、その要素のコンテンツが指定したコンテンツに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-119">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element and with some specified content, the contents of the element are replaced with the specified content.</span></span>
- <span data-ttu-id="a4b48-120">既存の要素の名前を指定して <xref:System.Xml.Linq.XElement.SetElementValue%2A> を呼び出し、コンテンツに `null` を指定すると、その要素が親から削除されます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-120">If you call <xref:System.Xml.Linq.XElement.SetElementValue%2A> with a name of an existing element, and specify `null` for the content, the element is removed from its parent.</span></span>

## <a name="example-use-setattributevalue-to-create-and-maintain-a-list-of-name-value-pairs"></a><span data-ttu-id="a4b48-121">例: `SetAttributeValue` を使用し、名前と値のペアの一覧を作成して保持する</span><span class="sxs-lookup"><span data-stu-id="a4b48-121">Example: Use `SetAttributeValue` to create and maintain a list of name-value pairs</span></span>

<span data-ttu-id="a4b48-122">次の例では、属性を持たない要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="a4b48-122">The following example creates an element with no attributes.</span></span> <span data-ttu-id="a4b48-123">次に、<xref:System.Xml.Linq.XElement.SetAttributeValue%2A> メソッドを使用して名前と値のペアの一覧を作成して保持します。</span><span class="sxs-lookup"><span data-stu-id="a4b48-123">It then uses the <xref:System.Xml.Linq.XElement.SetAttributeValue%2A> method to create and maintain a list of name-value pairs.</span></span>

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22);
root.SetAttributeValue("Left", 20);
root.SetAttributeValue("Bottom", 122);
root.SetAttributeValue("Right", 300);
root.SetAttributeValue("DefaultColor", "Color.Red");
Console.WriteLine(root);

// Replace the value of Top.
root.SetAttributeValue("Top", 10);
Console.WriteLine(root);

// Remove DefaultColor.
root.SetAttributeValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as attributes.
root.SetAttributeValue("Top", 22)
root.SetAttributeValue("Left", 20)
root.SetAttributeValue("Bottom", 122)
root.SetAttributeValue("Right", 300)
root.SetAttributeValue("DefaultColor", "Color.Red")
Console.WriteLine(root)

' Replace the value of Top.
root.SetAttributeValue("Top", 10)
Console.WriteLine(root)

' Remove DefaultColor.
root.SetAttributeValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

<span data-ttu-id="a4b48-124">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-124">This example produces the following output:</span></span>

```xml
<Root Top="22" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" DefaultColor="Color.Red" />
<Root Top="10" Left="20" Bottom="122" Right="300" />
```

## <a name="example-use-setelementvalue-to-create-and-maintain-a-list-of-name-value-pairs"></a><span data-ttu-id="a4b48-125">例: `SetElementValue` を使用し、名前と値のペアの一覧を作成して保持する</span><span class="sxs-lookup"><span data-stu-id="a4b48-125">Example: Use `SetElementValue` to create and maintain a list of name-value pairs</span></span>

<span data-ttu-id="a4b48-126">次の例では、子要素を持たない要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="a4b48-126">The following example creates an element with no child elements.</span></span> <span data-ttu-id="a4b48-127">次に、<xref:System.Xml.Linq.XElement.SetElementValue%2A> メソッドを使用して名前と値のペアの一覧を作成して保持します。</span><span class="sxs-lookup"><span data-stu-id="a4b48-127">It then uses the <xref:System.Xml.Linq.XElement.SetElementValue%2A> method to create and maintain a list of name-value pairs.</span></span>

```csharp
// Create an element with no content.
XElement root = new XElement("Root");

// Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22);
root.SetElementValue("Left", 20);
root.SetElementValue("Bottom", 122);
root.SetElementValue("Right", 300);
root.SetElementValue("DefaultColor", "Color.Red");
Console.WriteLine(root);
Console.WriteLine("----");

// Replace the value of Top.
root.SetElementValue("Top", 10);
Console.WriteLine(root);
Console.WriteLine("----");

// Remove DefaultColor.
root.SetElementValue("DefaultColor", null);
Console.WriteLine(root);
```

```vb
' Create an element with no content.
Dim root As XElement = <Root/>

' Add a number of name-value pairs as elements.
root.SetElementValue("Top", 22)
root.SetElementValue("Left", 20)
root.SetElementValue("Bottom", 122)
root.SetElementValue("Right", 300)
root.SetElementValue("DefaultColor", "Color.Red")
Console.WriteLine(root)
Console.WriteLine("----")

' Replace the value of Top.
root.SetElementValue("Top", 10)
Console.WriteLine(root)
Console.WriteLine("----")

' Remove DefaultColor.
root.SetElementValue("DefaultColor", Nothing)
Console.WriteLine(root)
```

<span data-ttu-id="a4b48-128">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a4b48-128">This example produces the following output:</span></span>

```xml
<Root>
  <Top>22</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
  <DefaultColor>Color.Red</DefaultColor>
</Root>
----
<Root>
  <Top>10</Top>
  <Left>20</Left>
  <Bottom>122</Bottom>
  <Right>300</Right>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="a4b48-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4b48-129">See also</span></span>

- <xref:System.Xml.Linq.XElement.SetAttributeValue%2A>
- <xref:System.Xml.Linq.XElement.SetElementValue%2A>
