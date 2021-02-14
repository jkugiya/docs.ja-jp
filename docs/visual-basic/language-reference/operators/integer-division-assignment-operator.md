---
description: '詳細情報: = 演算子'
title: '\= 演算子'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: a05e136cbf17eaf7102fb2213993adf9cf0e06be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665810"
---
# <a name="-operator"></a><span data-ttu-id="41bf5-103">\\= 演算子</span><span class="sxs-lookup"><span data-stu-id="41bf5-103">\\= Operator</span></span>

<span data-ttu-id="41bf5-104">変数またはプロパティの値を式の値で除算し、整数の結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="41bf5-104">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41bf5-105">構文</span><span class="sxs-lookup"><span data-stu-id="41bf5-105">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="41bf5-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="41bf5-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="41bf5-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="41bf5-107">Required.</span></span> <span data-ttu-id="41bf5-108">任意の数値変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="41bf5-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="41bf5-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="41bf5-109">Required.</span></span> <span data-ttu-id="41bf5-110">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="41bf5-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41bf5-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="41bf5-111">Remarks</span></span>  

 <span data-ttu-id="41bf5-112">`\=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="41bf5-112">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="41bf5-113">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="41bf5-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="41bf5-114">`\=` 演算子は、左側の変数またはプロパティの値を右側の値で除算し、整数の結果を左側の変数またはプロパティに代入します</span><span class="sxs-lookup"><span data-stu-id="41bf5-114">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="41bf5-115">整数除算の詳細については、「[\ 演算子 (Visual Basic)](integer-division-operator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41bf5-115">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="41bf5-116">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="41bf5-116">Overloading</span></span>  

 <span data-ttu-id="41bf5-117">`\` 演算子は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体で、演算子の動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="41bf5-117">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="41bf5-118">`\` 演算子をオーバーロードすると、`\=` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="41bf5-118">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="41bf5-119">コードで、`\` をオーバーロードするクラスまたは構造体で `\=` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="41bf5-119">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="41bf5-120">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41bf5-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41bf5-121">例</span><span class="sxs-lookup"><span data-stu-id="41bf5-121">Example</span></span>  

 <span data-ttu-id="41bf5-122">次の例では、`\=` 演算子を使用して 1 番目の `Integer` 変数を 2 番目の変数で除算し、整数の結果を 1 番目の変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="41bf5-122">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="41bf5-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="41bf5-123">See also</span></span>

- [<span data-ttu-id="41bf5-124">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41bf5-124">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="41bf5-125">/= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41bf5-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="41bf5-126">代入演算子</span><span class="sxs-lookup"><span data-stu-id="41bf5-126">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="41bf5-127">算術演算子</span><span class="sxs-lookup"><span data-stu-id="41bf5-127">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="41bf5-128">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="41bf5-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="41bf5-129">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="41bf5-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="41bf5-130">ステートメント</span><span class="sxs-lookup"><span data-stu-id="41bf5-130">Statements</span></span>](../../programming-guide/language-features/statements.md)
