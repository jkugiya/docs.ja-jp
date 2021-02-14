---
description: '詳細情報: -= 演算子 (Visual Basic)'
title: -= 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 55574fa56d0ebe02fa5aef1a2711dfb3e5161a9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795275"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="a8681-103">-= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8681-103">-= Operator (Visual Basic)</span></span>

<span data-ttu-id="a8681-104">変数またはプロパティの値から式の値を減算し、その結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="a8681-104">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8681-105">構文</span><span class="sxs-lookup"><span data-stu-id="a8681-105">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a8681-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="a8681-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="a8681-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="a8681-107">Required.</span></span> <span data-ttu-id="a8681-108">任意の数値変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="a8681-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="a8681-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="a8681-109">Required.</span></span> <span data-ttu-id="a8681-110">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="a8681-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8681-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a8681-111">Remarks</span></span>  

 <span data-ttu-id="a8681-112">`-=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a8681-112">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="a8681-113">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a8681-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="a8681-114">`-=` 演算子は、まず、式の値 (演算子の右側) を変数またはプロパティの値 (演算子の左側) から減算します。</span><span class="sxs-lookup"><span data-stu-id="a8681-114">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="a8681-115">次に、演算子はその演算の結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="a8681-115">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a8681-116">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="a8681-116">Overloading</span></span>  

 <span data-ttu-id="a8681-117">[- 演算子 (Visual Basic)](subtraction-operator.md) は "*オーバーロード*" できます。つまり、オペランドがあるクラスまたは構造体の型を持っているときに、そのクラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="a8681-117">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a8681-118">`-` 演算子をオーバーロードすると、`-=` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="a8681-118">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="a8681-119">コードで、`-` をオーバーロードするクラスまたは構造体で `-=` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a8681-119">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a8681-120">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8681-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8681-121">例</span><span class="sxs-lookup"><span data-stu-id="a8681-121">Example</span></span>  

 <span data-ttu-id="a8681-122">次の例では、`-=` 演算子を使用して、ある `Integer` 変数を別の変数から減算し、その結果を後者の変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="a8681-122">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="a8681-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8681-123">See also</span></span>

- [<span data-ttu-id="a8681-124">- 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8681-124">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="a8681-125">代入演算子</span><span class="sxs-lookup"><span data-stu-id="a8681-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="a8681-126">算術演算子</span><span class="sxs-lookup"><span data-stu-id="a8681-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="a8681-127">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="a8681-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a8681-128">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="a8681-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a8681-129">ステートメント</span><span class="sxs-lookup"><span data-stu-id="a8681-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
