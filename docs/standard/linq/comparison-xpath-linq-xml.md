---
title: XPath と LINQ to XML の比較 - LINQ to XML
description: XPath と LINQ to XML のクエリはどちらも XML ツリーに対してクエリを実行できます。 この記事では、2 つのオプションを比較し、全体として LINQ to XML クエリの方が、より強力で、汎用性が高く、高速で、安全性が高く、より便利な選択肢であることを確認します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412034"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="1c3bc-104">XPath と LINQ to XML の比較</span><span class="sxs-lookup"><span data-stu-id="1c3bc-104">Comparison of XPath and LINQ to XML</span></span>

<span data-ttu-id="1c3bc-105">XPath と LINQ to XML は、いくつかの点で似ています。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-105">XPath and LINQ to XML are similar in some ways.</span></span> <span data-ttu-id="1c3bc-106">どちらも XML ツリーに対してクエリを実行するために使用され、結果として、要素のコレクション、属性のコレクション、ノードのコレクション、要素や属性の値などを返します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="1c3bc-107">ただし、この 2 つのオプションには、大きな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-107">However, there are significant differences between the two options.</span></span>

## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="1c3bc-108">XPath と LINQ to XML の違い</span><span class="sxs-lookup"><span data-stu-id="1c3bc-108">Differences between XPath and LINQ to XML</span></span>

<span data-ttu-id="1c3bc-109">XPath では、新しい型を射影できません。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-109">XPath doesn't allow projection of new types.</span></span> <span data-ttu-id="1c3bc-110">XPath では、ツリーからノードのコレクションが返されるだけですが、LINQ to XML では、クエリを実行し、オブジェクト グラフまたは XML ツリーを新しい構造に射影できます。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="1c3bc-111">LINQ to XML クエリは、XPath 式よりもはるかに多くのことができます。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-111">LINQ to XML queries can do much more than XPath expressions.</span></span>

<span data-ttu-id="1c3bc-112">XPath 式は、文字列内に独立して存在します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="1c3bc-113">C# コンパイラは、コンパイル時に XPath 式を解析できません。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-113">The C# compiler can't help parse the XPath expression at compile time.</span></span> <span data-ttu-id="1c3bc-114">一方 LINQ to XML クエリは、C# コンパイラによって解析され、コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="1c3bc-115">コンパイラによって、多くのクエリ エラーをキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-115">The compiler can catch many query errors.</span></span>

<span data-ttu-id="1c3bc-116">XPath の結果は厳密に型指定されません。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-116">XPath results aren't strongly typed.</span></span> <span data-ttu-id="1c3bc-117">多くの場合、XPath 式を評価した結果はオブジェクトであり、開発者が適切な型を決定し、必要に応じて結果をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it's up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="1c3bc-118">一方、LINQ to XML クエリからの射影は厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>

## <a name="result-ordering"></a><span data-ttu-id="1c3bc-119">結果の順序付け</span><span class="sxs-lookup"><span data-stu-id="1c3bc-119">Result ordering</span></span>

<span data-ttu-id="1c3bc-120">XPath 1.0 勧告には、XPath 式の評価結果であるコレクションは順序付けされないことが記載されています。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-120">The XPath 1.0 Recommendation states that a collection that's the result of evaluating an XPath expression is unordered.</span></span>

<span data-ttu-id="1c3bc-121">ただし、LINQ to XML の XPath 軸メソッドから返されるコレクションを反復処理すると、コレクション内のノードがドキュメント順に返されます。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="1c3bc-122">これは、ドキュメントの逆順として述語が表現されている `preceding` や `preceding-sibling` などの XPath 軸にアクセスする場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>

<span data-ttu-id="1c3bc-123">これに対し、LINQ to XML 軸のほとんどは、ドキュメント順にコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-123">By contrast, most of the LINQ to XML axes return collections in document order.</span></span> <span data-ttu-id="1c3bc-124">ただし、これらのうち 2 つ (<xref:System.Xml.Linq.XNode.Ancestors%2A> と <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>) は、ドキュメントの逆順でコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-124">However, two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="1c3bc-125">次の表では、軸を列挙し、それぞれのコレクションの順序を示します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-125">The following table enumerates the axes, and indicates the collection order for each:</span></span>

|<span data-ttu-id="1c3bc-126">LINQ to XML 軸</span><span class="sxs-lookup"><span data-stu-id="1c3bc-126">LINQ to XML axis</span></span>|<span data-ttu-id="1c3bc-127">並べ替え</span><span class="sxs-lookup"><span data-stu-id="1c3bc-127">Ordering</span></span>|
|----------------------|--------------|
|<span data-ttu-id="1c3bc-128">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="1c3bc-128">XContainer.DescendantNodes</span></span>|<span data-ttu-id="1c3bc-129">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-129">Document order</span></span>|
|<span data-ttu-id="1c3bc-130">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="1c3bc-130">XContainer.Descendants</span></span>|<span data-ttu-id="1c3bc-131">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-131">Document order</span></span>|
|<span data-ttu-id="1c3bc-132">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="1c3bc-132">XContainer.Elements</span></span>|<span data-ttu-id="1c3bc-133">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-133">Document order</span></span>|
|<span data-ttu-id="1c3bc-134">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="1c3bc-134">XContainer.Nodes</span></span>|<span data-ttu-id="1c3bc-135">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-135">Document order</span></span>|
|<span data-ttu-id="1c3bc-136">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-136">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="1c3bc-137">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-137">Document order</span></span>|
|<span data-ttu-id="1c3bc-138">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-138">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="1c3bc-139">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-139">Document order</span></span>|
|<span data-ttu-id="1c3bc-140">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-140">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="1c3bc-141">ドキュメントの逆順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-141">Reverse document order</span></span>|
|<span data-ttu-id="1c3bc-142">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="1c3bc-142">XElement.Attributes</span></span>|<span data-ttu-id="1c3bc-143">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-143">Document order</span></span>|
|<span data-ttu-id="1c3bc-144">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-144">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="1c3bc-145">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-145">Document order</span></span>|
|<span data-ttu-id="1c3bc-146">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-146">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="1c3bc-147">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-147">Document order</span></span>|
|<span data-ttu-id="1c3bc-148">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="1c3bc-148">XNode.Ancestors</span></span>|<span data-ttu-id="1c3bc-149">ドキュメントの逆順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-149">Reverse document order</span></span>|
|<span data-ttu-id="1c3bc-150">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-150">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="1c3bc-151">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-151">Document order</span></span>|
|<span data-ttu-id="1c3bc-152">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-152">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="1c3bc-153">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-153">Document order</span></span>|
|<span data-ttu-id="1c3bc-154">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-154">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="1c3bc-155">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-155">Document order</span></span>|
|<span data-ttu-id="1c3bc-156">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="1c3bc-156">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="1c3bc-157">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="1c3bc-157">Document order</span></span>|

## <a name="positional-predicates"></a><span data-ttu-id="1c3bc-158">位置述語</span><span class="sxs-lookup"><span data-stu-id="1c3bc-158">Positional predicates</span></span>

<span data-ttu-id="1c3bc-159">XPath 式では、多くの軸で位置述語がドキュメント順として表現されますが、逆方向軸の場合は、ドキュメントの逆順で表現されます。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-159">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes.</span></span> <span data-ttu-id="1c3bc-160">逆方向軸は、`preceding`、`preceding-sibling`、`ancestor`、`ancestor-or-self` です。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-160">The reverse axes are: `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="1c3bc-161">たとえば、XPath 式 `preceding-sibling::*[1]` は、直前の兄弟を返します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-161">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="1c3bc-162">これは、最終的な結果セットがドキュメント順で表される場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-162">This is the case even though the final result set is presented in document order.</span></span>

<span data-ttu-id="1c3bc-163">一方、LINQ to XML の位置述語は、常に軸の順序として表現されます。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-163">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="1c3bc-164">たとえば、`anElement.ElementsBeforeSelf().ElementAt(0)` は、直前の兄弟ではなく、クエリされる要素の親の最初の子要素を返します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-164">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="1c3bc-165">別の例として、`anElement.Ancestors().ElementAt(0)` は親要素を返します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-165">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>

<span data-ttu-id="1c3bc-166">LINQ to XML で直前の要素を検索する場合は、次の式を記述します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-166">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a><span data-ttu-id="1c3bc-167">パフォーマンスの違い</span><span class="sxs-lookup"><span data-stu-id="1c3bc-167">Performance differences</span></span>

<span data-ttu-id="1c3bc-168">LINQ to XML 内の XPath 機能を使用する XPath クエリは、LINQ to XML クエリよりも遅くなります。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-168">XPath queries that use the XPath functionality in LINQ to XML will be slower than LINQ to XML queries.</span></span>

## <a name="comparison-of-composition"></a><span data-ttu-id="1c3bc-169">構成の比較</span><span class="sxs-lookup"><span data-stu-id="1c3bc-169">Comparison of composition</span></span>

<span data-ttu-id="1c3bc-170">LINQ to XML クエリの構成は、XPath 式の構成に似ていますが、構文は大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-170">Composition of a LINQ to XML query is similar to composition of an XPath expression, but the syntax is very different.</span></span>

<span data-ttu-id="1c3bc-171">たとえば、`customers` という変数に要素があり、`Customer` というすべての子要素の下で `CompanyName` という孫要素を検索する場合は、次のようにこの XPath 式を記述します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-171">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write this XPath expression:</span></span>

```csharp
customers.XPathSelectElements("./Customer/CompanyName")
```

```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

<span data-ttu-id="1c3bc-172">同等の LINQ to XML クエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-172">The equivalent LINQ to XML query is:</span></span>

```csharp
customers.Elements("Customer").Elements("CompanyName")
```

```vb
customers.Elements("Customer").Elements("CompanyName")
```

<span data-ttu-id="1c3bc-173">同様の対応関係が XPath 軸ごとに存在します。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-173">There are similar parallels for each of the XPath axes.</span></span>

|<span data-ttu-id="1c3bc-174">XPath 軸</span><span class="sxs-lookup"><span data-stu-id="1c3bc-174">XPath axis</span></span>|<span data-ttu-id="1c3bc-175">LINQ to XML 軸</span><span class="sxs-lookup"><span data-stu-id="1c3bc-175">LINQ to XML axis</span></span>|
|----------------|----------------------|
|<span data-ttu-id="1c3bc-176">child (既定の軸)</span><span class="sxs-lookup"><span data-stu-id="1c3bc-176">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-177">Parent (..)</span><span class="sxs-lookup"><span data-stu-id="1c3bc-177">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-178">attribute 軸 (@)</span><span class="sxs-lookup"><span data-stu-id="1c3bc-178">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1c3bc-179">or</span><span class="sxs-lookup"><span data-stu-id="1c3bc-179">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-180">ancestor 軸</span><span class="sxs-lookup"><span data-stu-id="1c3bc-180">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-181">ancestor-or-self 軸</span><span class="sxs-lookup"><span data-stu-id="1c3bc-181">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-182">descendant 軸 (//)</span><span class="sxs-lookup"><span data-stu-id="1c3bc-182">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1c3bc-183">、または</span><span class="sxs-lookup"><span data-stu-id="1c3bc-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-184">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="1c3bc-184">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1c3bc-185">、または</span><span class="sxs-lookup"><span data-stu-id="1c3bc-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-186">following-sibling</span><span class="sxs-lookup"><span data-stu-id="1c3bc-186">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1c3bc-187">、または</span><span class="sxs-lookup"><span data-stu-id="1c3bc-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-188">preceding-sibling</span><span class="sxs-lookup"><span data-stu-id="1c3bc-188">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="1c3bc-189">or</span><span class="sxs-lookup"><span data-stu-id="1c3bc-189">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1c3bc-190">following</span><span class="sxs-lookup"><span data-stu-id="1c3bc-190">following</span></span>|<span data-ttu-id="1c3bc-191">同等の軸はありません。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-191">No direct equivalent.</span></span>|
|<span data-ttu-id="1c3bc-192">preceding</span><span class="sxs-lookup"><span data-stu-id="1c3bc-192">preceding</span></span>|<span data-ttu-id="1c3bc-193">同等の軸はありません。</span><span class="sxs-lookup"><span data-stu-id="1c3bc-193">No direct equivalent.</span></span>|
