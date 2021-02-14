---
description: '詳細情報: = 演算子 (Visual Basic)'
title: = 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 3cf45fb93bf5138f9e7fa5a43650019ab58674fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774253"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bd75b-103">= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd75b-103">= Operator (Visual Basic)</span></span>

<span data-ttu-id="bd75b-104">変数またはプロパティに値を代入します。</span><span class="sxs-lookup"><span data-stu-id="bd75b-104">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd75b-105">構文</span><span class="sxs-lookup"><span data-stu-id="bd75b-105">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="bd75b-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="bd75b-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="bd75b-107">任意の書き込み可能な変数または任意のプロパティ。</span><span class="sxs-lookup"><span data-stu-id="bd75b-107">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="bd75b-108">任意のリテラル、定数、または式。</span><span class="sxs-lookup"><span data-stu-id="bd75b-108">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd75b-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="bd75b-109">Remarks</span></span>  

 <span data-ttu-id="bd75b-110">等号 (`=`) の左側の要素として、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd75b-110">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="bd75b-111">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bd75b-111">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span> <span data-ttu-id="bd75b-112">`=` 演算子は、右辺の値を左辺の変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="bd75b-112">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd75b-113">`=` 演算子は、比較演算子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd75b-113">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="bd75b-114">詳細については、「[比較演算子](comparison-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd75b-114">For details, see [Comparison Operators](comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bd75b-115">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="bd75b-115">Overloading</span></span>  

 <span data-ttu-id="bd75b-116">`=` 演算子は、代入演算子としてではなく、関係比較演算子としてのみオーバーロードできます。</span><span class="sxs-lookup"><span data-stu-id="bd75b-116">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="bd75b-117">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd75b-117">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd75b-118">例</span><span class="sxs-lookup"><span data-stu-id="bd75b-118">Example</span></span>  

 <span data-ttu-id="bd75b-119">代入演算子の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bd75b-119">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="bd75b-120">右辺の値が左辺の変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="bd75b-120">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="bd75b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd75b-121">See also</span></span>

- [<span data-ttu-id="bd75b-122">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="bd75b-122">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="bd75b-123">\*= 演算子</span><span class="sxs-lookup"><span data-stu-id="bd75b-123">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="bd75b-124">+= 演算子</span><span class="sxs-lookup"><span data-stu-id="bd75b-124">+= Operator</span></span>](addition-assignment-operator.md)
- [<span data-ttu-id="bd75b-125">-= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd75b-125">-= Operator (Visual Basic)</span></span>](subtraction-assignment-operator.md)
- [<span data-ttu-id="bd75b-126">/= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd75b-126">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="bd75b-127">\\= 演算子</span><span class="sxs-lookup"><span data-stu-id="bd75b-127">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="bd75b-128">^= 演算子</span><span class="sxs-lookup"><span data-stu-id="bd75b-128">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="bd75b-129">ステートメント</span><span class="sxs-lookup"><span data-stu-id="bd75b-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="bd75b-130">比較演算子</span><span class="sxs-lookup"><span data-stu-id="bd75b-130">Comparison Operators</span></span>](comparison-operators.md)
- [<span data-ttu-id="bd75b-131">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="bd75b-131">ReadOnly</span></span>](../modifiers/readonly.md)
- [<span data-ttu-id="bd75b-132">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="bd75b-132">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
