---
description: '詳細情報: パラメーターの一覧 (Visual Basic)'
title: パラメーター リスト
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: f69063fac82887ba4da3119d8ec4fcac11b7f4c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741407"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="0d82c-103">パラメーターの一覧 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d82c-103">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="0d82c-104">プロシージャが呼び出されるときに、プロシージャで期待するパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-104">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="0d82c-105">複数のパラメーターはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="0d82c-105">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="0d82c-106">次に 1 つのパラメーターの構文を示します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-106">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d82c-107">構文</span><span class="sxs-lookup"><span data-stu-id="0d82c-107">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="0d82c-108">指定項目</span><span class="sxs-lookup"><span data-stu-id="0d82c-108">Parts</span></span>

`attributelist`  
<span data-ttu-id="0d82c-109">任意。</span><span class="sxs-lookup"><span data-stu-id="0d82c-109">Optional.</span></span> <span data-ttu-id="0d82c-110">このパラメーターに適用される属性の一覧。</span><span class="sxs-lookup"><span data-stu-id="0d82c-110">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="0d82c-111">[属性リスト](attribute-list.md)は山かっこ ("`<`" および "`>`") で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d82c-111">You must enclose the [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="0d82c-112">任意。</span><span class="sxs-lookup"><span data-stu-id="0d82c-112">Optional.</span></span> <span data-ttu-id="0d82c-113">プロシージャが呼び出されるときに、このパラメーターが必須でないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-113">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="0d82c-114">任意。</span><span class="sxs-lookup"><span data-stu-id="0d82c-114">Optional.</span></span> <span data-ttu-id="0d82c-115">プロシージャで、呼び出し元のコード内の対応する引数の基になる変数要素を置換または再代入できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-115">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="0d82c-116">任意。</span><span class="sxs-lookup"><span data-stu-id="0d82c-116">Optional.</span></span> <span data-ttu-id="0d82c-117">プロシージャで、呼び出し元のコード自体で可能な同じ方法で、呼び出し元のコード内の基になる変数要素を変更できることを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-117">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="0d82c-118">任意。</span><span class="sxs-lookup"><span data-stu-id="0d82c-118">Optional.</span></span> <span data-ttu-id="0d82c-119">パラメーター リストの最後のパラメーターが、指定したデータ型の要素の省略可能な配列であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-119">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="0d82c-120">これにより、呼び出し元のコードで、プロシージャに任意の数の引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-120">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="0d82c-121">必須です。</span><span class="sxs-lookup"><span data-stu-id="0d82c-121">Required.</span></span> <span data-ttu-id="0d82c-122">パラメーターを表すローカル変数の名前。</span><span class="sxs-lookup"><span data-stu-id="0d82c-122">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="0d82c-123">`Option Strict` が `On` の場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="0d82c-123">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="0d82c-124">パラメーターを表すローカル変数のデータ型。</span><span class="sxs-lookup"><span data-stu-id="0d82c-124">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="0d82c-125">`Optional` パラメーターに必須です。</span><span class="sxs-lookup"><span data-stu-id="0d82c-125">Required for `Optional` parameters.</span></span> <span data-ttu-id="0d82c-126">パラメーターのデータ型に評価される定数または定数式。</span><span class="sxs-lookup"><span data-stu-id="0d82c-126">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="0d82c-127">型が `Object`、クラス、インターフェイス、配列、または構造体の場合、既定値は `Nothing` のみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-127">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="0d82c-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="0d82c-128">Remarks</span></span>

<span data-ttu-id="0d82c-129">パラメーターは、かっこで囲み、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="0d82c-129">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="0d82c-130">パラメーターは任意のデータ型で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-130">A parameter can be declared with any data type.</span></span> <span data-ttu-id="0d82c-131">`parametertype` を指定しない場合、既定で `Object` が設定されます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-131">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="0d82c-132">呼び出し元のコードでプロシージャを呼び出すと、各必須パラメーターに *引数* が渡されます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-132">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="0d82c-133">詳細については、「[パラメーターと引数の違い](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d82c-133">For more information, see [Differences Between Parameters and Arguments](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="0d82c-134">呼び出し元のコードから各パラメーターに渡される引数は、呼び出し元のコード内の基になる要素へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="0d82c-134">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="0d82c-135">この要素が *変数でない* (定数、リテラル、列挙型、または式) 場合、どのコードでもそれを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="0d82c-135">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="0d82c-136">それが *変数* 要素 (宣言された変数、フィールド、プロパティ、配列要素、または構造体要素) の場合は、呼び出し元のコードでそれを変更できます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-136">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="0d82c-137">詳細については、「[変更できる引数と変更できない引数の違い](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d82c-137">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="0d82c-138">変数要素が `ByRef` で渡された場合は、プロシージャでそれを変更できます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-138">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="0d82c-139">詳細については、「[引数の値渡しと参照渡しの違い](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d82c-139">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="0d82c-140">ルール</span><span class="sxs-lookup"><span data-stu-id="0d82c-140">Rules</span></span>

- <span data-ttu-id="0d82c-141">**かっこ。**</span><span class="sxs-lookup"><span data-stu-id="0d82c-141">**Parentheses.**</span></span> <span data-ttu-id="0d82c-142">パラメーター リストを指定する場合は、かっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d82c-142">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="0d82c-143">パラメーターがない場合でも、空のリストを囲むかっこを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-143">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="0d82c-144">これにより、要素がプロシージャであることを明確にすることで、コードの読みやすさが向上します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-144">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="0d82c-145">**省略可能なパラメーター。**</span><span class="sxs-lookup"><span data-stu-id="0d82c-145">**Optional Parameters.**</span></span> <span data-ttu-id="0d82c-146">パラメーターで `Optional` 修飾子を使用する場合、リスト内の後続のすべてのパラメーターも省略可能で、`Optional` 修飾子を使用して宣言されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d82c-146">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="0d82c-147">省略可能なすべてのパラメーター宣言で、`defaultvalue` 句を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d82c-147">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="0d82c-148">詳細については、「[省略可能なパラメーター](../../programming-guide/language-features/procedures/optional-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d82c-148">For more information, see [Optional Parameters](../../programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="0d82c-149">**パラメーター配列。**</span><span class="sxs-lookup"><span data-stu-id="0d82c-149">**Parameter Arrays.**</span></span> <span data-ttu-id="0d82c-150">`ParamArray` パラメーターには `ByVal` を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d82c-150">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="0d82c-151">同じパラメーター リストで `Optional` と `ParamArray` の両方を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="0d82c-151">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="0d82c-152">詳細については、「[パラメーター配列](../../programming-guide/language-features/procedures/parameter-arrays.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d82c-152">For more information, see [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="0d82c-153">**引渡し方法。**</span><span class="sxs-lookup"><span data-stu-id="0d82c-153">**Passing Mechanism.**</span></span> <span data-ttu-id="0d82c-154">すべての引数の既定の方法は `ByVal` です。これは、プロシージャで基になる変数要素を変更できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-154">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="0d82c-155">ただし、要素が参照型の場合、プロシージャで、オブジェクト自体の置換や再代入ができなくても、基になるオブジェクトの内容やメンバーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="0d82c-155">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="0d82c-156">**パラメーター名。**</span><span class="sxs-lookup"><span data-stu-id="0d82c-156">**Parameter Names.**</span></span> <span data-ttu-id="0d82c-157">パラメーターのデータ型が配列である場合は、`parametername` の直後にかっこで指定します。</span><span class="sxs-lookup"><span data-stu-id="0d82c-157">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="0d82c-158">パラメーター名の詳細については、「[宣言された要素の名前](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d82c-158">For more information on parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="0d82c-159">例</span><span class="sxs-lookup"><span data-stu-id="0d82c-159">Example</span></span>

<span data-ttu-id="0d82c-160">次の例では、2 つのパラメーターを定義する `Function` プロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="0d82c-160">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="0d82c-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d82c-161">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="0d82c-162">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="0d82c-162">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="0d82c-163">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="0d82c-163">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="0d82c-164">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="0d82c-164">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="0d82c-165">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="0d82c-165">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="0d82c-166">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="0d82c-166">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="0d82c-167">属性の概要</span><span class="sxs-lookup"><span data-stu-id="0d82c-167">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="0d82c-168">方法: コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="0d82c-168">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
