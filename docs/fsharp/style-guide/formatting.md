---
title: F# コードのフォーマットに関するガイドライン
description: 'F # コードを書式設定するためのガイドラインについて説明します。'
ms.date: 08/31/2020
ms.openlocfilehash: 6f1cf8decbaf02aa7d5e202010d4c240c24bdcf9
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102103674"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="78781-103">F# コードのフォーマットに関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="78781-103">F# code formatting guidelines</span></span>

<span data-ttu-id="78781-104">この記事では、F # コードが次のようになるようにコードを書式設定する方法に関するガイドラインを提供します。</span><span class="sxs-lookup"><span data-stu-id="78781-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="78781-105">より読みやすく</span><span class="sxs-lookup"><span data-stu-id="78781-105">More legible</span></span>
* <span data-ttu-id="78781-106">Visual Studio および他のエディターの書式設定ツールによって適用される規則に従います。</span><span class="sxs-lookup"><span data-stu-id="78781-106">In accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="78781-107">他のコードと同様</span><span class="sxs-lookup"><span data-stu-id="78781-107">Similar to other code online</span></span>

<span data-ttu-id="78781-108">これらのガイドラインは、 [: Ahn-dung Phan](https://github.com/dungpa)による[F # の書式設定規則に関する包括的なガイド](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="78781-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="78781-109">インデントの一般的な規則</span><span class="sxs-lookup"><span data-stu-id="78781-109">General rules for indentation</span></span>

<span data-ttu-id="78781-110">F # では、既定で有意な空白文字が使用されます。</span><span class="sxs-lookup"><span data-stu-id="78781-110">F# uses significant white space by default.</span></span> <span data-ttu-id="78781-111">次のガイドラインは、このような問題の対処方法に関するガイダンスを提供することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="78781-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="78781-112">スペースの使用</span><span class="sxs-lookup"><span data-stu-id="78781-112">Using spaces</span></span>

<span data-ttu-id="78781-113">インデントが必要な場合は、タブではなく、スペースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="78781-114">少なくとも1つのスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="78781-114">At least one space is required.</span></span> <span data-ttu-id="78781-115">組織では、インデントに使用するスペースの数を指定するためのコーディング標準を作成できます。インデントが発生する各レベルで、2つ、3つ、または4個のインデントが行われます。</span><span class="sxs-lookup"><span data-stu-id="78781-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three, or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="78781-116">**インデントごとに4つのスペースをお勧めします。**</span><span class="sxs-lookup"><span data-stu-id="78781-116">**We recommend four spaces per indentation.**</span></span>

<span data-ttu-id="78781-117">ただし、プログラムのインデントは主観的な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="78781-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="78781-118">バリエーションは問題ありませんが、最初に従う必要がある規則は、 *インデントの一貫性* です。</span><span class="sxs-lookup"><span data-stu-id="78781-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="78781-119">一般的に受け入れられているインデントのスタイルを選択し、コードベース全体で使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-white-space"></a><span data-ttu-id="78781-120">空白文字の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-120">Formatting white space</span></span>

<span data-ttu-id="78781-121">F # は空白を区別します。</span><span class="sxs-lookup"><span data-stu-id="78781-121">F# is white space sensitive.</span></span> <span data-ttu-id="78781-122">空白のほとんどのセマンティクスは適切なインデントによってカバーされますが、他にも考慮すべき点があります。</span><span class="sxs-lookup"><span data-stu-id="78781-122">Although most semantics from white space are covered by proper indentation, there are some other things to consider.</span></span>

### <a name="formatting-operators-in-arithmetic-expressions"></a><span data-ttu-id="78781-123">算術式での演算子の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-123">Formatting operators in arithmetic expressions</span></span>

<span data-ttu-id="78781-124">バイナリ算術式の前後には常に空白文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-124">Always use white space around binary arithmetic expressions:</span></span>

```fsharp
let subtractThenAdd x = x - 1 + 3
```

<span data-ttu-id="78781-125">単項 `-` 演算子の直後には、その後に、その値が否定されます。</span><span class="sxs-lookup"><span data-stu-id="78781-125">Unary `-` operators should always be immediately followed by the value they are negating:</span></span>

```fsharp
// OK
let negate x = -x

// Bad
let negateBad x = - x
```

<span data-ttu-id="78781-126">演算子の後に空白文字を追加すると、 `-` 他のユーザーの混乱を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="78781-126">Adding a white-space character after the `-` operator can lead to confusion for others.</span></span>

<span data-ttu-id="78781-127">要約すると、常に次のことが重要になります。</span><span class="sxs-lookup"><span data-stu-id="78781-127">In summary, it's important to always:</span></span>

* <span data-ttu-id="78781-128">バイナリ演算子を空白で囲む</span><span class="sxs-lookup"><span data-stu-id="78781-128">Surround binary operators with white space</span></span>
* <span data-ttu-id="78781-129">単項演算子の後に末尾の空白を含めることはできません</span><span class="sxs-lookup"><span data-stu-id="78781-129">Never have trailing white space after a unary operator</span></span>

<span data-ttu-id="78781-130">二項算術演算子のガイドラインは特に重要です。</span><span class="sxs-lookup"><span data-stu-id="78781-130">The binary arithmetic operator guideline is especially important.</span></span> <span data-ttu-id="78781-131">二項演算子を囲まない `-` と、特定の書式設定の選択肢と組み合わせると、単項演算子として解釈される可能性が `-` あります。</span><span class="sxs-lookup"><span data-stu-id="78781-131">Failing to surround a binary `-` operator, when combined with certain formatting choices, could lead to interpreting it as a unary `-`.</span></span>

### <a name="surround-a-custom-operator-definition-with-white-space"></a><span data-ttu-id="78781-132">カスタム演算子の定義を空白で囲む</span><span class="sxs-lookup"><span data-stu-id="78781-132">Surround a custom operator definition with white space</span></span>

<span data-ttu-id="78781-133">演算子の定義を囲むには、常に空白文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-133">Always use white space to surround an operator definition:</span></span>

```fsharp
// OK
let ( !> ) x f = f x

// Bad
let (!>) x f = f x
```

<span data-ttu-id="78781-134">で始まり、複数の文字を含むカスタム演算子については、コンパイラのあいまいさを `*` 避けるために、定義の先頭に空白を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-134">For any custom operator that starts with `*` and that has more than one character, you need to add a white space to the beginning of the definition to avoid a compiler ambiguity.</span></span> <span data-ttu-id="78781-135">このため、すべての演算子の定義を1つの空白文字で囲むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78781-135">Because of this, we recommend that you simply surround the definitions of all operators with a single white-space character.</span></span>

### <a name="surround-function-parameter-arrows-with-white-space"></a><span data-ttu-id="78781-136">関数パラメーターの矢印を空白で囲む</span><span class="sxs-lookup"><span data-stu-id="78781-136">Surround function parameter arrows with white space</span></span>

<span data-ttu-id="78781-137">関数の署名を定義するときは、記号の周りに空白文字を使用し `->` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-137">When defining the signature of a function, use white space around the `->` symbol:</span></span>

```fsharp
// OK
type MyFun = int -> int -> string

// Bad
type MyFunBad = int->int->string
```

### <a name="surround-function-arguments-with-white-space"></a><span data-ttu-id="78781-138">関数の引数を空白で囲む</span><span class="sxs-lookup"><span data-stu-id="78781-138">Surround function arguments with white space</span></span>

<span data-ttu-id="78781-139">関数を定義する場合は、各引数の前後に空白文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-139">When defining a function, use white space around each argument.</span></span>

```fsharp
// OK
let myFun (a: decimal) b c = a + b + c

// Bad
let myFunBad (a:decimal)(b)c = a + b + c
```

### <a name="avoid-name-sensitive-alignments"></a><span data-ttu-id="78781-140">名前を区別する配置を避ける</span><span class="sxs-lookup"><span data-stu-id="78781-140">Avoid name-sensitive alignments</span></span>

<span data-ttu-id="78781-141">一般に、名前付けの影響を受けるインデントとアラインメントを避けるためにシークします。</span><span class="sxs-lookup"><span data-stu-id="78781-141">In general, seek to avoid indentation and alignment that is sensitive to naming:</span></span>

```fsharp
// OK
let myLongValueName =
    someExpression
    |> anotherExpression


// Bad
let myLongValueName = someExpression
                      |> anotherExpression
```

<span data-ttu-id="78781-142">これは、"バニティ alignment" または "バニティインデント" と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="78781-142">This is sometimes called “vanity alignment” or “vanity indentation”.</span></span> <span data-ttu-id="78781-143">これを回避する主な理由は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="78781-143">The primary reasons for avoiding this are:</span></span>

* <span data-ttu-id="78781-144">重要なコードが一番右に移動します。</span><span class="sxs-lookup"><span data-stu-id="78781-144">Important code is moved far to the right</span></span>
* <span data-ttu-id="78781-145">実際のコードの幅が少なくなっています</span><span class="sxs-lookup"><span data-stu-id="78781-145">There is less width left for the actual code</span></span>
* <span data-ttu-id="78781-146">名前を変更すると配置が解除される</span><span class="sxs-lookup"><span data-stu-id="78781-146">Renaming can break the alignment</span></span>

<span data-ttu-id="78781-147">インデントをと一致させるには、に対して同じ操作を行い `do` / `do!` `let` / `let!` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-147">Do the same for `do`/`do!` in order to keep the indentation consistent with `let`/`let!`.</span></span> <span data-ttu-id="78781-148">クラスでを使用する例を次に示し `do` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-148">Here is an example using `do` in a class:</span></span>

```fsharp
// OK
type Foo () =
    let foo =
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog
    do
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog

// Bad - notice the "do" expression is indented one space less than the `let` expression
type Foo () =
    let foo =
        fooBarBaz
        |> loremIpsumDolorSitAmet
        |> theQuickBrownFoxJumpedOverTheLazyDog
    do fooBarBaz
       |> loremIpsumDolorSitAmet
       |> theQuickBrownFoxJumpedOverTheLazyDog
```

<span data-ttu-id="78781-149">次に示すのは、 `do!` 2 つのスペースのインデントを使用する例です (では、 `do!` 4 つのスペースのインデントを使用する場合の方法に違いはありません)。</span><span class="sxs-lookup"><span data-stu-id="78781-149">Here is an example with `do!` using 2 spaces of indentation (because with `do!` there is coincidentally no difference between the approaches when using 4 spaces of indentation):</span></span>

```fsharp
// OK
async {
  let! foo =
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
  do!
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
}

// Bad - notice the "do!" expression is indented two spaces more than the `let!` expression
async {
  let! foo =
    fooBarBaz
    |> loremIpsumDolorSitAmet
    |> theQuickBrownFoxJumpedOverTheLazyDog
  do! fooBarBaz
      |> loremIpsumDolorSitAmet
      |> theQuickBrownFoxJumpedOverTheLazyDog
}
```

### <a name="place-parameters-on-a-new-line-for-long-definitions"></a><span data-ttu-id="78781-150">長い定義のために新しい行にパラメーターを配置する</span><span class="sxs-lookup"><span data-stu-id="78781-150">Place parameters on a new line for long definitions</span></span>

<span data-ttu-id="78781-151">長い関数定義がある場合は、パラメーターを新しい行に配置し、それに続くパラメーターのインデントレベルと一致するようにインデントを設定します。</span><span class="sxs-lookup"><span data-stu-id="78781-151">If you have a long function definition, place the parameters on new lines and indent them to match the indentation level of the subsequent parameter.</span></span>

```fsharp
module M =
    let longFunctionWithLotsOfParameters
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method follows

    let longFunctionWithLotsOfParametersAndReturnType
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        : ReturnType =
        // ... the body of the method follows

    let longFunctionWithLongTupleParameter
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) =
        // ... the body of the method follows

    let longFunctionWithLongTupleParameterAndReturnType
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) : ReturnType =
        // ... the body of the method follows
```

<span data-ttu-id="78781-152">これは、組を使用するメンバー、コンストラクター、およびパラメーターにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="78781-152">This also applies to members, constructors, and parameters using tuples:</span></span>

```fsharp
type TM() =
    member _.LongMethodWithLotsOfParameters
        (
            aVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse,
            aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse
        ) =
        // ... the body of the method

type TC
    (
        aVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aSecondVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse,
        aThirdVeryLongCtorParam: AVeryLongTypeThatYouNeedToUse
    ) =
    // ... the body of the class follows
```

<span data-ttu-id="78781-153">パラメーターを修飾する場合は、 `=` 新しい行に戻り値の型と共に文字を配置します。</span><span class="sxs-lookup"><span data-stu-id="78781-153">If the parameters are currified, place the `=` character along with any return type on a new line:</span></span>

```fsharp
type C() =
    member _.LongMethodWithLotsOfCurrifiedParamsAndReturnType
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        : ReturnType =
        // ... the body of the method
    member _.LongMethodWithLotsOfCurrifiedParams
        (aVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aSecondVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        (aThirdVeryLongParam: AVeryLongTypeThatYouNeedToUse)
        =
        // ... the body of the method
```

<span data-ttu-id="78781-154">これは、長い行を回避する方法です (戻り値の型の名前が長い場合もあります)。パラメーターを追加すると、行の破損が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="78781-154">This is a way to avoid too long lines (in case return type might have long name) and have less line-damage when adding parameters.</span></span>

### <a name="type-annotations"></a><span data-ttu-id="78781-155">型の注釈</span><span class="sxs-lookup"><span data-stu-id="78781-155">Type annotations</span></span>

#### <a name="right-pad-function-argument-type-annotations"></a><span data-ttu-id="78781-156">右埋め込み関数の引数の型の注釈</span><span class="sxs-lookup"><span data-stu-id="78781-156">Right-pad function argument type annotations</span></span>

<span data-ttu-id="78781-157">型の注釈を持つ引数を定義する場合は、シンボルの後に空白文字を使用し `:` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-157">When defining arguments with type annotations, use white space after the `:` symbol:</span></span>

```fsharp
// OK
let complexFunction (a: int) (b: int) c = a + b + c

// Bad
let complexFunctionBad (a :int) (b :int) (c:int) = a + b + c
```

#### <a name="surround-return-type-annotations-with-white-space"></a><span data-ttu-id="78781-158">戻り値の型の注釈を空白で囲む</span><span class="sxs-lookup"><span data-stu-id="78781-158">Surround return type annotations with white space</span></span>

<span data-ttu-id="78781-159">Let バインド関数または値型の注釈 (関数の場合は戻り値の型) では、記号の前後に空白文字を使用し `:` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-159">In a let-bound function or value type annotation (return type in the case of a function), use white space before and after the `:` symbol:</span></span>

```fsharp
// OK
let expensiveToCompute : int = 0 // Type annotation for let-bound value
let myFun (a: decimal) b c : decimal = a + b + c // Type annotation for the return type of a function
// Bad
let expensiveToComputeBad1:int = 1
let expensiveToComputeBad2 :int = 2
let myFunBad (a: decimal) b c:decimal = a + b + c
```

## <a name="formatting-blank-lines"></a><span data-ttu-id="78781-160">空白行の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-160">Formatting blank lines</span></span>

* <span data-ttu-id="78781-161">最上位の関数とクラスの定義を、2つの空白行で区切ります。</span><span class="sxs-lookup"><span data-stu-id="78781-161">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="78781-162">クラス内のメソッド定義は、1つの空白行で区切られます。</span><span class="sxs-lookup"><span data-stu-id="78781-162">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="78781-163">関連する関数のグループを分離するために、余分な空白行を使用する (控えめに) ことがあります。</span><span class="sxs-lookup"><span data-stu-id="78781-163">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="78781-164">関連する1つの liners (たとえば、一連のダミーの実装) 間で空白行を省略することができます。</span><span class="sxs-lookup"><span data-stu-id="78781-164">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="78781-165">論理セクションを示すには、関数の空白行を控えめに使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-165">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="78781-166">コメントの書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-166">Formatting comments</span></span>

<span data-ttu-id="78781-167">一般に、ML スタイルのブロックコメントに対しては、複数のダブルスラッシュコメントを優先します。</span><span class="sxs-lookup"><span data-stu-id="78781-167">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="78781-168">インラインコメントは、最初の文字を大文字にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-168">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="78781-169">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="78781-169">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="78781-170">クラスバインド、式バインド、およびパターンバインドの値と関数にキャメルケースを使用する</span><span class="sxs-lookup"><span data-stu-id="78781-170">Use camelCase for class-bound, expression-bound, and pattern-bound values and functions</span></span>

<span data-ttu-id="78781-171">ローカル変数として、またはパターン一致と関数定義でバインドされたすべての名前にキャメルケースを使用するのが一般的で、F # スタイルで受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="78781-171">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="78781-172">クラスのローカルにバインドされた関数は、キャメルケースも使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-172">Locally bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="78781-173">モジュールバインドパブリック関数にキャメルケースを使用する</span><span class="sxs-lookup"><span data-stu-id="78781-173">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="78781-174">モジュールバインド関数がパブリック API の一部である場合、キャメルケースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-174">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="78781-175">内部およびプライベートのモジュールバインド値および関数にキャメルケースを使用する</span><span class="sxs-lookup"><span data-stu-id="78781-175">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="78781-176">次のように、プライベートのモジュールバインド値にはキャメルケースを使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-176">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="78781-177">スクリプト内のアドホック関数</span><span class="sxs-lookup"><span data-stu-id="78781-177">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="78781-178">モジュールまたは型の内部実装を構成する値</span><span class="sxs-lookup"><span data-stu-id="78781-178">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="78781-179">パラメーターにキャメルケースを使用する</span><span class="sxs-lookup"><span data-stu-id="78781-179">Use camelCase for parameters</span></span>

<span data-ttu-id="78781-180">すべてのパラメーターは、.NET の名前付け規則に従ってキャメルケースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-180">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="78781-181">モジュールに対してパスワードを使用する</span><span class="sxs-lookup"><span data-stu-id="78781-181">Use PascalCase for modules</span></span>

<span data-ttu-id="78781-182">すべてのモジュール (最上位レベル、内部、プライベート、入れ子になっている) では、文字を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-182">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="78781-183">型宣言、メンバー、およびラベルに対しては、文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-183">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="78781-184">クラス、インターフェイス、構造体、列挙型、デリゲート、レコード、および判別共用体の名前は、すべて、文字を使用した名前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-184">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="78781-185">レコードと判別共用体の型およびラベル内のメンバーも、文字を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-185">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="78781-186">.NET に固有の構造体には、パスワードを使用する</span><span class="sxs-lookup"><span data-stu-id="78781-186">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="78781-187">名前空間、例外、イベント、およびプロジェクト/ `.dll` 名前でも、文字を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-187">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="78781-188">他の .NET 言語からの消費が、コンシューマーにとって自然なものであるだけでなく、発生する可能性のある .NET の名前付け規則とも一貫しています。</span><span class="sxs-lookup"><span data-stu-id="78781-188">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="78781-189">名前にアンダースコアを使わない</span><span class="sxs-lookup"><span data-stu-id="78781-189">Avoid underscores in names</span></span>

<span data-ttu-id="78781-190">従来、一部の F # ライブラリでは、名前にアンダースコアが使用されていました。</span><span class="sxs-lookup"><span data-stu-id="78781-190">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="78781-191">ただし、これは .NET の名前付け規則と競合するため、広く受け入れられなくなりました。</span><span class="sxs-lookup"><span data-stu-id="78781-191">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="78781-192">ただし、一部の F # プログラマーでは、多くの場合、スコアが大きくなり、履歴上の理由から、許容範囲が重要になります。</span><span class="sxs-lookup"><span data-stu-id="78781-192">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="78781-193">ただし、スタイルは多くの場合、使用するかどうかを選択できる他のユーザーには適用されません。</span><span class="sxs-lookup"><span data-stu-id="78781-193">However, the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="78781-194">1つの例外として、ネイティブコンポーネントとの相互運用 (アンダースコアが共通) があります。</span><span class="sxs-lookup"><span data-stu-id="78781-194">One exception includes interoperating with native components, where underscores are common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="78781-195">標準 F # 演算子を使用する</span><span class="sxs-lookup"><span data-stu-id="78781-195">Use standard F# operators</span></span>

<span data-ttu-id="78781-196">次の演算子は、F # 標準ライブラリで定義されており、同等のを定義する代わりに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-196">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="78781-197">コードを読みやすくし、慣用的なする傾向があるため、これらの演算子を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78781-197">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="78781-198">OCaml または他の関数型プログラミング言語の背景を持つ開発者は、さまざまな表現方法に慣れている場合があります。</span><span class="sxs-lookup"><span data-stu-id="78781-198">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="78781-199">次の一覧は、推奨される F # 演算子をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="78781-199">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="78781-200">`Foo<T>`後置構文 () の場合は、ジェネリック () のプレフィックス構文を使用します `T Foo`</span><span class="sxs-lookup"><span data-stu-id="78781-200">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="78781-201">F # では、ジェネリック型の名前付けの後置形式の ML スタイル (たとえば `int list` ) と、プレフィックス .net スタイル (たとえば、) の両方が継承され `list<int>` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-201">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="78781-202">次の5つの特定の種類を除き、.NET スタイルを優先します。</span><span class="sxs-lookup"><span data-stu-id="78781-202">Prefer the .NET style, except for five specific types:</span></span>

1. <span data-ttu-id="78781-203">F # リストの場合は、ではなく、後置形式を使用します `int list` `list<int>` 。</span><span class="sxs-lookup"><span data-stu-id="78781-203">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="78781-204">F # オプションの場合は、ではなく、後置形式を使用します `int option` `option<int>` 。</span><span class="sxs-lookup"><span data-stu-id="78781-204">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="78781-205">F # 値オプションの場合は、ではなく、後置形式を使用し `int voption` `voption<int>` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-205">For F# Value Options, use the postfix form: `int voption` rather than `voption<int>`.</span></span>
4. <span data-ttu-id="78781-206">F # の配列の場合は、またはではなく構文名を使用し `int[]` `int array` `array<int>` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-206">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
5. <span data-ttu-id="78781-207">参照セルの場合 `int ref` は、またはではなくを使用 `ref<int>` `Ref<int>` します。</span><span class="sxs-lookup"><span data-stu-id="78781-207">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="78781-208">それ以外のすべての型については、プレフィックスフォームを使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-208">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="78781-209">タプルの書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-209">Formatting tuples</span></span>

<span data-ttu-id="78781-210">タプルのインスタンス化は、かっこで囲む必要があります。また、この中の区切り記号の後には、1つのスペースが必要です。たとえば、のようになり `(1, 2)` `(x, y, z)` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-210">A tuple instantiation should be parenthesized, and the delimiting commas within it should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="78781-211">通常は、組のパターンマッチングでかっこを省略することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78781-211">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

<span data-ttu-id="78781-212">タプルが関数の戻り値の場合は、通常、かっこを省略することもできます。</span><span class="sxs-lookup"><span data-stu-id="78781-212">It is also commonly accepted to omit parentheses if the tuple is the return value of a function:</span></span>

```fsharp
// OK
let update model msg =
    match msg with
    | 1 -> model + 1, []
    | _ -> model, [ msg ]
```

<span data-ttu-id="78781-213">まとめとして、かっこで囲まれたタプルのインスタンス化を使用しますが、パターンマッチングまたは戻り値に組を使用する場合は、かっこを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78781-213">In summary, prefer parenthesized tuple instantiations, but when using tuples for pattern matching or a return value, it is considered fine to avoid parentheses.</span></span>

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="78781-214">判別共用体宣言の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-214">Formatting discriminated union declarations</span></span>

<span data-ttu-id="78781-215">`|`4 つのスペースで型定義をインデントする:</span><span class="sxs-lookup"><span data-stu-id="78781-215">Indent `|` in type definition by four spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="78781-216">判別共用体の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-216">Formatting discriminated unions</span></span>

<span data-ttu-id="78781-217">かっこで囲まれるパラメーターの前にスペースを使用して、判別共用体のケースを判別します。</span><span class="sxs-lookup"><span data-stu-id="78781-217">Use a space before parenthesized/tupled parameters to discriminated union cases:</span></span>

```fsharp
// OK
let opt = Some ("A", 1)

// Not OK
let opt = Some("A", 1)
```

<span data-ttu-id="78781-218">複数の行に分割されるインスタンス化された判別共用体は、含まれるデータにインデントを含む新しいスコープを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-218">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode (BinaryValue 1, BinaryValue 2),
         BinaryNode (BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="78781-219">右かっこは、新しい行にも指定できます。</span><span class="sxs-lookup"><span data-stu-id="78781-219">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode (BinaryValue 1, BinaryValue 2),
        BinaryNode (BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="78781-220">レコード宣言の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-220">Formatting record declarations</span></span>

<span data-ttu-id="78781-221">`{`4 つのスペースで型定義をインデントし、同じ行でフィールドリストを開始します。</span><span class="sxs-lookup"><span data-stu-id="78781-221">Indent `{` in type definition by four spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

// Unusual in F#
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="78781-222">インターフェイスの実装やレコードのメンバーを宣言する場合は、開始トークンを新しい行に配置し、終了トークンを新しい行に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78781-222">Placing the opening token on a new line and the closing token on a new line is preferable if you are declaring interface implementations or members on the record:</span></span>

```fsharp
// Declaring additional members on PostalAddress
type PostalAddress =
    {
        Address: string
        City: string
        Zip: string
    }
    member x.ZipAndCity = $"{x.Zip} {x.City}"

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface
```

## <a name="formatting-records"></a><span data-ttu-id="78781-223">レコードの書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-223">Formatting records</span></span>

<span data-ttu-id="78781-224">短いレコードは、1行に記述できます。</span><span class="sxs-lookup"><span data-stu-id="78781-224">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="78781-225">ラベルに新しい行を使用する必要があるレコードは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="78781-225">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="78781-226">次の場合は、開始トークンを新しい行に配置し、1つのスコープの上にある [コンテンツ] タブと、新しい行の終了トークンを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78781-226">Placing the opening token on a new line, the contents tabbed over one scope, and the closing token on a new line is preferable if you are:</span></span>

* <span data-ttu-id="78781-227">異なるインデントスコープを持つコード内でのレコードの移動</span><span class="sxs-lookup"><span data-stu-id="78781-227">Moving records around in code with different indentation scopes</span></span>
* <span data-ttu-id="78781-228">関数にパイプする</span><span class="sxs-lookup"><span data-stu-id="78781-228">Piping them into a function</span></span>

```fsharp
let rainbow =
    {
        Boss1 = "Jeffrey"
        Boss2 = "Jeffrey"
        Boss3 = "Jeffrey"
        Boss4 = "Jeffrey"
        Boss5 = "Jeffrey"
        Boss6 = "Jeffrey"
        Boss7 = "Jeffrey"
        Boss8 = "Jeffrey"
        Lackeys = ["Zippy"; "George"; "Bungle"]
    }

type MyRecord =
    {
        SomeField: int
    }
    interface IMyInterface

let foo a =
    a
    |> Option.map
        (fun x ->
            {
                MyField = x
            })
```

<span data-ttu-id="78781-229">リストおよび配列要素にも同じ規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="78781-229">The same rules apply for list and array elements.</span></span>

## <a name="formatting-copy-and-update-record-expressions"></a><span data-ttu-id="78781-230">コピーおよび更新レコード式の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-230">Formatting copy-and-update record expressions</span></span>

<span data-ttu-id="78781-231">コピーと更新のレコード式は依然としてレコードであるため、同様のガイドラインが適用されます。</span><span class="sxs-lookup"><span data-stu-id="78781-231">A copy-and-update record expression is still a record, so similar guidelines apply.</span></span>

<span data-ttu-id="78781-232">短い式は、1行に収めることができます。</span><span class="sxs-lookup"><span data-stu-id="78781-232">Short expressions can fit on one line:</span></span>

```fsharp
let point2 = { point with X = 1; Y = 2 }
```

<span data-ttu-id="78781-233">長い式では、新しい行を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-233">Longer expressions should use new lines:</span></span>

```fsharp
let rainbow2 =
    { rainbow with
        Boss = "Jeffrey"
        Lackeys = [ "Zippy"; "George"; "Bungle" ] }
```

<span data-ttu-id="78781-234">レコードガイダンスと同様に、中かっこに個別の行を追加し、式を使用して1つのスコープを右側にインデントすることもできます。</span><span class="sxs-lookup"><span data-stu-id="78781-234">And as with the record guidance, you may want to dedicate separate lines for the braces and indent one scope to the right with the expression.</span></span> <span data-ttu-id="78781-235">かっこのない省略可能な値をラップするなどの特殊なケースでは、1行に中かっこを続ける必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="78781-235">In some special cases, such as wrapping a value with an optional without parentheses, you may need to keep a brace on one line:</span></span>

```fsharp
type S = { F1: int; F2: string }
type State = { Foo: S option }

let state = { Foo = Some { F1 = 1; F2 = "Hello" } }
let newState =
    {
        state with
            Foo =
                Some {
                    F1 = 0
                    F2 = ""
                }
    }
```

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="78781-236">リストと配列の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-236">Formatting lists and arrays</span></span>

<span data-ttu-id="78781-237">`x :: l`演算子の前後にスペースを使用して記述 `::` `::` します (は挿入演算子で、そのためスペースで囲みます)。</span><span class="sxs-lookup"><span data-stu-id="78781-237">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces).</span></span>

<span data-ttu-id="78781-238">1つの行で宣言されたリストと配列には、左角かっこの前と右角かっこの前にスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="78781-238">List and arrays declared on a single line should have a space after the opening bracket and before the closing bracket:</span></span>

```fsharp
let xs = [ 1; 2; 3 ]
let ys = [| 1; 2; 3; |]
```

<span data-ttu-id="78781-239">2つの異なるかっこで囲まれた演算子の間には、常に少なくとも1つの空白文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-239">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="78781-240">たとえば、との間にはスペースを入れ `[` `{` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-240">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="78781-241">組のリストまたは配列にも同じガイドラインが適用されます。</span><span class="sxs-lookup"><span data-stu-id="78781-241">The same guideline applies for lists or arrays of tuples.</span></span>

<span data-ttu-id="78781-242">複数の行にわたって分割されるリストと配列は、レコードと同様のルールに従います。</span><span class="sxs-lookup"><span data-stu-id="78781-242">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle =
    [|
        [| 1 |]
        [| 1; 1 |]
        [| 1; 2; 1 |]
        [| 1; 3; 3; 1 |]
        [| 1; 4; 6; 4; 1 |]
        [| 1; 5; 10; 10; 5; 1 |]
        [| 1; 6; 15; 20; 15; 6; 1 |]
        [| 1; 7; 21; 35; 35; 21; 7; 1 |]
        [| 1; 8; 28; 56; 70; 56; 28; 8; 1 |]
    |]
```

<span data-ttu-id="78781-243">レコードの場合と同様に、開始角かっこと右角かっこを独自の行で宣言すると、コードの移動や関数へのパイプ処理が容易になります。</span><span class="sxs-lookup"><span data-stu-id="78781-243">And as with records, declaring the opening and closing brackets on their own line will make moving code around and piping into functions easier.</span></span>

<span data-ttu-id="78781-244">プログラムによって配列とリストを生成する場合は、 `->` `do ... yield` 常に値が生成されるタイミングを優先します。</span><span class="sxs-lookup"><span data-stu-id="78781-244">When generating arrays and lists programmatically, prefer `->` over `do ... yield` when a value is always generated:</span></span>

```fsharp
// Preferred
let squares = [ for x in 1..10 -> x * x ]

// Not preferred
let squares' = [ for x in 1..10 do yield x * x ]
```

<span data-ttu-id="78781-245">以前のバージョンの F # 言語で `yield` は、データが条件付きで生成される場合や、連続する式が評価される場合があります。</span><span class="sxs-lookup"><span data-stu-id="78781-245">Older versions of the F# language required specifying `yield` in situations where data may be generated conditionally, or there may be consecutive expressions to be evaluated.</span></span> <span data-ttu-id="78781-246">`yield`古い F # 言語バージョンでコンパイルする必要がある場合を除き、これらのキーワードは省略してください。</span><span class="sxs-lookup"><span data-stu-id="78781-246">Prefer omitting these `yield` keywords unless you must compile with an older F# language version:</span></span>

```fsharp
// Preferred
let daysOfWeek includeWeekend =
    [
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    ]

// Not preferred
let daysOfWeek' includeWeekend =
    [
        yield "Monday"
        yield "Tuesday"
        yield "Wednesday"
        yield "Thursday"
        yield "Friday"
        if includeWeekend then
            yield "Saturday"
            yield "Sunday"
    ]
```

<span data-ttu-id="78781-247">場合によっては、 `do...yield` が読みやすくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="78781-247">In some cases, `do...yield` may aid in readability.</span></span> <span data-ttu-id="78781-248">ただし、このような場合は主観的に考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-248">These cases, though subjective, should be taken into consideration.</span></span>

## <a name="formatting-if-expressions"></a><span data-ttu-id="78781-249">If 式の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-249">Formatting if expressions</span></span>

<span data-ttu-id="78781-250">条件のインデントは、それらを作成する式のサイズと複雑さによって異なります。</span><span class="sxs-lookup"><span data-stu-id="78781-250">Indentation of conditionals depends on the size and complexity of the expressions that make them up.</span></span>
<span data-ttu-id="78781-251">次の場合に1行に記述します。</span><span class="sxs-lookup"><span data-stu-id="78781-251">Write them on one line when:</span></span>

- <span data-ttu-id="78781-252">`cond`、 `e1` 、および `e2` は省略されています。</span><span class="sxs-lookup"><span data-stu-id="78781-252">`cond`, `e1`, and `e2` are short</span></span>
- <span data-ttu-id="78781-253">`e1` と `e2` は式自体ではありません `if/then/else` 。</span><span class="sxs-lookup"><span data-stu-id="78781-253">`e1` and `e2` are not `if/then/else` expressions themselves.</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="78781-254">式のいずれかが複数行または式の場合 `if/then/else` 。</span><span class="sxs-lookup"><span data-stu-id="78781-254">If any of the expressions are multi-line or `if/then/else` expressions.</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="78781-255">とを含む複数の条件 `elif` `else` は、 `if` 1 つの行式の規則に従った場合と同じスコープでインデントされ `if/then/else` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-255">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if` when they follow the rules of the one line `if/then/else` expressions.</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

<span data-ttu-id="78781-256">条件または式のいずれかが複数行の場合、 `if/then/else` 式全体が複数行になります。</span><span class="sxs-lookup"><span data-stu-id="78781-256">If any of the conditions or expressions is multi-line, the entire `if/then/else` expression is multi-line:</span></span>

```fsharp
if cond1 then
    e1
elif cond2 then
    e2
elif cond3 then
    e3
else
    e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="78781-257">パターン一致のコンストラクト</span><span class="sxs-lookup"><span data-stu-id="78781-257">Pattern matching constructs</span></span>

<span data-ttu-id="78781-258">`|`インデントなしで一致の for each 句を使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-258">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="78781-259">式が短い場合は、各部分式も単純である場合は単一行を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="78781-259">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> x
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> x
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="78781-260">パターン一致の矢印の右側にある式が大きすぎる場合は、から1ステップインデントされた次の行に移動し `match` / `|` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-260">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="78781-261">匿名関数のパターンマッチングは、から開始 `function` すると、通常はあまりインデントされません。</span><span class="sxs-lookup"><span data-stu-id="78781-261">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="78781-262">たとえば、次のように1つのスコープをインデントすることは問題ありません。</span><span class="sxs-lookup"><span data-stu-id="78781-262">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map
    (function
        | Abs(x, body) -> 1 + sizeLambda 0 body
        | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
        | Var v -> 1)
```

<span data-ttu-id="78781-263">またはで定義された関数でパターンマッチングを `let` `let rec` 行う場合は `let` 、 `function` キーワードが使用されている場合でも、の開始後に4つのスペースをインデントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-263">Pattern matching in functions defined by `let` or `let rec` should be indented four spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="78781-264">矢印は配置しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78781-264">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="78781-265">Try/with 式の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-265">Formatting try/with expressions</span></span>

<span data-ttu-id="78781-266">例外の種類のパターンマッチングは、と同じレベルでインデントする必要があり `with` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-266">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="78781-267">関数パラメーターアプリケーションの書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-267">Formatting function parameter application</span></span>

<span data-ttu-id="78781-268">一般に、ほとんどの引数は同じ行にあります。</span><span class="sxs-lookup"><span data-stu-id="78781-268">In general, most arguments are provided on the same line:</span></span>

```fsharp
let x = sprintf "\t%s - %i\n\r" x.IngredientName x.Quantity

let printListWithOffset a list1 =
    List.iter (fun elem -> printfn $"%d{a + elem}") list1
```

<span data-ttu-id="78781-269">パイプラインに関係がある場合は、同じ行の引数としてカリー化関数が適用されるので、通常も同じことが言えます。</span><span class="sxs-lookup"><span data-stu-id="78781-269">When pipelines are concerned, the same is typically also true, where a curried function is applied as an argument on the same line:</span></span>

```
let printListWithOffsetPiped a list1 =
    list1
    |> List.iter (fun elem -> printfn $"%d{a + elem}")
```

<span data-ttu-id="78781-270">ただし、読みやすさの問題として、または引数のリストまたは引数名が長すぎるために、新しい行の関数に引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="78781-270">However, you may wish to pass arguments to a function on a new line, as a matter of readability or because the list of arguments or the argument names are too long.</span></span> <span data-ttu-id="78781-271">その場合は、1つのスコープでインデントします。</span><span class="sxs-lookup"><span data-stu-id="78781-271">In that case, indent with one scope:</span></span>

```fsharp

// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="78781-272">ラムダ式の場合は、ラムダ式の本体を新しい行に配置し、十分な長さである場合は、1つのスコープでインデントすることを検討することもできます。</span><span class="sxs-lookup"><span data-stu-id="78781-272">For lambda expressions, you may also want to consider placing the body of a lambda expression on a new line, indented by one scope, if it is long enough:</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn $"%d{a + elem}")
        list1

let printListWithOffsetPiped a list1 =
    list1
    |> List.iter
        (fun elem ->
            printfn $"%d{a + elem}")
```

<span data-ttu-id="78781-273">ラムダ式の本体が複数行の長さである場合は、ローカルスコープの関数にリファクタリングすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="78781-273">If the body of a lambda expression is multiple lines long, you should consider refactoring it into a locally-scoped function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="78781-274">挿入演算子の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-274">Formatting infix operators</span></span>

<span data-ttu-id="78781-275">演算子はスペースで区切ります。</span><span class="sxs-lookup"><span data-stu-id="78781-275">Separate operators by spaces.</span></span> <span data-ttu-id="78781-276">このルールの明確な例外は `!` 、 `.` 演算子と演算子です。</span><span class="sxs-lookup"><span data-stu-id="78781-276">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="78781-277">挿入式は、同じ列に編成することができます。</span><span class="sxs-lookup"><span data-stu-id="78781-277">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators-or-mutable-assignments"></a><span data-ttu-id="78781-278">パイプライン演算子または変更可能な代入の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-278">Formatting pipeline operators or mutable assignments</span></span>

<span data-ttu-id="78781-279">パイプライン `|>` 演算子は、操作対象の式の下にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-279">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat

// Not OK either
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
               |> List.ofArray
               |> List.map (fun assm -> assm.GetTypes())
               |> Array.concat
               |> List.ofArray
               |> List.map (fun t -> t.GetMethods())
               |> Array.concat
```

<span data-ttu-id="78781-280">これは、変更可能な setter にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="78781-280">This also applies to mutable setters:</span></span>

```fsharp
// Preferred approach
ctx.Response.Headers.[HeaderNames.ContentType] <-
    Constants.jsonApiMediaType |> StringValues
ctx.Response.Headers.[HeaderNames.ContentLength] <-
    bytes.Length |> string |> StringValues

// Not OK
ctx.Response.Headers.[HeaderNames.ContentType] <- Constants.jsonApiMediaType
                                                  |> StringValues
ctx.Response.Headers.[HeaderNames.ContentLength] <- bytes.Length
                                                    |> string
                                                    |> StringValues
```

### <a name="formatting-modules"></a><span data-ttu-id="78781-281">モジュールの書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-281">Formatting modules</span></span>

<span data-ttu-id="78781-282">ローカルモジュール内のコードは、モジュールに対して相対的にインデントする必要がありますが、最上位レベルのモジュール内のコードをインデントすることはできません。</span><span class="sxs-lookup"><span data-stu-id="78781-282">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="78781-283">名前空間要素をインデントする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="78781-283">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a * a + b * b

module A2 =
    let function2 a b = a * a - b * b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="78781-284">オブジェクト式およびインターフェイスの書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-284">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="78781-285">オブジェクトの式とインターフェイスは、4つのスペースの後にインデントを設定するのと同じ方法で配置する必要があり `member` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-285">Object expressions and interfaces should be aligned in the same way with `member` being indented after four spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s: String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="78781-286">式の空白の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-286">Formatting white space in expressions</span></span>

<span data-ttu-id="78781-287">F # の式に余分なスペースを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="78781-287">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="78781-288">名前付き引数には、を囲む領域を指定する必要もあり `=` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-288">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```

### <a name="formatting-constructors-static-members-and-member-invocations"></a><span data-ttu-id="78781-289">コンストラクター、静的メンバー、およびメンバー呼び出しの書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-289">Formatting constructors, static members, and member invocations</span></span>

<span data-ttu-id="78781-290">式が短い場合は、引数を空白で区切り、1行に保持します。</span><span class="sxs-lookup"><span data-stu-id="78781-290">If the expression is short, separate arguments with spaces and keep it in one line.</span></span>

```fsharp
let person = new Person(a1, a2)

let myRegexMatch = Regex.Match(input, regex)

let untypedRes = checker.ParseFile(file, source, opts)
```

<span data-ttu-id="78781-291">式が長い場合は、角かっこにインデントするのではなく、改行を使用して1つのスコープをインデントします。</span><span class="sxs-lookup"><span data-stu-id="78781-291">If the expression is long, use newlines and indent one scope, rather than indenting to the bracket.</span></span>

```fsharp
let person =
    new Person(
        argument1,
        argument2
    )

let myRegexMatch =
    Regex.Match(
        "my longer input string with some interesting content in it",
        "myRegexPattern"
    )

let untypedRes =
    checker.ParseFile(
        fileName,
        sourceText,
        parsingOptionsWithDefines
    )
```

## <a name="formatting-attributes"></a><span data-ttu-id="78781-292">属性の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-292">Formatting attributes</span></span>

<span data-ttu-id="78781-293">[属性](../language-reference/attributes.md) はコンストラクトの上に配置されます。</span><span class="sxs-lookup"><span data-stu-id="78781-293">[Attributes](../language-reference/attributes.md) are placed above a construct:</span></span>

```fsharp
[<SomeAttribute>]
type MyClass() = ...

[<RequireQualifiedAccess>]
module M =
    let f x = x

[<Struct>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="78781-294">これらは、XML ドキュメントの後に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-294">They should go after any XML documentation:</span></span>

```fsharp
/// Module with some things in it.
[<RequireQualifiedAccess>]
module M =
    let f x = x
```

### <a name="formatting-attributes-on-parameters"></a><span data-ttu-id="78781-295">パラメーターの属性の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-295">Formatting attributes on parameters</span></span>

<span data-ttu-id="78781-296">属性は、パラメーターにも配置できます。</span><span class="sxs-lookup"><span data-stu-id="78781-296">Attributes can also be placed on parameters.</span></span> <span data-ttu-id="78781-297">この場合は、パラメーターと名前の前に次の行を配置します。</span><span class="sxs-lookup"><span data-stu-id="78781-297">In this case, place then on the same line as the parameter and before the name:</span></span>

```fsharp
// Defines a class that takes an optional value as input defaulting to false.
type C() =
    member _.M([<Optional; DefaultParameterValue(false)>] doSomething: bool)
```

### <a name="formatting-multiple-attributes"></a><span data-ttu-id="78781-298">複数の属性の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-298">Formatting multiple attributes</span></span>

<span data-ttu-id="78781-299">パラメーターではないコンストラクトに複数の属性が適用されている場合は、1行につき1つの属性が存在するように配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-299">When multiple attributes are applied to a construct that is not a parameter, they should be placed such that there is one attribute per line:</span></span>

```fsharp
[<Struct>]
[<IsByRefLike>]
type MyRecord =
    { Label1: int
      Label2: string }
```

<span data-ttu-id="78781-300">パラメーターに適用する場合は、同じ行に配置し、区切り記号で区切る必要があり `;` ます。</span><span class="sxs-lookup"><span data-stu-id="78781-300">When applied to a parameter, they must be on the same line and separated by a `;` separator.</span></span>

## <a name="formatting-literals"></a><span data-ttu-id="78781-301">リテラルの書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-301">Formatting literals</span></span>

<span data-ttu-id="78781-302">属性を使用する[F # リテラル](../language-reference/literals.md)では `Literal` 、属性を独自の行に配置し、文字の名前付けを使用します。</span><span class="sxs-lookup"><span data-stu-id="78781-302">[F# literals](../language-reference/literals.md) using the `Literal` attribute should place the attribute on its own line and use PascalCase naming:</span></span>

```fsharp
[<Literal>]
let Path = __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let MyUrl = "www.mywebsitethatiamworkingwith.com"
```

<span data-ttu-id="78781-303">属性を値と同じ行に配置することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="78781-303">Avoid placing the attribute on the same line as the value.</span></span>

## <a name="formatting-computation-expression-operations"></a><span data-ttu-id="78781-304">計算式の演算の書式設定</span><span class="sxs-lookup"><span data-stu-id="78781-304">Formatting computation expression operations</span></span>

<span data-ttu-id="78781-305">[コンピュテーション式](../language-reference/computation-expressions.md)のカスタム操作を作成する場合は、キャメルケースの名前付けを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78781-305">When creating custom operations for [computation expressions](../language-reference/computation-expressions.md), it is recommended to use camelCase naming:</span></span>

```fsharp
type MathBuilder () =
    member _.Yield _ = 0

    [<CustomOperation("addOne")>]
    member _.AddOne (state: int) =
        state + 1

    [<CustomOperation("subtractOne")>]
    member _.SubtractOne (state: int) =
        state - 1

    [<CustomOperation("divideBy")>]
    member _.DivideBy (state: int, divisor: int) =
        state / divisor

    [<CustomOperation("multiplyBy")>]
    member _.MultiplyBy (state: int, factor: int) =
        state * factor

let math = MathBuilder()

// 10
let myNumber =
    math {
        addOne
        addOne
        addOne

        subtractOne

        divideBy 2

        multiplyBy 10
    }
```

<span data-ttu-id="78781-306">モデル化されているドメインは、最終的に名前付け規則を駆動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78781-306">The domain that's being modeled should ultimately drive the naming convention.</span></span>
<span data-ttu-id="78781-307">別の規則を使用する場合は、その規則を代わりに使用する必要があります慣用的なです。</span><span class="sxs-lookup"><span data-stu-id="78781-307">If it is idiomatic to use a different convention, that convention should be used instead.</span></span>
