---
description: '詳細情報: Visual Basic での変数宣言'
title: 変数宣言
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: ef0e7bc7a99f320bd40788ef019b05c7ebf4ce46
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462699"
---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="74767-103">Visual Basic での変数宣言</span><span class="sxs-lookup"><span data-stu-id="74767-103">Variable Declaration in Visual Basic</span></span>

<span data-ttu-id="74767-104">変数を宣言して、その名前と特性を指定します。</span><span class="sxs-lookup"><span data-stu-id="74767-104">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="74767-105">変数の宣言ステートメントは、[Dim ステートメント](../../../language-reference/statements/dim-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="74767-105">The declaration statement for variables is the [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="74767-106">その場所と内容によって、変数の特性が決まります。</span><span class="sxs-lookup"><span data-stu-id="74767-106">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="74767-107">変数の名前付け規則と考慮事項については、「[宣言された要素の名前](../declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74767-107">For variable naming rules and considerations, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="74767-108">宣言レベル</span><span class="sxs-lookup"><span data-stu-id="74767-108">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="74767-109">ローカル変数とメンバー変数</span><span class="sxs-lookup"><span data-stu-id="74767-109">Local and Member Variables</span></span>  

 <span data-ttu-id="74767-110">"*ローカル変数*" は、プロシージャ内で宣言されている変数です。</span><span class="sxs-lookup"><span data-stu-id="74767-110">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="74767-111">"*メンバー変数*" は、Visual Basic 型のメンバーです。この変数は、クラス、構造体、またはモジュールの内部のモジュール レベルで宣言されますが、そのクラス、構造体、またはモジュールの内部のプロシージャ内では宣言されません。</span><span class="sxs-lookup"><span data-stu-id="74767-111">A *member variable* is a member of a Visual Basic type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="74767-112">共有変数とインスタンス変数</span><span class="sxs-lookup"><span data-stu-id="74767-112">Shared and Instance Variables</span></span>  

 <span data-ttu-id="74767-113">クラス内または構造体内のメンバー変数のカテゴリは、そのメンバーが共有されているかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="74767-113">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="74767-114">[Shared](../../../language-reference/modifiers/shared.md) キーワードを使用して宣言されている場合、それは "*共有変数*" であり、クラスまたは構造体のすべてのインスタンス間で共有される 1 つのコピーに存在します。</span><span class="sxs-lookup"><span data-stu-id="74767-114">If it is declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="74767-115">そうでない場合は "*インスタンス変数*" であり、クラスまたは構造体のインスタンスごとに別のコピーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="74767-115">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="74767-116">インスタンス変数の特定のコピーは、それが作成されたクラスまたは構造体のインスタンスでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="74767-116">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="74767-117">それは、そのクラスまたは構造体の他のすべてのインスタンスのインスタンス変数のコピーとは無関係です。</span><span class="sxs-lookup"><span data-stu-id="74767-117">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="74767-118">データ型の宣言</span><span class="sxs-lookup"><span data-stu-id="74767-118">Declaring Data Type</span></span>  

 <span data-ttu-id="74767-119">宣言ステートメントの [As](../../../language-reference/statements/as-clause.md) 句を使用すると、宣言する変数のデータ型またはオブジェクト型を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="74767-119">The [As](../../../language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="74767-120">変数には、次のいずれかの型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="74767-120">You can specify any of the following types for a variable:</span></span>  
  
- <span data-ttu-id="74767-121">基本データ型 (`Boolean`、`Long`、`Decimal` など)</span><span class="sxs-lookup"><span data-stu-id="74767-121">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
- <span data-ttu-id="74767-122">複合データ型 (配列や構造体など)</span><span class="sxs-lookup"><span data-stu-id="74767-122">A composite data type, such as an array or structure</span></span>  
  
- <span data-ttu-id="74767-123">そのアプリケーション内または別のアプリケーション内で定義されているオブジェクト型 (クラス)</span><span class="sxs-lookup"><span data-stu-id="74767-123">An object type, or class, defined either in your application or in another application</span></span>  
  
- <span data-ttu-id="74767-124">.NET Framework クラス (<xref:System.Windows.Forms.Label> や <xref:System.Windows.Forms.TextBox> など)</span><span class="sxs-lookup"><span data-stu-id="74767-124">A .NET Framework class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
- <span data-ttu-id="74767-125">インターフェイス型 (<xref:System.IComparable> や <xref:System.IDisposable> など)</span><span class="sxs-lookup"><span data-stu-id="74767-125">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="74767-126">1 つのステートメントで複数の変数を宣言できます。データ型を繰り返す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="74767-126">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="74767-127">次のステートメントでは、変数 `i`、`j`、`k` は `Integer` 型として、変数 `l` と `m` は `Long` 型として、変数 `x` と `y` は `Single` 型として、宣言されています。</span><span class="sxs-lookup"><span data-stu-id="74767-127">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="74767-128">データ型について詳しくは、[データ型](../data-types/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="74767-128">For more information on data types, see [Data Types](../data-types/index.md).</span></span> <span data-ttu-id="74767-129">オブジェクトについて詳しくは、「[オブジェクトとクラス](../objects-and-classes/index.md)」および「[コンポーネントによるプログラミング](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="74767-129">For more information on objects, see [Objects and Classes](../objects-and-classes/index.md) and [Programming with Components](/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="74767-130">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="74767-130">Local Type Inference</span></span>  

 <span data-ttu-id="74767-131">`As` 句を使用しないでローカル変数を宣言すると、"*型の推定*" を使用してそのデータ型が決定されます。</span><span class="sxs-lookup"><span data-stu-id="74767-131">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="74767-132">コンパイラでは、初期化式の型から変数の型が推定されます。</span><span class="sxs-lookup"><span data-stu-id="74767-132">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="74767-133">これにより、型を明示的に指定せずに変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="74767-133">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="74767-134">次の例では、`num1` と `num2` はどちらも整数として厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="74767-134">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 <span data-ttu-id="74767-135">ローカル型推論を使用する場合は、`Option Infer` を `On` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="74767-135">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="74767-136">詳細については、「[ローカル型の推論](local-type-inference.md)」と「[Option Infer ステートメント](../../../language-reference/statements/option-infer-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74767-136">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="74767-137">宣言された変数の特性</span><span class="sxs-lookup"><span data-stu-id="74767-137">Characteristics of Declared Variables</span></span>  

 <span data-ttu-id="74767-138">変数の "*有効期間*" は、その変数を使用できる期間です。</span><span class="sxs-lookup"><span data-stu-id="74767-138">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="74767-139">一般に、変数は、それが宣言されている要素 (プロシージャやクラスなど) が存在し続ける限り、存在しています。</span><span class="sxs-lookup"><span data-stu-id="74767-139">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="74767-140">変数が含まれる要素の有効期間より長く、変数が存在し続ける必要がない場合は、宣言で特に何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="74767-140">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="74767-141">変数が含まれる要素より長く、変数が存在し続ける必要がある場合は、その `Dim` ステートメントに `Static` または `Shared` キーワードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="74767-141">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="74767-142">詳しくは、「[Visual Basic における有効期間](../declared-elements/lifetime.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="74767-142">For more information, see [Lifetime in Visual Basic](../declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="74767-143">変数の "*スコープ*" は、名前を修飾せずに変数を参照できるすべてのコードのセットです。</span><span class="sxs-lookup"><span data-stu-id="74767-143">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="74767-144">変数のスコープは、変数が宣言されている場所によって決まります。</span><span class="sxs-lookup"><span data-stu-id="74767-144">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="74767-145">特定の領域にあるコードは、その領域内で定義されている変数を、名前を修飾する必要なしに使用できます。</span><span class="sxs-lookup"><span data-stu-id="74767-145">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="74767-146">詳細については、「 [Scope in Visual Basic](../declared-elements/scope.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74767-146">For more information, see [Scope in Visual Basic](../declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="74767-147">変数の "*アクセス レベル*" は、変数にアクセスする権限を持つコードの範囲です。</span><span class="sxs-lookup"><span data-stu-id="74767-147">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="74767-148">これは、`Dim` ステートメントで使用されているアクセス修飾子 ([Public](../../../language-reference/modifiers/public.md) や [Private](../../../language-reference/modifiers/private.md) など) によって決まります。</span><span class="sxs-lookup"><span data-stu-id="74767-148">This is determined by the access modifier (such as [Public](../../../language-reference/modifiers/public.md) or [Private](../../../language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="74767-149">詳しくは、「[Visual Basic でのアクセス レベル](../declared-elements/access-levels.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="74767-149">For more information, see [Access levels in Visual Basic](../declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74767-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="74767-150">See also</span></span>

- [<span data-ttu-id="74767-151">方法: 新しい変数を作成する</span><span class="sxs-lookup"><span data-stu-id="74767-151">How to: Create a New Variable</span></span>](how-to-create-a-new-variable.md)
- [<span data-ttu-id="74767-152">方法: 変数に値を格納する、および変数から値を取得する</span><span class="sxs-lookup"><span data-stu-id="74767-152">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="74767-153">データの種類</span><span class="sxs-lookup"><span data-stu-id="74767-153">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="74767-154">Protected</span><span class="sxs-lookup"><span data-stu-id="74767-154">Protected</span></span>](../../../language-reference/modifiers/protected.md)
- [<span data-ttu-id="74767-155">Friend</span><span class="sxs-lookup"><span data-stu-id="74767-155">Friend</span></span>](../../../language-reference/modifiers/friend.md)
- [<span data-ttu-id="74767-156">Static</span><span class="sxs-lookup"><span data-stu-id="74767-156">Static</span></span>](../../../language-reference/modifiers/static.md)
- [<span data-ttu-id="74767-157">宣言された要素の特性</span><span class="sxs-lookup"><span data-stu-id="74767-157">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="74767-158">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="74767-158">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="74767-159">Option Infer ステートメント</span><span class="sxs-lookup"><span data-stu-id="74767-159">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
