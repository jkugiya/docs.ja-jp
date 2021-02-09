---
description: '詳細情報: 型リスト (Visual Basic)'
title: 型リスト
ms.date: 07/20/2015
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
ms.openlocfilehash: d4c8bcab4a39af0ac0747d6be0d04408edd98a55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740900"
---
# <a name="type-list-visual-basic"></a><span data-ttu-id="b12a3-103">型リスト (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b12a3-103">Type List (Visual Basic)</span></span>

<span data-ttu-id="b12a3-104">*ジェネリック* プログラミング要素の *型パラメーター* を指定します。</span><span class="sxs-lookup"><span data-stu-id="b12a3-104">Specifies the *type parameters* for a *generic* programming element.</span></span> <span data-ttu-id="b12a3-105">複数のパラメーターはコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-105">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="b12a3-106">次に、1 つの型パラメーターの構文を示します。</span><span class="sxs-lookup"><span data-stu-id="b12a3-106">Following is the syntax for one type parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b12a3-107">構文</span><span class="sxs-lookup"><span data-stu-id="b12a3-107">Syntax</span></span>

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a><span data-ttu-id="b12a3-108">指定項目</span><span class="sxs-lookup"><span data-stu-id="b12a3-108">Parts</span></span>

|<span data-ttu-id="b12a3-109">用語</span><span class="sxs-lookup"><span data-stu-id="b12a3-109">Term</span></span>|<span data-ttu-id="b12a3-110">定義</span><span class="sxs-lookup"><span data-stu-id="b12a3-110">Definition</span></span>|
|---|---|
|`genericmodifier`|<span data-ttu-id="b12a3-111">任意。</span><span class="sxs-lookup"><span data-stu-id="b12a3-111">Optional.</span></span> <span data-ttu-id="b12a3-112">ジェネリック インターフェイスとデリゲートのみで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b12a3-112">Can be used only in generic interfaces and delegates.</span></span> <span data-ttu-id="b12a3-113">[Out](../modifiers/out-generic-modifier.md) キーワードを使用して共変として、または [In](../modifiers/in-generic-modifier.md) キーワードを使用して反変として、型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="b12a3-113">You can declare a type covariant by using the [Out](../modifiers/out-generic-modifier.md) keyword or contravariant by using the [In](../modifiers/in-generic-modifier.md) keyword.</span></span> <span data-ttu-id="b12a3-114">「 [共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b12a3-114">See [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>|
|`typename`|<span data-ttu-id="b12a3-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="b12a3-115">Required.</span></span> <span data-ttu-id="b12a3-116">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="b12a3-116">Name of the type parameter.</span></span> <span data-ttu-id="b12a3-117">これは、対応する型引数で提供された、定義済みの型に置換されるプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="b12a3-117">This is a placeholder, to be replaced by a defined type supplied by the corresponding type argument.</span></span>|
|`constraintlist`|<span data-ttu-id="b12a3-118">任意。</span><span class="sxs-lookup"><span data-stu-id="b12a3-118">Optional.</span></span> <span data-ttu-id="b12a3-119">`typename` に指定できるデータ型を制約する要件の一覧。</span><span class="sxs-lookup"><span data-stu-id="b12a3-119">List of requirements that constrain the data type that can be supplied for `typename`.</span></span> <span data-ttu-id="b12a3-120">複数の制約がある場合は、それらを中かっこ (`{ }`) で囲み、コンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-120">If you have multiple constraints, enclose them in curly braces (`{ }`) and separate them with commas.</span></span> <span data-ttu-id="b12a3-121">[As](as-clause.md) キーワードを使用して、制約リストを取り込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-121">You must introduce the constraint list with the [As](as-clause.md) keyword.</span></span> <span data-ttu-id="b12a3-122">`As` は、リストの開始で 1 回だけ使用します。</span><span class="sxs-lookup"><span data-stu-id="b12a3-122">You use `As` only once, at the beginning of the list.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b12a3-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="b12a3-123">Remarks</span></span>

<span data-ttu-id="b12a3-124">すべてのジェネリック プログラミング要素で、少なくとも 1 つの型パラメーターを受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-124">Every generic programming element must take at least one type parameter.</span></span> <span data-ttu-id="b12a3-125">型パラメーターは、クライアント コードでジェネリック型のインスタンスを作成するときに指定する特定の型 (*構築された要素*) のプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="b12a3-125">A type parameter is a placeholder for a specific type (a *constructed element*) that client code specifies when it creates an instance of the generic type.</span></span> <span data-ttu-id="b12a3-126">ジェネリック クラス、構造体、インターフェイス、プロシージャ、またはデリゲートを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b12a3-126">You can define a generic class, structure, interface, procedure, or delegate.</span></span>

<span data-ttu-id="b12a3-127">ジェネリック型を定義する場合の詳細については、「[Visual Basic におけるジェネリック型](../../programming-guide/language-features/data-types/generic-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b12a3-127">For more information on when to define a generic type, see [Generic Types in Visual Basic](../../programming-guide/language-features/data-types/generic-types.md).</span></span> <span data-ttu-id="b12a3-128">型パラメーター名の詳細については、「[宣言された要素の名前](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b12a3-128">For more information on type parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="rules"></a><span data-ttu-id="b12a3-129">ルール</span><span class="sxs-lookup"><span data-stu-id="b12a3-129">Rules</span></span>

- <span data-ttu-id="b12a3-130">**かっこ。**</span><span class="sxs-lookup"><span data-stu-id="b12a3-130">**Parentheses.**</span></span> <span data-ttu-id="b12a3-131">型パラメーター リストを指定する場合は、かっこで囲む必要があります。また、[Of](of-clause.md) キーワードでリストを取り込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-131">If you supply a type parameter list, you must enclose it in parentheses, and you must introduce the list with the [Of](of-clause.md) keyword.</span></span> <span data-ttu-id="b12a3-132">`Of` は、リストの開始で 1 回だけ使用します。</span><span class="sxs-lookup"><span data-stu-id="b12a3-132">You use `Of` only once, at the beginning of the list.</span></span>

- <span data-ttu-id="b12a3-133">**制約。**</span><span class="sxs-lookup"><span data-stu-id="b12a3-133">**Constraints.**</span></span> <span data-ttu-id="b12a3-134">型パラメーターへの *制約* の一覧には、次の項目を任意の組み合わせで含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b12a3-134">A list of *constraints* on a type parameter can include the following items in any combination:</span></span>

  - <span data-ttu-id="b12a3-135">任意の数のインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="b12a3-135">Any number of interfaces.</span></span> <span data-ttu-id="b12a3-136">指定された型では、この一覧のすべてのインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-136">The supplied type must implement every interface in this list.</span></span>

  - <span data-ttu-id="b12a3-137">最大 1 つのクラス。</span><span class="sxs-lookup"><span data-stu-id="b12a3-137">At most one class.</span></span> <span data-ttu-id="b12a3-138">指定した型は、そのクラスから継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-138">The supplied type must inherit from that class.</span></span>

  - <span data-ttu-id="b12a3-139">`New` キーワード。</span><span class="sxs-lookup"><span data-stu-id="b12a3-139">The `New` keyword.</span></span> <span data-ttu-id="b12a3-140">指定した型では、ジェネリック型でアクセスできるパラメーターなしのコンストラクターを公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-140">The supplied type must expose a parameterless constructor that your generic type can access.</span></span> <span data-ttu-id="b12a3-141">これは、1 つまたは複数のインターフェイスによって型パラメーターを制約する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b12a3-141">This is useful if you constrain a type parameter by one or more interfaces.</span></span> <span data-ttu-id="b12a3-142">インターフェイスを実装する型では、必ずしもコンストラクターが公開されているとは限らず、コンストラクターのアクセス レベルによっては、ジェネリック型内のコードでそれにアクセスできない場合があります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-142">A type that implements interfaces does not necessarily expose a constructor, and depending on the access level of a constructor, the code within the generic type might not be able to access it.</span></span>

  - <span data-ttu-id="b12a3-143">`Class` キーワードまたは `Structure` キーワード。</span><span class="sxs-lookup"><span data-stu-id="b12a3-143">Either the `Class` keyword or the `Structure` keyword.</span></span> <span data-ttu-id="b12a3-144">`Class` キーワードでは、ジェネリック型パラメーターを制約して、すべての型引数が参照型 (文字列、配列、デリゲート、またはクラスから作成されたオブジェクトなど) として渡されることを必要とします。</span><span class="sxs-lookup"><span data-stu-id="b12a3-144">The `Class` keyword constrains a generic type parameter to require that any type argument passed to it be a reference type, for example a string, array, or delegate, or an object created from a class.</span></span> <span data-ttu-id="b12a3-145">`Structure` キーワードでは、ジェネリック型パラメーターを制約して、すべての型引数が値型 (構造体、列挙型、基本データ型など) として渡されることを必要とします。</span><span class="sxs-lookup"><span data-stu-id="b12a3-145">The `Structure` keyword constrains a generic type parameter to require that any type argument passed to it be a value type, for example a structure, enumeration, or elementary data type.</span></span> <span data-ttu-id="b12a3-146">`Class` と `Structure` を同じ `constraintlist` に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="b12a3-146">You cannot include both `Class` and `Structure` in the same `constraintlist`.</span></span>

  <span data-ttu-id="b12a3-147">指定した型は、`constraintlist` に含まれるすべての要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b12a3-147">The supplied type must satisfy every requirement you include in `constraintlist`.</span></span>

  <span data-ttu-id="b12a3-148">各型パラメーターに対する制約は、他の型パラメーターに対する制約と関係がありません。</span><span class="sxs-lookup"><span data-stu-id="b12a3-148">Constraints on each type parameter are independent of constraints on other type parameters.</span></span>

## <a name="behavior"></a><span data-ttu-id="b12a3-149">動作</span><span class="sxs-lookup"><span data-stu-id="b12a3-149">Behavior</span></span>

- <span data-ttu-id="b12a3-150">**コンパイル時置換。**</span><span class="sxs-lookup"><span data-stu-id="b12a3-150">**Compile-Time Substitution.**</span></span> <span data-ttu-id="b12a3-151">ジェネリック プログラミング要素から構築された型を作成する場合は、各型パラメーターに定義済みの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="b12a3-151">When you create a constructed type from a generic programming element, you supply a defined type for each type parameter.</span></span> <span data-ttu-id="b12a3-152">Visual Basic コンパイラによって、ジェネリック要素内の `typename` のすべての存在について、指定した型が使われます。</span><span class="sxs-lookup"><span data-stu-id="b12a3-152">The Visual Basic compiler substitutes that supplied type for every occurrence of `typename` within the generic element.</span></span>

- <span data-ttu-id="b12a3-153">**制約なし。**</span><span class="sxs-lookup"><span data-stu-id="b12a3-153">**Absence of Constraints.**</span></span> <span data-ttu-id="b12a3-154">型パラメーターに対して制約を指定しない場合、コードは、その型パラメーターの[オブジェクト データ型](../data-types/object-data-type.md)でサポートされる操作とメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="b12a3-154">If you do not specify any constraints on a type parameter, your code is limited to the operations and members supported by the [Object Data Type](../data-types/object-data-type.md) for that type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="b12a3-155">例</span><span class="sxs-lookup"><span data-stu-id="b12a3-155">Example</span></span>

<span data-ttu-id="b12a3-156">次の例に、ジェネリック ディクショナリ クラスのスケルトン定義を示しています。これには、新しいエントリをディクショナリに追加するスケルトン関数も含まれます。</span><span class="sxs-lookup"><span data-stu-id="b12a3-156">The following example shows a skeleton definition of a generic dictionary class, including a skeleton function to add a new entry to the dictionary.</span></span>

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a><span data-ttu-id="b12a3-157">例</span><span class="sxs-lookup"><span data-stu-id="b12a3-157">Example</span></span>

<span data-ttu-id="b12a3-158">`dictionary` はジェネリックであるため、それを使用するコードでは、それぞれが同じ機能を持ちながらも、異なるデータ型に対して動作する、さまざまなオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b12a3-158">Because `dictionary` is generic, the code that uses it can create a variety of objects from it, each having the same functionality but acting on a different data type.</span></span> <span data-ttu-id="b12a3-159">次の例に、`String` エントリと `Integer` キーを含む `dictionary` オブジェクトを作成するコード行を示しています。</span><span class="sxs-lookup"><span data-stu-id="b12a3-159">The following example shows a line of code that creates a `dictionary` object with `String` entries and `Integer` keys.</span></span>

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a><span data-ttu-id="b12a3-160">例</span><span class="sxs-lookup"><span data-stu-id="b12a3-160">Example</span></span>

<span data-ttu-id="b12a3-161">次の例は、前の例で生成された同等のスケルトン定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="b12a3-161">The following example shows the equivalent skeleton definition generated by the preceding example.</span></span>

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="b12a3-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="b12a3-162">See also</span></span>

- [<span data-ttu-id="b12a3-163">Of</span><span class="sxs-lookup"><span data-stu-id="b12a3-163">Of</span></span>](of-clause.md)
- [<span data-ttu-id="b12a3-164">New 演算子</span><span class="sxs-lookup"><span data-stu-id="b12a3-164">New Operator</span></span>](../operators/new-operator.md)
- [<span data-ttu-id="b12a3-165">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="b12a3-165">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="b12a3-166">Object 型</span><span class="sxs-lookup"><span data-stu-id="b12a3-166">Object Data Type</span></span>](../data-types/object-data-type.md)
- [<span data-ttu-id="b12a3-167">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="b12a3-167">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="b12a3-168">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="b12a3-168">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="b12a3-169">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="b12a3-169">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="b12a3-170">方法: ジェネリック クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="b12a3-170">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="b12a3-171">共変性と反変性</span><span class="sxs-lookup"><span data-stu-id="b12a3-171">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="b12a3-172">In</span><span class="sxs-lookup"><span data-stu-id="b12a3-172">In</span></span>](../modifiers/in-generic-modifier.md)
- [<span data-ttu-id="b12a3-173">Out</span><span class="sxs-lookup"><span data-stu-id="b12a3-173">Out</span></span>](../modifiers/out-generic-modifier.md)
