---
description: '詳細情報: Visual Basic の演算子および式'
title: 演算子および式
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: 526051e16da29cd139abf587e1393ad331fdcdaa
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471397"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="ed14a-103">Visual Basic の演算子および式</span><span class="sxs-lookup"><span data-stu-id="ed14a-103">Operators and Expressions in Visual Basic</span></span>

<span data-ttu-id="ed14a-104">*演算子* は、値が格納されている 1 つ以上のコード要素に対して演算を実行するコード要素です。</span><span class="sxs-lookup"><span data-stu-id="ed14a-104">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="ed14a-105">値要素は、変数、定数、リテラル、プロパティ、`Function` プロシージャおよび `Operator` プロシージャからの戻り値、式などです。</span><span class="sxs-lookup"><span data-stu-id="ed14a-105">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="ed14a-106">*式* は、演算子で結合され、新しい値を生成する一連の値要素です。</span><span class="sxs-lookup"><span data-stu-id="ed14a-106">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="ed14a-107">演算子は、値要素に対して、計算、比較、またはその他の演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="ed14a-107">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="ed14a-108">演算子の種類</span><span class="sxs-lookup"><span data-stu-id="ed14a-108">Types of Operators</span></span>  

 <span data-ttu-id="ed14a-109">Visual Basic には、次のような種類の演算子があります。</span><span class="sxs-lookup"><span data-stu-id="ed14a-109">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="ed14a-110">[算術演算子](arithmetic-operators.md)は、数値に対して一般的な計算を実行します (ビット パターンのシフトも含まれます)。</span><span class="sxs-lookup"><span data-stu-id="ed14a-110">[Arithmetic Operators](arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="ed14a-111">[比較演算子](comparison-operators.md)は、2 つの式を比較し、比較の結果を表す `Boolean` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="ed14a-111">[Comparison Operators](comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="ed14a-112">[連結演算子](concatenation-operators.md)は、複数の文字列を結合して 1 つの文字列にします。</span><span class="sxs-lookup"><span data-stu-id="ed14a-112">[Concatenation Operators](concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="ed14a-113">[Visual Basic の論理演算子およびビット処理演算子](logical-and-bitwise-operators.md)は、`Boolean` 値または数値を組み合わせて、同じデータ型の結果を値として返します。</span><span class="sxs-lookup"><span data-stu-id="ed14a-113">[Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="ed14a-114">演算子で結合される値要素は、演算子の *オペランド* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ed14a-114">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="ed14a-115">演算子は値要素と結合されると *式* になります。ただし、代入演算子は例外で、これはステートメントになります。</span><span class="sxs-lookup"><span data-stu-id="ed14a-115">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="ed14a-116">詳細については、「[ステートメント](../statements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed14a-116">For more information, see [Statements](../statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="ed14a-117">式の評価</span><span class="sxs-lookup"><span data-stu-id="ed14a-117">Evaluation of Expressions</span></span>  

 <span data-ttu-id="ed14a-118">式の最終的な結果は、通常、`Boolean`、`String`、または数値型などの一般的なデータ型で表されます。</span><span class="sxs-lookup"><span data-stu-id="ed14a-118">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="ed14a-119">次に式の例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="ed14a-119">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="ed14a-120">次の例のように、1 つの式またはステートメントで複数の演算子を使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="ed14a-120">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="ed14a-121">この例では、Visual Basic によって代入演算子 (`=`) の右側にある式の演算が実行され、次にその結果の値が左側にある変数 `x` に代入されます。</span><span class="sxs-lookup"><span data-stu-id="ed14a-121">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="ed14a-122">1 つの式で使用できる演算子の数には、事実上制限はありません。ただし、正しい結果を得るには、[Visual Basic における演算子の優先順位](../../../language-reference/operators/operator-precedence.md)を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed14a-122">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="ed14a-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed14a-123">See also</span></span>

- [<span data-ttu-id="ed14a-124">演算子</span><span class="sxs-lookup"><span data-stu-id="ed14a-124">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="ed14a-125">演算子の効率のよい組み合わせ</span><span class="sxs-lookup"><span data-stu-id="ed14a-125">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="ed14a-126">ステートメント</span><span class="sxs-lookup"><span data-stu-id="ed14a-126">Statements</span></span>](../../../language-reference/statements/index.md)
