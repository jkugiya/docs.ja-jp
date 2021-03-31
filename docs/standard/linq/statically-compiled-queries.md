---
title: 静的にコンパイルされたクエリ - LINQ to XML
description: LINQ to XML クエリを静的にコンパイルすることで、XMLDocument に勝るパフォーマンスの優位性を得る方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 53dd47247eae8802dcf8187d0e82eb1c8bead9f9
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412036"
---
# <a name="statically-compiled-queries-linq-to-xml"></a><span data-ttu-id="f8dcf-103">静的にコンパイルされたクエリ (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f8dcf-103">Statically compiled queries (LINQ to XML)</span></span>

<span data-ttu-id="f8dcf-104"><xref:System.Xml.XmlDocument> と比べて、LINQ to XML の最も重要なパフォーマンスの優位性の 1 つは、XPath のクエリは実行時に解釈する必要がある一方で LINQ to XML のクエリは静的にコンパイルされるという点です。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-104">One of the most important performance advantages of LINQ to XML, as compared to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="f8dcf-105">この機能は LINQ to XML に組み込まれているので、追加の手順を実行することなく利用できますが、その違いを理解しておくと、この 2 つの技術のどちらかを選ぶときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-105">This feature is built into LINQ to XML, so you don't have to perform extra steps to take advantage of it, but it's helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="f8dcf-106">この記事では違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-106">This article explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="f8dcf-107">静的にコンパイルされたクエリと XPath</span><span class="sxs-lookup"><span data-stu-id="f8dcf-107">Statically compiled queries vs. XPath</span></span>

<span data-ttu-id="f8dcf-108">次の例は、指定した名前と指定した値の属性がある子孫要素を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-108">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span> <span data-ttu-id="f8dcf-109">これに相当する XPath 式は、`//Address[@Type='Shipping']` です。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-109">The equivalent XPath expression is `//Address[@Type='Shipping']`.</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    from el in po.Descendants("Address")
    where (string)el.Attribute("Type") == "Shipping"
    select el;

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = From el In po.Descendants("Address")
            Where el.@Type = "Shipping"

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f8dcf-110">この例のクエリ式は、コンパイラによってメソッドベースのクエリ構文に書き換えられています。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-110">The query expression in this example is rewritten by the compiler to method-based query syntax.</span></span> <span data-ttu-id="f8dcf-111">メソッドベースのクエリ構文で書かれた次の例では、前の例と同じ結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-111">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    po
    .Descendants("Address")
    .Where(el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

 ```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f8dcf-112"><xref:System.Linq.Enumerable.Where%2A> メソッドは拡張メソッドです。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-112">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="f8dcf-113">詳細については、「[拡張メソッド (C# プログラミング ガイド)](../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-113">For more information, see [Extension Methods (C# Programming Guide)](../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="f8dcf-114"><xref:System.Linq.Enumerable.Where%2A> は拡張メソッドであるため、上記のクエリは次のように書かれたかのようにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-114">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```csharp
XDocument po = XDocument.Load("PurchaseOrders.xml");

IEnumerable<XElement> list1 =
    System.Linq.Enumerable.Where(
        po.Descendants("Address"),
        el => (string)el.Attribute("Type") == "Shipping");

foreach (XElement el in list1)
    Console.WriteLine(el);
```

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f8dcf-115">この例では、前の 2 つの例と同じ結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-115">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="f8dcf-116">これは、静的にリンクされたメソッド呼び出しにクエリが効果的にコンパイルされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-116">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="f8dcf-117">これと反復子の遅延実行セマンティクスが組み合わさることで、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-117">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="f8dcf-118">反復子の遅延実行セマンティクスの詳細については、「[遅延実行とレイジー評価](deferred-execution-lazy-evaluation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-118">For more information about the deferred execution semantics of iterators, see [Deferred execution and lazy evaluation](deferred-execution-lazy-evaluation.md).</span></span>

> [!NOTE]
> <span data-ttu-id="f8dcf-119">これらは、コンパイラが書き込むコードの例です。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-119">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="f8dcf-120">実際の実装はこれらの例と若干異なる可能性がありますが、パフォーマンスは同じか類似したものになります。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-120">The actual implementation might differ slightly from these examples, but the performance will be the same as, or similar to, these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="f8dcf-121">XmlDocument を使用した XPath 式の実行</span><span class="sxs-lookup"><span data-stu-id="f8dcf-121">Executing XPath expressions with XmlDocument</span></span>

<span data-ttu-id="f8dcf-122">次の例では、<xref:System.Xml.XmlDocument> を使用して前の例と同じ結果を達成します。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-122">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

```csharp
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");
XmlDocument doc = new XmlDocument();
doc.Load(reader);
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");
foreach (XmlNode n in nl)
    Console.WriteLine(n.OuterXml);
reader.Close();
```

```vb
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")
Dim doc As New Xml.XmlDocument()
doc.Load(reader)
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")
For Each n As Xml.XmlNode In nl
    Console.WriteLine(n.OuterXml)
Next
reader.Close()
```

<span data-ttu-id="f8dcf-123">このクエリは、LINQ to XML を使用する例と同じ出力を返します。唯一の違いは、出力する XML が LINQ to XML ではインデントされるのに対し、<xref:System.Xml.XmlDocument> ではされないという点です。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-123">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> doesn't.</span></span>

<span data-ttu-id="f8dcf-124">ただし、一般に <xref:System.Xml.XmlDocument> の方法では、<xref:System.Xml.XmlNode.SelectNodes%2A> メソッドが呼び出されるたびに次の処理を行わなければならないため、LINQ to XML ほどのパフォーマンスは達成できません。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-124">However, the <xref:System.Xml.XmlDocument> approach generally doesn't perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following every time it's called:</span></span>

- <span data-ttu-id="f8dcf-125">XPath 式を含んでいる文字列を解析してトークンに分解します。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-125">Parse the string that contains the XPath expression, breaking the string into tokens.</span></span>
- <span data-ttu-id="f8dcf-126">トークンを検証して、XPath 式が有効であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-126">Validate the tokens to make sure that the XPath expression is valid.</span></span>
- <span data-ttu-id="f8dcf-127">式を内部式ツリーに変換します。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-127">Translate the expression into an internal expression tree.</span></span>
- <span data-ttu-id="f8dcf-128">ノードを反復処理し、式の評価に基づいて結果セットのノードを適切に選択します。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-128">Iterate through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="f8dcf-129">この場合、対応する LINQ to XML のクエリよりも処理量がかなり多くなります。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-129">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="f8dcf-130">具体的なパフォーマンスの違いはクエリの種類によって異なりますが、一般に LINQ to XML のクエリは処理量が少ないため、<xref:System.Xml.XmlDocument> を使用して XPath 式を評価するよりも良いパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="f8dcf-130">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>
