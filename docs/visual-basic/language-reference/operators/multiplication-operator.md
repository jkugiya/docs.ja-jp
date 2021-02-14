---
description: '詳細情報: * 演算子 (Visual Basic)'
title: '* 演算子'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 9a9f7eff9468fd6784b705a50871bc79fd6c1faa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665394"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="bddf8-103">\* 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bddf8-103">\* Operator (Visual Basic)</span></span>

<span data-ttu-id="bddf8-104">2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="bddf8-104">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bddf8-105">構文</span><span class="sxs-lookup"><span data-stu-id="bddf8-105">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="bddf8-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="bddf8-106">Parts</span></span>  
  
|<span data-ttu-id="bddf8-107">用語</span><span class="sxs-lookup"><span data-stu-id="bddf8-107">Term</span></span>|<span data-ttu-id="bddf8-108">定義</span><span class="sxs-lookup"><span data-stu-id="bddf8-108">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="bddf8-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="bddf8-109">Required.</span></span> <span data-ttu-id="bddf8-110">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="bddf8-110">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="bddf8-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="bddf8-111">Required.</span></span> <span data-ttu-id="bddf8-112">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="bddf8-112">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="bddf8-113">結果</span><span class="sxs-lookup"><span data-stu-id="bddf8-113">Result</span></span>  

 <span data-ttu-id="bddf8-114">結果は `number1` と `number2` の積になります。</span><span class="sxs-lookup"><span data-stu-id="bddf8-114">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="bddf8-115">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="bddf8-115">Supported Types</span></span>  

 <span data-ttu-id="bddf8-116">すべての数値型。これには、符号なしおよび浮動小数点型と `Decimal` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bddf8-116">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bddf8-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="bddf8-117">Remarks</span></span>  

 <span data-ttu-id="bddf8-118">結果のデータ型は、オペランドの型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="bddf8-118">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="bddf8-119">次の表は、結果のデータ型がどのように決定されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="bddf8-119">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="bddf8-120">オペランドのデータ型</span><span class="sxs-lookup"><span data-stu-id="bddf8-120">Operand data types</span></span>|<span data-ttu-id="bddf8-121">結果のデータ型</span><span class="sxs-lookup"><span data-stu-id="bddf8-121">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="bddf8-122">両方の式が整数データ型 ([SByte](../data-types/sbyte-data-type.md)、[Byte](../data-types/byte-data-type.md)、[Short](../data-types/short-data-type.md)、[UShort](../data-types/ushort-data-type.md)、[Integer](../data-types/integer-data-type.md)、[UInteger](../data-types/uinteger-data-type.md)、[Long](../data-types/long-data-type.md)、[ULong](../data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="bddf8-122">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="bddf8-123">`number1` と `number2` のデータ型に適した数値データ型。</span><span class="sxs-lookup"><span data-stu-id="bddf8-123">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="bddf8-124">「[演算子の結果のデータ型](data-types-of-operator-results.md)」の「整数演算」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bddf8-124">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="bddf8-125">両方の式が [decimal](../data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="bddf8-125">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="bddf8-126">両方の式が [Single](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="bddf8-126">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="bddf8-127">一方の式が浮動小数点データ型 (`Single` または [Double](../data-types/double-data-type.md)) で、両方が `Single` ではない (`Decimal` は浮動小数点データ型ではないので注意してください)</span><span class="sxs-lookup"><span data-stu-id="bddf8-127">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="bddf8-128">式が [Nothing](../nothing.md) に評価される場合、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="bddf8-128">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="bddf8-129">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="bddf8-129">Overloading</span></span>  

 <span data-ttu-id="bddf8-130">`*` 演算子は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体で、演算子の動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="bddf8-130">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="bddf8-131">コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="bddf8-131">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="bddf8-132">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bddf8-132">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bddf8-133">例</span><span class="sxs-lookup"><span data-stu-id="bddf8-133">Example</span></span>  

 <span data-ttu-id="bddf8-134">この例では、`*` 演算子を使用して 2 つの数値を乗算しています。</span><span class="sxs-lookup"><span data-stu-id="bddf8-134">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="bddf8-135">結果は 2 つのオペランドの積になります。</span><span class="sxs-lookup"><span data-stu-id="bddf8-135">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bddf8-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="bddf8-136">See also</span></span>

- [<span data-ttu-id="bddf8-137">\*= 演算子</span><span class="sxs-lookup"><span data-stu-id="bddf8-137">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="bddf8-138">算術演算子</span><span class="sxs-lookup"><span data-stu-id="bddf8-138">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="bddf8-139">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="bddf8-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="bddf8-140">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="bddf8-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="bddf8-141">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="bddf8-141">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
