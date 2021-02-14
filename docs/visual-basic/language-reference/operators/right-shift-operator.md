---
description: '詳細情報: >> 演算子 (Visual Basic)'
title: '>> 演算子'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 125b93f129734d196bd1f7f9c4fde86ab5d66319
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795301"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1d84a-103">>> 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d84a-103">>> Operator (Visual Basic)</span></span>

<span data-ttu-id="1d84a-104">ビット パターンに対して算術右シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d84a-104">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d84a-105">構文</span><span class="sxs-lookup"><span data-stu-id="1d84a-105">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="1d84a-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="1d84a-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="1d84a-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-107">Required.</span></span> <span data-ttu-id="1d84a-108">整数数値。</span><span class="sxs-lookup"><span data-stu-id="1d84a-108">Integral numeric value.</span></span> <span data-ttu-id="1d84a-109">ビット パターンをシフトした結果。</span><span class="sxs-lookup"><span data-stu-id="1d84a-109">The result of shifting the bit pattern.</span></span> <span data-ttu-id="1d84a-110">データ型は `pattern` のデータ型と同じです。</span><span class="sxs-lookup"><span data-stu-id="1d84a-110">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="1d84a-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-111">Required.</span></span> <span data-ttu-id="1d84a-112">整数数値式。</span><span class="sxs-lookup"><span data-stu-id="1d84a-112">Integral numeric expression.</span></span> <span data-ttu-id="1d84a-113">シフトするビット パターン。</span><span class="sxs-lookup"><span data-stu-id="1d84a-113">The bit pattern to be shifted.</span></span> <span data-ttu-id="1d84a-114">データ型は、整数型 (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、または `ULong`) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d84a-114">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="1d84a-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-115">Required.</span></span> <span data-ttu-id="1d84a-116">数値式。</span><span class="sxs-lookup"><span data-stu-id="1d84a-116">Numeric expression.</span></span> <span data-ttu-id="1d84a-117">ビット パターンをシフトするビット数。</span><span class="sxs-lookup"><span data-stu-id="1d84a-117">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="1d84a-118">データ型は `Integer` であるか、`Integer` に拡大変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d84a-118">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d84a-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="1d84a-119">Remarks</span></span>  

 <span data-ttu-id="1d84a-120">算術シフトは循環ではありません。つまり、結果の一方の端からシフトされたビットはもう一方の端に再入されません。</span><span class="sxs-lookup"><span data-stu-id="1d84a-120">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="1d84a-121">算術右シフトでは、右端のビット位置を超えてシフトされたビットは破棄され、左端 (符号) ビットは左側の空いたビット位置に伝搬されます。</span><span class="sxs-lookup"><span data-stu-id="1d84a-121">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="1d84a-122">したがって、`pattern` に負の値がある場合、空いている位置は 1 に設定されます。それ以外の場合は 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1d84a-122">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="1d84a-123">`Byte`、`UShort`、`UInteger`、および `ULong` データ型は符号なしであるため、伝搬する符号ビットはありません。</span><span class="sxs-lookup"><span data-stu-id="1d84a-123">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="1d84a-124">`pattern` が符号なしの型の場合、空いている位置は常に 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1d84a-124">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="1d84a-125">結果で保持できるよりも多くのビットがシフトされないようにするため、Visual Basic は `pattern` のデータ型に対応するサイズ マスクを使用して `amount` の値をマスクします。</span><span class="sxs-lookup"><span data-stu-id="1d84a-125">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="1d84a-126">これらの値のバイナリ AND がシフト量に使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d84a-126">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="1d84a-127">サイズ マスクを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d84a-127">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="1d84a-128">`pattern` のデータ型</span><span class="sxs-lookup"><span data-stu-id="1d84a-128">Data type of `pattern`</span></span>|<span data-ttu-id="1d84a-129">サイズ マスク (10 進数)</span><span class="sxs-lookup"><span data-stu-id="1d84a-129">Size mask (decimal)</span></span>|<span data-ttu-id="1d84a-130">サイズ マスク (16 進数)</span><span class="sxs-lookup"><span data-stu-id="1d84a-130">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="1d84a-131">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="1d84a-131">`SByte`, `Byte`</span></span>|<span data-ttu-id="1d84a-132">7</span><span class="sxs-lookup"><span data-stu-id="1d84a-132">7</span></span>|<span data-ttu-id="1d84a-133">&H00000007</span><span class="sxs-lookup"><span data-stu-id="1d84a-133">&H00000007</span></span>|  
|<span data-ttu-id="1d84a-134">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="1d84a-134">`Short`, `UShort`</span></span>|<span data-ttu-id="1d84a-135">15</span><span class="sxs-lookup"><span data-stu-id="1d84a-135">15</span></span>|<span data-ttu-id="1d84a-136">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="1d84a-136">&H0000000F</span></span>|  
|<span data-ttu-id="1d84a-137">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="1d84a-137">`Integer`, `UInteger`</span></span>|<span data-ttu-id="1d84a-138">31</span><span class="sxs-lookup"><span data-stu-id="1d84a-138">31</span></span>|<span data-ttu-id="1d84a-139">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="1d84a-139">&H0000001F</span></span>|  
|<span data-ttu-id="1d84a-140">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="1d84a-140">`Long`, `ULong`</span></span>|<span data-ttu-id="1d84a-141">63</span><span class="sxs-lookup"><span data-stu-id="1d84a-141">63</span></span>|<span data-ttu-id="1d84a-142">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="1d84a-142">&H0000003F</span></span>|  
  
 <span data-ttu-id="1d84a-143">`amount` が 0 の場合、`result` の値は `pattern` の値と同じになります。</span><span class="sxs-lookup"><span data-stu-id="1d84a-143">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="1d84a-144">`amount` が負の場合は、符号なしの値として扱われ、適切なサイズ マスクでマスクされます。</span><span class="sxs-lookup"><span data-stu-id="1d84a-144">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="1d84a-145">算術シフトではオーバーフロー例外は生成されません。</span><span class="sxs-lookup"><span data-stu-id="1d84a-145">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1d84a-146">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="1d84a-146">Overloading</span></span>  

 <span data-ttu-id="1d84a-147">`>>` 演算子は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体で、演算子の動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="1d84a-147">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1d84a-148">コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1d84a-148">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1d84a-149">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d84a-149">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d84a-150">例</span><span class="sxs-lookup"><span data-stu-id="1d84a-150">Example</span></span>  

 <span data-ttu-id="1d84a-151">次の例では、`>>` 演算子を使用して、整数値に対して算術右シフトを実行しています。</span><span class="sxs-lookup"><span data-stu-id="1d84a-151">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="1d84a-152">結果のデータ型は、シフトする式のデータ型と常に同じになります。</span><span class="sxs-lookup"><span data-stu-id="1d84a-152">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="1d84a-153">前の例の結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1d84a-153">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="1d84a-154">`result1` は 2560 (0000 1010 0000 0000) です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-154">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="1d84a-155">`result2` は 160 (0000 0000 1010 0000) です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-155">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="1d84a-156">`result3` は 2 (0000 0000 0000 0010) です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-156">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="1d84a-157">`result4` は 640 (0000 0010 1000 0000) です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-157">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="1d84a-158">`result5` は 0 (右に 15 桁シフト)。</span><span class="sxs-lookup"><span data-stu-id="1d84a-158">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="1d84a-159">`result4` のシフト量は 18 AND 15 として計算されます。これは 2 と同等です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-159">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="1d84a-160">次の例は、負の値に対する算術シフトを示しています。</span><span class="sxs-lookup"><span data-stu-id="1d84a-160">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="1d84a-161">前の例の結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="1d84a-161">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="1d84a-162">`negresult1` は -512 (1111 1110 0000 0000) です。</span><span class="sxs-lookup"><span data-stu-id="1d84a-162">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="1d84a-163">`negresult2` は -1 です (符号ビットが伝播されます)。</span><span class="sxs-lookup"><span data-stu-id="1d84a-163">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d84a-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d84a-164">See also</span></span>

- [<span data-ttu-id="1d84a-165">ビット シフト演算子</span><span class="sxs-lookup"><span data-stu-id="1d84a-165">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="1d84a-166">代入演算子</span><span class="sxs-lookup"><span data-stu-id="1d84a-166">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="1d84a-167">>>= 演算子</span><span class="sxs-lookup"><span data-stu-id="1d84a-167">>>= Operator</span></span>](right-shift-assignment-operator.md)
- [<span data-ttu-id="1d84a-168">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="1d84a-168">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1d84a-169">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="1d84a-169">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="1d84a-170">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="1d84a-170">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
