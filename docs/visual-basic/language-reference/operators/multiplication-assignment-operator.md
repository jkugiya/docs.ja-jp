---
description: '詳細情報: *= 演算子 (Visual Basic)'
title: '*= 演算子'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: d5a88dc71a05c6375a09fe3f4b55eff704c13910
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665420"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0bdb3-103">\*= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bdb3-103">\*= Operator (Visual Basic)</span></span>

<span data-ttu-id="0bdb3-104">変数またはプロパティの値を式の値で乗算し、その結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-104">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bdb3-105">構文</span><span class="sxs-lookup"><span data-stu-id="0bdb3-105">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0bdb3-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="0bdb3-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="0bdb3-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-107">Required.</span></span> <span data-ttu-id="0bdb3-108">任意の数値変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="0bdb3-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-109">Required.</span></span> <span data-ttu-id="0bdb3-110">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bdb3-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="0bdb3-111">Remarks</span></span>  

 <span data-ttu-id="0bdb3-112">`*=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-112">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="0bdb3-113">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="0bdb3-114">`*=` 演算子は、最初に (演算子の右側にある) 式の値に、(演算子の左側にある) 変数またはプロパティの値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-114">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="0bdb3-115">次に、その演算の結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-115">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0bdb3-116">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="0bdb3-116">Overloading</span></span>  

 <span data-ttu-id="0bdb3-117">[\* 演算子](multiplication-operator.md)は "*オーバーロード*" できます。つまり、オペランドがクラスまたは構造体の型を持っているときに、クラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-117">The [\* Operator](multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0bdb3-118">`*` 演算子をオーバーロードすると、`*=` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-118">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="0bdb3-119">コードで、`*` をオーバーロードするクラスまたは構造体で `*=` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-119">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0bdb3-120">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bdb3-121">例</span><span class="sxs-lookup"><span data-stu-id="0bdb3-121">Example</span></span>  

 <span data-ttu-id="0bdb3-122">次の例では、`*=` 演算子を使用して、最初の `Integer` 変数に 2 番目の変数を乗算し、その結果を最初の変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="0bdb3-122">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="0bdb3-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bdb3-123">See also</span></span>

- [<span data-ttu-id="0bdb3-124">\* 演算子</span><span class="sxs-lookup"><span data-stu-id="0bdb3-124">\* Operator</span></span>](multiplication-operator.md)
- [<span data-ttu-id="0bdb3-125">代入演算子</span><span class="sxs-lookup"><span data-stu-id="0bdb3-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="0bdb3-126">算術演算子</span><span class="sxs-lookup"><span data-stu-id="0bdb3-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="0bdb3-127">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="0bdb3-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="0bdb3-128">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="0bdb3-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="0bdb3-129">ステートメント</span><span class="sxs-lookup"><span data-stu-id="0bdb3-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
