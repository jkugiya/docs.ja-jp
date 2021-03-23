---
title: Iterators
description: 組み込み C# の反復子を使用して、独自のカスタム反復子メソッドを作成する方法について説明します。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.openlocfilehash: 357f05f6ae1a4cec7566ddc821036354c932af90
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872640"
---
# <a name="iterators"></a><span data-ttu-id="db0e7-103">Iterators</span><span class="sxs-lookup"><span data-stu-id="db0e7-103">Iterators</span></span>

<span data-ttu-id="db0e7-104">プログラムを記述するうえで、ほとんどのプログラムに必要になるのがコレクションの反復処理です。</span><span class="sxs-lookup"><span data-stu-id="db0e7-104">Almost every program you write will have some need to iterate over a collection.</span></span> <span data-ttu-id="db0e7-105">反復処理が必要な場合は、コレクション内のすべての項目を調べるコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="db0e7-105">You'll write code that examines every item in a collection.</span></span>

<span data-ttu-id="db0e7-106">また、クラスの要素に対して反復子 (コンテナーを横断するオブジェクト。特にリスト) を生成するメソッドである、反復子メソッドも作成することになります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-106">You'll also create iterator methods which are methods that produces an iterator (which is an object that traverses a container, particularly lists) for the elements of that class.</span></span> <span data-ttu-id="db0e7-107">反復子メソッドは以下のような目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-107">These can be used for:</span></span>

+ <span data-ttu-id="db0e7-108">コレクション内の各項目に対するアクションの実行。</span><span class="sxs-lookup"><span data-stu-id="db0e7-108">Performing an action on each item in a collection.</span></span>
+ <span data-ttu-id="db0e7-109">カスタム コレクションの列挙。</span><span class="sxs-lookup"><span data-stu-id="db0e7-109">Enumerating a custom collection.</span></span>
+ <span data-ttu-id="db0e7-110">[LINQ](linq/index.md) やその他のライブラリの拡張。</span><span class="sxs-lookup"><span data-stu-id="db0e7-110">Extending [LINQ](linq/index.md) or other libraries.</span></span>
+ <span data-ttu-id="db0e7-111">反復子メソッドによってデータ フローを効率化するデータ パイプラインの作成。</span><span class="sxs-lookup"><span data-stu-id="db0e7-111">Creating a data pipeline where data flows efficiently through iterator methods.</span></span>

<span data-ttu-id="db0e7-112">C# 言語には、上記の両方のシナリオに対応するための機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="db0e7-112">The C# language provides features for both these scenarios.</span></span> <span data-ttu-id="db0e7-113">この記事では、それらの機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="db0e7-113">This article provides an overview of those features.</span></span>

<span data-ttu-id="db0e7-114">このチュートリアルには、複数の手順があります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-114">This tutorial has multiple steps.</span></span> <span data-ttu-id="db0e7-115">各手順の後に、アプリケーションを実行して進行状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-115">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="db0e7-116">このトピックの[完全なサンプルを表示またはダウンロードする](https://github.com/dotnet/samples/blob/main/csharp/iterators)こともできます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-116">You can also [view or download the completed sample](https://github.com/dotnet/samples/blob/main/csharp/iterators) for this topic.</span></span> <span data-ttu-id="db0e7-117">ダウンロード方法については、「[サンプルおよびチュートリアル](../samples-and-tutorials/index.md#view-and-download-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db0e7-117">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#view-and-download-samples).</span></span>

## <a name="iterating-with-foreach"></a><span data-ttu-id="db0e7-118">foreach を使用した反復処理</span><span class="sxs-lookup"><span data-stu-id="db0e7-118">Iterating with foreach</span></span>

<span data-ttu-id="db0e7-119">コレクションの列挙処理は単純です。`foreach` キーワードによってコレクション内の要素ごとに埋め込みステートメントを 1 回実行し、コレクションを列挙します。</span><span class="sxs-lookup"><span data-stu-id="db0e7-119">Enumerating a collection is simple: The `foreach` keyword enumerates a collection, executing the embedded statement once for each element in the collection:</span></span>

```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="db0e7-120">これで完成です。</span><span class="sxs-lookup"><span data-stu-id="db0e7-120">That's all there is to it.</span></span> <span data-ttu-id="db0e7-121">`foreach` ステートメントさえあれば、コレクションに含まれるすべての内容を反復処理できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-121">To iterate over all the contents of a collection, the `foreach` statement is all you need.</span></span> <span data-ttu-id="db0e7-122">ただし、`foreach` ステートメントは魔法ではありません。</span><span class="sxs-lookup"><span data-stu-id="db0e7-122">The `foreach` statement isn't magic, though.</span></span> <span data-ttu-id="db0e7-123">コレクションの反復処理に必要なコードを生成するためには、.NET コア ライブラリに定義されている 2 つのジェネリック インターフェイス、`IEnumerable<T>` と `IEnumerator<T>` が不可欠です。</span><span class="sxs-lookup"><span data-stu-id="db0e7-123">It relies on two generic interfaces defined in the .NET core library in order to generate the code necessary to iterate a collection: `IEnumerable<T>` and `IEnumerator<T>`.</span></span> <span data-ttu-id="db0e7-124">このメカニズムについては、後ほど詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="db0e7-124">This mechanism is explained in more detail below.</span></span>

<span data-ttu-id="db0e7-125">これら 2 つのインターフェイスに対応する非ジェネリック インターフェイスとして、`IEnumerable` と `IEnumerator` があります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-125">Both of these interfaces also have non-generic counterparts: `IEnumerable` and `IEnumerator`.</span></span> <span data-ttu-id="db0e7-126">最新のコード向けには[ジェネリック](programming-guide/generics/index.md) バージョンが適しています。</span><span class="sxs-lookup"><span data-stu-id="db0e7-126">The [generic](programming-guide/generics/index.md) versions are preferred for modern code.</span></span>

## <a name="enumeration-sources-with-iterator-methods"></a><span data-ttu-id="db0e7-127">反復子メソッドを使用した列挙型のソース</span><span class="sxs-lookup"><span data-stu-id="db0e7-127">Enumeration sources with iterator methods</span></span>

<span data-ttu-id="db0e7-128">C# 言語のもう 1 つの優れた機能を利用することで、列挙型用のソースを作成するメソッドを構築できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-128">Another great feature of the C# language enables you to build methods that create a source for an enumeration.</span></span> <span data-ttu-id="db0e7-129">このようなメソッドを、"*反復子メソッド*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-129">These are referred to as *iterator methods*.</span></span> <span data-ttu-id="db0e7-130">反復子メソッドでは、要求があった場合にオブジェクトがどのようなシーケンスで生成されるかを定義します。</span><span class="sxs-lookup"><span data-stu-id="db0e7-130">An iterator method defines how to generate the objects in a sequence when requested.</span></span> <span data-ttu-id="db0e7-131">反復子メソッドを定義するには、`yield return` コンテキスト キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="db0e7-131">You use the `yield return` contextual keywords to define an iterator method.</span></span>

<span data-ttu-id="db0e7-132">次のメソッドを記述することで、0 ～ 9 の整数からなるシーケンスを生成できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-132">You could write this method to produce the sequence of integers from 0 through 9:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

<span data-ttu-id="db0e7-133">上記のコードでは、複数の `yield return` ステートメントを反復子メソッド内で個別に使用できるという点を強調するために、さまざまな `yield return` ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="db0e7-133">The code above shows distinct `yield return` statements to highlight the fact that you can use multiple discrete `yield return` statements in an iterator method.</span></span>
<span data-ttu-id="db0e7-134">反復子メソッドのコードを簡略化するために、他の言語構成要素を使用することができます (実際、頻繁に使用します)。</span><span class="sxs-lookup"><span data-stu-id="db0e7-134">You can (and often do) use other language constructs to simplify the code of an iterator method.</span></span> <span data-ttu-id="db0e7-135">次のメソッド定義では、まったく同じ数値のシーケンスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-135">The method definition below produces the exact same sequence of numbers:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;
}
```

<span data-ttu-id="db0e7-136">どちらか一方に決める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="db0e7-136">You don't have to decide one or the other.</span></span> <span data-ttu-id="db0e7-137">メソッドのニーズに合わせて必要な数だけ `yield return` ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-137">You can have as many `yield return` statements as necessary to meet the needs of your method:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    index = 100;
    while (index < 110)
        yield return index++;
}
```

<span data-ttu-id="db0e7-138">これが基本的な構文です。</span><span class="sxs-lookup"><span data-stu-id="db0e7-138">That's the basic syntax.</span></span> <span data-ttu-id="db0e7-139">反復子メソッドを記述することになるであろう実際の例について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="db0e7-139">Let's consider a real world example where you would write an iterator method.</span></span> <span data-ttu-id="db0e7-140">自分が IoT プロジェクトに参加しているとして、デバイス センサーから膨大な量のデータ ストリームが生成されている状況を想像してください。</span><span class="sxs-lookup"><span data-stu-id="db0e7-140">Imagine you're on an IoT project and the device sensors generate a very large stream of data.</span></span> <span data-ttu-id="db0e7-141">データをおおまかに把握するためには、N 番目ごとにデータ要素をサンプリングするメソッドを記述することになります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-141">To get a feel for the data, you might write a method that samples every Nth data element.</span></span> <span data-ttu-id="db0e7-142">このような処理は、次の小さな反復子メソッドで実現できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-142">This small iterator method does the trick:</span></span>

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

<span data-ttu-id="db0e7-143">反復子メソッドには重要な制限事項が 1 つあり、`return` ステートメントと `yield return` ステートメントの両方を同じメソッド内で使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="db0e7-143">There is one important restriction on iterator methods: you can't have both a `return` statement and a `yield return` statement in the same method.</span></span> <span data-ttu-id="db0e7-144">そのため、次のコードはコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="db0e7-144">The following will not compile:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    // generates a compile time error:
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;
}
```

<span data-ttu-id="db0e7-145">通常は、この制限が問題になることはありません。</span><span class="sxs-lookup"><span data-stu-id="db0e7-145">This restriction normally isn't a problem.</span></span> <span data-ttu-id="db0e7-146">メソッド全体で `yield return` を使用するか、元のメソッドを複数に分割して一部のメソッドでは `return`、一部のメソッドでは `yield return` を使用するか、いずれかの方法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-146">You have a choice of either using `yield return` throughout the method, or separating the original method into multiple methods, some using `return`, and some using `yield return`.</span></span>

<span data-ttu-id="db0e7-147">前のメソッドを少し修正すると、メソッド全体で `yield return` のみを使用するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-147">You can modify the last method slightly to use `yield return` everywhere:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index < 10)
        yield return index++;

    yield return 50;

    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```

<span data-ttu-id="db0e7-148">反復子メソッドを 2 つの異なるメソッドに分割することが正解となる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-148">Sometimes, the right answer is to split an iterator method into two different methods.</span></span> <span data-ttu-id="db0e7-149">つまり、`return` を使用するメソッドと `yield return` を使用するメソッドの 2 つです。</span><span class="sxs-lookup"><span data-stu-id="db0e7-149">One that uses `return`, and a second that uses `yield return`.</span></span> <span data-ttu-id="db0e7-150">ブール型の引数を基に、空のコレクションまたは最初の 5 つの奇数を返す必要があるような場合を考えてみてください。</span><span class="sxs-lookup"><span data-stu-id="db0e7-150">Consider a situation where you might want to return an empty collection, or the first 5 odd numbers, based on a boolean argument.</span></span> <span data-ttu-id="db0e7-151">この処理は、次の 2 つのメソッドとして記述できます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-151">You could write that as these two methods:</span></span>

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index < 10)
    {
        if (index % 2 == 1)
            yield return index;
        index++;
    }
}
```

<span data-ttu-id="db0e7-152">上記のメソッドを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="db0e7-152">Look at the methods above.</span></span> <span data-ttu-id="db0e7-153">1 つ目のメソッドでは、標準の `return` ステートメントを使用して空のコレクションまたは 2 つ目のメソッドで作成された反復子のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="db0e7-153">The first uses the standard `return` statement to return either an empty collection, or the iterator created by the second method.</span></span> <span data-ttu-id="db0e7-154">2 つ目のメソッドでは、`yield return` ステートメントを使用して要求されたシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="db0e7-154">The second method uses the `yield return` statement to create the requested sequence.</span></span>

## <a name="deeper-dive-into-foreach"></a><span data-ttu-id="db0e7-155">`foreach` の詳細</span><span class="sxs-lookup"><span data-stu-id="db0e7-155">Deeper Dive into `foreach`</span></span>

<span data-ttu-id="db0e7-156">`foreach` ステートメントは、`IEnumerable<T>` および `IEnumerator<T>` インターフェイスを使用してコレクションの全要素を反復処理する標準的な表現形式に展開されます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-156">The `foreach` statement expands into a standard idiom that uses the `IEnumerable<T>` and `IEnumerator<T>` interfaces to iterate across all elements of a collection.</span></span> <span data-ttu-id="db0e7-157">また、開発者の不適切なリソース管理によって生じるエラーを最小化する効果もあります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-157">It also  minimizes errors developers make by not properly managing resources.</span></span>

<span data-ttu-id="db0e7-158">最初の例に登場する `foreach` ループは、コンパイラによって次のコンストラクトに似たコードに変換されます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-158">The compiler translates the `foreach` loop shown in the first example into something similar to this construct:</span></span>

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="db0e7-159">上記のコンストラクトは、バージョン 5 以降の C# コンパイラによって生成されるコードを表しています。</span><span class="sxs-lookup"><span data-stu-id="db0e7-159">The construct above represents the code generated by the C# compiler as of version 5 and above.</span></span> <span data-ttu-id="db0e7-160">バージョン 5 より前のバージョンでは、`item` 変数のスコープが異なります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-160">Prior to version 5, the `item` variable had a different scope:</span></span>

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

<span data-ttu-id="db0e7-161">この点が変更された理由は、以前の動作に、ラムダ式に関連する微妙なバグや診断の難しいバグを発生させる可能性があったためです。</span><span class="sxs-lookup"><span data-stu-id="db0e7-161">This was changed because the earlier behavior could lead to subtle and hard to diagnose bugs involving lambda expressions.</span></span> <span data-ttu-id="db0e7-162">ラムダ式について詳しくは、「[ラムダ式](language-reference/operators/lambda-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="db0e7-162">For more information about lambda expressions, see [Lambda expressions](language-reference/operators/lambda-expressions.md).</span></span>

<span data-ttu-id="db0e7-163">コンパイラによって実際に生成されるコードはもう少し複雑であり、`GetEnumerator()` から返されるオブジェクトで `IDisposable` インターフェイスを実装する場合の処理も含まれています。</span><span class="sxs-lookup"><span data-stu-id="db0e7-163">The exact code generated by the compiler is somewhat more complicated, and handles situations where the object returned by `GetEnumerator()` implements the `IDisposable` interface.</span></span> <span data-ttu-id="db0e7-164">全展開によって生成されるコードは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-164">The full expansion generates code more like this:</span></span>

```csharp
{
    var enumerator = collection.GetEnumerator();
    try
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally
    {
        // dispose of enumerator.
    }
}
```

<span data-ttu-id="db0e7-165">列挙子が破棄される場合、その方法は `enumerator` の型の特性によって異なります。</span><span class="sxs-lookup"><span data-stu-id="db0e7-165">The manner in which the enumerator is disposed of depends on the characteristics of the type of `enumerator`.</span></span> <span data-ttu-id="db0e7-166">一般的なケースでは、`finally` 句は次のように展開されます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-166">In the general case, the `finally` clause expands to:</span></span>

```csharp
finally
{
   (enumerator as IDisposable)?.Dispose();
}
```

<span data-ttu-id="db0e7-167">ただし、`enumerator` の型がシール型で、`enumerator` から `IDisposable` への暗黙的な型変換がない場合、`finally` 句は空のブロックに展開されます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-167">However, if the type of `enumerator` is a sealed type and there is no implicit conversion from the type of `enumerator` to `IDisposable`, the `finally` clause expands to an empty block:</span></span>

```csharp
finally
{
}
```

<span data-ttu-id="db0e7-168">`enumerator` から `IDisposable` への暗黙的な型変換があり、`enumerator` が null 非許容の値型である場合、`finally` 句は次のように展開されます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-168">If there is an implicit conversion from the type of `enumerator` to `IDisposable`, and `enumerator` is a non-nullable value type, the `finally` clause expands to:</span></span>

```csharp
finally
{
   ((IDisposable)enumerator).Dispose();
}
```

<span data-ttu-id="db0e7-169">さいわいなことに、これらの詳細をすべて覚えておく必要はありません。</span><span class="sxs-lookup"><span data-stu-id="db0e7-169">Thankfully, you don't need to remember all these details.</span></span> <span data-ttu-id="db0e7-170">このような微妙な差異は、いずれも `foreach` ステートメントによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-170">The `foreach` statement handles all those nuances for you.</span></span> <span data-ttu-id="db0e7-171">コンパイラでは、これらすべてのコンストラクトに対して正しいコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="db0e7-171">The compiler will generate the correct code for any of these constructs.</span></span>
