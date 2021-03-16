---
title: 関数
description: F# での関数と、F# で共通の関数型プログラミング コンストラクトをサポートする方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: e49183e0634dee1750757abadbfe9e9c824f51a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596475"
---
# <a name="functions"></a><span data-ttu-id="a59be-103">関数</span><span class="sxs-lookup"><span data-stu-id="a59be-103">Functions</span></span>

<span data-ttu-id="a59be-104">関数は、あらゆるプログラミング言語においてプログラムの実行の基本となる単位です。</span><span class="sxs-lookup"><span data-stu-id="a59be-104">Functions are the fundamental unit of program execution in any programming language.</span></span> <span data-ttu-id="a59be-105">他の言語の場合と同様に、F# の関数にもそれぞれ名前と本体があり、パラメーターや引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a59be-105">As in other languages, an F# function has a name, can have parameters and take arguments, and has a body.</span></span> <span data-ttu-id="a59be-106">F# ではさらに、関数型プログラミング構成要素もサポートしています。たとえば、関数を値として処理したり、名前のない関数を式で使用したりできます。また、関数の合成による新しい関数の作成、カリー化関数、関数の引数の部分適用による関数の暗黙の定義などがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a59be-106">F# also supports functional programming constructs such as treating functions as values, using unnamed functions in expressions, composition of functions to form new functions, curried functions, and the implicit definition of functions by way of the partial application of function arguments.</span></span>

<span data-ttu-id="a59be-107">関数を定義するには `let` キーワードを使用します。再帰関数の場合は、`let rec` というキーワードの組み合わせを使用します。</span><span class="sxs-lookup"><span data-stu-id="a59be-107">You define functions by using the `let` keyword, or, if the function is recursive, the `let rec` keyword combination.</span></span>

## <a name="syntax"></a><span data-ttu-id="a59be-108">構文</span><span class="sxs-lookup"><span data-stu-id="a59be-108">Syntax</span></span>

```fsharp
// Non-recursive function definition.
let [inline] function-name parameter-list [ : return-type ] = function-body
// Recursive function definition.
let rec function-name parameter-list = recursive-function-body
```

## <a name="remarks"></a><span data-ttu-id="a59be-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="a59be-109">Remarks</span></span>

<span data-ttu-id="a59be-110">*function-name* は、関数を表す識別子です。</span><span class="sxs-lookup"><span data-stu-id="a59be-110">The *function-name* is an identifier that represents the function.</span></span> <span data-ttu-id="a59be-111">*parameter-list* は、スペースで区切られた一連のパラメーターで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-111">The *parameter-list* consists of successive parameters that are separated by spaces.</span></span> <span data-ttu-id="a59be-112">「パラメーター」で説明するように、各パラメーターの明示的な型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a59be-112">You can specify an explicit type for each parameter, as described in the Parameters section.</span></span> <span data-ttu-id="a59be-113">特定の引数型を指定しない場合は、コンパイラによって型が関数本体から推測されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-113">If you do not specify a specific argument type, the compiler attempts to infer the type from the function body.</span></span> <span data-ttu-id="a59be-114">*function-body* は式で構成されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-114">The *function-body* consists of an expression.</span></span> <span data-ttu-id="a59be-115">関数本体を構成する式は、通常、複数の式から成る複合式で、その最後の式が戻り値になります。</span><span class="sxs-lookup"><span data-stu-id="a59be-115">The expression that makes up the function body is typically a compound expression consisting of a number of expressions that culminate in a final expression that is the return value.</span></span> <span data-ttu-id="a59be-116">*return-type* では、コロンの後に戻り値の型を指定します。これは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="a59be-116">The *return-type* is a colon followed by a type and is optional.</span></span> <span data-ttu-id="a59be-117">戻り値の型を明示的に指定しない場合は、コンパイラによって最後の式から特定されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-117">If you do not specify the type of the return value explicitly, the compiler determines the return type from the final expression.</span></span>

<span data-ttu-id="a59be-118">単純な関数定義は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a59be-118">A simple function definition resembles the following:</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="a59be-119">この例では、関数の名前は `f`、引数は `x`、引数の型は `int`、関数本体は `x + 1`、戻り値の型は `int` です。</span><span class="sxs-lookup"><span data-stu-id="a59be-119">In the previous example, the function name is `f`, the argument is `x`, which has type `int`, the function body is `x + 1`, and the return value is of type `int`.</span></span>

<span data-ttu-id="a59be-120">関数は、`inline` としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="a59be-120">Functions can be marked `inline`.</span></span> <span data-ttu-id="a59be-121">`inline` の詳細については、「[Inline Functions](inline-functions.md)」(インライン関数) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a59be-121">For information about `inline`, see [Inline Functions](inline-functions.md).</span></span>

## <a name="scope"></a><span data-ttu-id="a59be-122">スコープ</span><span class="sxs-lookup"><span data-stu-id="a59be-122">Scope</span></span>

<span data-ttu-id="a59be-123">モジュール スコープ以外のスコープの任意のレベルでは、値または関数の名前を再利用してもエラーになりません。</span><span class="sxs-lookup"><span data-stu-id="a59be-123">At any level of scope other than module scope, it is not an error to reuse a value or function name.</span></span> <span data-ttu-id="a59be-124">名前を再利用する場合、後から宣言した名前が前に宣言した名前をシャドウします。</span><span class="sxs-lookup"><span data-stu-id="a59be-124">If you reuse a name, the name declared later shadows the name declared earlier.</span></span> <span data-ttu-id="a59be-125">ただし、モジュールの最上位のスコープでは名前が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a59be-125">However, at the top level scope in a module, names must be unique.</span></span> <span data-ttu-id="a59be-126">たとえば次のコードは、モジュール スコープではエラーになりますが、関数内ではエラーになりません。</span><span class="sxs-lookup"><span data-stu-id="a59be-126">For example, the following code produces an error when it appears at module scope, but not when it appears inside a function:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet101.fs)]

<span data-ttu-id="a59be-127">しかし、次のコードはどのスコープ レベルでも許容されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-127">But the following code is acceptable at any level of scope:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet102.fs)]

### <a name="parameters"></a><span data-ttu-id="a59be-128">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a59be-128">Parameters</span></span>

<span data-ttu-id="a59be-129">パラメーターの名前は、関数名の後に指定されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-129">Names of parameters are listed after the function name.</span></span> <span data-ttu-id="a59be-130">次の例のように、パラメーターの型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a59be-130">You can specify a type for a parameter, as shown in the following example:</span></span>

```fsharp
let f (x : int) = x + 1
```

<span data-ttu-id="a59be-131">型を指定する場合は、パラメーターの名前の後にコロンで区切って指定します。</span><span class="sxs-lookup"><span data-stu-id="a59be-131">If you specify a type, it follows the name of the parameter and is separated from the name by a colon.</span></span> <span data-ttu-id="a59be-132">パラメーターの型を省略した場合、パラメーターの型がコンパイラによって推論されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-132">If you omit the type for the parameter, the parameter type is inferred by the compiler.</span></span> <span data-ttu-id="a59be-133">たとえば、次の関数定義で、1 の型が `int` であるため、引数 `x` の型は `int` と推論されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-133">For example, in the following function definition, the argument `x` is inferred to be of type `int` because 1 is of type `int`.</span></span>

```fsharp
let f x = x + 1
```

<span data-ttu-id="a59be-134">ただし、コンパイラは、可能な限り、関数を汎用的にしようとします。</span><span class="sxs-lookup"><span data-stu-id="a59be-134">However, the compiler will attempt to make the function as generic as possible.</span></span> <span data-ttu-id="a59be-135">たとえば次のようなコードがあるとします。</span><span class="sxs-lookup"><span data-stu-id="a59be-135">For example, note the following code:</span></span>

```fsharp
let f x = (x, x)
```

<span data-ttu-id="a59be-136">関数は、任意の型の 1 つの引数からタプルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a59be-136">The function creates a tuple from one argument of any type.</span></span> <span data-ttu-id="a59be-137">型が指定されていないために、任意の引数の型と関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a59be-137">Because the type is not specified, the function can be used with any argument type.</span></span> <span data-ttu-id="a59be-138">詳細については、「[自動ジェネリック化](../generics/automatic-generalization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a59be-138">For more information, see [Automatic Generalization](../generics/automatic-generalization.md).</span></span>

## <a name="function-bodies"></a><span data-ttu-id="a59be-139">関数本体</span><span class="sxs-lookup"><span data-stu-id="a59be-139">Function Bodies</span></span>

<span data-ttu-id="a59be-140">関数本体には、ローカル変数と関数の定義を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a59be-140">A function body can contain definitions of local variables and functions.</span></span> <span data-ttu-id="a59be-141">それらの変数と関数のスコープは、現在の関数の本体内に限られます。</span><span class="sxs-lookup"><span data-stu-id="a59be-141">Such variables and functions are in scope in the body of the current function but not outside it.</span></span> <span data-ttu-id="a59be-142">軽量構文オプションを有効にしている場合は、次の例に示すように、定義が関数本体に含まれていることをインデントによって示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a59be-142">When you have the lightweight syntax option enabled, you must use indentation to indicate that a definition is in a function body, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet103.fs)]

<span data-ttu-id="a59be-143">詳細については、「[コードのフォーマットに関するガイドライン](../../style-guide/formatting.md)」および「[Verbose Syntax](../verbose-syntax.md)」 (冗語構文) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a59be-143">For more information, see [Code Formatting Guidelines](../../style-guide/formatting.md) and [Verbose Syntax](../verbose-syntax.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="a59be-144">戻り値</span><span class="sxs-lookup"><span data-stu-id="a59be-144">Return Values</span></span>

<span data-ttu-id="a59be-145">コンパイラは、関数本体の最後の式を使用して戻り値とその型を特定します。</span><span class="sxs-lookup"><span data-stu-id="a59be-145">The compiler uses the final expression in a function body to determine the return value and type.</span></span> <span data-ttu-id="a59be-146">最後の式の型が前の式から推論される場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a59be-146">The compiler might infer the type of the final expression from previous expressions.</span></span> <span data-ttu-id="a59be-147">前のセクションの関数 `cylinderVolume` では、`pi` の型は、リテラル `3.14159` の型から `float` と特定されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-147">In the function `cylinderVolume`, shown in the previous section, the type of `pi` is determined from the type of the literal `3.14159` to be `float`.</span></span> <span data-ttu-id="a59be-148">コンパイラは、`pi` の型を使用して、式 `h * pi * r * r` の型が `float` であると判断します。</span><span class="sxs-lookup"><span data-stu-id="a59be-148">The compiler uses the type of `pi` to determine the type of the expression `h * pi * r * r` to be `float`.</span></span> <span data-ttu-id="a59be-149">このため、関数全体の戻り値の型が `float` になります。</span><span class="sxs-lookup"><span data-stu-id="a59be-149">Therefore, the overall return type of the function is `float`.</span></span>

<span data-ttu-id="a59be-150">戻り値を明示的に指定するには、次のようにコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="a59be-150">To specify the return value explicitly, write the code as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet105.fs)]

<span data-ttu-id="a59be-151">上記のコードが書き込まれると、コンパイラは関数全体に **float** を適用します。パラメーターの型にも適用する場合は、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a59be-151">As the code is written above, the compiler applies **float** to the entire function; if you mean to apply it to the parameter types as well, use the following code:</span></span>

```fsharp
let cylinderVolume (radius : float) (length : float) : float
```

## <a name="calling-a-function"></a><span data-ttu-id="a59be-152">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="a59be-152">Calling a Function</span></span>

<span data-ttu-id="a59be-153">関数を呼び出すには、関数名の後にスペースを入れ、その後にスペースで区切った引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a59be-153">You call functions by specifying the function name followed by a space and then any arguments separated by spaces.</span></span> <span data-ttu-id="a59be-154">たとえば、関数 **cylinderVolume** を呼び出して結果を値 **vol** に割り当てるには、次のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="a59be-154">For example, to call the function **cylinderVolume** and assign the result to the value **vol**, you write the following code:</span></span>

```fsharp
let vol = cylinderVolume 2.0 3.0
```

## <a name="partial-application-of-arguments"></a><span data-ttu-id="a59be-155">引数の部分適用</span><span class="sxs-lookup"><span data-stu-id="a59be-155">Partial Application of Arguments</span></span>

<span data-ttu-id="a59be-156">指定されている数より少ない数の引数を渡すと、残りの引数を使用する新しい関数が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-156">If you supply fewer than the specified number of arguments, you create a new function that expects the remaining arguments.</span></span> <span data-ttu-id="a59be-157">これは、*カリー化* と呼ばれる引数の処理方法で、F# のような関数型プログラミング言語の特徴の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="a59be-157">This method of handling arguments is referred to as *currying* and is a characteristic of functional programming languages like F#.</span></span> <span data-ttu-id="a59be-158">たとえば、半径がそれぞれ **2.0** と **3.0** の 2 つのパイプを使用しているとします。</span><span class="sxs-lookup"><span data-stu-id="a59be-158">For example, suppose you are working with two sizes of pipe: one has a radius of **2.0** and the other has a radius of **3.0**.</span></span> <span data-ttu-id="a59be-159">次のようにして、パイプの体積を特定する関数を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="a59be-159">You could create functions that determine the volume of pipe as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet106.fs)]

<span data-ttu-id="a59be-160">その後、必要に応じて、2 つのサイズのパイプのさまざまな長さを追加の引数として指定します。</span><span class="sxs-lookup"><span data-stu-id="a59be-160">You would then supply the additional argument as needed for various lengths of pipe of the two different sizes:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet107.fs)]

## <a name="recursive-functions"></a><span data-ttu-id="a59be-161">再帰関数</span><span class="sxs-lookup"><span data-stu-id="a59be-161">Recursive Functions</span></span>

<span data-ttu-id="a59be-162">*再帰関数* はそれらの関数自体を呼び出す関数です。</span><span class="sxs-lookup"><span data-stu-id="a59be-162">*Recursive functions* are functions that call themselves.</span></span> <span data-ttu-id="a59be-163">再帰関数を使用するには、**let** キーワードの後に **rec** キーワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a59be-163">They require that you specify the **rec** keyword following the **let** keyword.</span></span> <span data-ttu-id="a59be-164">関数の本体から再帰関数を呼び出す方法は、他の関数呼び出しの場合と変わりません。</span><span class="sxs-lookup"><span data-stu-id="a59be-164">Invoke the recursive function from within the body of the function just as you would invoke any function call.</span></span> <span data-ttu-id="a59be-165">次の再帰関数は、*n*<sup></sup> 番目のフィボナッチ数を計算します。</span><span class="sxs-lookup"><span data-stu-id="a59be-165">The following recursive function computes the *n*<sup>th</sup> Fibonacci number.</span></span> <span data-ttu-id="a59be-166">フィボナッチ数列は、古代から知られている数列で、数例の各数値が、前の 2 つの連続する数値の和になります。</span><span class="sxs-lookup"><span data-stu-id="a59be-166">The Fibonacci number sequence has been known since antiquity and is a sequence in which each successive number is the sum of the previous two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet108.fs)]

<span data-ttu-id="a59be-167">再帰関数は、特殊な手法 (アキュムレータや継続の使用など) を意識して慎重に使用しないと、プログラム スタックのオーバーフローを引き起こしたり、プログラムの実行効率が低下したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a59be-167">Some recursive functions might overflow the program stack or perform inefficiently if you do not write them with care and with awareness of special techniques, such as the use of accumulators and continuations.</span></span>

## <a name="function-values"></a><span data-ttu-id="a59be-168">関数の値</span><span class="sxs-lookup"><span data-stu-id="a59be-168">Function Values</span></span>

<span data-ttu-id="a59be-169">F# では、すべての関数が値と見なされ、実際に、*関数値* と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="a59be-169">In F#, all functions are considered values; in fact, they are known as *function values*.</span></span> <span data-ttu-id="a59be-170">関数は値であるため、他の関数の引数として使用したり、値が使用されるその他のコンテキストで使用したりできます。</span><span class="sxs-lookup"><span data-stu-id="a59be-170">Because functions are values, they can be used as arguments to other functions or in other contexts where values are used.</span></span> <span data-ttu-id="a59be-171">次に関数値を引数として受け取る関数の例を示します。</span><span class="sxs-lookup"><span data-stu-id="a59be-171">Following is an example of a function that takes a function value as an argument:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet109.fs)]

<span data-ttu-id="a59be-172">関数値の型を指定するには、`->` トークンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a59be-172">You specify the type of a function value by using the `->` token.</span></span> <span data-ttu-id="a59be-173">このトークンの左側に引数の型を、右側に戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="a59be-173">On the left side of this token is the type of the argument, and on the right side is the return value.</span></span> <span data-ttu-id="a59be-174">上の例の `apply1` は、関数 `transform` を引数として受け取る関数で、`transform` は、整数を受け取る、別の整数を返す関数です。</span><span class="sxs-lookup"><span data-stu-id="a59be-174">In the previous example, `apply1` is a function that takes a function `transform` as an argument, where `transform` is a function that takes an integer and returns another integer.</span></span> <span data-ttu-id="a59be-175">`apply1` の使用例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="a59be-175">The following code shows how to use `apply1`:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet110.fs)]

<span data-ttu-id="a59be-176">前のコードを実行した後の `result` の値は 101 になります。</span><span class="sxs-lookup"><span data-stu-id="a59be-176">The value of `result` will be 101 after the previous code runs.</span></span>

<span data-ttu-id="a59be-177">複数の引数を指定するには、次の例に示すように、連続する `->` トークンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="a59be-177">Multiple arguments are separated by successive `->` tokens, as shown in the following example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet111.fs)]

<span data-ttu-id="a59be-178">結果は 200 になります。</span><span class="sxs-lookup"><span data-stu-id="a59be-178">The result is 200.</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="a59be-179">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="a59be-179">Lambda Expressions</span></span>

<span data-ttu-id="a59be-180">*ラムダ式* とは、名前のない関数です。</span><span class="sxs-lookup"><span data-stu-id="a59be-180">A *lambda expression* is an unnamed function.</span></span> <span data-ttu-id="a59be-181">前の例では、名前のある関数 **increment** と **mul** を定義しましたが、次のように、代わりにラムダ式を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a59be-181">In the previous examples, instead of defining named functions **increment** and **mul**, you could use lambda expressions as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet112.fs)]

<span data-ttu-id="a59be-182">ラムダ式を定義するには、`fun` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="a59be-182">You define lambda expressions by using the `fun` keyword.</span></span> <span data-ttu-id="a59be-183">ラムダ式は関数定義に似ていますが、引数リストと関数本体の区切りに `=` トークンではなく `->` トークンを使用する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="a59be-183">A lambda expression resembles a function definition, except that instead of the `=` token, the `->` token is used to separate the argument list from the function body.</span></span> <span data-ttu-id="a59be-184">通常の関数定義と同様に、引数の型は、推論されるようにすることも、明示的に指定することもできます。ラムダ式の戻り値の型も、本体の最後の式の型から推論されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-184">As in a regular function definition, the argument types can be inferred or specified explicitly, and the return type of the lambda expression is inferred from the type of the last expression in the body.</span></span> <span data-ttu-id="a59be-185">詳細については、「[ラムダ式: `fun` キーワード](lambda-expressions-the-fun-keyword.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a59be-185">For more information, see [Lambda Expressions: The `fun` Keyword](lambda-expressions-the-fun-keyword.md).</span></span>

## <a name="function-composition-and-pipelining"></a><span data-ttu-id="a59be-186">関数合成とパイプライン処理</span><span class="sxs-lookup"><span data-stu-id="a59be-186">Function Composition and Pipelining</span></span>

<span data-ttu-id="a59be-187">F# の関数は、その他の関数から構成することができます。</span><span class="sxs-lookup"><span data-stu-id="a59be-187">Functions in F# can be composed from other functions.</span></span> <span data-ttu-id="a59be-188">**function1** と **function2** という 2 つの関数を合成すると、**function1** に続いて **function2** を適用する別の関数になります。</span><span class="sxs-lookup"><span data-stu-id="a59be-188">The composition of two functions **function1** and **function2** is another function that represents the application of **function1** followed the application of **function2**:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet113.fs)]

<span data-ttu-id="a59be-189">結果は 202 になります。</span><span class="sxs-lookup"><span data-stu-id="a59be-189">The result is 202.</span></span>

<span data-ttu-id="a59be-190">パイプライン処理を使用すると、複数の関数呼び出しを一連の操作として連結することができます。</span><span class="sxs-lookup"><span data-stu-id="a59be-190">Pipelining enables function calls to be chained together as successive operations.</span></span> <span data-ttu-id="a59be-191">パイプラインは次のように処理されます。</span><span class="sxs-lookup"><span data-stu-id="a59be-191">Pipelining works as follows:</span></span>

```fsharp
let result = 100 |> function1 |> function2
```

<span data-ttu-id="a59be-192">結果は再び 202 になります。</span><span class="sxs-lookup"><span data-stu-id="a59be-192">The result is again 202.</span></span>

<span data-ttu-id="a59be-193">合成演算子は 2 個の関数を受け取り、関数を返します。これに対し、パイプライン演算子は、関数と引数を受け取り、値を返します。</span><span class="sxs-lookup"><span data-stu-id="a59be-193">The composition operators take two functions and return a function; by contrast, the pipeline operators take a function and an argument and return a value.</span></span> <span data-ttu-id="a59be-194">次のコード例は、関数のシグネチャと使用の違いを示すことによって、パイプラインと合成演算子の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="a59be-194">The following code example shows the difference between the pipeline and composition operators by showing the differences in the function signatures and usage.</span></span>

```fsharp
// Function composition and pipeline operators compared.

let addOne x = x + 1
let timesTwo x = 2 * x

// Composition operator
// ( >> ) : ('T1 -> 'T2) -> ('T2 -> 'T3) -> 'T1 -> 'T3
let Compose2 = addOne >> timesTwo

// Backward composition operator
// ( << ) : ('T2 -> 'T3) -> ('T1 -> 'T2) -> 'T1 -> 'T3
let Compose1 = addOne << timesTwo

// Result is 5
let result1 = Compose1 2

// Result is 6
let result2 = Compose2 2

// Pipelining
// Pipeline operator
// ( |> ) : 'T1 -> ('T1 -> 'U) -> 'U
let Pipeline2 x = addOne x |> timesTwo

// Backward pipeline operator
// ( <| ) : ('T -> 'U) -> 'T -> 'U
let Pipeline1 x = addOne <| timesTwo x

// Result is 5
let result3 = Pipeline1 2

// Result is 6
let result4 = Pipeline2 2
```

## <a name="overloading-functions"></a><span data-ttu-id="a59be-195">オーバーロードの対象となる関数</span><span class="sxs-lookup"><span data-stu-id="a59be-195">Overloading Functions</span></span>

<span data-ttu-id="a59be-196">関数ではなく型のメソッドをオーバー ロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="a59be-196">You can overload methods of a type but not functions.</span></span> <span data-ttu-id="a59be-197">詳細については、「[メソッド](../members/methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a59be-197">For more information, see [Methods](../members/methods.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a59be-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="a59be-198">See also</span></span>

- [<span data-ttu-id="a59be-199">値</span><span class="sxs-lookup"><span data-stu-id="a59be-199">Values</span></span>](../values/index.md)
- [<span data-ttu-id="a59be-200">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="a59be-200">F# Language Reference</span></span>](../index.md)
