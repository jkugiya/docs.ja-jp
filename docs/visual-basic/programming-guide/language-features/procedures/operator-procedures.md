---
description: '詳細情報: 演算子プロシージャ (Visual Basic)'
title: 演算子プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: 836eeb2e705a96c49b5fa53e277ccf025d1915b2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479960"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="e0033-103">演算子プロシージャ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0033-103">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="e0033-104">演算子プロシージャは、定義済みのクラスまたは構造体での標準演算子 (`*`、`<>`、`And` など) の動作を定義する一連の Visual Basic ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e0033-104">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="e0033-105">これは、"*演算子のオーバーロード*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e0033-105">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="e0033-106">演算子プロシージャを定義する場合</span><span class="sxs-lookup"><span data-stu-id="e0033-106">When to Define Operator Procedures</span></span>

<span data-ttu-id="e0033-107">クラスまたは構造体を定義したら、そのクラスまたは構造体の型で変数を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="e0033-107">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="e0033-108">このような変数は、式の一部として演算に関与することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e0033-108">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="e0033-109">そのためには、演算子のオペランドである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0033-109">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="e0033-110">Visual Basic では、基本的なデータ型でのみ演算子を定義します。</span><span class="sxs-lookup"><span data-stu-id="e0033-110">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="e0033-111">オペランドの一方または両方がクラスまたは構造体の型である場合、演算子の動作を定義できます。</span><span class="sxs-lookup"><span data-stu-id="e0033-111">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="e0033-112">詳細については、「[Operator Statement](../../../language-reference/statements/operator-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e0033-112">For more information, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="e0033-113">演算子プロシージャの型</span><span class="sxs-lookup"><span data-stu-id="e0033-113">Types of Operator Procedure</span></span>

<span data-ttu-id="e0033-114">演算子プロシージャは、次のいずれかの型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="e0033-114">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="e0033-115">引数がクラスまたは構造体の型である単項演算子の定義。</span><span class="sxs-lookup"><span data-stu-id="e0033-115">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="e0033-116">引数の少なくとも 1 つがクラスまたは構造体の型である 2 項演算子の定義。</span><span class="sxs-lookup"><span data-stu-id="e0033-116">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="e0033-117">引数がクラスまたは構造体の型である変換演算子の定義。</span><span class="sxs-lookup"><span data-stu-id="e0033-117">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="e0033-118">クラスまたは構造体の型を返す変換演算子の定義。</span><span class="sxs-lookup"><span data-stu-id="e0033-118">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="e0033-119">変換演算子は常に単項であり、定義する演算子として常に `CType` を使用します。</span><span class="sxs-lookup"><span data-stu-id="e0033-119">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="e0033-120">宣言の構文</span><span class="sxs-lookup"><span data-stu-id="e0033-120">Declaration Syntax</span></span>

<span data-ttu-id="e0033-121">演算子プロシージャを宣言するための構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e0033-121">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="e0033-122">`Widening` または `Narrowing` キーワードは、型変換演算子でのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="e0033-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="e0033-123">型変換演算子では、演算子記号は常に [CType 関数](../../../language-reference/functions/ctype-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="e0033-123">The operator symbol is always [CType Function](../../../language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="e0033-124">2 項演算子を定義するには、2 つのオペランドを宣言し、型変換演算子を含め、単項演算子を定義するには、1 つのオペランドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e0033-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="e0033-125">すべてのオペランドを `ByVal` で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0033-125">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="e0033-126">[Sub プロシージャ](./sub-procedures.md)のパラメーターを宣言する場合と同様に、各オペランドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e0033-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="e0033-127">データの種類</span><span class="sxs-lookup"><span data-stu-id="e0033-127">Data Type</span></span>

<span data-ttu-id="e0033-128">定義済みのクラスまたは構造体で演算子を定義するため、オペランドの少なくとも一方は、そのクラスまたは構造体のデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0033-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="e0033-129">型変換演算子の場合、オペランドまたは戻り値の型が、クラスまたは構造体のデータ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e0033-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="e0033-130">詳細については、「[Operator Statement](../../../language-reference/statements/operator-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e0033-130">For more details, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="e0033-131">呼び出しの構文</span><span class="sxs-lookup"><span data-stu-id="e0033-131">Calling Syntax</span></span>

<span data-ttu-id="e0033-132">演算子プロシージャは、式で演算子記号を使用して暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e0033-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="e0033-133">事前定義された演算子の場合と同様にオペランドを指定します。</span><span class="sxs-lookup"><span data-stu-id="e0033-133">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="e0033-134">演算子プロシージャの暗黙的な呼び出しの構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e0033-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="e0033-135">`Dim testStruct As`  *構造体名*</span><span class="sxs-lookup"><span data-stu-id="e0033-135">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="e0033-136">`Dim testNewStruct As`  *構造体名*  `= testStruct`  *演算子記号*  `10`</span><span class="sxs-lookup"><span data-stu-id="e0033-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="e0033-137">宣言と呼び出しの実例</span><span class="sxs-lookup"><span data-stu-id="e0033-137">Illustration of Declaration and Call</span></span>

<span data-ttu-id="e0033-138">次の構造体は、構成要素の上位および下位の要素として、符号付き 128 ビット整数値を格納します。</span><span class="sxs-lookup"><span data-stu-id="e0033-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="e0033-139">2 つの `veryLong` 値を加算し、結果の `veryLong` 値を生成する `+` 演算子を定義します。</span><span class="sxs-lookup"><span data-stu-id="e0033-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="e0033-140">次の例は、`veryLong` で定義された `+` 演算子の一般的な呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="e0033-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="e0033-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="e0033-141">See also</span></span>

- [<span data-ttu-id="e0033-142">手順</span><span class="sxs-lookup"><span data-stu-id="e0033-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="e0033-143">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e0033-143">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="e0033-144">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e0033-144">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="e0033-145">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e0033-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e0033-146">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="e0033-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e0033-147">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="e0033-147">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="e0033-148">方法: 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="e0033-148">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="e0033-149">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="e0033-149">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="e0033-150">方法: 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="e0033-150">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="e0033-151">方法: 演算子を定義するクラスを使用する</span><span class="sxs-lookup"><span data-stu-id="e0033-151">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
