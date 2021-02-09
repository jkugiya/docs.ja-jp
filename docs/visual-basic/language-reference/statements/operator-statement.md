---
description: '詳細情報: Operator Statement'
title: Operator Statement
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: f6a8ae2ac51e8bc8fe1be0de3549004b9dda4ef4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768819"
---
# <a name="operator-statement"></a><span data-ttu-id="54e3d-103">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="54e3d-103">Operator Statement</span></span>

<span data-ttu-id="54e3d-104">クラスまたは構造体に演算子プロシージャを定義する演算子シンボル、オペランド、およびコードを宣言します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-104">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="54e3d-105">構文</span><span class="sxs-lookup"><span data-stu-id="54e3d-105">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="54e3d-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="54e3d-106">Parts</span></span>

`attrlist`  
<span data-ttu-id="54e3d-107">任意。</span><span class="sxs-lookup"><span data-stu-id="54e3d-107">Optional.</span></span> <span data-ttu-id="54e3d-108">「[属性リスト](attribute-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e3d-108">See [Attribute List](attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="54e3d-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-109">Required.</span></span> <span data-ttu-id="54e3d-110">この演算子プロシージャが [Public](../modifiers/public.md) アクセス権を持つことを示します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-110">Indicates that this operator procedure has [Public](../modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="54e3d-111">任意。</span><span class="sxs-lookup"><span data-stu-id="54e3d-111">Optional.</span></span> <span data-ttu-id="54e3d-112">「[Overloads](../modifiers/overloads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e3d-112">See [Overloads](../modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="54e3d-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-113">Required.</span></span> <span data-ttu-id="54e3d-114">この演算子プロシージャが [Shared](../modifiers/shared.md)プロシージャであることを示します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-114">Indicates that this operator procedure is a [Shared](../modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="54e3d-115">任意。</span><span class="sxs-lookup"><span data-stu-id="54e3d-115">Optional.</span></span> <span data-ttu-id="54e3d-116">「[Shadows](../modifiers/shadows.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e3d-116">See [Shadows](../modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="54e3d-117">`Narrowing` を指定しない場合、変換演算子に必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-117">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="54e3d-118">この演算子プロシージャでは、[拡大](../modifiers/widening.md)変換を定義していることを示します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-118">Indicates that this operator procedure defines a [Widening](../modifiers/widening.md) conversion.</span></span> <span data-ttu-id="54e3d-119">このヘルプページの「拡大変換と縮小変換」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e3d-119">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="54e3d-120">`Widening` を指定しない場合、変換演算子に必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-120">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="54e3d-121">この演算子プロシージャでは、[縮小](../modifiers/narrowing.md)変換を定義していることを示します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-121">Indicates that this operator procedure defines a [Narrowing](../modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="54e3d-122">このヘルプページの「拡大変換と縮小変換」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e3d-122">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="54e3d-123">必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-123">Required.</span></span> <span data-ttu-id="54e3d-124">この演算子プロシージャで定義する演算子のシンボルまたは識別子。</span><span class="sxs-lookup"><span data-stu-id="54e3d-124">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="54e3d-125">必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-125">Required.</span></span> <span data-ttu-id="54e3d-126">単項演算子 (変換演算子を含む) の 1 つのオペランドまたは二項演算子の左オペランドの名前と型。</span><span class="sxs-lookup"><span data-stu-id="54e3d-126">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="54e3d-127">二項演算子に必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-127">Required for binary operators.</span></span> <span data-ttu-id="54e3d-128">二項演算子の右オペランドの名前と型。</span><span class="sxs-lookup"><span data-stu-id="54e3d-128">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="54e3d-129">`operand1` と `operand2` の構文と指定項目は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54e3d-129">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="54e3d-130">パーツ</span><span class="sxs-lookup"><span data-stu-id="54e3d-130">Part</span></span>|<span data-ttu-id="54e3d-131">説明</span><span class="sxs-lookup"><span data-stu-id="54e3d-131">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="54e3d-132">省略可能ですが、引渡し方法は [ByVal](../modifiers/byval.md) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-132">Optional, but the passing mechanism must be [ByVal](../modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="54e3d-133">必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-133">Required.</span></span> <span data-ttu-id="54e3d-134">このオペランドを表す変数の名前。</span><span class="sxs-lookup"><span data-stu-id="54e3d-134">Name of the variable representing this operand.</span></span> <span data-ttu-id="54e3d-135">「 [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e3d-135">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="54e3d-136">`Option Strict` が `On` である場合を除き、省略可能です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-136">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="54e3d-137">このオペランドのデータ型。</span><span class="sxs-lookup"><span data-stu-id="54e3d-137">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="54e3d-138">`Option Strict` が `On` である場合を除き、省略可能です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-138">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="54e3d-139">演算子プロシージャで返される値のデータ型。</span><span class="sxs-lookup"><span data-stu-id="54e3d-139">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="54e3d-140">任意。</span><span class="sxs-lookup"><span data-stu-id="54e3d-140">Optional.</span></span> <span data-ttu-id="54e3d-141">演算子プロシージャで実行されるステートメントのブロック。</span><span class="sxs-lookup"><span data-stu-id="54e3d-141">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="54e3d-142">必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-142">Required.</span></span> <span data-ttu-id="54e3d-143">演算子プロシージャから呼び出し元のコードに返される値。</span><span class="sxs-lookup"><span data-stu-id="54e3d-143">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="54e3d-144">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="54e3d-144">`End` `Operator`</span></span>  
<span data-ttu-id="54e3d-145">必須です。</span><span class="sxs-lookup"><span data-stu-id="54e3d-145">Required.</span></span> <span data-ttu-id="54e3d-146">この演算子プロシージャの定義を終了します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-146">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="54e3d-147">Remarks</span><span class="sxs-lookup"><span data-stu-id="54e3d-147">Remarks</span></span>

<span data-ttu-id="54e3d-148">`Operator` は、クラスまたは構造体でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-148">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="54e3d-149">つまり、演算子の *宣言コンテキスト* は、ソース ファイル、名前空間、モジュール、インターフェイス、プロシージャ、ブロックにすることができません。</span><span class="sxs-lookup"><span data-stu-id="54e3d-149">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="54e3d-150">詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e3d-150">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="54e3d-151">すべての演算子は `Public Shared` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-151">All operators must be `Public Shared`.</span></span> <span data-ttu-id="54e3d-152">どのオペランドにも `ByRef`、`Optional`、`ParamArray` を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="54e3d-152">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="54e3d-153">戻り値を保持するために、演算子シンボルや識別子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="54e3d-153">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="54e3d-154">`Return` ステートメントを使用する必要があり、それによって値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-154">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="54e3d-155">任意の数の `Return` ステートメントをプロシージャ内の任意の場所に記述できます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-155">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="54e3d-156">この方法で演算子を定義することは、`Overloads` キーワードを使用するかどうかにかかわらず、*演算子のオーバーロード* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-156">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="54e3d-157">定義可能な演算子を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-157">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="54e3d-158">種類</span><span class="sxs-lookup"><span data-stu-id="54e3d-158">Type</span></span>|<span data-ttu-id="54e3d-159">演算子</span><span class="sxs-lookup"><span data-stu-id="54e3d-159">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="54e3d-160">単項</span><span class="sxs-lookup"><span data-stu-id="54e3d-160">Unary</span></span>|<span data-ttu-id="54e3d-161">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="54e3d-161">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="54e3d-162">2 項</span><span class="sxs-lookup"><span data-stu-id="54e3d-162">Binary</span></span>|<span data-ttu-id="54e3d-163">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="54e3d-163">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="54e3d-164">変換 (単項)</span><span class="sxs-lookup"><span data-stu-id="54e3d-164">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="54e3d-165">2 項の一覧に示した `=` 演算子は比較演算子であり、代入演算子ではありません。</span><span class="sxs-lookup"><span data-stu-id="54e3d-165">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="54e3d-166">`CType` を定義する場合、`Widening` または `Narrowing` のどちらかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-166">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="54e3d-167">一致したペア</span><span class="sxs-lookup"><span data-stu-id="54e3d-167">Matched Pairs</span></span>

<span data-ttu-id="54e3d-168">特定の演算子を一致したペアとして定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-168">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="54e3d-169">そのようなペアのどちらかの演算子を定義する場合は、他方の演算子も定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-169">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="54e3d-170">一致したペアは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="54e3d-170">The matched pairs are the following:</span></span>

- <span data-ttu-id="54e3d-171">`=` および `<>`</span><span class="sxs-lookup"><span data-stu-id="54e3d-171">`=` and `<>`</span></span>

- <span data-ttu-id="54e3d-172">`>` および `<`</span><span class="sxs-lookup"><span data-stu-id="54e3d-172">`>` and `<`</span></span>

- <span data-ttu-id="54e3d-173">`>=` および `<=`</span><span class="sxs-lookup"><span data-stu-id="54e3d-173">`>=` and `<=`</span></span>

- <span data-ttu-id="54e3d-174">`IsTrue` および `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="54e3d-174">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="54e3d-175">データ型の制限</span><span class="sxs-lookup"><span data-stu-id="54e3d-175">Data Type Restrictions</span></span>

<span data-ttu-id="54e3d-176">定義するすべての演算子には、それを定義するクラスまたは構造体が関係している必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-176">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="54e3d-177">つまり、クラスまたは構造体が、次のデータ型として指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-177">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="54e3d-178">単項演算子のオペランド。</span><span class="sxs-lookup"><span data-stu-id="54e3d-178">The operand of a unary operator.</span></span>

- <span data-ttu-id="54e3d-179">二項演算子の少なくとも 1 つのオペランド。</span><span class="sxs-lookup"><span data-stu-id="54e3d-179">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="54e3d-180">変換演算子のオペランドまたは戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="54e3d-180">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="54e3d-181">特定の演算子には、次のような追加のデータ型の制限があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-181">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="54e3d-182">`IsTrue` 演算子と `IsFalse` 演算子を定義する場合、それらはどちらも `Boolean` 型を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-182">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="54e3d-183">`<<` 演算子と `>>` 演算子を定義する場合、それらはどちらも `operand2` の `operandtype` に `Integer` 型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-183">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="54e3d-184">戻り値の型は、どちらかのオペランドの型に対応している必要はありません。</span><span class="sxs-lookup"><span data-stu-id="54e3d-184">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="54e3d-185">たとえば、`=` や `<>` などの比較演算子では、どちらのオペランドも `Boolean` でない場合でも `Boolean` を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-185">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="54e3d-186">論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="54e3d-186">Logical and Bitwise Operators</span></span>

<span data-ttu-id="54e3d-187">`And`、`Or`、`Not`、および `Xor` の各演算子では、Visual Basic で論理演算またはビットごとの演算を実行できます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-187">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="54e3d-188">ただし、クラスまたは構造体でこれらの演算子のいずれかを定義した場合は、そのビットごとの演算のみを定義できます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-188">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="54e3d-189">`Operator` ステートメントで、`AndAlso` 演算子を直接定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="54e3d-189">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="54e3d-190">ただし、次の条件を満たしている場合は、`AndAlso` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-190">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="54e3d-191">`AndAlso` に使用する同じオペランド型に対して `And` を定義している。</span><span class="sxs-lookup"><span data-stu-id="54e3d-191">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="54e3d-192">`And` の定義で、それを定義したクラスまたは構造体と同じ型を返す。</span><span class="sxs-lookup"><span data-stu-id="54e3d-192">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="54e3d-193">`And` を定義したクラスまたは構造体に `IsFalse` 演算子を定義している。</span><span class="sxs-lookup"><span data-stu-id="54e3d-193">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="54e3d-194">同様に、クラスまたは構造体の戻り値の型で同じオペランドに対して `Or` を定義し、クラスまたは構造体に `IsTrue` を定義している場合、`OrElse` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-194">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="54e3d-195">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="54e3d-195">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="54e3d-196">*拡大変換* は実行時に常に成功しますが、*縮小変換* は実行時に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-196">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="54e3d-197">詳細については、「 [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54e3d-197">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="54e3d-198">変換プロシージャを `Widening` として宣言する場合、プロシージャ コードでエラーが発生しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-198">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="54e3d-199">これは、次のことを意味します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-199">This means the following:</span></span>

- <span data-ttu-id="54e3d-200">常に `type` 型の有効な値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-200">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="54e3d-201">これは、可能性のあるすべての例外とその他のエラー条件を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-201">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="54e3d-202">これが呼び出すすべてのプロシージャからのエラーを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-202">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="54e3d-203">変換プロシージャが成功しない可能性がある場合、または未処理の例外が発生する可能性がある場合は、それを `Narrowing` として宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="54e3d-203">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="54e3d-204">例</span><span class="sxs-lookup"><span data-stu-id="54e3d-204">Example</span></span>

<span data-ttu-id="54e3d-205">次のコード例では、`Operator` ステートメントを使用して、`And`、`Or`、`IsFalse`、および `IsTrue` 演算子の演算子プロシージャを含む構造体のアウトラインを定義しています。</span><span class="sxs-lookup"><span data-stu-id="54e3d-205">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="54e3d-206">`And` および `Or` は、それぞれ `abc` 型の 2 つのオペランドを受け取り、`abc` 型を返します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-206">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="54e3d-207">`IsFalse` および `IsTrue` は、それぞれ `abc` 型の 1 つのオペランドを受け取り、`Boolean` 型を返します。</span><span class="sxs-lookup"><span data-stu-id="54e3d-207">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="54e3d-208">これらの定義により、呼び出し元のコードでは、`abc` 型のオペランドを使用して、`And`、`AndAlso`、`Or`、および `OrElse` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="54e3d-208">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="54e3d-209">関連項目</span><span class="sxs-lookup"><span data-stu-id="54e3d-209">See also</span></span>

- [<span data-ttu-id="54e3d-210">IsFalse 演算子</span><span class="sxs-lookup"><span data-stu-id="54e3d-210">IsFalse Operator</span></span>](../operators/isfalse-operator.md)
- [<span data-ttu-id="54e3d-211">IsTrue 演算子</span><span class="sxs-lookup"><span data-stu-id="54e3d-211">IsTrue Operator</span></span>](../operators/istrue-operator.md)
- [<span data-ttu-id="54e3d-212">Widening</span><span class="sxs-lookup"><span data-stu-id="54e3d-212">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="54e3d-213">Narrowing</span><span class="sxs-lookup"><span data-stu-id="54e3d-213">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="54e3d-214">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="54e3d-214">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="54e3d-215">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="54e3d-215">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="54e3d-216">方法: 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="54e3d-216">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="54e3d-217">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="54e3d-217">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="54e3d-218">方法: 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="54e3d-218">How to: Call an Operator Procedure</span></span>](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="54e3d-219">方法: 演算子を定義するクラスを使用する</span><span class="sxs-lookup"><span data-stu-id="54e3d-219">How to: Use a Class that Defines Operators</span></span>](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
