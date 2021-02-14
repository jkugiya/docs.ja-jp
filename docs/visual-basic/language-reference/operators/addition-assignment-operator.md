---
description: '詳細情報: += 演算子 (Visual Basic)'
title: += 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: e5a6b8fcc75e44c00ee18fec9cd57e68b1218de7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640473"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="fbbe0-103">+= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbbe0-103">+= Operator (Visual Basic)</span></span>

<span data-ttu-id="fbbe0-104">数値式の値を数値変数またはプロパティの値に加算し、結果をその変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-104">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="fbbe0-105">また、`String` 式を `String` 変数またはプロパティに連結し、結果をその変数またはプロパティに代入するために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-105">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbbe0-106">構文</span><span class="sxs-lookup"><span data-stu-id="fbbe0-106">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="fbbe0-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="fbbe0-107">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="fbbe0-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-108">Required.</span></span> <span data-ttu-id="fbbe0-109">任意の数値または `String` 変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-109">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="fbbe0-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-110">Required.</span></span> <span data-ttu-id="fbbe0-111">任意の数値または `String` 式。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-111">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbbe0-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="fbbe0-112">Remarks</span></span>  

 <span data-ttu-id="fbbe0-113">`+=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-113">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="fbbe0-114">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-114">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="fbbe0-115">`+=` 演算子は、右側の値を左側の変数またはプロパティに追加し、その結果を左側の変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-115">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="fbbe0-116">`+=` 演算子を使用して、右側の `String` 式を左側の `String` 変数またはプロパティに連結し、その結果を左側の変数またはプロパティに代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-116">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbbe0-117">`+=` 演算子を使用すると、加算と文字列連結のどちらが行われるのか判断できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-117">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="fbbe0-118">あいまいさをなくし、自己文書化コードを実現するために、連結には `&=` 演算子を使用してください。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-118">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="fbbe0-119">コンパイル環境で厳密なセマンティクスが適用されている場合、この代入演算子は拡大変換を暗黙的に実行しますが、縮小変換は実行しません。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-119">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="fbbe0-120">これらの変換の詳細については、「[拡大変換と縮小変換](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-120">For more information on these conversions, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="fbbe0-121">厳密なセマンティクスおよび寛容なセマンティクスの詳細については、「[Option Strict ステートメント](../statements/option-strict-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-121">For more information on strict and permissive semantics, see [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="fbbe0-122">寛容なセマンティクスが許可されている場合、`+=` 演算子は、`+` 演算子によって実行されるものと同じ各種変換 (文字列変換および数値変換) を暗黙的に実行します。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-122">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="fbbe0-123">これらの変換の詳細については、「[+ 演算子](addition-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-123">For details on these conversions, see [+ Operator](addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="fbbe0-124">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="fbbe0-124">Overloading</span></span>  

 <span data-ttu-id="fbbe0-125">`+` 演算子は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体で、演算子の動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-125">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fbbe0-126">`+` 演算子をオーバーロードすると、`+=` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-126">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="fbbe0-127">コードで、`+` をオーバーロードするクラスまたは構造体で `+=` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-127">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fbbe0-128">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-128">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbbe0-129">例</span><span class="sxs-lookup"><span data-stu-id="fbbe0-129">Example</span></span>  

 <span data-ttu-id="fbbe0-130">次の例では、`+=` 演算子を使用して、ある変数の値を別の値と結合します。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-130">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="fbbe0-131">最初の部分では `+=` を数値変数と共に使用して、ある値を別の値に追加します。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-131">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="fbbe0-132">2 番目の部分では、`+=` を `String` 変数と共に使用して、ある値を別の値と連結します。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-132">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="fbbe0-133">どちらの場合も、結果は最初の変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-133">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="fbbe0-134">`num1` の値は 13 になり、`str1` の値は "103" になりました。</span><span class="sxs-lookup"><span data-stu-id="fbbe0-134">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbbe0-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbbe0-135">See also</span></span>

- [<span data-ttu-id="fbbe0-136">+ 演算子</span><span class="sxs-lookup"><span data-stu-id="fbbe0-136">+ Operator</span></span>](addition-operator.md)
- [<span data-ttu-id="fbbe0-137">代入演算子</span><span class="sxs-lookup"><span data-stu-id="fbbe0-137">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="fbbe0-138">算術演算子</span><span class="sxs-lookup"><span data-stu-id="fbbe0-138">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="fbbe0-139">連結演算子</span><span class="sxs-lookup"><span data-stu-id="fbbe0-139">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="fbbe0-140">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="fbbe0-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="fbbe0-141">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="fbbe0-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="fbbe0-142">ステートメント</span><span class="sxs-lookup"><span data-stu-id="fbbe0-142">Statements</span></span>](../../programming-guide/language-features/statements.md)
