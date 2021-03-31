---
title: 属性の値を取得する方法 - LINQ to XML
description: 属性の値を取得します。 XAttribute を目的の型にキャストすることも、XAttribute.Value プロパティを使用することもできます。
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 7af3616c9808cad5dfb52f53c74b21a59da5c954
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412195"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml"></a><span data-ttu-id="f35f9-104">属性の値を取得する方法 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f35f9-104">How to retrieve the value of an attribute (LINQ to XML)</span></span>

<span data-ttu-id="f35f9-105">この記事では、属性の値を取得する方法について示します。</span><span class="sxs-lookup"><span data-stu-id="f35f9-105">This article shows how to obtain the value of attributes.</span></span> <span data-ttu-id="f35f9-106">主に 2 つの方法があります。1 つは、<xref:System.Xml.Linq.XAttribute> を目的の型にキャストする方法です。その後、明示的な変換演算子によって、要素または属性のコンテンツが指定した型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f35f9-106">There are two main ways: You can cast an <xref:System.Xml.Linq.XAttribute> to the desired type; the explicit conversion operator then converts the contents of the element or attribute to the specified type.</span></span> <span data-ttu-id="f35f9-107">もう 1 つは、<xref:System.Xml.Linq.XAttribute.Value%2A> プロパティを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="f35f9-107">Alternatively, you can use the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span> <span data-ttu-id="f35f9-108">ただし、通常はキャストがより適切な方法です。</span><span class="sxs-lookup"><span data-stu-id="f35f9-108">However, casting is generally the better approach.</span></span> <span data-ttu-id="f35f9-109">属性を null 許容の値の型にキャストすると、存在しているかどうかが不明確な属性の値を取得する場合にコードをより簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="f35f9-109">If you cast the attribute to a nullable value type, the code is simpler to write when retrieving the value of an attribute that might or might not exist.</span></span> <span data-ttu-id="f35f9-110">この手法の例については、「[要素の値を取得する方法](retrieve-value-element.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f35f9-110">For examples of this technique, see [How to retrieve the value of an element](retrieve-value-element.md).</span></span>

## <a name="example-use-a-cast-to-retrieve-the-value-of-an-attribute"></a><span data-ttu-id="f35f9-111">例: 属性の値を取得するためにキャストを使用する</span><span class="sxs-lookup"><span data-stu-id="f35f9-111">Example: Use a cast to retrieve the value of an attribute</span></span>

<span data-ttu-id="f35f9-112">C# で属性の値を取得するには、<xref:System.Xml.Linq.XAttribute> オブジェクトを目的の型にキャストします。</span><span class="sxs-lookup"><span data-stu-id="f35f9-112">To retrieve the value of an attribute in C#, you cast the <xref:System.Xml.Linq.XAttribute> object to your desired type.</span></span> <span data-ttu-id="f35f9-113">Visual Basic では、統合属性プロパティを使用して値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="f35f9-113">In Visual Basic, you can use the integrated attribute property to retrieve the value.</span></span>

```csharp
XElement root = new XElement("Root",
                    new XAttribute("Attr", "abcde")
                );
Console.WriteLine(root);
string str = (string)root.Attribute("Attr");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root Attr="abcde"/>
Console.WriteLine(root)
Dim str As String = root.@Attr
Console.WriteLine(str)
```

<span data-ttu-id="f35f9-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f35f9-114">This example produces the following output:</span></span>

```output
<Root Attr="abcde" />
abcde
```

## <a name="example-use-a-cast-to-retrieve-from-xml-thats-in-a-namespace"></a><span data-ttu-id="f35f9-115">例: 名前空間にある XML からの取得にキャストを使用する</span><span class="sxs-lookup"><span data-stu-id="f35f9-115">Example: Use a cast to retrieve from XML that's in a namespace</span></span>

<span data-ttu-id="f35f9-116">属性が名前空間内にある場合にその属性の値を取得する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="f35f9-116">The following example shows how to retrieve the value of an attribute if the attribute is in a namespace.</span></span> <span data-ttu-id="f35f9-117">詳細については、「[名前空間の概要](namespaces-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f35f9-117">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
                    new XAttribute(aw + "Attr", "abcde")
                );
string str = (string)root.Attribute(aw + "Attr");
Console.WriteLine(str);
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root aw:Attr="abcde"/>
        Dim str As String = root.@aw:Attr
        Console.WriteLine(str)
    End Sub
End Module
```

<span data-ttu-id="f35f9-118">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f35f9-118">This example produces the following output:</span></span>

```output
abcde
```

## <a name="see-also"></a><span data-ttu-id="f35f9-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="f35f9-119">See also</span></span>

- [<span data-ttu-id="f35f9-120">LINQ to XML 軸の概要</span><span class="sxs-lookup"><span data-stu-id="f35f9-120">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
