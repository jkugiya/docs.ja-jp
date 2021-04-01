---
title: LINQ to XML を使用してディクショナリを操作する方法 - LINQ to XML
description: さまざまな種類のデータ構造を XML に変換したり、XML を構造体に変換したりすることができます。 Generic.Dictionary を XML に変換して元に戻す例を次に示します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: c9f4d6ad3dfe12f49b907095312477717a73c2c9
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2020
ms.locfileid: "103412174"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml"></a><span data-ttu-id="03746-104">LINQ to XML を使用してディクショナリを操作する方法</span><span class="sxs-lookup"><span data-stu-id="03746-104">How to work with dictionaries using LINQ to XML</span></span>

<span data-ttu-id="03746-105">多くの場合、さまざまな種類のデータ構造を XML に変換した後、XML から他のデータ構造に変換すると便利です。</span><span class="sxs-lookup"><span data-stu-id="03746-105">It's often convenient to convert data structures of various kinds to XML, and then from XML to other data structures.</span></span> <span data-ttu-id="03746-106">この記事は、<xref:System.Collections.Generic.Dictionary%602> から XML への変換と、その逆について示しています。</span><span class="sxs-lookup"><span data-stu-id="03746-106">This article shows a conversion of a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>

## <a name="example-create-a-dictionary-and-convert-its-contents-to-xml"></a><span data-ttu-id="03746-107">例: ディクショナリを作成し、その内容を XML に変換する</span><span class="sxs-lookup"><span data-stu-id="03746-107">Example: Create a Dictionary and convert its contents to XML</span></span>

<span data-ttu-id="03746-108">この最初の例では、<xref:System.Collections.Generic.Dictionary%602> を作成し、それを XML に変換します。</span><span class="sxs-lookup"><span data-stu-id="03746-108">This first example creates a <xref:System.Collections.Generic.Dictionary%602>, and then converts it to XML.</span></span>

<span data-ttu-id="03746-109">この C# バージョンの例では、クエリによって新しい <xref:System.Xml.Linq.XElement> オブジェクトが射影され、関数型構築の形式を使用します。結果のコレクションは、引数として Root <xref:System.Xml.Linq.XElement> オブジェクトのコンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="03746-109">This C# version of the example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>

<span data-ttu-id="03746-110">Visual Basic バージョンでは、XML リテラルと組み込み式内のクエリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="03746-110">The Visual Basic version uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="03746-111">このクエリによって、新しい <xref:System.Xml.Linq.XElement> オブジェクトが射影されます。その後、これは `Root` <xref:System.Xml.Linq.XElement> オブジェクトの新しいコンテンツになります。</span><span class="sxs-lookup"><span data-stu-id="03746-111">The query projects new <xref:System.Xml.Linq.XElement> objects which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>

```csharp
Dictionary<string, string> dict = new Dictionary<string, string>();
dict.Add("Child1", "Value1");
dict.Add("Child2", "Value2");
dict.Add("Child3", "Value3");
dict.Add("Child4", "Value4");
XElement root = new XElement("Root",
    from keyValue in dict
    select new XElement(keyValue.Key, keyValue.Value)
);
Console.WriteLine(root);
```

```vb
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()
dict.Add("Child1", "Value1")
dict.Add("Child2", "Value2")
dict.Add("Child3", "Value3")
dict.Add("Child4", "Value4")
Dim root As XElement = _
    <Root>
        <%= From keyValue In dict _
            Select New XElement(keyValue.Key, keyValue.Value) %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="03746-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="03746-112">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Value1</Child1>
  <Child2>Value2</Child2>
  <Child3>Value3</Child3>
  <Child4>Value4</Child4>
</Root>
```

## <a name="example-create-a-dictionary-and-load-it-from-xml-data"></a><span data-ttu-id="03746-113">例: ディクショナリを作成し、XML データから読み込む</span><span class="sxs-lookup"><span data-stu-id="03746-113">Example: Create a dictionary and load it from XML data</span></span>

<span data-ttu-id="03746-114">次の例では、ディクショナリを作成して XML データから読み込みます。</span><span class="sxs-lookup"><span data-stu-id="03746-114">The next example creates a dictionary loads it from XML data.</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "Value1"),
    new XElement("Child2", "Value2"),
    new XElement("Child3", "Value3"),
    new XElement("Child4", "Value4")
);

Dictionary<string, string> dict = new Dictionary<string, string>();
foreach (XElement el in root.Elements())
    dict.Add(el.Name.LocalName, el.Value);
foreach (string str in dict.Keys)
    Console.WriteLine("{0}:{1}", str, dict[str]);
```

```vb
Dim root As XElement = _
        <Root>
            <Child1>Value1</Child1>
            <Child2>Value2</Child2>
            <Child3>Value3</Child3>
            <Child4>Value4</Child4>
        </Root>

Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)
For Each el As XElement In root.Elements
    dict.Add(el.Name.LocalName, el.Value)
Next
For Each str As String In dict.Keys
    Console.WriteLine("{0}:{1}", str, dict(str))
Next
```

<span data-ttu-id="03746-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="03746-115">This example produces the following output:</span></span>

```output
Child1:Value1
Child2:Value2
Child3:Value3
Child4:Value4
```

## <a name="see-also"></a><span data-ttu-id="03746-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="03746-116">See also</span></span>

- [<span data-ttu-id="03746-117">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03746-117">Projection Operations (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
