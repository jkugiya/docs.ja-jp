---
description: '詳細情報: &amp;= 演算子 (Visual Basic)'
title: '&amp;= 演算子'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: ffc4de352ee29f4c7d18a257dd3699b37c668db7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774318"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="f4ef7-103">&amp;= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4ef7-103">&amp;= Operator (Visual Basic)</span></span>

<span data-ttu-id="f4ef7-104">`String` 式を `String` 変数またはプロパティに連結し、結果をその変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-104">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4ef7-105">構文</span><span class="sxs-lookup"><span data-stu-id="f4ef7-105">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f4ef7-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="f4ef7-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="f4ef7-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-107">Required.</span></span> <span data-ttu-id="f4ef7-108">任意の `String` 変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-108">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="f4ef7-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-109">Required.</span></span> <span data-ttu-id="f4ef7-110">任意のブール型 ( `String` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-110">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4ef7-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f4ef7-111">Remarks</span></span>  

 <span data-ttu-id="f4ef7-112">`&=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-112">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f4ef7-113">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="f4ef7-114">`&=` 演算子は、右側の `String` 式を左側の `String` 変数またはプロパティに連結し、結果を左側の変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-114">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f4ef7-115">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="f4ef7-115">Overloading</span></span>  

 <span data-ttu-id="f4ef7-116">[& 演算子](concatenation-operator.md)は "*オーバーロード*" できます。つまり、オペランドがあるクラスまたは構造体の型を持っているときに、そのクラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-116">The [& Operator](concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f4ef7-117">`&` 演算子をオーバーロードすると、`&=` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-117">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="f4ef7-118">コードで、`&` をオーバーロードするクラスまたは構造体で `&=` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-118">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f4ef7-119">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4ef7-120">例</span><span class="sxs-lookup"><span data-stu-id="f4ef7-120">Example</span></span>  

 <span data-ttu-id="f4ef7-121">次の例では、`&=` 演算子を使用して 2 つの `String` 変数を連結し、その結果を最初の変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="f4ef7-121">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f4ef7-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4ef7-122">See also</span></span>

- [<span data-ttu-id="f4ef7-123">& 演算子</span><span class="sxs-lookup"><span data-stu-id="f4ef7-123">& Operator</span></span>](concatenation-operator.md)
- [<span data-ttu-id="f4ef7-124">+= 演算子</span><span class="sxs-lookup"><span data-stu-id="f4ef7-124">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="f4ef7-125">代入演算子</span><span class="sxs-lookup"><span data-stu-id="f4ef7-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="f4ef7-126">連結演算子</span><span class="sxs-lookup"><span data-stu-id="f4ef7-126">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="f4ef7-127">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="f4ef7-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f4ef7-128">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="f4ef7-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f4ef7-129">ステートメント</span><span class="sxs-lookup"><span data-stu-id="f4ef7-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
