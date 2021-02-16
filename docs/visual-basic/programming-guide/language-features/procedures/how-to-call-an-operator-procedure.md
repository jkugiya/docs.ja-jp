---
description: '詳細情報: 方法:演算子プロシージャを呼び出す (Visual Basic)'
title: '方法: 演算子プロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: f58d12ac5e4c9071646073184f7824946c00b39b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472606"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="70044-103">方法: 演算子プロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70044-103">How to: Call an Operator Procedure (Visual Basic)</span></span>

<span data-ttu-id="70044-104">演算子プロシージャは、式で演算子記号を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="70044-104">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="70044-105">変換演算子の場合は、[CType 関数](../../../language-reference/functions/ctype-function.md)を呼び出して、あるデータ型から別のデータ型に値を変換します。</span><span class="sxs-lookup"><span data-stu-id="70044-105">In the case of a conversion operator, you call the [CType Function](../../../language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="70044-106">演算子プロシージャを明示的に呼び出すことはありません。</span><span class="sxs-lookup"><span data-stu-id="70044-106">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="70044-107">演算子を通常使用する場合と同様に、代入ステートメントまたは式で、演算子または `CType` 関数を使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="70044-107">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="70044-108">Visual Basic が演算子プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="70044-108">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="70044-109">クラスまたは構造体での演算子の定義は、演算子の "*オーバーロード*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="70044-109">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="70044-110">演算子プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="70044-110">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="70044-111">通常どおり、式で演算子記号を使用します。</span><span class="sxs-lookup"><span data-stu-id="70044-111">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="70044-112">オペランドのデータ型がその演算子に適しており、正しい順序であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="70044-112">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="70044-113">演算子は想定どおりに式の値を返します。</span><span class="sxs-lookup"><span data-stu-id="70044-113">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="70044-114">変換演算子プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="70044-114">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="70044-115">式内で `CType` を使用します。</span><span class="sxs-lookup"><span data-stu-id="70044-115">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="70044-116">オペランドのデータ型が変換に適しており、正しい順序であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="70044-116">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="70044-117">`CType` は変換演算子プロシージャを呼び出し、変換された値を返します。</span><span class="sxs-lookup"><span data-stu-id="70044-117">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70044-118">例</span><span class="sxs-lookup"><span data-stu-id="70044-118">Example</span></span>  

 <span data-ttu-id="70044-119">次の例では、2 つの <xref:System.TimeSpan> 構造体を作成し、それらを合計して、結果を 3 番目の <xref:System.TimeSpan> 構造体に格納します。</span><span class="sxs-lookup"><span data-stu-id="70044-119">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="70044-120"><xref:System.TimeSpan> 構造体では、複数の標準演算子をオーバーロードする演算子プロシージャを定義します。</span><span class="sxs-lookup"><span data-stu-id="70044-120">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="70044-121"><xref:System.TimeSpan> は標準の `+` 演算子をオーバーロードするため、前の例では `combinedSpan` の値を計算するときに演算子プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="70044-121">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="70044-122">会話演算子プロシージャの呼び出しの例については、「[方法: 演算子を定義するクラスを使用する](./how-to-use-a-class-that-defines-operators.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="70044-122">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="70044-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="70044-123">Compile the code</span></span>  

 <span data-ttu-id="70044-124">使用しているクラスまたは構造体で、使用する演算子が定義されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="70044-124">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70044-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="70044-125">See also</span></span>

- [<span data-ttu-id="70044-126">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="70044-126">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="70044-127">方法: 演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="70044-127">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="70044-128">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="70044-128">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="70044-129">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="70044-129">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="70044-130">Widening</span><span class="sxs-lookup"><span data-stu-id="70044-130">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="70044-131">Narrowing</span><span class="sxs-lookup"><span data-stu-id="70044-131">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="70044-132">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="70044-132">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="70044-133">方法: 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="70044-133">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="70044-134">暗黙の型変換と明示的な型変換</span><span class="sxs-lookup"><span data-stu-id="70044-134">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="70044-135">拡大変換と縮小変換</span><span class="sxs-lookup"><span data-stu-id="70044-135">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
