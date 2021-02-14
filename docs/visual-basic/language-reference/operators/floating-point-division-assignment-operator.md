---
description: '詳細情報: /= 演算子 (Visual Basic)'
title: /= 演算子
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 3020372be18f554df18fa6dac539ab9d0b2f725e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666031"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="321a4-103">/= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="321a4-103">/= Operator (Visual Basic)</span></span>

<span data-ttu-id="321a4-104">変数またはプロパティの値を式の値で除算し、その浮動小数点の結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="321a4-104">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321a4-105">構文</span><span class="sxs-lookup"><span data-stu-id="321a4-105">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="321a4-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="321a4-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="321a4-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="321a4-107">Required.</span></span> <span data-ttu-id="321a4-108">任意の数値変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="321a4-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="321a4-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="321a4-109">Required.</span></span> <span data-ttu-id="321a4-110">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="321a4-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="321a4-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="321a4-111">Remarks</span></span>  

 <span data-ttu-id="321a4-112">`/=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="321a4-112">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="321a4-113">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="321a4-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="321a4-114">`/=` 演算子は、最初に (演算子の左側にある) 変数またはプロパティの値を (演算子の右側にある) 式の値で除算します。</span><span class="sxs-lookup"><span data-stu-id="321a4-114">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="321a4-115">次に、この演算子はその演算の浮動小数点の結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="321a4-115">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="321a4-116">このステートメントにより、左側の変数またはプロパティに `Double` 値が代入されます。</span><span class="sxs-lookup"><span data-stu-id="321a4-116">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="321a4-117">`Option Strict` が `On` の場合、`variableorproperty` は `Double` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="321a4-117">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="321a4-118">`Option Strict` が `Off` の場合、Visual Basic によって暗黙的な変換が実行され、結果の値が `variableorproperty` に代入されます。実行時にエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="321a4-118">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="321a4-119">詳細については、「[拡大変換と縮小変換](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」および「[Option Strict ステートメント](../statements/option-strict-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="321a4-119">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="321a4-120">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="321a4-120">Overloading</span></span>  

 <span data-ttu-id="321a4-121">[/ 演算子 (Visual Basic)](floating-point-division-operator.md) は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体でその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="321a4-121">The [/ Operator (Visual Basic)](floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="321a4-122">`/` 演算子をオーバーロードすると、`/=` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="321a4-122">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="321a4-123">コードで、`/` をオーバーロードするクラスまたは構造体で `/=` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="321a4-123">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="321a4-124">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="321a4-124">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="321a4-125">例</span><span class="sxs-lookup"><span data-stu-id="321a4-125">Example</span></span>  

 <span data-ttu-id="321a4-126">次の例では、`/=` 演算子を使用して 1 番目の `Integer` 変数を 2 番目の変数で除算し、商を 1 番目の変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="321a4-126">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="321a4-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="321a4-127">See also</span></span>

- [<span data-ttu-id="321a4-128">/ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="321a4-128">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="321a4-129">\\= 演算子</span><span class="sxs-lookup"><span data-stu-id="321a4-129">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="321a4-130">代入演算子</span><span class="sxs-lookup"><span data-stu-id="321a4-130">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="321a4-131">算術演算子</span><span class="sxs-lookup"><span data-stu-id="321a4-131">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="321a4-132">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="321a4-132">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="321a4-133">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="321a4-133">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="321a4-134">ステートメント</span><span class="sxs-lookup"><span data-stu-id="321a4-134">Statements</span></span>](../../programming-guide/language-features/statements.md)
