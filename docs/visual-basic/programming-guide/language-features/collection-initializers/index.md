---
description: '詳細情報: コレクション初期化子 (Visual Basic)'
title: コレクション初期化子
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: afae9278092934ead4572f16fb1ec4a29d631803
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475462"
---
# <a name="collection-initializers-visual-basic"></a><span data-ttu-id="dc87f-103">コレクション初期化子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc87f-103">Collection Initializers (Visual Basic)</span></span>

<span data-ttu-id="dc87f-104">*コレクション初期化子* とは、コレクションを作成して一連の初期値を設定できる、短い構文です。</span><span class="sxs-lookup"><span data-stu-id="dc87f-104">*Collection initializers* provide a shortened syntax that enables you to create a collection and populate it with an initial set of values.</span></span> <span data-ttu-id="dc87f-105">コレクション初期化子は、コレクションを既知の値のセットから作成する場合に便利です。値のセットの例として、メニュー オプションやカテゴリのリスト、数値の初期セット、曜日や月の名前の静的文字列のリスト、検証に使用する州のリストなどの地理的な場所が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-105">Collection initializers are useful when you are creating a collection from a set of known values, for example, a list of menu options or categories, an initial set of numeric values, a static list of strings such as day or month names, or geographic locations such as a list of states that is used for validation.</span></span>

<span data-ttu-id="dc87f-106">コレクションの詳細については、「[コレクション](../../concepts/collections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc87f-106">For more information about collections, see [Collections](../../concepts/collections.md).</span></span>

<span data-ttu-id="dc87f-107">コレクション初期化子は、`From` キーワードの後に中かっこ (`{}`) を使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-107">You identify a collection initializer by using the `From` keyword followed by braces (`{}`).</span></span> <span data-ttu-id="dc87f-108">これは、「[配列](../arrays/index.md)」で説明する配列リテラルの構文と似ています。</span><span class="sxs-lookup"><span data-stu-id="dc87f-108">This is similar to the array literal syntax that is described in [Arrays](../arrays/index.md).</span></span> <span data-ttu-id="dc87f-109">次の例では、コレクション初期化子を使用してコレクションを作成するさまざまな方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc87f-109">The following examples show various ways to use collection initializers to create collections.</span></span>

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> <span data-ttu-id="dc87f-110">C# にもコレクション初期化子はあります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-110">C# also provides collection initializers.</span></span> <span data-ttu-id="dc87f-111">C# のコレクション初期化子には、Visual Basic のコレクション初期化子と同じ機能があります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-111">C# collection initializers provide the same functionality as Visual Basic collection initializers.</span></span> <span data-ttu-id="dc87f-112">C# のコレクション初期化子の詳細については、「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc87f-112">For more information about C# collection initializers, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="dc87f-113">構文</span><span class="sxs-lookup"><span data-stu-id="dc87f-113">Syntax</span></span>

<span data-ttu-id="dc87f-114">コレクション初期化子は、次のコードのように、先頭に `From` キーワードが付いた、中かっこ (`{}`) で囲まれたコンマ区切りの値の一覧で構成されます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-114">A collection initializer consists of a list of comma-separated values that are enclosed in braces (`{}`), preceded by the `From` keyword, as shown in the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

<span data-ttu-id="dc87f-115"><xref:System.Collections.Generic.List%601> や <xref:System.Collections.Generic.Dictionary%602> などのコレクションを作成する場合、次のコードに示すように、コレクション初期化子の前に、コレクションの種類を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-115">When you create a collection, such as a <xref:System.Collections.Generic.List%601> or a <xref:System.Collections.Generic.Dictionary%602>, you must supply the collection type before the collection initializer, as shown in the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> <span data-ttu-id="dc87f-116">コレクション初期化子とオブジェクト初期化子を組み合わせて、同じコレクション オブジェクトを初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="dc87f-116">You cannot combine both a collection initializer and an object initializer to initialize the same collection object.</span></span> <span data-ttu-id="dc87f-117">コレクション初期化子内のオブジェクトを初期化するには、オブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc87f-117">You can use object initializers to initialize objects in a collection initializer.</span></span>

## <a name="creating-a-collection-by-using-a-collection-initializer"></a><span data-ttu-id="dc87f-118">コレクション初期化子を使用してコレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="dc87f-118">Creating a Collection by Using a Collection Initializer</span></span>

<span data-ttu-id="dc87f-119">コレクション初期化子を使用してコレクションを作成する場合、コレクション初期化子内の各値は、コレクション内の適切な `Add` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-119">When you create a collection by using a collection initializer, each value that is supplied in the collection initializer is passed to the appropriate `Add` method of the collection.</span></span> <span data-ttu-id="dc87f-120">たとえば、コレクション初期化子を使用して <xref:System.Collections.Generic.List%601> 作成する場合、コレクション初期化子内の各文字列値は <xref:System.Collections.Generic.List%601.Add%2A> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-120">For example, if you create a <xref:System.Collections.Generic.List%601> by using a collection initializer, each string value in the collection initializer is passed to the <xref:System.Collections.Generic.List%601.Add%2A> method.</span></span> <span data-ttu-id="dc87f-121">コレクション初期化子を使用してコレクションを作成する場合は、指定した型は有効なコレクション型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-121">If you want to create a collection by using a collection initializer, the specified type must be valid collection type.</span></span> <span data-ttu-id="dc87f-122">有効なコレクションの型には、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するクラスや、<xref:System.Collections.CollectionBase> クラスを継承するクラスなどがあります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-122">Examples of valid collection types include classes that implement the <xref:System.Collections.Generic.IEnumerable%601> interface or inherit the <xref:System.Collections.CollectionBase> class.</span></span> <span data-ttu-id="dc87f-123">指定した型には、次の条件を満たす `Add` メソッドも公開されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-123">The specified type must also expose an `Add` method that meets the following criteria.</span></span>

- <span data-ttu-id="dc87f-124">`Add` メソッドは、コレクション初期化子の呼び出し元の範囲から使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-124">The `Add` method must be available from the scope in which the collection initializer is being called.</span></span> <span data-ttu-id="dc87f-125">そのコレクションのパブリックでないメソッドにアクセスできるシナリオでコレクション初期化子を使用する場合は、`Add` メソッドは、パブリックである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dc87f-125">The `Add` method does not have to be public if you are using the collection initializer in a scenario where non-public methods of the collection can be accessed.</span></span>

- <span data-ttu-id="dc87f-126">`Add` メソッドはインスタンス メンバー、またはコレクション クラスの `Shared` メンバーまたは拡張メソッドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-126">The `Add` method must be an instance member or `Shared` member of the collection class, or an extension method.</span></span>

- <span data-ttu-id="dc87f-127">オーバーロード解決規則に基づいて、コレクション初期化子で提供される型に対応付けることができる `Add` メソッドが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-127">An `Add` method must exist that can be matched, based on overload resolution rules, to the types that are supplied in the collection initializer.</span></span>

 <span data-ttu-id="dc87f-128">たとえば、コレクション初期化子を使用して、`List(Of Customer)` コレクションを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dc87f-128">For example, the following code example shows how to create a `List(Of Customer)` collection by using a collection initializer.</span></span> <span data-ttu-id="dc87f-129">このコードを実行すると、`Customer` の各オブジェクトは汎用リストの `Add(Customer)` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-129">When the code is run, each `Customer` object is passed to the `Add(Customer)` method of the generic list.</span></span>

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

<span data-ttu-id="dc87f-130">次では、コレクション初期化子を使用しない同等のコード例を示します。</span><span class="sxs-lookup"><span data-stu-id="dc87f-130">The following code example shows equivalent code that does not use a collection initializer.</span></span>

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

<span data-ttu-id="dc87f-131">`Customer` オブジェクトのコンストラクターと一致するパラメーターを持つ `Add` メソッドがコレクションにある場合、次のセクションで説明するように、コレクション初期化子内に `Add` メソッドのパラメーター値を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-131">If the collection has an `Add` method that has parameters that match the constructor for the `Customer` object, you could nest parameter values for the `Add` method within collection initializers, as discussed in the next section.</span></span> <span data-ttu-id="dc87f-132">コレクションにこのような `Add` メソッドがない場合、それを拡張メソッドとして作成できます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-132">If the collection does not have such an `Add` method, you can create one as an extension method.</span></span> <span data-ttu-id="dc87f-133">コレクションの拡張メソッドとして `Add` メソッドを作成する方法の例については、「[方法: コレクション初期化子によって使用される Add 拡張メソッドを作成する](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc87f-133">For an example of how to create an `Add` method as an extension method for a collection, see [How to: Create an Add Extension Method Used by a Collection Initializer](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md).</span></span> <span data-ttu-id="dc87f-134">コレクション初期化子で使用できるカスタム コレクションを作成する方法の例については、「[方法: コレクション初期化子を使用してコレクションを作成する](how-to-create-a-collection-used-by-a-collection-initializer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc87f-134">For an example of how to create a custom collection that can be used with a collection initializer, see [How to: Create a Collection Used by a Collection Initializer](how-to-create-a-collection-used-by-a-collection-initializer.md).</span></span>

## <a name="nesting-collection-initializers"></a><span data-ttu-id="dc87f-135">コレクション初期化子を入れ子にする</span><span class="sxs-lookup"><span data-stu-id="dc87f-135">Nesting Collection Initializers</span></span>

<span data-ttu-id="dc87f-136">作成するコレクションの `Add` メソッドで固有のオーバーロードを指定するため、コレクション初期化子内の値を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-136">You can nest values within a collection initializer to identify a specific overload of an `Add` method for the collection that is being created.</span></span> <span data-ttu-id="dc87f-137">`Add` メソッドに渡す値は、配列リテラルまたはコレクション初期化子の場合と同じように、コンマで区切り、中かっこ (`{}`) で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc87f-137">The values passed to the `Add` method must be separated by commas and enclosed in braces (`{}`), like you would do in an array literal or collection initializer.</span></span>

<span data-ttu-id="dc87f-138">入れ子にした値でコレクションを作成する場合、入れ子になった値一覧の各要素は、要素の型に一致する `Add` メソッドに引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-138">When you create a collection by using nested values, each element of the nested value list is passed as an argument to the `Add` method that matches the element types.</span></span> <span data-ttu-id="dc87f-139">たとえば、次のコード例では、キーは `Integer` 型で値は `String` 型の <xref:System.Collections.Generic.Dictionary%602> が作成されます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-139">For example, the following code example creates a <xref:System.Collections.Generic.Dictionary%602> in which the keys are of type `Integer` and the values are of type `String`.</span></span> <span data-ttu-id="dc87f-140">一連の入れ子になった値は、それぞれ `Dictionary` の <xref:System.Collections.Generic.Dictionary%602.Add%2A> メソッドと照合されます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-140">Each of the nested value lists is matched to the <xref:System.Collections.Generic.Dictionary%602.Add%2A> method for the `Dictionary`.</span></span>

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

<span data-ttu-id="dc87f-141">前のコード例は、次のコードと同じです。</span><span class="sxs-lookup"><span data-stu-id="dc87f-141">The previous code example is equivalent to the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

<span data-ttu-id="dc87f-142">入れ子の最初のレベルの一連の入れ子になった値のみが、それぞれそのコレクション型の `Add` メソッドに送信されます。</span><span class="sxs-lookup"><span data-stu-id="dc87f-142">Only nested value lists from the first level of nesting are sent to the `Add` method for the collection type.</span></span> <span data-ttu-id="dc87f-143">より深いレベルの入れ子は配列リテラルとして扱われ、入れ子になった一連の値はどのコレクションの `Add` メソッドとも照合されません。</span><span class="sxs-lookup"><span data-stu-id="dc87f-143">Deeper levels of nesting are treated as array literals and the nested value lists are not matched to the `Add` method of any collection.</span></span>

## <a name="related-topics"></a><span data-ttu-id="dc87f-144">関連トピック</span><span class="sxs-lookup"><span data-stu-id="dc87f-144">Related Topics</span></span>

|<span data-ttu-id="dc87f-145">Title</span><span class="sxs-lookup"><span data-stu-id="dc87f-145">Title</span></span>|<span data-ttu-id="dc87f-146">説明</span><span class="sxs-lookup"><span data-stu-id="dc87f-146">Description</span></span>|
|---|---|
|[<span data-ttu-id="dc87f-147">方法: コレクション初期化子によって使用される Add 拡張メソッドを作成する</span><span class="sxs-lookup"><span data-stu-id="dc87f-147">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|<span data-ttu-id="dc87f-148">コレクション初期化子の値をコレクションに入力するために使用できる `Add` と呼ばれる拡張メソッドを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dc87f-148">Shows how to create an extension method called `Add` that can be used to populate a collection with values from a collection initializer.</span></span>|
|[<span data-ttu-id="dc87f-149">方法: コレクション初期化子によって使用されるコレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="dc87f-149">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)|<span data-ttu-id="dc87f-150">`IEnumerable` を実装するコレクション クラスに `Add` メソッドを含めてコレクション初期化子を使用できるようにする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="dc87f-150">Shows how to enable use of a collection initializer by including an `Add` method in a collection class that implements `IEnumerable`.</span></span>|

## <a name="see-also"></a><span data-ttu-id="dc87f-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc87f-151">See also</span></span>

- [<span data-ttu-id="dc87f-152">コレクション</span><span class="sxs-lookup"><span data-stu-id="dc87f-152">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="dc87f-153">配列</span><span class="sxs-lookup"><span data-stu-id="dc87f-153">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="dc87f-154">オブジェクト初期化子: 名前付きの型と匿名型</span><span class="sxs-lookup"><span data-stu-id="dc87f-154">Object Initializers: Named and Anonymous Types</span></span>](../objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="dc87f-155">New 演算子</span><span class="sxs-lookup"><span data-stu-id="dc87f-155">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="dc87f-156">自動実装プロパティ</span><span class="sxs-lookup"><span data-stu-id="dc87f-156">Auto-Implemented Properties</span></span>](../procedures/auto-implemented-properties.md)
- [<span data-ttu-id="dc87f-157">方法: Visual Basic で配列変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="dc87f-157">How to: Initialize an Array Variable in Visual Basic</span></span>](../arrays/how-to-initialize-an-array-variable.md)
- [<span data-ttu-id="dc87f-158">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="dc87f-158">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="dc87f-159">匿名型</span><span class="sxs-lookup"><span data-stu-id="dc87f-159">Anonymous Types</span></span>](../objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="dc87f-160">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="dc87f-160">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="dc87f-161">方法: 項目のリストを作成する</span><span class="sxs-lookup"><span data-stu-id="dc87f-161">How to: Create a List of Items</span></span>](../../concepts/linq/how-to-create-a-list-of-items.md)
