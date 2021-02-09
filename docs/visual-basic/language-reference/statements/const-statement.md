---
description: '詳細情報: Const ステートメント (Visual Basic)'
title: Const ステートメント
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 61d898823c7697c91b207a502417b49cdeaf5eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673857"
---
# <a name="const-statement-visual-basic"></a><span data-ttu-id="1eba7-103">Const ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1eba7-103">Const Statement (Visual Basic)</span></span>

<span data-ttu-id="1eba7-104">1 つ以上の定数を宣言して定義します。</span><span class="sxs-lookup"><span data-stu-id="1eba7-104">Declares and defines one or more constants.</span></span>

## <a name="syntax"></a><span data-ttu-id="1eba7-105">構文</span><span class="sxs-lookup"><span data-stu-id="1eba7-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a><span data-ttu-id="1eba7-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="1eba7-106">Parts</span></span>

`attributelist`  
<span data-ttu-id="1eba7-107">任意。</span><span class="sxs-lookup"><span data-stu-id="1eba7-107">Optional.</span></span> <span data-ttu-id="1eba7-108">このステートメントで宣言されているすべての定数に適用される属性の一覧。</span><span class="sxs-lookup"><span data-stu-id="1eba7-108">List of attributes that apply to all the constants declared in this statement.</span></span> <span data-ttu-id="1eba7-109">山かっこ ("`<`" および "`>`") 内の[属性リスト](attribute-list.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1eba7-109">See [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`accessmodifier`  
<span data-ttu-id="1eba7-110">任意。</span><span class="sxs-lookup"><span data-stu-id="1eba7-110">Optional.</span></span> <span data-ttu-id="1eba7-111">これらの定数にアクセスできるコードを指定するには、これを使用します。</span><span class="sxs-lookup"><span data-stu-id="1eba7-111">Use this to specify what code can access these constants.</span></span> <span data-ttu-id="1eba7-112">[Public](../modifiers/public.md)、[Protected](../modifiers/protected.md)、[Friend](../modifiers/friend.md)、[Protected Friend](../modifiers/protected-friend.md)、[Private](../modifiers/private.md)、または [Private Protected](../modifiers/private-protected.md) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-112">Can be [Public](../modifiers/public.md), [Protected](../modifiers/protected.md), [Friend](../modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../modifiers/private.md), or [Private Protected](../modifiers/private-protected.md).</span></span>

`Shadows`  
<span data-ttu-id="1eba7-113">任意。</span><span class="sxs-lookup"><span data-stu-id="1eba7-113">Optional.</span></span> <span data-ttu-id="1eba7-114">基底クラスのプログラミング要素を再宣言し、隠すには、これを使用します。</span><span class="sxs-lookup"><span data-stu-id="1eba7-114">Use this to redeclare and hide a programming element in a base class.</span></span> <span data-ttu-id="1eba7-115">「[Shadows](../modifiers/shadows.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1eba7-115">See [Shadows](../modifiers/shadows.md).</span></span>

`constantlist`  
<span data-ttu-id="1eba7-116">必須です。</span><span class="sxs-lookup"><span data-stu-id="1eba7-116">Required.</span></span> <span data-ttu-id="1eba7-117">このステートメントで宣言されている定数の一覧。</span><span class="sxs-lookup"><span data-stu-id="1eba7-117">List of constants being declared in this statement.</span></span>

<span data-ttu-id="1eba7-118">`constant` `[ ,` `constant` `... ]`</span><span class="sxs-lookup"><span data-stu-id="1eba7-118">`constant` `[ ,` `constant` `... ]`</span></span>

<span data-ttu-id="1eba7-119">`constant` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1eba7-119">Each `constant` has the following syntax and parts:</span></span>

<span data-ttu-id="1eba7-120">`constantname` `[ As` `datatype` `] =` `initializer`</span><span class="sxs-lookup"><span data-stu-id="1eba7-120">`constantname` `[ As` `datatype` `] =` `initializer`</span></span>

|<span data-ttu-id="1eba7-121">パーツ</span><span class="sxs-lookup"><span data-stu-id="1eba7-121">Part</span></span>|<span data-ttu-id="1eba7-122">説明</span><span class="sxs-lookup"><span data-stu-id="1eba7-122">Description</span></span>|
|----------|-----------------|
|`constantname`|<span data-ttu-id="1eba7-123">必須です。</span><span class="sxs-lookup"><span data-stu-id="1eba7-123">Required.</span></span> <span data-ttu-id="1eba7-124">定数の名前。</span><span class="sxs-lookup"><span data-stu-id="1eba7-124">Name of the constant.</span></span> <span data-ttu-id="1eba7-125">「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1eba7-125">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`datatype`|<span data-ttu-id="1eba7-126">`Option Strict` が `On` の場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="1eba7-126">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="1eba7-127">定数のデータ型。</span><span class="sxs-lookup"><span data-stu-id="1eba7-127">Data type of the constant.</span></span>|
|`initializer`|<span data-ttu-id="1eba7-128">必須です。</span><span class="sxs-lookup"><span data-stu-id="1eba7-128">Required.</span></span> <span data-ttu-id="1eba7-129">コンパイル時に評価され、定数に代入される式。</span><span class="sxs-lookup"><span data-stu-id="1eba7-129">Expression that is evaluated at compile time and assigned to the constant.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1eba7-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="1eba7-130">Remarks</span></span>

<span data-ttu-id="1eba7-131">アプリケーションで変更されない値がある場合は、名前付き定数を定義し、リテラル値の代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-131">If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value.</span></span> <span data-ttu-id="1eba7-132">名前は、値よりも覚えやすくなります。</span><span class="sxs-lookup"><span data-stu-id="1eba7-132">A name is easier to remember than a value.</span></span> <span data-ttu-id="1eba7-133">定数は 1 回だけ定義すれば、コード内の多くの場所で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-133">You can define the constant just once and use it in many places in your code.</span></span> <span data-ttu-id="1eba7-134">後のバージョンで値を再定義する必要がある場合、変更する必要がある場所は、`Const` ステートメントだけです。</span><span class="sxs-lookup"><span data-stu-id="1eba7-134">If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.</span></span>

<span data-ttu-id="1eba7-135">`Const` はモジュールまたはプロシージャ レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-135">You can use `Const` only at module or procedure level.</span></span> <span data-ttu-id="1eba7-136">つまり、変数の *宣言コンテキスト* は、クラス、構造体、モジュール、プロシージャ、またはブロックであることが必要で、ソース ファイル、名前空間、インターフェイスにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-136">This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface.</span></span> <span data-ttu-id="1eba7-137">詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1eba7-137">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="1eba7-138">プロシージャ内のローカル定数は、既定でパブリック アクセスに設定されていて、それらでアクセス修飾子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-138">Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="1eba7-139">クラスおよびモジュール メンバー定数 (プロシージャの外部) の既定は、プライベート アクセスに設定され、構造体メンバー定数の既定は、パブリック アクセスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-139">Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access.</span></span> <span data-ttu-id="1eba7-140">アクセス修飾子を使用してこれらのアクセス レベルを調整できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-140">You can adjust their access levels with the access modifiers.</span></span>

## <a name="rules"></a><span data-ttu-id="1eba7-141">ルール</span><span class="sxs-lookup"><span data-stu-id="1eba7-141">Rules</span></span>

- <span data-ttu-id="1eba7-142">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-142">**Declaration Context.**</span></span> <span data-ttu-id="1eba7-143">モジュール レベルでプロシージャの外部で宣言された定数は *メンバー定数* です。これは、それを宣言するクラス、構造体、またはモジュールのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="1eba7-143">A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.</span></span>

  <span data-ttu-id="1eba7-144">プロシージャ レベルで宣言された定数は *ローカル定数* です。これは、それを宣言するプロシージャまたはブロックに対してローカルです。</span><span class="sxs-lookup"><span data-stu-id="1eba7-144">A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.</span></span>

- <span data-ttu-id="1eba7-145">**属性。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-145">**Attributes.**</span></span> <span data-ttu-id="1eba7-146">属性は、メンバー定数にのみ適用でき、ローカル定数には適用できません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-146">You can apply attributes only to member constants, not to local constants.</span></span> <span data-ttu-id="1eba7-147">属性は、アセンブリのメタデータに情報を提供します。これは、ローカル定数などの一時ストレージには意味がありません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-147">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.</span></span>

- <span data-ttu-id="1eba7-148">**修飾子。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-148">**Modifiers.**</span></span> <span data-ttu-id="1eba7-149">既定で、すべての定数は `Shared`、`Static`、および `ReadOnly` です。</span><span class="sxs-lookup"><span data-stu-id="1eba7-149">By default, all constants are `Shared`, `Static`, and `ReadOnly`.</span></span> <span data-ttu-id="1eba7-150">定数の宣言時に、これらのキーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-150">You cannot use any of these keywords when declaring a constant.</span></span>

  <span data-ttu-id="1eba7-151">プロシージャ レベルで、`Shadows` または任意のアクセス修飾子を使用して、ローカル定数を宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-151">At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.</span></span>

- <span data-ttu-id="1eba7-152">**複数の定数。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-152">**Multiple Constants.**</span></span> <span data-ttu-id="1eba7-153">同じ宣言ステートメントで複数の定数を宣言し、それぞれに `constantname` 部分を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-153">You can declare several constants in the same declaration statement, specifying the `constantname` part for each one.</span></span> <span data-ttu-id="1eba7-154">複数の定数はコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="1eba7-154">Multiple constants are separated by commas.</span></span>

## <a name="data-type-rules"></a><span data-ttu-id="1eba7-155">データ型ルール</span><span class="sxs-lookup"><span data-stu-id="1eba7-155">Data Type Rules</span></span>

- <span data-ttu-id="1eba7-156">**データ型。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-156">**Data Types.**</span></span> <span data-ttu-id="1eba7-157">`Const` ステートメントでは、変数のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-157">The `Const` statement can declare the data type of a variable.</span></span> <span data-ttu-id="1eba7-158">任意のデータ型や列挙の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-158">You can specify any data type or the name of an enumeration.</span></span>

- <span data-ttu-id="1eba7-159">**既定の型。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-159">**Default Type.**</span></span> <span data-ttu-id="1eba7-160">`datatype` を指定しない場合、定数は `initializer` のデータ型を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1eba7-160">If you do not specify `datatype`, the constant takes the data type of `initializer`.</span></span> <span data-ttu-id="1eba7-161">`datatype` と `initializer` の両方を指定した場合、`initializer` のデータ型は `datatype` に変換可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eba7-161">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="1eba7-162">`datatype` も `initializer` も存在しない場合、データ型は既定で `Object` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-162">If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.</span></span>

- <span data-ttu-id="1eba7-163">**さまざまな型。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-163">**Different Types.**</span></span> <span data-ttu-id="1eba7-164">宣言する定数ごとに個別の `As` 句を使用して、異なる定数に異なるデータ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-164">You can specify different data types for different constants by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="1eba7-165">ただし、共通の `As` 句を使用して、複数の定数を同じ型として宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-165">However, you cannot declare several constants to be of the same type by using a common `As` clause.</span></span>

- <span data-ttu-id="1eba7-166">**初期化。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-166">**Initialization.**</span></span> <span data-ttu-id="1eba7-167">`constantlist` 内のすべての定数の値を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eba7-167">You must initialize the value of every constant in `constantlist`.</span></span> <span data-ttu-id="1eba7-168">`initializer` を使用して、定数に代入される式を指定します。</span><span class="sxs-lookup"><span data-stu-id="1eba7-168">You use `initializer` to supply an expression to be assigned to the constant.</span></span> <span data-ttu-id="1eba7-169">式には、リテラルの任意の組み合わせ、既に定義されている他の定数、および既に定義されている列挙型メンバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-169">The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined.</span></span> <span data-ttu-id="1eba7-170">算術演算子と論理演算子を使用して、そのような要素を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-170">You can use arithmetic and logical operators to combine such elements.</span></span>

  <span data-ttu-id="1eba7-171">`initializer` では、変数や関数を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-171">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="1eba7-172">ただし、`CByte` や `CShort` などの変換キーワードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-172">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="1eba7-173">定数 `String` または `Char` 引数でそれを呼び出す場合は、コンパイル時に評価できるため、`AscW` を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-173">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

## <a name="behavior"></a><span data-ttu-id="1eba7-174">動作</span><span class="sxs-lookup"><span data-stu-id="1eba7-174">Behavior</span></span>

- <span data-ttu-id="1eba7-175">**範囲**。</span><span class="sxs-lookup"><span data-stu-id="1eba7-175">**Scope.**</span></span> <span data-ttu-id="1eba7-176">ローカル定数は、それらのプロシージャまたはブロック内からのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-176">Local constants are accessible only from within their procedure or block.</span></span> <span data-ttu-id="1eba7-177">メンバー定数は、それらのクラス、構造体、またはモジュール内のどこからでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-177">Member constants are accessible from anywhere within their class, structure, or module.</span></span>

- <span data-ttu-id="1eba7-178">**修飾。**</span><span class="sxs-lookup"><span data-stu-id="1eba7-178">**Qualification.**</span></span> <span data-ttu-id="1eba7-179">クラス、構造体、またはモジュールの外部のコードでは、メンバー定数の名前を、そのクラス、構造体、またはモジュールの名前で修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1eba7-179">Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="1eba7-180">プロシージャまたはブロックの外部のコードでは、そのプロシージャまたはブロック内のローカル定数を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="1eba7-180">Code outside a procedure or block cannot refer to any local constants within that procedure or block.</span></span>

## <a name="example"></a><span data-ttu-id="1eba7-181">例</span><span class="sxs-lookup"><span data-stu-id="1eba7-181">Example</span></span>

<span data-ttu-id="1eba7-182">次の例では、`Const` ステートメントを使用して、リテラル値の代わりに使用する定数を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="1eba7-182">The following example uses the `Const` statement to declare constants for use in place of literal values.</span></span>

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a><span data-ttu-id="1eba7-183">例</span><span class="sxs-lookup"><span data-stu-id="1eba7-183">Example</span></span>

<span data-ttu-id="1eba7-184">`Object` データ型の定数を定義すると、Visual Basic コンパイラによって `Object` ではなく `initializer` の型が指定されます。</span><span class="sxs-lookup"><span data-stu-id="1eba7-184">If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`.</span></span> <span data-ttu-id="1eba7-185">次の例では、定数 `naturalLogBase` はランタイム型 `Decimal` になります。</span><span class="sxs-lookup"><span data-stu-id="1eba7-185">In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.</span></span>

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

<span data-ttu-id="1eba7-186">前の例では、[GetType 演算子](../operators/gettype-operator.md)によって返された <xref:System.Type> オブジェクトに対して <xref:System.Type.ToString%2A> メソッドを使用しています。<xref:System.Type> は `CStr` を使用して `String` に変換できないためです。</span><span class="sxs-lookup"><span data-stu-id="1eba7-186">The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.</span></span>

## <a name="see-also"></a><span data-ttu-id="1eba7-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="1eba7-187">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="1eba7-188">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="1eba7-188">Enum Statement</span></span>](enum-statement.md)
- [<span data-ttu-id="1eba7-189">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="1eba7-189">#Const Directive</span></span>](../directives/const-directive.md)
- [<span data-ttu-id="1eba7-190">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="1eba7-190">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="1eba7-191">ReDim ステートメント</span><span class="sxs-lookup"><span data-stu-id="1eba7-191">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="1eba7-192">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="1eba7-192">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="1eba7-193">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="1eba7-193">Constants and Enumerations</span></span>](../../programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="1eba7-194">定数と列挙体</span><span class="sxs-lookup"><span data-stu-id="1eba7-194">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="1eba7-195">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="1eba7-195">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
