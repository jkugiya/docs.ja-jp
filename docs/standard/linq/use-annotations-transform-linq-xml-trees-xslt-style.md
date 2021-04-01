---
title: 注釈を使用して XSLT スタイルの LINQ to XML ツリーを変換する - LINQ to XML
description: 注釈を使用し、コンテンツが混在しているドキュメント中心の XML ドキュメントを変換する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 3cecc1b868983f1fa19d29d4bf5e73182a1af295
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412188"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-linq-to-xml"></a><span data-ttu-id="055a7-103">注釈を使用して XSLT スタイルの LINQ to XML ツリーを変換する (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="055a7-103">How to use annotations to transform LINQ to XML trees in an XSLT style (LINQ to XML)</span></span>

<span data-ttu-id="055a7-104">注釈を使用することで、XML ツリーの変換が容易になります。</span><span class="sxs-lookup"><span data-stu-id="055a7-104">Annotations can be used to facilitate transforms of an XML tree.</span></span>

<span data-ttu-id="055a7-105">一部の XML ドキュメントは、"コンテンツが混在し、ドキュメント中心" です。</span><span class="sxs-lookup"><span data-stu-id="055a7-105">Some XML documents are "document-centric with mixed content."</span></span> <span data-ttu-id="055a7-106">このようなドキュメントでは、必ずしも要素の子ノードの構造を把握する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="055a7-106">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="055a7-107">たとえば、テキストを含んでいるノードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="055a7-107">For instance, a node that contains text may look like this:</span></span>

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

<span data-ttu-id="055a7-108">どのテキスト ノードにも、任意の数の `<b>` と `<i>` が子要素として存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="055a7-108">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="055a7-109">この方法は、通常の段落、箇条書きの段落、およびビットマップのさまざまな子要素を含むページなどのその他の多数の状況におよびます。</span><span class="sxs-lookup"><span data-stu-id="055a7-109">This approach extends to a number of other situations, such as pages that can contain a variety of child elements, which could be regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="055a7-110">テーブルのセルには、テキスト、ドロップダウン リスト、またはビットマップが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="055a7-110">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="055a7-111">ドキュメント中心の XML の主要な特性の 1 つは、特定の要素がどの子要素を持つかがわからない点です。</span><span class="sxs-lookup"><span data-stu-id="055a7-111">One of the primary characteristics of document-centric XML is that you don't know which child element any particular element will have.</span></span>

<span data-ttu-id="055a7-112">ツリー内の要素を変換するとき、その要素の子について詳しく理解している必要がない場合は、注釈を使用するこの方法が効果的です。</span><span class="sxs-lookup"><span data-stu-id="055a7-112">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective one.</span></span>

<span data-ttu-id="055a7-113">この方法の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="055a7-113">The summary of the approach is:</span></span>

- <span data-ttu-id="055a7-114">最初に、ツリー内の要素に置換要素を使用して注釈を付けます。</span><span class="sxs-lookup"><span data-stu-id="055a7-114">First, annotate elements in the tree with a replacement element.</span></span>
- <span data-ttu-id="055a7-115">2 番目に、ツリー全体を反復処理して、各要素をその注釈で置換する新しいツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="055a7-115">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="055a7-116">この記事の例では、`XForm` という名前の関数で新しいツリーの反復処理と作成を実装しています。</span><span class="sxs-lookup"><span data-stu-id="055a7-116">The examples in this article implement the iteration and creation of the new tree in a function named `XForm`.</span></span>

<span data-ttu-id="055a7-117">この方法の詳細な構成は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="055a7-117">In detail, the approach consists of:</span></span>

- <span data-ttu-id="055a7-118">構造を変換する一連の要素を返す 1 つ以上の LINQ to XML クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="055a7-118">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="055a7-119">クエリ内の要素ごとに、新しい <xref:System.Xml.Linq.XElement> オブジェクトをその要素に対する注釈として追加します。</span><span class="sxs-lookup"><span data-stu-id="055a7-119">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="055a7-120">変換後の新しいツリーでは、注釈付きの要素がこの新しい要素で置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="055a7-120">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="055a7-121">例で示すように、このコードは簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="055a7-121">This is simple code to write, as demonstrated by the example.</span></span>
- <span data-ttu-id="055a7-122">注釈として追加する新しい要素には、新しい子ノードを含めることができます。これでは、希望の構造のサブツリーを形成できます。</span><span class="sxs-lookup"><span data-stu-id="055a7-122">The new element that's added as an annotation can contain new child nodes; it can form a subtree with any desired shape.</span></span>
- <span data-ttu-id="055a7-123">新しい要素の子ノードが、この目的のために作成された別の名前空間にある場合 (この例で名前空間は `http://www.microsoft.com/LinqToXmlTransform/2007`)、その子要素は新しいツリーにはコピーされないという特別な規則があります。</span><span class="sxs-lookup"><span data-stu-id="055a7-123">There is a special rule: If a child node of the new element is in a different namespace, a namespace that's made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element isn't copied to the new tree.</span></span> <span data-ttu-id="055a7-124">名前空間が上記の特別な名前空間で、かつ要素のローカル名が `ApplyTransforms` である場合は、代わりに、ソース ツリー内の要素の子ノードは反復処理され、新しいツリーにコピーされます (例外として、注釈付きの子要素自体はここで示す規則に従って変換されます)。</span><span class="sxs-lookup"><span data-stu-id="055a7-124">Instead, if the namespace is the above-mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>
- <span data-ttu-id="055a7-125">これは、XSL での変換の仕様にある程度似ています。</span><span class="sxs-lookup"><span data-stu-id="055a7-125">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="055a7-126">一連のノードを選択するクエリは、テンプレートの XPath 式に似ています。</span><span class="sxs-lookup"><span data-stu-id="055a7-126">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="055a7-127">注釈として保存される新しい <xref:System.Xml.Linq.XElement> を作成するコードは、XSL のシーケンス コンストラクターに似ています。また、`ApplyTransforms` 要素は、XSL の `xsl:apply-templates` 要素と機能的に似ています。</span><span class="sxs-lookup"><span data-stu-id="055a7-127">The code to create the new <xref:System.Xml.Linq.XElement> that's saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>
- <span data-ttu-id="055a7-128">この方法の利点の 1 つは、クエリを作成するときに、常に未変更のソース ツリーに対してクエリを記述する点です。</span><span class="sxs-lookup"><span data-stu-id="055a7-128">One advantage to taking this approach is that, as you formulate queries, you're  always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="055a7-129">ツリーに対する変更が記述中のクエリに与える影響を考慮する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="055a7-129">You don't need to worry about how modifications to the tree affect the queries that you're writing.</span></span>

## <a name="example-rename-all-paragraph-nodes"></a><span data-ttu-id="055a7-130">例: すべての段落ノードを名前変更する</span><span class="sxs-lookup"><span data-stu-id="055a7-130">Example: Rename all paragraph nodes</span></span>

<span data-ttu-id="055a7-131">この例では、すべての `Paragraph` ノードが `para` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="055a7-131">This example renames all `Paragraph` nodes to `para`.</span></span>

```csharp
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";
XName at = xf + "ApplyTransforms";

XElement root = XElement.Parse(@"
<Root>
    <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>
    <Paragraph>More text.</Paragraph>
</Root>");

// replace Paragraph with para
foreach (var el in root.Descendants("Paragraph"))
    el.AddAnnotation(
        new XElement("para",
            // same idea as xsl:apply-templates
            new XElement(xf + "ApplyTransforms")
        )
    );

// The XForm method, shown later in this article, accomplishes the transform
XElement newRoot = XForm(root);

Console.WriteLine(newRoot);
```

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>
                <Paragraph>More text.</Paragraph>
            </Root>

        ' Replace Paragraph with p.
        For Each el In root...<Paragraph>
            ' same idea as xsl:apply-templates
            el.AddAnnotation( _
                <para>
                    <<%= at %>></>
                </para>)
        Next

        ' The XForm function, shown later in this article, accomplishes the transform
        Dim newRoot As XElement = XForm(root)
        Console.WriteLine(newRoot)
    End Sub
End Module
```

<span data-ttu-id="055a7-132">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="055a7-132">This example produces the following output:</span></span>

```xml
<Root>
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>
  <para>More text.</para>
</Root>
```

## <a name="example-calculate-averages-and-sums-and-add-them-as-new-elements-to-the-tree"></a><span data-ttu-id="055a7-133">例: 平均と合計を計算し、それらを新しい要素としてツリーに追加する</span><span class="sxs-lookup"><span data-stu-id="055a7-133">Example: Calculate averages and sums and add them as new elements to the tree</span></span>

<span data-ttu-id="055a7-134">次の例では、`Data` 要素の平均と合計を計算し、それらをツリーに新しい要素として追加します。</span><span class="sxs-lookup"><span data-stu-id="055a7-134">The following example calculates the average and sum of the `Data` elements and adds them as new elements to the tree.</span></span>

```csharp
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";
XName at = xf + "ApplyTransforms";

XElement data = new XElement("Root",
    new XElement("Data", 20),
    new XElement("Data", 10),
    new XElement("Data", 3)
);

// while adding annotations, you can query the source tree all you want,
// as the tree isn't mutated while annotating.
var avg = data.Elements("Data").Select(z => (Decimal)z).Average();
data.AddAnnotation(
    new XElement("Root",
        new XElement(xf + "ApplyTransforms"),
        new XElement("Average", $"{avg:F4}"),
        new XElement("Sum",
            data
            .Elements("Data")
            .Select(z => (int)z)
            .Sum()
        )
    )
);

Console.WriteLine("Before Transform");
Console.WriteLine("----------------");
Console.WriteLine(data);
Console.WriteLine();
Console.WriteLine();

// The XForm method, shown later in this article, accomplishes the transform
XElement newData = XForm(data);

Console.WriteLine("After Transform");
Console.WriteLine("----------------");
Console.WriteLine(newData);
```

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim data As XElement = _
            <Root>
                <Data>20</Data>
                <Data>10</Data>
                <Data>3</Data>
            </Root>

        ' While adding annotations, you can query the source tree all you want,
        ' as the tree isn't mutated while annotating.
        data.AddAnnotation( _
            <Root>
                <<%= at %>/>
                <Average>
                    <%= _
                        String.Format("{0:F4}", _
                        data.Elements("Data") _
                        .Select(Function(z) CDec(z)).Average()) _
                    %>
                </Average>
                <Sum>
                    <%= _
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _
                    %>
                </Sum>
            </Root> _
        )

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(data)
        Console.WriteLine(vbNewLine)

        ' The XForm function, shown later in this article, accomplishes the transform
        Dim newData As XElement = XForm(data)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newData)
    End Sub
End Module
```

<span data-ttu-id="055a7-135">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="055a7-135">This example produces the following output:</span></span>

```output
Before Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
</Root>

After Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
  <Average>11.0000</Average>
  <Sum>33</Sum>
</Root>
```

## <a name="example-create-a-new-transformed-tree-from-the-original-annotated-tree"></a><span data-ttu-id="055a7-136">例: 元の注釈付きツリーから変換された新しいツリーを作成する</span><span class="sxs-lookup"><span data-stu-id="055a7-136">Example: Create a new transformed tree from the original annotated tree</span></span>

<span data-ttu-id="055a7-137">小さな関数 `XForm` によって、元の注釈付きツリーから変換された新しいツリーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="055a7-137">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span> <span data-ttu-id="055a7-138">この関数の擬似コードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="055a7-138">The following is pseudocode for this function:</span></span>

> <span data-ttu-id="055a7-139">この関数は、引数として XElement を受け取り、XElement を返します。</span><span class="sxs-lookup"><span data-stu-id="055a7-139">The function takes an XElement as an argument and returns an XElement.</span></span>
>
> <span data-ttu-id="055a7-140">要素に XElement の注釈がある場合、返される XElement には次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="055a7-140">If an element has an XElement annotation, the returned XElement has these characteristics:</span></span>
>
> - <span data-ttu-id="055a7-141">新しい XElement の名前は、注釈要素の名前です。</span><span class="sxs-lookup"><span data-stu-id="055a7-141">The name of the new XElement is the annotation element's name.</span></span>
> - <span data-ttu-id="055a7-142">すべての属性が注釈から新しいノードにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="055a7-142">All attributes are copied from the annotation to the new node.</span></span>
> - <span data-ttu-id="055a7-143">すべての子ノードが注釈からコピーされます (特殊なノード xf:ApplyTransforms が認識されて、ソース要素の子ノードが反復処理される場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="055a7-143">All child nodes are copied from the annotation, with the exception that the special node xf:ApplyTransforms is recognized, and the source element's child nodes are iterated.</span></span> <span data-ttu-id="055a7-144">ソースの子ノードが XElement ではない場合、それが新しいツリーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="055a7-144">If the source child node isn't an XElement, it's copied to the new tree.</span></span> <span data-ttu-id="055a7-145">ソースの子が XElement である場合、それは、この関数を再帰的に呼び出すことによって変換されます。</span><span class="sxs-lookup"><span data-stu-id="055a7-145">If the source child is an XElement, then it's transformed by calling this function recursively.</span></span>
>
> <span data-ttu-id="055a7-146">それ以外の場合、返される XElement には次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="055a7-146">Otherwise, the returned XElement has these characteristics:</span></span>
>
> - <span data-ttu-id="055a7-147">新しい XElement の名前は、ソース要素の名前です。</span><span class="sxs-lookup"><span data-stu-id="055a7-147">The name of the new XElement is the source element's name.</span></span>
> - <span data-ttu-id="055a7-148">すべての属性がソース要素からターゲットの要素にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="055a7-148">All attributes are copied from the source element to the destination's element.</span></span>
> - <span data-ttu-id="055a7-149">すべての子ノードがソース要素からコピーされます。</span><span class="sxs-lookup"><span data-stu-id="055a7-149">All child nodes are copied from the source element.</span></span>
> - <span data-ttu-id="055a7-150">ソースの子ノードが XElement ではない場合、それが新しいツリーにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="055a7-150">If the source child node isn't an XElement, it's copied to the new tree.</span></span> <span data-ttu-id="055a7-151">ソースの子が XElement である場合、それは、この関数を再帰的に呼び出すことによって変換されます。</span><span class="sxs-lookup"><span data-stu-id="055a7-151">If the source child is an XElement, then it's transformed by calling this function recursively.</span></span>

<span data-ttu-id="055a7-152">この関数のコードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="055a7-152">The following is code for this function:</span></span>

```csharp
// Build a transformed XML tree per the annotations
static XElement XForm(XElement source)
{
    XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";
    XName at = xf + "ApplyTransforms";

    if (source.Annotation<XElement>() != null)
    {
        XElement anno = source.Annotation<XElement>();
        return new XElement(anno.Name,
            anno.Attributes(),
            anno
            .Nodes()
            .Select(
                (XNode n) =>
                {
                    XElement annoEl = n as XElement;
                    if (annoEl != null)
                    {
                        if (annoEl.Name == at)
                            return (object)(
                                source.Nodes()
                                .Select(
                                    (XNode n2) =>
                                    {
                                        XElement e2 = n2 as XElement;
                                        if (e2 == null)
                                            return n2;
                                        else
                                            return XForm(e2);
                                    }
                                )
                            );
                        else
                            return n;
                    }
                    else
                        return n;
                }
            )
        );
    }
    else
    {
        return new XElement(source.Name,
            source.Attributes(),
            source
                .Nodes()
                .Select(n =>
                {
                    XElement el = n as XElement;
                    if (el == null)
                        return n;
                    else
                        return XForm(el);
                }
                )
        );
    }
}
```

```vb
' Build a transformed XML tree per the annotations.
Function XForm(ByVal source As XElement) As XElement
    If source.Annotation(Of XElement)() IsNot Nothing Then
        Dim anno As XElement = source.Annotation(Of XElement)()
        Return _
            <<%= anno.Name.ToString() %>>
                <%= anno.Attributes() %>
                <%= anno.Nodes().Select(Function(n As XNode) _
                    GetSubNodes(n, source)) %>
            </>
    Else
        Return _
            <<%= source.Name %>>
                <%= source.Attributes() %>
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
            </>
    End If
End Function

Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
    Dim annoEl As XElement = TryCast(n, XElement)
    If annoEl IsNot Nothing Then
        If annoEl.Name = at Then
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
        End If
    End If
    Return n
End Function

Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
    Dim e2 As XElement = TryCast(n2, XElement)
    If e2 Is Nothing Then
        Return n2
    Else
        Return XForm(e2)
    End If
End Function
```

## <a name="example-show-xform-in-typical-uses-of-this-type-of-transform"></a><span data-ttu-id="055a7-153">例: この種の変換における `XForm` の一般的な使用方法</span><span class="sxs-lookup"><span data-stu-id="055a7-153">Example: Show `XForm` in typical uses of this type of transform</span></span>

<span data-ttu-id="055a7-154">次の例では、`XForm` 関数と、この種の変換の一般的な使用例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="055a7-154">The following example includes the `XForm` function and a few of the typical uses of this type of transform:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Xml;
using System.Xml.Linq;

class Program
{
    static XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";
    static XName at = xf + "ApplyTransforms";

    // Build a transformed XML tree per the annotations
    static XElement XForm(XElement source)
    {
        if (source.Annotation<XElement>() != null)
        {
            XElement anno = source.Annotation<XElement>();
            return new XElement(anno.Name,
                anno.Attributes(),
                anno
                .Nodes()
                .Select(
                    (XNode n) =>
                    {
                        XElement annoEl = n as XElement;
                        if (annoEl != null)
                        {
                            if (annoEl.Name == at)
                                return (object)(
                                    source.Nodes()
                                    .Select(
                                        (XNode n2) =>
                                        {
                                            XElement e2 = n2 as XElement;
                                            if (e2 == null)
                                                return n2;
                                            else
                                                return XForm(e2);
                                        }
                                    )
                                );
                            else
                                return n;
                        }
                        else
                            return n;
                    }
                )
            );
        }
        else
        {
            return new XElement(source.Name,
                source.Attributes(),
                source
                    .Nodes()
                    .Select(n =>
                    {
                        XElement el = n as XElement;
                        if (el == null)
                            return n;
                        else
                            return XForm(el);
                    }
                    )
            );
        }
    }

    static void Main(string[] args)
    {
        XElement root = new XElement("Root",
            new XComment("A comment"),
            new XAttribute("Att1", 123),
            new XElement("Child", 1),
            new XElement("Child", 2),
            new XElement("Other",
                new XElement("GC", 3),
                new XElement("GC", 4)
            ),
            XElement.Parse(
              "<SomeMixedContent>This is <i>an</i> element that " +
              "<b>has</b> some mixed content</SomeMixedContent>"),
            new XElement("AnUnchangedElement", 42)
        );

        // each of the following serves the same semantic purpose as
        // XSLT templates and sequence constructors

        // replace Child with NewChild
        foreach (var el in root.Elements("Child"))
            el.AddAnnotation(new XElement("NewChild", (string)el));

        // replace first GC with GrandChild, add an attribute
        foreach (var el in root.Descendants("GC").Take(1))
            el.AddAnnotation(
                new XElement("GrandChild",
                    new XAttribute("ANewAttribute", 999),
                    (string)el
                )
            );

        // replace Other with NewOther, add new child elements around original content
        foreach (var el in root.Elements("Other"))
            el.AddAnnotation(
                new XElement("NewOther",
                    new XElement("MyNewChild", 1),
                    // same idea as xsl:apply-templates
                    new XElement(xf + "ApplyTransforms"),
                    new XElement("ChildThatComesAfter")
                )
            );

        // change name of element that has mixed content
        root.Descendants("SomeMixedContent").First().AddAnnotation(
            new XElement("MixedContent",
                new XElement(xf + "ApplyTransforms")
            )
        );

        // replace <b> with <Bold>
        foreach (var el in root.Descendants("b"))
            el.AddAnnotation(
                new XElement("Bold",
                    new XElement(xf + "ApplyTransforms")
                )
            );

        // replace <i> with <Italic>
        foreach (var el in root.Descendants("i"))
            el.AddAnnotation(
                new XElement("Italic",
                    new XElement(xf + "ApplyTransforms")
                )
            );

        Console.WriteLine("Before Transform");
        Console.WriteLine("----------------");
        Console.WriteLine(root);
        Console.WriteLine();
        Console.WriteLine();
        XElement newRoot = XForm(root);

        Console.WriteLine("After Transform");
        Console.WriteLine("----------------");
        Console.WriteLine(newRoot);
    }
}
```

```vb
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports System.Xml
Imports System.Xml.Linq

Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    ' Build a transformed XML tree per the annotations.
    Function XForm(ByVal source As XElement) As XElement
        If source.Annotation(Of XElement)() IsNot Nothing Then
            Dim anno As XElement = source.Annotation(Of XElement)()
            Return _
                <<%= anno.Name.ToString() %>>
                    <%= anno.Attributes() %>
                    <%= anno.Nodes().Select(Function(n As XNode) _
                        GetSubNodes(n, source)) %>
                </>
        Else
            Return _
                <<%= source.Name %>>
                    <%= source.Attributes() %>
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
                </>
        End If
    End Function

    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
        Dim annoEl As XElement = TryCast(n, XElement)
        If annoEl IsNot Nothing Then
            If annoEl.Name = at Then
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
            End If
        End If
        Return n
    End Function

    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
        Dim e2 As XElement = TryCast(n2, XElement)
        If e2 Is Nothing Then
            Return n2
        Else
            Return XForm(e2)
        End If
    End Function

    Sub Main()
        Dim root As XElement = _
<Root Att1='123'>
    <!--A comment-->
    <Child>1</Child>
    <Child>2</Child>
    <Other>
        <GC>3</GC>
        <GC>4</GC>
    </Other>
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
    <AnUnchangedElement>42</AnUnchangedElement>
</Root>

        ' Each of the following serves the same semantic purpose as
        ' XSLT templates and sequence constructors.

        ' Replace Child with NewChild.
        For Each el In root.<Child>
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)
        Next

        ' Replace first GC with GrandChild, add an attribute.
        For Each el In root...<GC>.Take(1)
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)
        Next

        ' Replace Other with NewOther, add new child elements around original content.
        For Each el In root.<Other>
            el.AddAnnotation( _
                <NewOther>
                    <MyNewChild>1</MyNewChild>
                    <<%= at %>></>
                    <ChildThatComesAfter/>
                </NewOther>)
        Next

        ' Change name of element that has mixed content.
        root...<SomeMixedContent>(0).AddAnnotation( _
                <MixedContent><<%= at %>></></MixedContent>)

        ' Replace <b> with <Bold>.
        For Each el In root...<b>
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)
        Next

        ' Replace <i> with <Italic>.
        For Each el In root...<i>
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)
        Next

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(root)
        Console.WriteLine(vbNewLine)
        Dim newRoot As XElement = XForm(root)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newRoot)
    End Sub
End Module
```

<span data-ttu-id="055a7-155">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="055a7-155">This example produces the following output:</span></span>

```output
Before Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <Child>1</Child>
  <Child>2</Child>
  <Other>
    <GC>3</GC>
    <GC>4</GC>
  </Other>
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>

After Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <NewChild>1</NewChild>
  <NewChild>2</NewChild>
  <NewOther>
    <MyNewChild>1</MyNewChild>
    <GrandChild ANewAttribute="999">3</GrandChild>
    <GC>4</GC>
    <ChildThatComesAfter />
  </NewOther>
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>
```
