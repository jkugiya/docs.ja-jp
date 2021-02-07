---
title: デリゲート - C# プログラミング ガイド
description: C# におけるデリゲートとは、パラメーター リストおよび戻り値の型を使用して、メソッドを参照する型です。 デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。
ms.date: 02/02/2021
helpviewer_keywords:
- C# language, delegates
- delegates [C#]
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
ms.openlocfilehash: 86f7908501c075881786d16caffdd765b8aaf6b5
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548072"
---
# <a name="delegates-c-programming-guide"></a><span data-ttu-id="ff0a6-104">デリゲート (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ff0a6-104">Delegates (C# Programming Guide)</span></span>

<span data-ttu-id="ff0a6-105">[デリゲート](../../language-reference/builtin-types/reference-types.md)は、特定のパラメーター リストおよび戻り値の型を使用して、メソッドへの参照を表す型です。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-105">A [delegate](../../language-reference/builtin-types/reference-types.md) is a type that represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="ff0a6-106">デリゲートをインスタンス化するときは、互換性のあるシグネチャと戻り値の型を持つ任意のメソッドにそのインスタンスを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-106">When you instantiate a delegate, you can associate its instance with any method with a compatible signature and return type.</span></span> <span data-ttu-id="ff0a6-107">メソッドは、デリゲート インスタンスを使用して起動する (呼び出す) ことができます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-107">You can invoke (or call) the method through the delegate instance.</span></span>

<span data-ttu-id="ff0a6-108">デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-108">Delegates are used to pass methods as arguments to other methods.</span></span> <span data-ttu-id="ff0a6-109">イベント ハンドラーは、デリゲートを介して呼び出されるメソッドにすぎません。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-109">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="ff0a6-110">カスタム メソッドを作成して、特定のイベントの発生時に、作成したメソッドが Windows コントロールなどのクラスから呼び出されるようにできます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-110">You create a custom method, and a class such as a windows control can call your method when a certain event occurs.</span></span> <span data-ttu-id="ff0a6-111">次の例にデリゲート宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-111">The following example shows a delegate declaration:</span></span>

[!code-csharp[csProgGuideDelegates#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#20)]

<span data-ttu-id="ff0a6-112">デリゲート型と一致するアクセス可能なクラスまたは構造体のメソッドはすべて、デリゲートに代入できます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-112">Any method from any accessible class or struct that matches the delegate type can be assigned to the delegate.</span></span> <span data-ttu-id="ff0a6-113">メソッドは、静的メソッドとインスタンス メソッドのいずれかにできます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-113">The method can be either static or an instance method.</span></span> <span data-ttu-id="ff0a6-114">この柔軟性により、メソッド呼び出しをプログラムによって変更したり、新しいコードを既存のクラスに接続したりできます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-114">This flexibility means you can programmatically change method calls, or plug new code into existing classes.</span></span>

> [!NOTE]
> <span data-ttu-id="ff0a6-115">メソッドのオーバーロードのコンテキストでは、メソッドのシグネチャに戻り値は含まれません。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-115">In the context of method overloading, the signature of a method does not include the return value.</span></span> <span data-ttu-id="ff0a6-116">しかしデリゲートのコンテキストでは、シグネチャに戻り値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-116">But in the context of delegates, the signature does include the return value.</span></span> <span data-ttu-id="ff0a6-117">つまり、メソッドにはデリゲートと同じ戻り値の型が必要です。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-117">In other words, a method must have the same return type as the delegate.</span></span>

<span data-ttu-id="ff0a6-118">このようにメソッドをパラメーターとして参照できるため、デリゲートはコールバック メソッドを定義するのに最適です。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-118">This ability to refer to a method as a parameter makes delegates ideal for defining callback methods.</span></span> <span data-ttu-id="ff0a6-119">アプリケーション内の 2 つのオブジェクトを比較するメソッドを記述できます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-119">You can write a method that compares two objects in your application.</span></span> <span data-ttu-id="ff0a6-120">このメソッドは、並べ替えアルゴリズムのデリゲートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-120">That method can be used in a delegate for a sort algoritym.</span></span> <span data-ttu-id="ff0a6-121">比較コードはライブラリとは別であるため、並べ替えメソッドの方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-121">Because the comparison code is separate from the library, the sort method can be more general.</span></span>

<span data-ttu-id="ff0a6-122">同様のシナリオで、呼び出し規則をより細かく制御する必要がある場合のために、[関数ポインター](~/_csharplang/proposals/csharp-9.0/function-pointers.md)が C# 9 に追加されました。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-122">[Function pointers](~/_csharplang/proposals/csharp-9.0/function-pointers.md) were added to C# 9 for similar scenarios, where you need more control over the calling convention.</span></span> <span data-ttu-id="ff0a6-123">デリゲートに関連付けられたコードは、デリゲート型に追加された仮想メソッドを使用して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-123">The code associated with a delegate is invoked using a virtual method added to a delegate type.</span></span> <span data-ttu-id="ff0a6-124">関数ポインターを使用して、さまざまな規則を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-124">Using function pointers, you can specify different conventions.</span></span>

## <a name="delegates-overview"></a><span data-ttu-id="ff0a6-125">デリゲートの概要</span><span class="sxs-lookup"><span data-stu-id="ff0a6-125">Delegates Overview</span></span>

<span data-ttu-id="ff0a6-126">デリゲートには、次の特徴があります。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-126">Delegates have the following properties:</span></span>

- <span data-ttu-id="ff0a6-127">デリゲートは C++ 関数ポインターと似ていますが、デリゲートは完全なオブジェクト指向です。また、メンバー関数への C++ ポインターとは異なり、デリゲートではオブジェクト インスタンスとメソッドの両方をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-127">Delegates are similar to C++ function pointers, but delegates are fully object-oriented, and unlike C++ pointers to member functions, delegates encapsulate both an object instance and a method.</span></span>
- <span data-ttu-id="ff0a6-128">デリゲートを使用すると、メソッドをパラメーターとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-128">Delegates allow methods to be passed as parameters.</span></span>
- <span data-ttu-id="ff0a6-129">デリゲートは、コールバック メソッドを定義するのに使用できます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-129">Delegates can be used to define callback methods.</span></span>
- <span data-ttu-id="ff0a6-130">デリゲートは連結でき、たとえば、複数のメソッドを 1 つのイベントで呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-130">Delegates can be chained together; for example, multiple methods can be called on a single event.</span></span>
- <span data-ttu-id="ff0a6-131">メソッドは、デリゲート型に正確に一致する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-131">Methods don't have to match the delegate type exactly.</span></span> <span data-ttu-id="ff0a6-132">詳細については、「[デリゲートの分散の使用](../concepts/covariance-contravariance/using-variance-in-delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-132">For more information, see [Using Variance in Delegates](../concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span>
- <span data-ttu-id="ff0a6-133">ラムダ式は、インライン コード ブロックをより簡潔に記述する方法です。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-133">Lambda expressions are a more concise way of writing inline code blocks.</span></span> <span data-ttu-id="ff0a6-134">(特定のコンテキストにおける) ラムダ式は、デリゲート型にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-134">Lambda expressions (in certain contexts) are compiled to delegate types.</span></span> <span data-ttu-id="ff0a6-135">ラムダ式について詳しくは、「[ラムダ式](../../language-reference/operators/lambda-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-135">For more information about lambda expressions, see [Lambda expressions](../../language-reference/operators/lambda-expressions.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="ff0a6-136">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ff0a6-136">In This Section</span></span>

- [<span data-ttu-id="ff0a6-137">デリゲートの使用</span><span class="sxs-lookup"><span data-stu-id="ff0a6-137">Using Delegates</span></span>](./using-delegates.md)
- <span data-ttu-id="ff0a6-138">[インターフェイス (c# プログラミング ガイド) ではなくデリゲートを使用する場合](/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ff0a6-138">[When to Use Delegates Instead of Interfaces (C# Programming Guide)](/previous-versions/visualstudio/visual-studio-2010/ms173173(v=vs.100))</span></span>
- [<span data-ttu-id="ff0a6-139">名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート</span><span class="sxs-lookup"><span data-stu-id="ff0a6-139">Delegates with Named vs. Anonymous Methods</span></span>](./delegates-with-named-vs-anonymous-methods.md)
- [<span data-ttu-id="ff0a6-140">デリゲートの変性の使用</span><span class="sxs-lookup"><span data-stu-id="ff0a6-140">Using Variance in Delegates</span></span>](../concepts/covariance-contravariance/using-variance-in-delegates.md)
- [<span data-ttu-id="ff0a6-141">デリゲートを結合する方法 (マルチキャスト デリゲート)</span><span class="sxs-lookup"><span data-stu-id="ff0a6-141">How to combine delegates (Multicast Delegates)</span></span>](./how-to-combine-delegates-multicast-delegates.md)
- [<span data-ttu-id="ff0a6-142">デリゲートを宣言し、インスタンス化して、使用する方法</span><span class="sxs-lookup"><span data-stu-id="ff0a6-142">How to declare, instantiate, and use a delegate</span></span>](./how-to-declare-instantiate-and-use-a-delegate.md)

## <a name="c-language-specification"></a><span data-ttu-id="ff0a6-143">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ff0a6-143">C# Language Specification</span></span>

<span data-ttu-id="ff0a6-144">詳細については、「[C# 言語の仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の「[デリゲート](~/_csharplang/spec/delegates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-144">For more information, see [Delegates](~/_csharplang/spec/delegates.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="ff0a6-145">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="ff0a6-145">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="featured-book-chapters"></a><span data-ttu-id="ff0a6-146">参考書籍の該当する章</span><span class="sxs-lookup"><span data-stu-id="ff0a6-146">Featured Book Chapters</span></span>

- <span data-ttu-id="ff0a6-147">「[Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式)](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10))」(『[C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers (C# 3.0 クックブック (第 3 版): C# 3.0 プログラマ向けの 250 以上のソリューション)](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))』)</span><span class="sxs-lookup"><span data-stu-id="ff0a6-147">[Delegates, Events, and Lambda Expressions](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span></span>
- <span data-ttu-id="ff0a6-148">「[デリゲートとイベント](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10))」(『[Learning C# 3.0: Master the fundamentals of C# 3.0 (C# 3.0 の学習: C# 3.0 の基礎を習得)](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))』)</span><span class="sxs-lookup"><span data-stu-id="ff0a6-148">[Delegates and Events](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) in [Learning C# 3.0: Master the fundamentals of C# 3.0](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="ff0a6-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff0a6-149">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="ff0a6-150">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ff0a6-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ff0a6-151">イベント</span><span class="sxs-lookup"><span data-stu-id="ff0a6-151">Events</span></span>](../events/index.md)
