---
description: '詳細情報: Not 演算子 (Visual Basic)'
title: Not 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 91f3525b52d6f38081b8e5ba208c193f714a4045
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665355"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="354fb-103">Not 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="354fb-103">Not Operator (Visual Basic)</span></span>

<span data-ttu-id="354fb-104">`Boolean` 式の場合は論理否定、数値式の場合はビットごとの否定を求めます。</span><span class="sxs-lookup"><span data-stu-id="354fb-104">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="354fb-105">構文</span><span class="sxs-lookup"><span data-stu-id="354fb-105">Syntax</span></span>  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="354fb-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="354fb-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="354fb-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="354fb-107">Required.</span></span> <span data-ttu-id="354fb-108">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="354fb-108">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="354fb-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="354fb-109">Required.</span></span> <span data-ttu-id="354fb-110">任意の `Boolean` または数値式。</span><span class="sxs-lookup"><span data-stu-id="354fb-110">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="354fb-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="354fb-111">Remarks</span></span>  

 <span data-ttu-id="354fb-112">次の表は、`Boolean` 式で、`result` がどのように決定されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="354fb-112">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="354fb-113">`expression` が次の場合</span><span class="sxs-lookup"><span data-stu-id="354fb-113">If `expression` is</span></span>|<span data-ttu-id="354fb-114">`result` の値は次のようになります</span><span class="sxs-lookup"><span data-stu-id="354fb-114">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="354fb-115">数値式の場合、`Not` 演算子は、次の表に従って数値式のビット値を反転させ、`result` に対応するビットを設定します。</span><span class="sxs-lookup"><span data-stu-id="354fb-115">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="354fb-116">`expression` 内のビットが次の場合</span><span class="sxs-lookup"><span data-stu-id="354fb-116">If bit in `expression` is</span></span>|<span data-ttu-id="354fb-117">`result` 内のビットは次のようになります</span><span class="sxs-lookup"><span data-stu-id="354fb-117">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="354fb-118">1</span><span class="sxs-lookup"><span data-stu-id="354fb-118">1</span></span>|<span data-ttu-id="354fb-119">0</span><span class="sxs-lookup"><span data-stu-id="354fb-119">0</span></span>|  
|<span data-ttu-id="354fb-120">0</span><span class="sxs-lookup"><span data-stu-id="354fb-120">0</span></span>|<span data-ttu-id="354fb-121">1</span><span class="sxs-lookup"><span data-stu-id="354fb-121">1</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="354fb-122">論理演算子とビット演算子は、他の算術演算子および関係演算子より優先順位が低いので、正確に実行するために、ビットごとの演算はかっこで囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="354fb-122">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="354fb-123">データの種類</span><span class="sxs-lookup"><span data-stu-id="354fb-123">Data Types</span></span>  

 <span data-ttu-id="354fb-124">ブール値の否定の場合、結果のデータ型は `Boolean` になります。</span><span class="sxs-lookup"><span data-stu-id="354fb-124">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="354fb-125">ビットごとの否定の場合、結果のデータ型は `expression` のデータ型と同じになります。</span><span class="sxs-lookup"><span data-stu-id="354fb-125">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="354fb-126">ただし、式が `Decimal` の場合、結果は `Long` になります。</span><span class="sxs-lookup"><span data-stu-id="354fb-126">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="354fb-127">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="354fb-127">Overloading</span></span>  

 <span data-ttu-id="354fb-128">`Not` 演算子は "*オーバーロード*" できます。つまり、オペランドがあるクラスまたは構造体の型を持っているときに、そのクラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="354fb-128">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="354fb-129">コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="354fb-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="354fb-130">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="354fb-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="354fb-131">例</span><span class="sxs-lookup"><span data-stu-id="354fb-131">Example</span></span>  

 <span data-ttu-id="354fb-132">次の例では、`Boolean` 式で `Not` 演算子を使用して論理否定を実行しています。</span><span class="sxs-lookup"><span data-stu-id="354fb-132">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="354fb-133">この結果は、式の値の反転を表す `Boolean` 値です。</span><span class="sxs-lookup"><span data-stu-id="354fb-133">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 <span data-ttu-id="354fb-134">前の例では、それぞれ `False` と `True` の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="354fb-134">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="354fb-135">例</span><span class="sxs-lookup"><span data-stu-id="354fb-135">Example</span></span>  

 <span data-ttu-id="354fb-136">次の例では、`Not` 演算子を使用して、数値式の個々のビットの論理否定を実行しています。</span><span class="sxs-lookup"><span data-stu-id="354fb-136">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="354fb-137">結果パターンのビットは、オペランド パターンの対応するビットの反転に設定されます (符号ビットを含む)。</span><span class="sxs-lookup"><span data-stu-id="354fb-137">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 <span data-ttu-id="354fb-138">前の例では、結果としてそれぞれ –11、–9、および –7 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="354fb-138">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="354fb-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="354fb-139">See also</span></span>

- [<span data-ttu-id="354fb-140">論理演算子とビット処理演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="354fb-140">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="354fb-141">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="354fb-141">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="354fb-142">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="354fb-142">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="354fb-143">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="354fb-143">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
