---
description: '詳細情報: 方法:LINQ クエリのカスタム メソッドを追加する (Visual Basic)'
title: '方法: LINQ クエリのカスタム メソッドを追加する'
ms.date: 08/28/2020
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 62acf22a8be9986388233ee34121a97d65a87f43
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424529"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="8fa3d-103">方法: LINQ クエリのカスタム メソッドを追加する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8fa3d-103">How to: Add custom methods for LINQ queries (Visual Basic)</span></span>

<span data-ttu-id="8fa3d-104"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加することで、LINQ クエリに使用するメソッド セットを拡張します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-104">You extend the set of methods that you use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="8fa3d-105">たとえば、一連の値から単一の値を計算するために、平均や最大を求める標準的な演算に加えて、カスタムの集計メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-105">For example, in addition to the standard average or maximum operations, you create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="8fa3d-106">また、一連の値を受け取って新しい一連の値を返す特定のデータ変換やカスタム フィルターとして動作するメソッドも作成します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-106">You also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="8fa3d-107">このようなメソッドには、<xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A>、<xref:System.Linq.Enumerable.Reverse%2A> があります。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-107">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="8fa3d-108"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスを拡張すると、列挙可能なコレクションにカスタム メソッドを適用できます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-108">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="8fa3d-109">詳細については、「[拡張メソッド](../../language-features/procedures/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-109">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="8fa3d-110">集計メソッドを追加する</span><span class="sxs-lookup"><span data-stu-id="8fa3d-110">Adding an aggregate method</span></span>

<span data-ttu-id="8fa3d-111">集計メソッドは、一連の値から単一の値を計算するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-111">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="8fa3d-112">LINQ は、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Max%2A> などの集計メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-112">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="8fa3d-113"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスに拡張メソッドを追加することで、独自の集計メソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-113">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="8fa3d-114">次のコード例は、`double` 型の一連の数値から中央値を求める `Median` という拡張メソッドの作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-114">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

:::code language="vb" source="./snippets/LinqExtension.vb" :::

<span data-ttu-id="8fa3d-115">この拡張メソッドは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにある他の集計メソッドを呼び出すときと同じように、列挙可能な任意のコレクションに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-115">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="8fa3d-116">Visual Basic では、`Aggregate` 句または `Group By` 句の代わりに、メソッド呼び出しまたは標準クエリ構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-116">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="8fa3d-117">詳細については、「[Aggregate 句](../../../language-reference/queries/aggregate-clause.md)」および「[Group By 句](../../../language-reference/queries/group-by-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-117">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="8fa3d-118">`double` 型の配列に対して `Median` メソッドを使用する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-118">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="8fa3d-119">さまざまな型を受け取るために集計メソッドをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="8fa3d-119">Overloading an aggregate method to accept various types</span></span>

<span data-ttu-id="8fa3d-120">集計メソッドでさまざまな型を受け取るように、集計メソッドをオーバーロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-120">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="8fa3d-121">その標準的な方法として、型ごとにオーバーロードを作成します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-121">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="8fa3d-122">または、ジェネリック型を受け取り、デリゲートを使って特定の型に変換するオーバーロードを作成する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-122">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="8fa3d-123">その両方の方法を組み合わせることもできます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-123">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="8fa3d-124">型ごとにオーバーロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="8fa3d-124">To create an overload for each type</span></span>

<span data-ttu-id="8fa3d-125">サポート予定の型ごとに固有のオーバーロードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-125">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="8fa3d-126">次のコード例では、`integer` 型の `Median` メソッドのオーバーロードを示します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-126">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="IntOverload":::

<span data-ttu-id="8fa3d-127">これで、次のコードに示すように、`integer` 型と `double` 型の両方に対して、`Median` のオーバーロードを呼び出すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-127">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="8fa3d-128">ジェネリック オーバーロードを作成するには</span><span class="sxs-lookup"><span data-stu-id="8fa3d-128">To create a generic overload</span></span>

<span data-ttu-id="8fa3d-129">一連のジェネリック オブジェクトを受け取るオーバーロードを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-129">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="8fa3d-130">このオーバーロードは、デリゲートをパラメーターとして受け取り、ジェネリック型の一連のオブジェクトを特定の型に変換します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-130">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="8fa3d-131">次のコードは、<xref:System.Func%602> デリゲートをパラメーターとして受け取る `Median` メソッドのオーバーロードを示しています。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-131">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="8fa3d-132">このデリゲートは、ジェネリック型 `T` のオブジェクトを受け取り、`double` 型のオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-132">This delegate takes an object of generic type `T` and returns an object of type `double`.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="GenericOverload":::

<span data-ttu-id="8fa3d-133">これで、任意の型の一連のオブジェクトに対して `Median` メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-133">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="8fa3d-134">型に固有のメソッド オーバーロードがない場合は、デリゲート パラメーターを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-134">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="8fa3d-135">この目的で、Visual Basic ではラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-135">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="8fa3d-136">また、メソッド呼び出しの代わりに `Aggregate` 句または `Group By` 句を使用した場合、その句のスコープにある任意の値または式を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-136">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="8fa3d-137">次のコード例では、整数の配列と文字列の配列に対して `Median` メソッドを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-137">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="8fa3d-138">文字列の場合は、配列に格納されている文字列の長さの中央値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-138">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="8fa3d-139">この例は、それぞれのケースについて、`Median` メソッドに <xref:System.Func%602> デリゲート パラメーターを渡す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-139">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="8fa3d-140">コレクションを返すメソッドを追加する</span><span class="sxs-lookup"><span data-stu-id="8fa3d-140">Adding a method that returns a collection</span></span>

<span data-ttu-id="8fa3d-141"><xref:System.Collections.Generic.IEnumerable%601> インターフェイスは、一連の値を返すカスタム クエリ メソッドを追加することで拡張できます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-141">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="8fa3d-142">その場合、メソッドで型 <xref:System.Collections.Generic.IEnumerable%601> のコレクションを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-142">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="8fa3d-143">このようなメソッドを使用すると、一連の値にフィルターまたはデータ変換を適用することができます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-143">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="8fa3d-144">次の例では、コレクション内の最初の要素から 1 つおきに要素を返す `AlternateElements` という名前の拡張メソッドを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-144">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

:::code language="vb" source="./snippets/OtherExtensions.vb" ID="SequenceElement":::

<span data-ttu-id="8fa3d-145">この拡張メソッドは、次のコードに示すとおり、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスにある他のメソッドを呼び出すときと同じように、列挙可能な任意のコレクションに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8fa3d-145">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

:::code language="vb" source="./snippets/Program.vb" ID="SequenceUsage":::

## <a name="see-also"></a><span data-ttu-id="8fa3d-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fa3d-146">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="8fa3d-147">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="8fa3d-147">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
