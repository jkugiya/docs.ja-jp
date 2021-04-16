---
title: 自動ジェネリック化
description: F# で関数の引数や型を自動的にジェネリック化して、可能な場合に複数の型を処理できるようにする方法を説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630626"
---
# <a name="automatic-generalization"></a><span data-ttu-id="0ab7a-103">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="0ab7a-103">Automatic Generalization</span></span>

<span data-ttu-id="0ab7a-104">F# では、型の推定を使用して関数と式の型を評価します。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="0ab7a-105">このトピックでは、F# で関数の引数や型を自動的にジェネリック化して、可能な場合に複数の型を処理できるようにする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="0ab7a-106">自動ジェネリック化</span><span class="sxs-lookup"><span data-stu-id="0ab7a-106">Automatic Generalization</span></span>

<span data-ttu-id="0ab7a-107">F# コンパイラによって関数に対して型の推定が実行されるときには、特定のパラメーターをジェネリックにできるかどうかが判断されます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="0ab7a-108">コンパイラによって各パラメーターが調査され、関数にそのパラメーターの特定の型に対する依存関係があるかどうかが判定されます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="0ab7a-109">ない場合は、型はジェネリックと推論されます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="0ab7a-110">次のコード例では、コンパイラによってジェネリックと推論される関数を示しています。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="0ab7a-111">型は、`'a -> 'a -> 'a` と推論されます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="0ab7a-112">この型により、この関数は、不明である同じ型を持つ 2 つの引数を指定されて、その同じ型の値を返すことがわかります。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="0ab7a-113">前の関数がジェネリックになれる理由の 1 つは、大なり演算子 (`>`) 自体がジェネリックであることです。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="0ab7a-114">大なり演算子のシグネチャは `'a -> 'a -> bool` です。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="0ab7a-115">すべての演算子がジェネリックであるとは限りません。関数内のコードで、あるパラメーター型が非ジェネリック関数または演算子と共に使用されている場合、そのパラメーター型をジェネリック化することはできません。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="0ab7a-116">`max` はジェネリックであるため、次の例に示すように、`int`、`float` などの型で使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="0ab7a-117">ただし、2 つの引数は同じ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="0ab7a-118">シグネチャは `'a -> 'a -> 'a` であり、`'a -> 'b -> 'a` ではありません。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="0ab7a-119">したがって、次のコードでは型が一致しないため、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="0ab7a-120">`max` 関数は、大なり演算子をサポートするどの型でも動作します。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="0ab7a-121">したがって、次のコードに示すように、文字列で使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="0ab7a-122">値制限</span><span class="sxs-lookup"><span data-stu-id="0ab7a-122">Value Restriction</span></span>

<span data-ttu-id="0ab7a-123">コンパイラで自動ジェネリック化が実行されるのは、明示的な引数を持つ完全な関数定義と、単純な不変の値に対してのみです。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="0ab7a-124">つまり、特定の型とするには制約が不十分であるものの、ジェネリック化することもできないコードをコンパイルしようとすると、コンパイラからエラーが発行されるということです。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="0ab7a-125">この問題のエラー メッセージで、値の自動ジェネリック化に関するこの制約は "*値制限*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="0ab7a-126">通常、値制限エラーが発生するのは、コンストラクトをジェネリックにすることを希望しているものの、それをジェネリック化するための情報がコンパイラに不足している場合か、誤って非ジェネリック コンストラクトで十分な型情報を省略してしまった場合です。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="0ab7a-127">値制限エラーの解決策は、型の推定の問題をより十分に制限するために、次のいずれかの方法で、より明示的な情報を提供することです。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="0ab7a-128">値またはパラメーターに明示的な型の注釈を追加することにより、型を非ジェネリックに制約します。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="0ab7a-129">ジェネリック化できないコンストラクトを使ってジェネリック関数を定義していることが問題の場合 (関数合成や、完全適用されていないカリー化関数の引数など)、通常の関数定義として関数を書き直してみてください。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="0ab7a-130">式が複雑すぎてジェネリック化できないことが問題である場合は、使用しない余分なパラメーターを追加して、式を関数にします。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="0ab7a-131">明示的なジェネリック型パラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="0ab7a-132">このオプションはほとんど使用されません。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-132">This option is rarely used.</span></span>

- <span data-ttu-id="0ab7a-133">次のコード例は、これらの各シナリオを示しています。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="0ab7a-134">ケース 1: 式が複雑すぎる。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="0ab7a-135">この例で、リスト `counter` は `int option ref` となるよう意図されていますが、単純な不変の値として定義されていません。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="0ab7a-136">ケース 2: ジェネリック化できないコンストラクトを使用してジェネリック関数を定義する。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="0ab7a-137">この例では、コンストラクトは、関数の引数の部分適用を伴うため、ジェネリック化できません。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="0ab7a-138">ケース 3: 使用されない余分なパラメーターを追加する。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="0ab7a-139">この式はジェネリック化できるほど単純ではないため、コンパイラから値制限エラーが発行されます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="0ab7a-140">ケース 4: 型パラメーターを追加する。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="0ab7a-141">最後のケースでは、値が型関数になり、次に示す例のように、さまざまな型の値を作成するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ab7a-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="0ab7a-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ab7a-142">See also</span></span>

- [<span data-ttu-id="0ab7a-143">型推論</span><span class="sxs-lookup"><span data-stu-id="0ab7a-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="0ab7a-144">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="0ab7a-144">Generics</span></span>](index.md)
- [<span data-ttu-id="0ab7a-145">静的に解決される型パラメーター</span><span class="sxs-lookup"><span data-stu-id="0ab7a-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="0ab7a-146">制約</span><span class="sxs-lookup"><span data-stu-id="0ab7a-146">Constraints</span></span>](constraints.md)
