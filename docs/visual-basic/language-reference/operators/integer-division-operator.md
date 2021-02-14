---
description: '詳細情報: 演算子 (Visual Basic)'
title: '\ 演算子'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: e15a630d37e423b7a7d0040e495f2543889f37b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665784"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="7982c-103">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7982c-103">\ Operator (Visual Basic)</span></span>

<span data-ttu-id="7982c-104">2 つの数値の商を計算し、結果を整数で返します。</span><span class="sxs-lookup"><span data-stu-id="7982c-104">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7982c-105">構文</span><span class="sxs-lookup"><span data-stu-id="7982c-105">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="7982c-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="7982c-106">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="7982c-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="7982c-107">Required.</span></span> <span data-ttu-id="7982c-108">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="7982c-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="7982c-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="7982c-109">Required.</span></span> <span data-ttu-id="7982c-110">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="7982c-110">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="7982c-111">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="7982c-111">Supported Types</span></span>  

 <span data-ttu-id="7982c-112">符号なし型、浮動小数点型、`Decimal` を含む、すべての数値型。</span><span class="sxs-lookup"><span data-stu-id="7982c-112">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="7982c-113">結果</span><span class="sxs-lookup"><span data-stu-id="7982c-113">Result</span></span>  

 <span data-ttu-id="7982c-114">結果は、`expression1` を `expression2` で除算した整数の商で、小数部分はすべて破棄され、整数部分のみ保持されます。</span><span class="sxs-lookup"><span data-stu-id="7982c-114">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="7982c-115">これは "*切り捨て*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7982c-115">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="7982c-116">結果のデータ型は `expression1` および `expression2` のデータ型に適した数値型になります。</span><span class="sxs-lookup"><span data-stu-id="7982c-116">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="7982c-117">「[演算子の結果のデータ型](data-types-of-operator-results.md)」の「整数演算」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7982c-117">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="7982c-118">[/演算子 (Visual Basic)](floating-point-division-operator.md) は、小数部分の剰余を保持する完全な商を返します。</span><span class="sxs-lookup"><span data-stu-id="7982c-118">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7982c-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="7982c-119">Remarks</span></span>  

 <span data-ttu-id="7982c-120">除算を実行する前に、Visual Basic は浮動小数点数値式を `Long` に変換しようとします。</span><span class="sxs-lookup"><span data-stu-id="7982c-120">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="7982c-121">`Option Strict` が `On` の場合は、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7982c-121">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="7982c-122">`Option Strict` が `Off` の場合、値が [Long データ型](../data-types/long-data-type.md)の範囲外の場合は <xref:System.OverflowException> が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7982c-122">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../data-types/long-data-type.md).</span></span> <span data-ttu-id="7982c-123">`Long` への変換は、"*銀行型丸め*" の対象にもなります。</span><span class="sxs-lookup"><span data-stu-id="7982c-123">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="7982c-124">詳細については、「[データ型変換関数](../functions/type-conversion-functions.md)」の「小数部」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7982c-124">For more information, see "Fractional Parts" in [Type Conversion Functions](../functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="7982c-125">`expression1` または `expression2` が [Nothing](../nothing.md) に評価される場合、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="7982c-125">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="7982c-126">0 除算を試行した場合</span><span class="sxs-lookup"><span data-stu-id="7982c-126">Attempted Division by Zero</span></span>  

 <span data-ttu-id="7982c-127">`expression2` が 0 に評価される場合、`\` 演算子は <xref:System.DivideByZeroException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="7982c-127">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="7982c-128">これは、オペランドのすべての数値データ型に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="7982c-128">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7982c-129">`\` 演算子は "*オーバーロード*" できます。つまり、オペランドがクラスまたは構造体の型を持っているときに、クラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="7982c-129">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7982c-130">コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7982c-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7982c-131">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7982c-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7982c-132">例</span><span class="sxs-lookup"><span data-stu-id="7982c-132">Example</span></span>  

 <span data-ttu-id="7982c-133">次の例では、`\` 演算子を使用して整数除算を実行します。</span><span class="sxs-lookup"><span data-stu-id="7982c-133">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="7982c-134">結果は、2 つのオペランドの整数商を表す整数で、剰余は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="7982c-134">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="7982c-135">上の例の式では、それぞれ 2、3、33、-22 の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="7982c-135">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7982c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="7982c-136">See also</span></span>

- [<span data-ttu-id="7982c-137">\\= 演算子</span><span class="sxs-lookup"><span data-stu-id="7982c-137">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="7982c-138">/ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7982c-138">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="7982c-139">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="7982c-139">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="7982c-140">算術演算子</span><span class="sxs-lookup"><span data-stu-id="7982c-140">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="7982c-141">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="7982c-141">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="7982c-142">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="7982c-142">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="7982c-143">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="7982c-143">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
