---
description: '詳細情報: 位置と名前による引数渡し (Visual Basic)'
title: 位置と名前による引数渡し
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: 2938638bbdeb411bec53f338371d4215140dc4a0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466693"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="849f8-103">位置と名前による引数渡し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="849f8-103">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="849f8-104">`Sub` または `Function` プロシージャを呼び出すときに、引数を "*位置*" (プロシージャの定義に表示されている順序) で渡すことができます。また、位置に関係なく、"*名前*" で渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="849f8-104">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="849f8-105">引数を名前で渡す場合は、引数の宣言名の後にコロンと等号 (`:=`) を入力し、その後に引数の値を指定します。</span><span class="sxs-lookup"><span data-stu-id="849f8-105">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="849f8-106">名前付き引数は任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="849f8-106">You can supply named arguments in any order.</span></span>

<span data-ttu-id="849f8-107">たとえば、次の `Sub` プロシージャは 3 つの引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="849f8-107">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="849f8-108">このプロシージャを呼び出すときに、位置、名前、またはこの両方の組み合わせを使用して引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="849f8-108">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="849f8-109">引数を位置で渡す</span><span class="sxs-lookup"><span data-stu-id="849f8-109">Passing Arguments by Position</span></span>

<span data-ttu-id="849f8-110">次の例に示すように、位置で渡す引数をコンマで区切って指定して、`Display` メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="849f8-110">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="849f8-111">位置引数リストで省略可能な引数を省略する場合は、コンマを使用してその場所を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="849f8-111">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="849f8-112">次の例では、`age` 引数を指定せずに `Display` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="849f8-112">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="849f8-113">引数を名前で渡す</span><span class="sxs-lookup"><span data-stu-id="849f8-113">Passing Arguments by Name</span></span>

<span data-ttu-id="849f8-114">次の例に示すように、名前で渡す引数をコンマで区切って指定して、`Display` メソッドを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="849f8-114">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="849f8-115">このような名前による引数渡しは、省略可能な引数が複数あるプロシージャを呼び出すときに特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="849f8-115">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="849f8-116">引数を名前で指定する場合、連続するコンマを使用して欠けている位置引数を示す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="849f8-116">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="849f8-117">また、引数を名前で渡すと、渡す引数と省略する引数を追跡しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="849f8-117">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="849f8-118">位置と名前の組み合わせで引数を渡す</span><span class="sxs-lookup"><span data-stu-id="849f8-118">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="849f8-119">次の例に示すように、1 つのプロシージャ呼び出しで、位置と名前の両方で引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="849f8-119">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="849f8-120">前の例では、`birth` が名前で渡されているため、省略された `age` 引数の場所を保持するためにコンマを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="849f8-120">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="849f8-121">Visual Basic 15.5 より前のバージョンでは、位置と名前の組み合わせで引数を指定するときに、位置引数を常に最初に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="849f8-121">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="849f8-122">引数を名前で指定したら、残りの引数はすべて名前で渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="849f8-122">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="849f8-123">たとえば、次の `Display` メソッドの呼び出しでは、"[BC30241: Named argument expected\(名前付き引数が必要です\)](../../../misc/bc30241.md)" というコンパイラ エラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="849f8-123">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="849f8-124">Visual Basic 15.5 以降では、末尾の位置引数が正しい位置にあれば、位置引数を名前付き引数の後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="849f8-124">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="849f8-125">Visual Basic 15.5 でコンパイルすると、前の `Display` メソッドの呼び出しは正常にコンパイルされ、コンパイラ エラー [BC30241](../../../misc/bc30241.md) は生成されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="849f8-125">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="849f8-126">名前付き引数と位置引数を任意の順序で組み合わせるこの機能は、名前付き引数を使用してコードを読みやすくする場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="849f8-126">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="849f8-127">たとえば、次の `Person` クラスのコンストラクターには、`Person` 型の 2 つの引数が必要であり、どちらも `Nothing` にすることができます。</span><span class="sxs-lookup"><span data-stu-id="849f8-127">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="849f8-128">名前付き引数と位置引数の組み合わせを使用すると、`father` および `mother` 引数の値が `Nothing` の場合に、コードの意図を明確にすることができます。</span><span class="sxs-lookup"><span data-stu-id="849f8-128">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="849f8-129">位置引数の後に名前付き引数を指定するには、Visual Basic プロジェクト (\*.vbproj) ファイルに次の要素を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="849f8-129">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="849f8-130">詳細については、[Visual Basic 言語バージョンの設定](../../../language-reference/configure-language-version.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="849f8-130">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="849f8-131">引数を名前で指定する場合の制限事項</span><span class="sxs-lookup"><span data-stu-id="849f8-131">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="849f8-132">必須の引数の入力を避けるために、引数を名前で渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="849f8-132">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="849f8-133">省略できるのは、省略可能な引数だけです。</span><span class="sxs-lookup"><span data-stu-id="849f8-133">You can omit only the optional arguments.</span></span>

<span data-ttu-id="849f8-134">パラメーター配列を名前で渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="849f8-134">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="849f8-135">これは、プロシージャを呼び出すときに、パラメーター配列に対して不特定数のコンマ区切りの引数を指定しますが、コンパイラは複数の引数を 1 つの名前に関連付けることができないためです。</span><span class="sxs-lookup"><span data-stu-id="849f8-135">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="849f8-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="849f8-136">See also</span></span>

- [<span data-ttu-id="849f8-137">手順</span><span class="sxs-lookup"><span data-stu-id="849f8-137">Procedures</span></span>](./index.md)
- [<span data-ttu-id="849f8-138">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="849f8-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="849f8-139">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="849f8-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="849f8-140">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="849f8-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="849f8-141">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="849f8-141">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="849f8-142">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="849f8-142">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="849f8-143">Optional</span><span class="sxs-lookup"><span data-stu-id="849f8-143">Optional</span></span>](../../../language-reference/modifiers/optional.md)
- [<span data-ttu-id="849f8-144">ParamArray</span><span class="sxs-lookup"><span data-stu-id="849f8-144">ParamArray</span></span>](../../../language-reference/modifiers/paramarray.md)
