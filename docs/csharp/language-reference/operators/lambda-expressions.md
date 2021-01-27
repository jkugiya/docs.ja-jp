---
title: ラムダ式 - C# リファレンス
description: ラムダ式について説明します。 本体として式を持つ式形式のラムダと、本体としてステートメント ブロックを持つステートメント形式のラムダがあります。
ms.date: 09/25/2020
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 2ae63396c0b1bb0bf1fe5c33b1103f69f6dcf664
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615868"
---
# <a name="lambda-expressions-c-reference"></a><span data-ttu-id="6977d-104">ラムダ式 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6977d-104">Lambda expressions (C# reference)</span></span>

<span data-ttu-id="6977d-105">"*ラムダ式*" を使用して匿名関数を作成します。</span><span class="sxs-lookup"><span data-stu-id="6977d-105">You use a *lambda expression* to create an anonymous function.</span></span> <span data-ttu-id="6977d-106">[ラムダ宣言演算子`=>`](lambda-operator.md)を使用して、ラムダのパラメーター リストを式本体から分離します。</span><span class="sxs-lookup"><span data-stu-id="6977d-106">Use the [lambda declaration operator `=>`](lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="6977d-107">ラムダ式は、次の 2 つの形式のいずれかにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6977d-107">A lambda expression can be of any of the following two forms:</span></span>

- <span data-ttu-id="6977d-108">[式形式のラムダ](#expression-lambdas)は、式本体に式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6977d-108">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="6977d-109">[ステートメント形式のラムダ](#statement-lambdas)は、式本体にステートメント ブロックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="6977d-109">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="6977d-110">ラムダ式を作成するには、ラムダ演算子の左辺に入力パラメーターを指定し (ある場合)、右辺に式またはステートメント ブロックを指定します。</span><span class="sxs-lookup"><span data-stu-id="6977d-110">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="6977d-111">ラムダ式は、[デリゲート](../builtin-types/reference-types.md#the-delegate-type)型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-111">Any lambda expression can be converted to a [delegate](../builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="6977d-112">ラムダ式を変換できるデリゲート型は、パラメータと戻り値の型で定義されます。</span><span class="sxs-lookup"><span data-stu-id="6977d-112">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="6977d-113">ラムダ式が値を返さない場合は `Action` デリゲート型のいずれかに変換でき、値を返す場合は`Func` デリゲート型のいずれかに変換できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-113">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="6977d-114">たとえば、2 つのパラメーターがあり、値を返さないラムダ式は、<xref:System.Action%602> デリゲートに変換できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-114">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="6977d-115">1 つのパラメーターがあり、値を返すラムダ式は、<xref:System.Func%602> デリゲートに変換できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-115">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="6977d-116">次の例では、`x` という名前のパラメーターを指定し、`x` の二乗の値を返すラムダ式 `x => x * x` を、デリゲート型の変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6977d-116">In the following example, the lambda expression `x => x * x`, which specifies a parameter that's named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](snippets/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="6977d-117">式形式のラムダは、次の例に示すように、[式ツリー](../../programming-guide/concepts/expression-trees/index.md)型にも変換できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-117">Expression lambdas can also be converted to the [expression tree](../../programming-guide/concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](snippets/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="6977d-118">ラムダ式は、デリゲート型または式ツリーのインスタンスを必要とするすべてのコードで使用できます。たとえば、<xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> メソッドの引数として使用すると、バックグラウンドで実行する必要があるコードを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="6977d-118">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="6977d-119">また、次の例に示すように、[C# で LINQ](../../linq/index.md) を作成する場合にもラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-119">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](snippets/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="6977d-120">メソッド ベースの構文を使用して <xref:System.Linq.Enumerable?displayProperty=nameWithType> クラス (たとえば、LINQ to Objects、LINQ to XML など) の <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> メソッドを呼び出すと、パラメーターはデリゲート型 <xref:System.Func%602?displayProperty=nameWithType> になります。</span><span class="sxs-lookup"><span data-stu-id="6977d-120">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6977d-121"><xref:System.Linq.Queryable?displayProperty=nameWithType> クラス (たとえば、LINQ to SQL など) の <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> メソッドを呼び出すと、パラメーター型は式ツリー型 [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>) になります。</span><span class="sxs-lookup"><span data-stu-id="6977d-121">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="6977d-122">どちらの場合も、同じラムダ式を使用してパラメーター値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-122">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="6977d-123">これにより、2 つの `Select` 呼び出しは外観が似ていますが、ラムダから実際に作成されるオブジェクトの型は異なります。</span><span class="sxs-lookup"><span data-stu-id="6977d-123">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="6977d-124">式形式のラムダ</span><span class="sxs-lookup"><span data-stu-id="6977d-124">Expression lambdas</span></span>

<span data-ttu-id="6977d-125">`=>` 演算子の右辺に式があるラムダ式を "*式形式のラムダ*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="6977d-125">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="6977d-126">式形式のラムダは式の結果を返します。基本的な形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6977d-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="6977d-127">式形式のラムダの本体を、メソッド呼び出しで構成できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-127">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="6977d-128">ただし、SQL Server などの .NET 共通言語ランタイム (CLR) のコンテキスト外部で評価される[式ツリー](../../programming-guide/concepts/expression-trees/index.md)を作成する場合は、ラムダ式内でメソッド呼び出しを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6977d-128">However, if you are creating [expression trees](../../programming-guide/concepts/expression-trees/index.md) that are evaluated outside the context of the .NET Common Language Runtime (CLR), such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="6977d-129">.NET 共通言語ランタイム (CLR) のコンテキストの外部では、これらのメソッドは通用しません。</span><span class="sxs-lookup"><span data-stu-id="6977d-129">The methods will have no meaning outside the context of the .NET Common Language Runtime (CLR).</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="6977d-130">ステートメント形式のラムダ</span><span class="sxs-lookup"><span data-stu-id="6977d-130">Statement lambdas</span></span>

<span data-ttu-id="6977d-131">ステートメント形式のラムダは式形式のラムダに似ていますが、ステートメントが中かっこで囲まれる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="6977d-131">A statement lambda resembles an expression lambda except that its statements are enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="6977d-132">ステートメント形式のラムダの本体は任意の数のステートメントで構成できますが、実際面では通常、2、3 個以下にします。</span><span class="sxs-lookup"><span data-stu-id="6977d-132">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetStatementLambda":::

<span data-ttu-id="6977d-133">ステートメント形式のラムダを使用して式ツリーを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="6977d-133">You cannot use statement lambdas to create expression trees.</span></span>

## <a name="input-parameters-of-a-lambda-expression"></a><span data-ttu-id="6977d-134">ラムダ式の入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="6977d-134">Input parameters of a lambda expression</span></span>

<span data-ttu-id="6977d-135">ラムダ式の入力パラメーターをかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="6977d-135">You enclose input parameters of a lambda expression in parentheses.</span></span> <span data-ttu-id="6977d-136">入力パラメーターがないことを指定するには、次のように空のかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="6977d-136">Specify zero input parameters with empty parentheses:</span></span>  

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetZeroParameters":::

<span data-ttu-id="6977d-137">ラムダ式に入力パラメーターが 1 つしかない場合、かっこは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6977d-137">If a lambda expression has only one input parameter, parentheses are optional:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetOneParameter":::

<span data-ttu-id="6977d-138">入力パラメーターが 2 つ以上ある場合は、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="6977d-138">Two or more input parameters are separated by commas:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetTwoParameters":::

<span data-ttu-id="6977d-139">場合によっては、コンパイラで入力パラメーターの型を推論できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="6977d-139">Sometimes the compiler can't infer the types of input parameters.</span></span> <span data-ttu-id="6977d-140">次の例のように、型を明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-140">You can specify the types explicitly as shown in the following example:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetExplicitlyTypedParameters":::

<span data-ttu-id="6977d-141">入力パラメーターの型は、すべて明示的またはすべて暗黙的である必要があります。それ以外の場合は、[CS0748](../../misc/cs0748.md) コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6977d-141">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="6977d-142">C# 9.0 以降では、[破棄](../../discards.md)を使用して、式で使用しないラムダ式の 2 つ以上の入力パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-142">Beginning with C# 9.0, you can use [discards](../../discards.md) to specify two or more input parameters of a lambda expression that aren't used in the expression:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetDiscards":::

<span data-ttu-id="6977d-143">ラムダの破棄パラメーターは、ラムダ式を使用して[イベント ハンドラー指定する](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="6977d-143">Lambda discard parameters may be useful when you use a lambda expression to [provide an event handler](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6977d-144">下位互換性のために、1 つの入力パラメーターにのみ `_` という名前が付けられた場合、ラムダ式内で `_` はそのパラメーターの名前として扱われます。</span><span class="sxs-lookup"><span data-stu-id="6977d-144">For backwards compatibility, if only a single input parameter is named `_`, then, within a lambda expression, `_` is treated as the name of that parameter.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="6977d-145">非同期ラムダ</span><span class="sxs-lookup"><span data-stu-id="6977d-145">Async lambdas</span></span>

<span data-ttu-id="6977d-146">[async](../keywords/async.md) キーワードと [await](await.md) キーワードを使用すると、非同期処理を組み込んだラムダ式およびステートメントを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../keywords/async.md) and [await](await.md) keywords.</span></span> <span data-ttu-id="6977d-147">たとえば、次に示す Windows フォーム例には、非同期メソッド `ExampleMethodAsync`を呼び出して待機するイベント ハンドラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6977d-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="6977d-148">非同期ラムダを使用して、同じイベント ハンドラーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-148">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="6977d-149">このハンドラーを追加するには、次の例に示すように、ラムダ パラメーター リストの前に `async` 修飾子を追加します。</span><span class="sxs-lookup"><span data-stu-id="6977d-149">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="6977d-150">非同期メソッドの作成および使用方法の詳細については、「[Async および Await を使用した非同期プログラミング](../../programming-guide/concepts/async/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6977d-150">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="6977d-151">ラムダ式とタプル</span><span class="sxs-lookup"><span data-stu-id="6977d-151">Lambda expressions and tuples</span></span>

<span data-ttu-id="6977d-152">C# 7.0 以降、C# 言語には、[タプル](../builtin-types/value-tuples.md)のサポートが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="6977d-152">Starting with C# 7.0, the C# language provides built-in support for [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="6977d-153">タプルは、ラムダ式への引数として指定できるほか、ラムダ式で返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="6977d-153">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="6977d-154">場合によっては、C# コンパイラは、型の推定を使用して、タプル コンポーネントの型を判定することもあります。</span><span class="sxs-lookup"><span data-stu-id="6977d-154">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="6977d-155">タプルを定義するには、そのコンポーネントのコンマ区切りリストをかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="6977d-155">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="6977d-156">次の例では、3 つのコンポーネントを持つタプルを使用して、ラムダ式に連続した数値を渡します。このラムダ式により、各値が 2 倍になり、乗算の結果を格納する 3 つのコンポーネントを持つタプルが返されます。</span><span class="sxs-lookup"><span data-stu-id="6977d-156">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="6977d-157">通常、タプルのフィールド名は `Item1`、`Item2` のようになります。ただし、次の例のとおり、名前付きのコンポーネントを持つタプルを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="6977d-157">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](snippets/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="6977d-158">C# のタプルの詳細については、[タプル型](../../language-reference/builtin-types/value-tuples.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6977d-158">For more information about C# tuples, see [Tuple types](../../language-reference/builtin-types/value-tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="6977d-159">標準クエリ演算子を使用したラムダ</span><span class="sxs-lookup"><span data-stu-id="6977d-159">Lambdas with the standard query operators</span></span>

<span data-ttu-id="6977d-160">いくつかある実装の中で特に、LINQ to Objects は、汎用デリゲートの <xref:System.Func%601> ファミリに属する型の入力パラメーターを持ちます。</span><span class="sxs-lookup"><span data-stu-id="6977d-160">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="6977d-161">これらのデリゲートは、型パラメーターを使用して、入力パラメーターの数と型に加え、デリゲートの戻り値の型を定義します。</span><span class="sxs-lookup"><span data-stu-id="6977d-161">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="6977d-162">`Func` デリゲートは、ソース データのセット内の各要素に適用されるユーザー定義の式をカプセル化する場合に非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="6977d-162">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="6977d-163">たとえば、<xref:System.Func%602>デリゲート型を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="6977d-163">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="6977d-164">このデリゲートを `Func<int, bool>` としてインスタンス化できます。 `int` は入力パラメーター、`bool` は戻り値です。</span><span class="sxs-lookup"><span data-stu-id="6977d-164">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="6977d-165">戻り値は必ず最後の型パラメーターで指定されます。</span><span class="sxs-lookup"><span data-stu-id="6977d-165">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="6977d-166">たとえば、`Func<int, string, bool>` は 2 つの入力パラメーター ( `int` と `string`) と戻り値の型 `bool` を持つデリゲートを定義しています。</span><span class="sxs-lookup"><span data-stu-id="6977d-166">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="6977d-167">次の `Func` デリゲートを呼び出すと、入力パラメーターが 5 に等しいかどうかを示す true または false が返されます。</span><span class="sxs-lookup"><span data-stu-id="6977d-167">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="6977d-168">たとえば、<xref:System.Linq.Queryable> 型で定義された標準クエリ演算子において、引数型が <xref:System.Linq.Expressions.Expression%601> の場合もラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-168">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="6977d-169"><xref:System.Linq.Expressions.Expression%601> 引数を指定すると、ラムダは式ツリーにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="6977d-169">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="6977d-170">次の例では、<xref:System.Linq.Enumerable.Count%2A> 標準クエリ演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="6977d-170">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="6977d-171">入力パラメーターの型はコンパイラが推論できますが、明示的に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="6977d-171">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="6977d-172">この特定のラムダ式は、2 で除算したときに剰余が 1 になる整数 (`n`) をカウントします。</span><span class="sxs-lookup"><span data-stu-id="6977d-172">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="6977d-173">次の例では、`numbers` 配列内で 9 より前にある要素をすべて含むシーケンスを作成します。これは、9 がシーケンス内で条件を満たさない最初の数値であるためです。</span><span class="sxs-lookup"><span data-stu-id="6977d-173">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="6977d-174">次の例では、複数の入力パラメーターをかっこで囲んで指定します。</span><span class="sxs-lookup"><span data-stu-id="6977d-174">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="6977d-175">このメソッドは、値が `numbers` 配列内のその位置を表す序数よりも小さい数値が出現するまで、その配列に含まれるすべての要素を返します。</span><span class="sxs-lookup"><span data-stu-id="6977d-175">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](snippets/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="6977d-176">ラムダ式の型の推定</span><span class="sxs-lookup"><span data-stu-id="6977d-176">Type inference in lambda expressions</span></span>

<span data-ttu-id="6977d-177">ラムダを記述する際、多くの場合は入力パラメーターの型を指定する必要はありません。これは、ラムダ本体やパラメーターの型など C# 言語仕様に記述されている要素に基づいて、コンパイラが型を推定できるためです。</span><span class="sxs-lookup"><span data-stu-id="6977d-177">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="6977d-178">ほとんどの標準クエリ演算子では、最初の入力がソース シーケンス内の要素の型です。</span><span class="sxs-lookup"><span data-stu-id="6977d-178">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="6977d-179">`IEnumerable<Customer>` を問い合わせると、入力変数は `Customer` オブジェクトであると推論されます。これは、そのメソッドとプロパティにアクセスできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6977d-179">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="6977d-180">ラムダの型の推定の一般規則は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6977d-180">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="6977d-181">ラムダにはデリゲート型と同じ数のパラメーターが含まれていなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6977d-181">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="6977d-182">ラムダに含まれる各入力パラメーターは、対応するデリゲート パラメーターに暗黙的に変換できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6977d-182">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="6977d-183">ラムダの戻り値 (ある場合) は、デリゲートの戻り値の型に暗黙的に変換できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6977d-183">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="6977d-184">共通型システムには "ラムダ式" の概念が組み込まれていないため、ラムダ式自体は型を持ちません。</span><span class="sxs-lookup"><span data-stu-id="6977d-184">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="6977d-185">しかし、変則的ではあってもラムダ式の "型" を表現できると都合が良い場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6977d-185">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="6977d-186">このような場合の型は、ラムダ式の変換後のデリゲート型または <xref:System.Linq.Expressions.Expression> 型を指します。</span><span class="sxs-lookup"><span data-stu-id="6977d-186">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="6977d-187">ラムダ式における外部変数のキャプチャと変数のスコープ</span><span class="sxs-lookup"><span data-stu-id="6977d-187">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="6977d-188">ラムダでは "*外部変数*" を参照できます。</span><span class="sxs-lookup"><span data-stu-id="6977d-188">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="6977d-189">それは、そのラムダ式を定義しているメソッドのスコープ内にある変数、またはそのラムダ式を含む型のスコープ内にある変数です。</span><span class="sxs-lookup"><span data-stu-id="6977d-189">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="6977d-190">こうして取り込まれた変数は、ラムダ式で使用するために格納されます。これは、変数がスコープ外に出てガベージ コレクトされる場合でも変わりません。</span><span class="sxs-lookup"><span data-stu-id="6977d-190">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="6977d-191">外部変数は、ラムダ式で使用される前に明示的に代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6977d-191">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="6977d-192">次の例は、こうした規則を示しています。</span><span class="sxs-lookup"><span data-stu-id="6977d-192">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](snippets/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="6977d-193">ラムダ式における変数のスコープには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="6977d-193">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="6977d-194">取り込まれた変数は、その変数を参照するデリゲートがガベージ コレクションの対象になるまでガベージ コレクトされません。</span><span class="sxs-lookup"><span data-stu-id="6977d-194">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="6977d-195">ラムダ式内に導入された変数は、外側のメソッドでは参照できません。</span><span class="sxs-lookup"><span data-stu-id="6977d-195">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="6977d-196">ラムダ式は、外側のメソッドから [in](../keywords/in-parameter-modifier.md)、[ref](../keywords/ref.md)、または [out](../keywords/out-parameter-modifier.md) パラメーターを直接取り込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="6977d-196">A lambda expression cannot directly capture an [in](../keywords/in-parameter-modifier.md), [ref](../keywords/ref.md), or [out](../keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="6977d-197">ラムダ式に含まれる [return](../keywords/return.md) ステートメントで外側のメソッドが戻ることはありません。</span><span class="sxs-lookup"><span data-stu-id="6977d-197">A [return](../keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="6977d-198">ジャンプ先がラムダ式ブロックの外側にある場合は、ラムダ式に [goto](../keywords/goto.md)、[break](../keywords/break.md)、または [continue](../keywords/continue.md) ステートメントを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="6977d-198">A lambda expression cannot contain a [goto](../keywords/goto.md), [break](../keywords/break.md), or [continue](../keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="6977d-199">また、ジャンプ先がブロックの内部にある場合に、ラムダ式ブロックの外部でジャンプ ステートメントを使用するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="6977d-199">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

<span data-ttu-id="6977d-200">C# 9.0 以降では、ラムダ式に `static` 修飾子を適用して、ラムダによる意図しないローカル変数またはインスタンスの状態のキャプチャを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="6977d-200">Beginning with C# 9.0, you can apply the `static` modifier to a lambda expression to prevent unintentional capture of local variables or instance state by the lambda:</span></span>

:::code language="csharp" source="snippets/lambda-expressions/GeneralExamples.cs" id="SnippetStatic":::

<span data-ttu-id="6977d-201">静的ラムダでは外側のスコープからローカル変数またはインスタンスの状態をキャプチャすることはできませんが、静的メンバーと定数の定義は参照することができます。</span><span class="sxs-lookup"><span data-stu-id="6977d-201">A static lambda can't capture local variables or instance state from enclosing scopes, but may reference static members and constant definitions.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6977d-202">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6977d-202">C# language specification</span></span>

<span data-ttu-id="6977d-203">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の[無名関数の式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6977d-203">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="6977d-204">C# 9.0 で追加された機能の詳細については、機能の提案に関する次の記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6977d-204">For more information about features added in C# 9.0, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="6977d-205">ラムダ ディスカード パラメーター</span><span class="sxs-lookup"><span data-stu-id="6977d-205">Lambda discard parameters</span></span>](~/_csharplang/proposals/csharp-9.0/lambda-discard-parameters.md)
- [<span data-ttu-id="6977d-206">静的な匿名関数</span><span class="sxs-lookup"><span data-stu-id="6977d-206">Static anonymous functions</span></span>](~/_csharplang/proposals/csharp-9.0/static-anonymous-functions.md)

## <a name="see-also"></a><span data-ttu-id="6977d-207">関連項目</span><span class="sxs-lookup"><span data-stu-id="6977d-207">See also</span></span>

- [<span data-ttu-id="6977d-208">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6977d-208">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6977d-209">C# の演算子と式</span><span class="sxs-lookup"><span data-stu-id="6977d-209">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="6977d-210">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6977d-210">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="6977d-211">式ツリー</span><span class="sxs-lookup"><span data-stu-id="6977d-211">Expression Trees</span></span>](../../programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="6977d-212">ローカル関数とラムダ式の比較</span><span class="sxs-lookup"><span data-stu-id="6977d-212">Local functions vs. lambda expressions</span></span>](../../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="6977d-213">Visual Studio 2008 C# Samples (Visual Studio 2008 の C# サンプル) (LINQ サンプル クエリ ファイルと XQuery プログラムを参照してください)</span><span class="sxs-lookup"><span data-stu-id="6977d-213">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
