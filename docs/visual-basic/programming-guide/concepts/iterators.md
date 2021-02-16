---
description: '詳細情報: 反復子 (Visual Basic)'
title: Iterators
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 9d12bd436a976e3f84dbd063ca746fc7e3b17bfb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462153"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="948ef-103">反復子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="948ef-103">Iterators (Visual Basic)</span></span>

<span data-ttu-id="948ef-104">*反復子* を使用して、リストや配列などのコレクションをステップ実行することができます。</span><span class="sxs-lookup"><span data-stu-id="948ef-104">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="948ef-105">iterator メソッドまたは `get` アクセサーは、コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="948ef-105">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="948ef-106">iterator メソッドは、[Yield](../../language-reference/statements/yield-statement.md) ステートメントを使用して、各要素を 1 回に 1 つ返します。</span><span class="sxs-lookup"><span data-stu-id="948ef-106">An iterator method uses the [Yield](../../language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="948ef-107">`Yield` ステートメントに達すると、コードの現在の場所が記憶されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-107">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="948ef-108">次回、iterator 関数が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-108">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="948ef-109">[For Each…Next](../../language-reference/statements/for-each-next-statement.md) ステートメントまたは LINQ クエリを使用して、クライアント コードから反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="948ef-109">You consume an iterator from client code by using a [For Each…Next](../../language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>

<span data-ttu-id="948ef-110">次の例では、`For Each` ループの最初の反復子により、最初の `Yield` ステートメントに達するまで `SomeNumbers` iterator メソッドで実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-110">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="948ef-111">このイテレーションは 3 の値を返し、iterator メソッドの現在の場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-111">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="948ef-112">ループの次のイテレーションでは、iterator メソッドの実行が中断した場所から続行し、`Yield` ステートメントに達したときに再度停止します。</span><span class="sxs-lookup"><span data-stu-id="948ef-112">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="948ef-113">このイテレーションは 5 の値を返し、ここでも iterator メソッドの現在の場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-113">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="948ef-114">iterator メソッドの最後に達すると、ループが完了します。</span><span class="sxs-lookup"><span data-stu-id="948ef-114">The loop completes when the end of the iterator method is reached.</span></span>

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

<span data-ttu-id="948ef-115">Iterator メソッドまたは `get` アクセサーの戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> となります。</span><span class="sxs-lookup"><span data-stu-id="948ef-115">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="948ef-116">`Exit Function` または `Return` ステートメントを使用すると、反復を終了できます。</span><span class="sxs-lookup"><span data-stu-id="948ef-116">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>

<span data-ttu-id="948ef-117">Visual Basic の iterator 関数と `get` アクセサー宣言には、[Iterator](../../language-reference/modifiers/iterator.md) 修飾子が含まれています。</span><span class="sxs-lookup"><span data-stu-id="948ef-117">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../language-reference/modifiers/iterator.md) modifier.</span></span>

<span data-ttu-id="948ef-118">反復子は、Visual Studio 2012 の Visual Basic で導入されました。</span><span class="sxs-lookup"><span data-stu-id="948ef-118">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>

<span data-ttu-id="948ef-119">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="948ef-119">**In this topic**</span></span>

- [<span data-ttu-id="948ef-120">単純な反復子</span><span class="sxs-lookup"><span data-stu-id="948ef-120">Simple Iterator</span></span>](#BKMK_SimpleIterator)

- [<span data-ttu-id="948ef-121">コレクション クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="948ef-121">Creating a Collection Class</span></span>](#BKMK_CollectionClass)

- [<span data-ttu-id="948ef-122">Try ブロック</span><span class="sxs-lookup"><span data-stu-id="948ef-122">Try Blocks</span></span>](#BKMK_TryBlocks)

- [<span data-ttu-id="948ef-123">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="948ef-123">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)

- [<span data-ttu-id="948ef-124">ジェネリック リストと共に反復子を使用する</span><span class="sxs-lookup"><span data-stu-id="948ef-124">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)

- [<span data-ttu-id="948ef-125">構文情報</span><span class="sxs-lookup"><span data-stu-id="948ef-125">Syntax Information</span></span>](#BKMK_SyntaxInformation)

- [<span data-ttu-id="948ef-126">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="948ef-126">Technical Implementation</span></span>](#BKMK_Technical)

- [<span data-ttu-id="948ef-127">反復子の使用</span><span class="sxs-lookup"><span data-stu-id="948ef-127">Use of Iterators</span></span>](#BKMK_UseOfIterators)

> [!NOTE]
> <span data-ttu-id="948ef-128">このトピックの単純な反復子の例を除くすべての例には、`System.Collections` および `System.Collections.Generic` 名前空間の [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) ステートメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="948ef-128">For all examples in the topic except the Simple Iterator example, include [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a> <span data-ttu-id="948ef-129">単純な反復子</span><span class="sxs-lookup"><span data-stu-id="948ef-129">Simple Iterator</span></span>

<span data-ttu-id="948ef-130">次の例では、[For…Next](../../language-reference/statements/for-next-statement.md) ループ内に 1 つの `Yield` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="948ef-130">The following example has a single `Yield` statement that is inside a [For…Next](../../language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="948ef-131">`Main` では、`For Each` ステートメント本文の各イテレーションで iterator 関数が呼び出され、これが次の `Yield` ステートメントに続行されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-131">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a> <span data-ttu-id="948ef-132">コレクション クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="948ef-132">Creating a Collection Class</span></span>

<span data-ttu-id="948ef-133">次の例の `DaysOfTheWeek` クラスは、<xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを必要とする <xref:System.Collections.IEnumerable> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="948ef-133">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="948ef-134">コンパイラは、<xref:System.Collections.IEnumerator> を返す `GetEnumerator` メソッドを暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="948ef-134">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="948ef-135">`GetEnumerator` メソッドは、`Yield` ステートメントを使用して各文字列を 1 つずつ返すもので、関数の宣言には `Iterator` 修飾子が存在します。</span><span class="sxs-lookup"><span data-stu-id="948ef-135">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

<span data-ttu-id="948ef-136">次の例では、動物のコレクションを含む `Zoo` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="948ef-136">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="948ef-137">クラス インスタンス (`theZoo`) を参照する `For Each` ステートメントでは、`GetEnumerator` メソッドが暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-137">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="948ef-138">`Birds` および `Mammals` プロパティを参照する `For Each` ステートメントでは、`AnimalsForType` という名前の iterator メソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-138">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a> <span data-ttu-id="948ef-139">Try ブロック</span><span class="sxs-lookup"><span data-stu-id="948ef-139">Try Blocks</span></span>

<span data-ttu-id="948ef-140">Visual Basic では、[Try...Catch...Finally ステートメント](../../language-reference/statements/try-catch-finally-statement.md)の `Try` ブロックで `Yield` ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="948ef-140">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="948ef-141">`Yield` ステートメントがある `Try` ブロックには、`Catch` ブロックと `Finally` ブロックを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="948ef-141">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>

<span data-ttu-id="948ef-142">次の例では、iterator 関数の中に `Try`、`Catch`、`Finally` の各ブロックが存在します。</span><span class="sxs-lookup"><span data-stu-id="948ef-142">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="948ef-143">iterator 関数内の `Finally` ブロックは、`For Each` の反復が完了する前に実行されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-143">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

<span data-ttu-id="948ef-144">`Yield` ステートメントを `Catch` ブロックや `Finally` ブロックに記述することはできません。</span><span class="sxs-lookup"><span data-stu-id="948ef-144">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="948ef-145">(iterator メソッドではなく) `For Each` 本体で例外がスローされた場合、iterator 関数の `Catch` ブロックは実行されず、iterator 関数の `Finally` ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-145">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="948ef-146">iterator 関数内の `Catch` ブロックでキャッチされるのは、iterator 関数内で発生した例外だけです。</span><span class="sxs-lookup"><span data-stu-id="948ef-146">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a> <span data-ttu-id="948ef-147">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="948ef-147">Anonymous Methods</span></span>

<span data-ttu-id="948ef-148">Visual Basic では、iterator 関数として匿名関数を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="948ef-148">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="948ef-149">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="948ef-149">The following example illustrates this.</span></span>

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

<span data-ttu-id="948ef-150">次の例に示したのは、iterator メソッドではない、引数を検証するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="948ef-150">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="948ef-151">このメソッドは、コレクション要素を表す匿名反復子の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="948ef-151">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

<span data-ttu-id="948ef-152">このようにせず、検証を iterator 関数内で行った場合、`For Each` 本体の最初の反復の開始まで検証を実行できません。</span><span class="sxs-lookup"><span data-stu-id="948ef-152">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a> <span data-ttu-id="948ef-153">ジェネリック リストと共に反復子を使用する</span><span class="sxs-lookup"><span data-stu-id="948ef-153">Using Iterators with a Generic List</span></span>

<span data-ttu-id="948ef-154">次の例の `Stack(Of T)` ジェネリック クラスは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="948ef-154">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="948ef-155">`Push` メソッドでは、`T` 型の配列に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="948ef-155">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="948ef-156"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドは、`Yield` ステートメントを使って配列値を返します。</span><span class="sxs-lookup"><span data-stu-id="948ef-156">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>

<span data-ttu-id="948ef-157">ジェネリック メソッド <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> だけでなく、非ジェネリック メソッド <xref:System.Collections.IEnumerable.GetEnumerator%2A> も実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="948ef-157">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="948ef-158">これは、<xref:System.Collections.Generic.IEnumerable%601> が <xref:System.Collections.IEnumerable> から継承するためです。</span><span class="sxs-lookup"><span data-stu-id="948ef-158">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="948ef-159">非ジェネリック実装は、ジェネリック実装に従います。</span><span class="sxs-lookup"><span data-stu-id="948ef-159">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="948ef-160">例では名前付き反復子を使用して、同じデータ コレクションでのさまざまな反復処理をサポートします。</span><span class="sxs-lookup"><span data-stu-id="948ef-160">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="948ef-161">この場合の名前付き反復子は、`TopToBottom` プロパティと `BottomToTop` プロパティ、および `TopN` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="948ef-161">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="948ef-162">`BottomToTop` プロパティの宣言には、`Iterator` キーワードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="948ef-162">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="948ef-163">構文情報</span><span class="sxs-lookup"><span data-stu-id="948ef-163">Syntax Information</span></span>

<span data-ttu-id="948ef-164">反復子は、メソッドまたは `get` アクセサーとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="948ef-164">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="948ef-165">反復子を、イベント、インスタンス コンストラクター、静的コンストラクター、静的デストラクターで指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="948ef-165">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>

<span data-ttu-id="948ef-166">`Yield` ステートメント内の式の型から反復子の戻り値の型への暗黙的な変換が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="948ef-166">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>

<span data-ttu-id="948ef-167">Visual Basic の場合、iterator メソッドで `ByRef` パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="948ef-167">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>

<span data-ttu-id="948ef-168">Visual Basic の場合、"Yield" は予約語ではなく、`Iterator` メソッドまたは `get` アクセサーで使用される場合にのみ、特別な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="948ef-168">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a> <span data-ttu-id="948ef-169">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="948ef-169">Technical Implementation</span></span>

<span data-ttu-id="948ef-170">メソッドとして反復子を記述しても、コンパイラが入れ子のクラス (つまり、事実上、ステート マシン) に変換します。</span><span class="sxs-lookup"><span data-stu-id="948ef-170">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="948ef-171">このクラスは、クライアント コードで `For Each...Next` ループが続く限り、反復子の位置を追跡します。</span><span class="sxs-lookup"><span data-stu-id="948ef-171">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>

<span data-ttu-id="948ef-172">コンパイラの動作を確認するには、Ildasm.exe ツールを使用して、iterator メソッドに対して生成される Microsoft 中間言語コードを表示します。</span><span class="sxs-lookup"><span data-stu-id="948ef-172">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>

<span data-ttu-id="948ef-173">[クラス](../../language-reference/statements/class-statement.md)または[構造体](../../language-reference/statements/structure-statement.md)用の反復子を作成する場合、<xref:System.Collections.IEnumerator> インターフェイス全体を実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="948ef-173">When you create an iterator for a [class](../../language-reference/statements/class-statement.md) or [struct](../../language-reference/statements/structure-statement.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="948ef-174">コンパイラは、反復子を検出すると、<xref:System.Collections.IEnumerator> または <xref:System.Collections.Generic.IEnumerator%601> インターフェイスの `Current`、`MoveNext`、および `Dispose` メソッドを自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="948ef-174">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="948ef-175">`For Each…Next` ループの連続する反復ごとに (または `IEnumerator.MoveNext` を直接呼び出すと)、前の `Yield` ステートメントの後で次の反復子コード本体が再開されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-175">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="948ef-176">その後、反復子本体の最後に到達するか、`Exit Function` または `Return` ステートメントが検出されるまで、次の `Yield` ステートメントに続行されます。</span><span class="sxs-lookup"><span data-stu-id="948ef-176">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>

<span data-ttu-id="948ef-177">反復子は、<xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> メソッドをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="948ef-177">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="948ef-178">反復処理を最初から再度行う場合は、新しい反復子を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="948ef-178">To re-iterate from the start, you must obtain a new iterator.</span></span>

<span data-ttu-id="948ef-179">詳細については、「[Visual Basic 言語の仕様](../../reference/language-specification/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="948ef-179">For additional information, see the [Visual Basic Language Specification](../../reference/language-specification/index.md).</span></span>

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a> <span data-ttu-id="948ef-180">反復子の使用</span><span class="sxs-lookup"><span data-stu-id="948ef-180">Use of Iterators</span></span>

<span data-ttu-id="948ef-181">反復子を使用すると、複雑なコードを使用して一覧シーケンスを設定する必要がある場合に、`For Each` ループの単純さを維持することができます。</span><span class="sxs-lookup"><span data-stu-id="948ef-181">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="948ef-182">これは次のような場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="948ef-182">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="948ef-183">最初の `For Each` ループ イテレーションの後に一覧シーケンスを変更する。</span><span class="sxs-lookup"><span data-stu-id="948ef-183">Modify the list sequence after the first `For Each` loop iteration.</span></span>

- <span data-ttu-id="948ef-184">最初の `For Each` ループ イテレーションの前に大きい一覧が完全に読み込まれないようにする。</span><span class="sxs-lookup"><span data-stu-id="948ef-184">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="948ef-185">例として、ページ フェッチでのテーブル行のバッチの読み込みなどがあります。</span><span class="sxs-lookup"><span data-stu-id="948ef-185">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="948ef-186">また、別の例として、<xref:System.IO.DirectoryInfo.EnumerateFiles%2A> メソッドでの .NET Framework 内の反復子の実装があります。</span><span class="sxs-lookup"><span data-stu-id="948ef-186">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="948ef-187">反復子に一覧の作成をカプセル化する。</span><span class="sxs-lookup"><span data-stu-id="948ef-187">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="948ef-188">iterator メソッドでは、一覧を作成してから、ループで各結果を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="948ef-188">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="948ef-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="948ef-189">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="948ef-190">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="948ef-190">For Each...Next Statement</span></span>](../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="948ef-191">Yield ステートメント</span><span class="sxs-lookup"><span data-stu-id="948ef-191">Yield Statement</span></span>](../../language-reference/statements/yield-statement.md)
- [<span data-ttu-id="948ef-192">Iterator</span><span class="sxs-lookup"><span data-stu-id="948ef-192">Iterator</span></span>](../../language-reference/modifiers/iterator.md)
