---
title: メモリ内の XML ツリーの変更と関数型構築の比較 - LINQ to XML
description: XML ツリーを変更する 2 つの別の方法の例について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103411966"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a><span data-ttu-id="00094-103">メモリ内の XML ツリーの変更と関数型構築の比較 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="00094-103">In-memory XML tree modification vs. functional construction (LINQ to XML)</span></span>

<span data-ttu-id="00094-104">XML ドキュメントの構造を変更する場合は、XML ツリーを直接変更するのが従来の方法です。</span><span class="sxs-lookup"><span data-stu-id="00094-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="00094-105">一般的なアプリケーションでは、ドキュメントを DOM や LINQ to XML などのデータ ストアに読み込み、プログラミング インターフェイスを使用してノードを挿入、削除、またはその内容を変更し、その後に XML をファイルに保存するか、それをネットワーク上で送信します。</span><span class="sxs-lookup"><span data-stu-id="00094-105">A typical application loads a document into a data store such as DOM or LINQ to XML; uses a programming interface to insert or delete nodes, or change their content; and then saves the XML to a file or transmits it over a network.</span></span>

<span data-ttu-id="00094-106">LINQ to XML には、もう 1 つ、多数のシナリオで役立つ "*関数型構築*" という方法があります。</span><span class="sxs-lookup"><span data-stu-id="00094-106">LINQ to XML enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="00094-107">関数型構築では、データの変更が、データ ストアの詳細な操作としてではなく変換の問題として扱われます。</span><span class="sxs-lookup"><span data-stu-id="00094-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="00094-108">データの表現をある形式から別の形式に効率よく変換できれば、データ ストアを何らかの方法で操作して別の構造にする場合と同じ結果を得られます。</span><span class="sxs-lookup"><span data-stu-id="00094-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="00094-109">関数型構築の方法で重要なのは、クエリの結果を <xref:System.Xml.Linq.XDocument> コンストラクターと <xref:System.Xml.Linq.XElement> コンストラクターに渡す処理です。</span><span class="sxs-lookup"><span data-stu-id="00094-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>

<span data-ttu-id="00094-110">多くの場合、変換コードは、データ ストアを操作する場合に比べてわずかな時間で作成でき、その結果のコードはより堅牢で保守性に優れています。</span><span class="sxs-lookup"><span data-stu-id="00094-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and the resulting code is more robust and easier to maintain.</span></span> <span data-ttu-id="00094-111">この場合、変換する方法では、より大きな処理能力を必要とする可能性はありますが、より効率的にデータを変更できます。</span><span class="sxs-lookup"><span data-stu-id="00094-111">In these cases, even though the transformational approach can take more processing power, it's a more effective way to modify data.</span></span> <span data-ttu-id="00094-112">開発者が関数型の方法に精通していれば、多くの場合、結果として得られるコードは理解しやすく、ツリーの各部分を変更するコードを簡単に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="00094-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand, and it's easy to find the code that modifies each part of the tree.</span></span>

<span data-ttu-id="00094-113">DOM プログラマの多くは、XML ツリーを直接変更する方法に慣れています。これに対し、関数型の方法で記述されたコードは、それをまだ理解していない開発者とっては、なじみのないものです。</span><span class="sxs-lookup"><span data-stu-id="00094-113">The approach where you modify an XML tree in place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="00094-114">大きな XML ツリーに小さな変更を加えるだけであれば、ツリーを直接変更する方法の方が使用する CPU 時間が少ない場合がほとんどです。</span><span class="sxs-lookup"><span data-stu-id="00094-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>

<span data-ttu-id="00094-115">この記事では、両方の方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="00094-115">This article provides examples of both approaches.</span></span> <span data-ttu-id="00094-116">属性が要素となるように、次の単純な XML ドキュメントを変更したいとします。</span><span class="sxs-lookup"><span data-stu-id="00094-116">Suppose you want to modify the following simple XML document so that the attributes become elements:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

<span data-ttu-id="00094-117">次の最初の例では、従来の直接変更する方法を使用し、2 番目の例では関数型構築の方法を使用しています。</span><span class="sxs-lookup"><span data-stu-id="00094-117">The first of the following examples uses the traditional in-place modification approach, and the second uses the functional construction approach.</span></span>

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a><span data-ttu-id="00094-118">例: 従来の直接の方法を使用して属性を要素に変換する</span><span class="sxs-lookup"><span data-stu-id="00094-118">Example: Transform attributes into elements with the traditional in-place approach</span></span>

<span data-ttu-id="00094-119">属性から要素を作成した後に属性を削除する、次のようなプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="00094-119">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

<span data-ttu-id="00094-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="00094-120">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a><span data-ttu-id="00094-121">例: 関数型構築方法を使用して属性を要素に変換する</span><span class="sxs-lookup"><span data-stu-id="00094-121">Example: Transform attributes into elements with the functional construction approach</span></span>

<span data-ttu-id="00094-122">対照的に、関数型の方法のコードでは、新しいツリーを作成し、ソース ツリーから要素と属性を選択し、その要素と属性を新しいツリーに追加するときに適宜変換します。</span><span class="sxs-lookup"><span data-stu-id="00094-122">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they're added to the new tree.</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

<span data-ttu-id="00094-123">この例では、最初の例と同じ XML が出力されます。</span><span class="sxs-lookup"><span data-stu-id="00094-123">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="00094-124">ただし、関数型の方法では、新しい XML の構造が実際に作成されます。</span><span class="sxs-lookup"><span data-stu-id="00094-124">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="00094-125">`Root` 要素、ソース ツリーから `Child1` 要素を取り出すコード、およびソース ツリーから取得した属性を新しいツリーの要素に変換するコードが作成されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="00094-125">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>

<span data-ttu-id="00094-126">ここで示した関数型の例は、最初の例と比べて短くも、単純でもありません。</span><span class="sxs-lookup"><span data-stu-id="00094-126">The functional example in this case is neither shorter nor simpler than the first example.</span></span> <span data-ttu-id="00094-127">しかし XML ツリーに多数の変更を加える場合、手続き型の方法はかなり複雑で、効率的ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="00094-127">However, if you have many changes to make to an XML tree, the procedural approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="00094-128">一方、関数型の方法では、クエリと式を適宜組み込んだ必要な XML を作成するだけで、必要な内容を取り出せます。</span><span class="sxs-lookup"><span data-stu-id="00094-128">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="00094-129">関数型の方法で生成されたコードの方が、保守も簡単です。</span><span class="sxs-lookup"><span data-stu-id="00094-129">The functional approach yields code that is easier to maintain.</span></span>

<span data-ttu-id="00094-130">この例では、ツリーを操作する方法に比べて関数型の方法のパフォーマンスが低くなる可能性があるので注意してください。</span><span class="sxs-lookup"><span data-stu-id="00094-130">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="00094-131">主な問題は、関数型の方法では存続期間の短いオブジェクトがより多く作成されることです。</span><span class="sxs-lookup"><span data-stu-id="00094-131">The main issue is that the functional approach creates more short-lived objects.</span></span> <span data-ttu-id="00094-132">その代わりに、関数型の方法の方がプログラマの生産性が高いという効果があります。</span><span class="sxs-lookup"><span data-stu-id="00094-132">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>

<span data-ttu-id="00094-133">ここで示したのはごく単純な例ですが、2 つの方法に関する考え方の違いをよく表しています。</span><span class="sxs-lookup"><span data-stu-id="00094-133">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="00094-134">大きな XML ドキュメントを変換する場合は、関数型の方法を使用した方が生産性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="00094-134">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>
