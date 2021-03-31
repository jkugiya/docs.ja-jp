---
title: 宣言型と命令型のコードの混在時のバグ - LINQ to XML
description: コードで 1 つの軸が反復処理されるときに発生するおそれのある問題を把握し、回避する方法について説明します。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fada62d0-0680-4e73-945a-2b00d7a507af
ms.openlocfilehash: 280bb62d15ff28d1fd09ca2d0c52c0a0c36d7282
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "103412011"
---
# <a name="mixed-declarativeimperative-code-bugs-linq-to-xml"></a><span data-ttu-id="9e83d-103">宣言型と命令型のコードの混在時のバグ (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9e83d-103">Mixed declarative/imperative code bugs (LINQ to XML)</span></span>

<span data-ttu-id="9e83d-104">LINQ to XML には、XML ツリーを直接変更する方法が多数あります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-104">LINQ to XML contains various methods that allow you to modify an XML tree directly.</span></span> <span data-ttu-id="9e83d-105">たとえば、要素の追加、要素の削除、要素の内容の変更、属性の追加などの操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-105">You can add elements, delete elements, change the contents of an element, add attributes, and so on.</span></span> <span data-ttu-id="9e83d-106">このプログラミング インターフェイスについては、[XML ツリーの変更](in-memory-xml-tree-modification-vs-functional-construction.md)に関するページで説明しています。</span><span class="sxs-lookup"><span data-stu-id="9e83d-106">This programming interface is described in [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span> <span data-ttu-id="9e83d-107">いずれかの軸 (<xref:System.Xml.Linq.XContainer.Elements%2A> など) を反復処理する場合に、その過程で XML ツリーを変更すると、見慣れないバグが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-107">If you're iterating through one of the axes, such as <xref:System.Xml.Linq.XContainer.Elements%2A>, and you're modifying the XML tree as you iterate through the axis, you can end up with some strange bugs.</span></span>

<span data-ttu-id="9e83d-108">この問題は、"ハロウィーン問題" と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-108">This problem is sometimes known as "The Halloween Problem".</span></span>

<span data-ttu-id="9e83d-109">コレクションを反復処理するコードを LINQ を使用して記述する場合は、宣言型スタイルでコードを記述することになります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-109">When you write some code using LINQ that iterates through a collection, you're writing code in a declarative style.</span></span> <span data-ttu-id="9e83d-110">この場合、"*どのように*" 処理するかではなく、"*何が*" 必要かを記述します。</span><span class="sxs-lookup"><span data-stu-id="9e83d-110">It's more akin to describing *what* you want, rather that *how* you want to get it done.</span></span> <span data-ttu-id="9e83d-111">たとえば、1) 最初の要素を取得する、2) この要素を何らかの条件に対してテストする、3) この要素を変更する、4) この要素をリストに戻す、というコードを記述した場合、それは命令型のコードです。</span><span class="sxs-lookup"><span data-stu-id="9e83d-111">If you write code that 1) gets the first element, 2) tests it for some condition, 3) modifies it, and 4) puts it back into the list, then this would be imperative code.</span></span> <span data-ttu-id="9e83d-112">コンピューターに、必要な処理を "*どのように*" 行うかを指示します。</span><span class="sxs-lookup"><span data-stu-id="9e83d-112">You're telling the computer *how* to do what you want done.</span></span>

<span data-ttu-id="9e83d-113">この 2 つのスタイルのコードが同じ操作に混在していると、問題の原因になります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-113">Mixing these styles of code in the same operation is what leads to problems.</span></span> <span data-ttu-id="9e83d-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9e83d-114">Consider the following:</span></span>

<span data-ttu-id="9e83d-115">3 つの項目 (a、b、および c) を含むリンク リストがあるとします。</span><span class="sxs-lookup"><span data-stu-id="9e83d-115">Suppose you have a linked list with three items in it (a, b, and c):</span></span>

> <span data-ttu-id="9e83d-116">a -> b -> c</span><span class="sxs-lookup"><span data-stu-id="9e83d-116">a -> b -> c</span></span>

<span data-ttu-id="9e83d-117">このリンク リスト内を移動しながら 3 つの新しい項目 (a'、b'、および c') を追加して、</span><span class="sxs-lookup"><span data-stu-id="9e83d-117">Now, suppose that you want to move through the linked list, adding three new items (a', b', and c').</span></span> <span data-ttu-id="9e83d-118">次のようなリンク リストが生成されるようにします。</span><span class="sxs-lookup"><span data-stu-id="9e83d-118">You want the resulting linked list to look like this:</span></span>

 > <span data-ttu-id="9e83d-119">a -> a' -> b -> b' -> c -> c'</span><span class="sxs-lookup"><span data-stu-id="9e83d-119">a -> a' -> b -> b' -> c -> c'</span></span>

<span data-ttu-id="9e83d-120">ここで、リストを反復処理して各項目の後ろに新しいアイテムを追加するコードを記述した場合、</span><span class="sxs-lookup"><span data-stu-id="9e83d-120">So you write code that iterates through the list, and for every item, adds a new item right after it.</span></span> <span data-ttu-id="9e83d-121">その結果は、コードによって最初に `a` 要素が検出され、その後ろに `a'` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-121">What happens is that your code will first see the `a` element, and insert `a'` after it.</span></span> <span data-ttu-id="9e83d-122">これで、お使いのコードは現在は `a'` のリストの次のノードに移動します。つまり、リストの a' と b の間に新しい項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-122">Now, your code will move to the next node in the list, which is now `a'`, so it adds a new item between a' and b to the list!</span></span>

<span data-ttu-id="9e83d-123">これを解決するにはどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="9e83d-123">How would you solve this?</span></span> <span data-ttu-id="9e83d-124">まず、元のリンク リストをコピーして、まったく新しいリストを作成する方法が考えられます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-124">Well, you might make a copy of the original linked list, and create a completely new list.</span></span> <span data-ttu-id="9e83d-125">また、純粋な命令型のコードを記述するのであれば、最初の項目を検出し、新しい項目を追加したら、リンク リストの 2 つ先 (追加した要素を越えた先) に移動するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-125">Or if you're writing purely imperative code, you might find the first item, add the new item, and then advance twice in the linked list, advancing over the element that you just added.</span></span>

## <a name="example-adding-while-iterating"></a><span data-ttu-id="9e83d-126">例: 反復処理しながら追加する</span><span class="sxs-lookup"><span data-stu-id="9e83d-126">Example: Adding while iterating</span></span>

<span data-ttu-id="9e83d-127">たとえば、次のように、ツリーのすべての要素の複製を作成するコードを記述したいとします。</span><span class="sxs-lookup"><span data-stu-id="9e83d-127">For example, suppose you want to write code to create a duplicate of every element in a tree:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    root.Add(new XElement(e.Name, (string)e));
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    root.Add(New XElement(e.Name, e.Value))
Next
```

<span data-ttu-id="9e83d-128">このコードは、無限ループに入ります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-128">This code goes into an infinite loop.</span></span> <span data-ttu-id="9e83d-129">`foreach` ステートメントは、`Elements()` 軸を反復処理して `doc` 要素に新しい要素を追加しますが、</span><span class="sxs-lookup"><span data-stu-id="9e83d-129">The `foreach` statement iterates through the `Elements()` axis, adding new elements to the `doc` element.</span></span> <span data-ttu-id="9e83d-130">追加した要素も反復処理されることになります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-130">It ends up iterating also through the elements it just added.</span></span> <span data-ttu-id="9e83d-131">ループが繰り返されるたびに新しいオブジェクトが割り当てられるため、最後には使用可能なメモリがすべて消費されてしまいます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-131">And because it allocates new objects with every iteration of the loop, it will eventually consume all available memory.</span></span>

<span data-ttu-id="9e83d-132">この問題を修正するには、次のように、標準クエリ演算子の <xref:System.Linq.Enumerable.ToList%2A> を使用してコレクションをメモリに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-132">You can fix this problem by pulling the collection into memory using the <xref:System.Linq.Enumerable.ToList%2A> standard query operator, as follows:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    root.Add(new XElement(e.Name, (string)e));
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    root.Add(New XElement(e.Name, e.Value))
Next
Console.WriteLine(root)
```

<span data-ttu-id="9e83d-133">これで、コードが機能するようになります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-133">Now the code works.</span></span> <span data-ttu-id="9e83d-134">結果の XML ツリーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-134">The resulting XML tree is the following:</span></span>

```xml
<Root>
  <A>1</A>
  <B>2</B>
  <C>3</C>
  <A>1</A>
  <B>2</B>
  <C>3</C>
</Root>
```

## <a name="example-deleting-while-iterating"></a><span data-ttu-id="9e83d-135">例: 反復処理しながら削除する</span><span class="sxs-lookup"><span data-stu-id="9e83d-135">Example: Deleting while iterating</span></span>

<span data-ttu-id="9e83d-136">特定のレベルのノードをすべて削除する場合、次のようなコードを記述することが考えられます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-136">If you want to delete all nodes at a certain level, you might be tempted to write code like the following:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements()
    e.Remove()
Next
Console.WriteLine(root)
```

<span data-ttu-id="9e83d-137">しかし、これでは目的の処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="9e83d-137">However, this doesn't do what you want.</span></span> <span data-ttu-id="9e83d-138">この場合、最初の要素 A を削除すると、ルートに含まれる XML ツリーから削除され、反復処理を行っている Elements メソッド内のコードが次の要素を見つけられなくなります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-138">In this situation, after you've removed the first element, A, it's removed from the XML tree contained in root, and the code in the Elements method that does the iterating can't find the next element.</span></span>

<span data-ttu-id="9e83d-139">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-139">This example produces the following output:</span></span>

```xml
<Root>
  <B>2</B>
  <C>3</C>
</Root>
```

<span data-ttu-id="9e83d-140">この問題を解決するには、先ほどと同じように、<xref:System.Linq.Enumerable.ToList%2A> を呼び出してコレクションを具体化します。</span><span class="sxs-lookup"><span data-stu-id="9e83d-140">The solution again is to call <xref:System.Linq.Enumerable.ToList%2A> to materialize the collection, as follows:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
foreach (XElement e in root.Elements().ToList())
    e.Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
For Each e As XElement In root.Elements().ToList()
    e.Remove()
Next
Console.WriteLine(root)
```

<span data-ttu-id="9e83d-141">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-141">This example produces the following output:</span></span>

```xml
<Root />
```

<span data-ttu-id="9e83d-142">他の方法として、親要素で <xref:System.Xml.Linq.XElement.RemoveAll%2A> を呼び出して、反復処理を完全に取り除くこともできます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-142">Alternatively, you can eliminate the iteration altogether by calling <xref:System.Xml.Linq.XElement.RemoveAll%2A> on the parent element:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
root.RemoveAll();
Console.WriteLine(root);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
root.RemoveAll()
Console.WriteLine(root)
```

## <a name="example-why-linq-cant-automatically-handle-these-issues"></a><span data-ttu-id="9e83d-143">例: LINQ がこれらの問題を自動的に処理できない理由</span><span class="sxs-lookup"><span data-stu-id="9e83d-143">Example: Why LINQ can't automatically handle these issues</span></span>

<span data-ttu-id="9e83d-144">まず、レイジー評価を行う代わりに常にすべてをメモリに読み込む方法が考えられます。</span><span class="sxs-lookup"><span data-stu-id="9e83d-144">One approach would be to always bring everything into memory instead of doing lazy evaluation.</span></span> <span data-ttu-id="9e83d-145">しかし、この方法では、パフォーマンスとメモリ使用量のコストが非常に高くなります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-145">However, it would be very expensive in terms of performance and memory use.</span></span> <span data-ttu-id="9e83d-146">実際、LINQ および LINQ to XML でこの方法を使用したとしても、現実には使いものにならないでしょう。</span><span class="sxs-lookup"><span data-stu-id="9e83d-146">In fact, if LINQ, and LINQ to XML, were to take this approach, it would fail in real-world situations.</span></span>

<span data-ttu-id="9e83d-147">その他に、ある種のトランザクション構文を LINQ に追加して、特定のコレクションを具体化する必要があるかどうかをコンパイラにコードを分析させ判断させる方法があります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-147">Another possible approach would be to put some sort of transaction syntax into LINQ, and have the compiler attempt to analyze the code to determine if any particular collection needed to be materialized.</span></span> <span data-ttu-id="9e83d-148">しかし、副作用のあるコードをすべて特定しようとすると非常に複雑になります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-148">However, attempting to determine all code that has side-effects is incredibly complex.</span></span> <span data-ttu-id="9e83d-149">次のコードがあるとします。</span><span class="sxs-lookup"><span data-stu-id="9e83d-149">Consider the following code:</span></span>

```csharp
var z =
    from e in root.Elements()
    where TestSomeCondition(e)
    select DoMyProjection(e);
```

```vb
Dim z = _
    From e In root.Elements() _
    Where (TestSomeCondition(e)) _
    Select DoMyProjection(e)
```

<span data-ttu-id="9e83d-150">このような分析コードで副作用のあるコードの有無を特定するには、TestSomeCondition および DoMyProjection の 2 つのメソッドと、これらが呼び出すすべてのメソッドを分析する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-150">Such analysis code would need to analyze the methods TestSomeCondition and DoMyProjection, and all methods that those methods called, to determine if any code had side-effects.</span></span> <span data-ttu-id="9e83d-151">しかし、その分析コードでは、ただ副作用のあるコードを探すだけでなく、</span><span class="sxs-lookup"><span data-stu-id="9e83d-151">But the analysis code could not just look for any code that had side-effects.</span></span> <span data-ttu-id="9e83d-152">この状況では、`root` の子要素に対して副作用があるコードのみを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-152">It would need to select for just the code that had side-effects on the child elements of `root` in this situation.</span></span>

<span data-ttu-id="9e83d-153">LINQ to XML ではこのような分析は行いません。</span><span class="sxs-lookup"><span data-stu-id="9e83d-153">LINQ to XML doesn't attempt to do any such analysis.</span></span> <span data-ttu-id="9e83d-154">これらの問題は、自分で回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-154">It's up to you to avoid these problems.</span></span>

## <a name="example-use-declarative-code-to-generate-a-new-xml-tree-rather-than-modify-the-existing-tree"></a><span data-ttu-id="9e83d-155">例: 既存のツリーを変更するのではなく、宣言型コードを使用して新しい XML ツリーを生成する</span><span class="sxs-lookup"><span data-stu-id="9e83d-155">Example: Use declarative code to generate a new XML tree rather than modify the existing tree</span></span>

<span data-ttu-id="9e83d-156">このような問題を回避するには、お使いのコレクションのセマンティクスと XML ツリーを変更するメソッドのセマンティクスを正確に把握している場合でも、宣言型と命令型のコードを混在させないでください。</span><span class="sxs-lookup"><span data-stu-id="9e83d-156">To avoid such problems, don't mix declarative and imperative code, even if you know exactly the semantics of your collections and the semantics of the methods that modify the XML tree.</span></span> <span data-ttu-id="9e83d-157">問題を回避するコードを記述した場合でも、今後、その問題を明確に把握していない他の開発者が自分のコードを管理することになります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-157">If you write code that avoids problems, your code will need to be maintained by other developers in the future, and they may not be as clear on the issues.</span></span> <span data-ttu-id="9e83d-158">宣言型と命令型のコーディング スタイルが混在していると、コードが不安定になります。</span><span class="sxs-lookup"><span data-stu-id="9e83d-158">If you mix declarative and imperative coding styles, your code will be more brittle.</span></span>  <span data-ttu-id="9e83d-159">これらの問題を回避するためにコレクションを具体化するコードを記述する場合は、コードを保守するプログラマが問題を把握できるように、必要に応じてコメントを付けるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9e83d-159">If you write code that materializes a collection so that these problems are avoided, note it with comments as appropriate in your code, so that maintenance programmers will understand the issue.</span></span>

<span data-ttu-id="9e83d-160">パフォーマンスやその他の事情が許すのであれば、宣言型のコードのみを使用するようにします。</span><span class="sxs-lookup"><span data-stu-id="9e83d-160">If performance and other considerations allow, use only declarative code.</span></span> <span data-ttu-id="9e83d-161">既存の XML ツリーは変更せずに、</span><span class="sxs-lookup"><span data-stu-id="9e83d-161">Don't modify your existing XML tree.</span></span> <span data-ttu-id="9e83d-162">代わりに、次の例のとおり新しいものを生成します。</span><span class="sxs-lookup"><span data-stu-id="9e83d-162">Instead, generate a new one as shown in the following example:</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("A", "1"),
    new XElement("B", "2"),
    new XElement("C", "3")
);
XElement newRoot = new XElement("Root",
    root.Elements(),
    root.Elements()
);
Console.WriteLine(newRoot);
```

```vb
Dim root As XElement = _
    <Root>
        <A>1</A>
        <B>2</B>
        <C>3</C>
    </Root>
Dim newRoot As XElement = New XElement("Root", _
    root.Elements(), root.Elements())
Console.WriteLine(newRoot)
```
