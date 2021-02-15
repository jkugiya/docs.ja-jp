---
description: '詳細情報: >>= 演算子 (Visual Basic)'
title: '>>= 演算子'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 80f614042403ad9179de0025b289bd83c71008b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795314"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3fb68-103">>>= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fb68-103">>>= Operator (Visual Basic)</span></span>

<span data-ttu-id="3fb68-104">変数またはプロパティの値に算術右シフトを実行し、結果をその変数またはプロパティに戻して代入します。</span><span class="sxs-lookup"><span data-stu-id="3fb68-104">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fb68-105">構文</span><span class="sxs-lookup"><span data-stu-id="3fb68-105">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="3fb68-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="3fb68-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="3fb68-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="3fb68-107">Required.</span></span> <span data-ttu-id="3fb68-108">整数型の変数またはプロパティ (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="3fb68-108">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="3fb68-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="3fb68-109">Required.</span></span> <span data-ttu-id="3fb68-110">`Integer` に拡大されるデータ型の数値式。</span><span class="sxs-lookup"><span data-stu-id="3fb68-110">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fb68-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="3fb68-111">Remarks</span></span>  

 <span data-ttu-id="3fb68-112">`>>=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3fb68-112">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="3fb68-113">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3fb68-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="3fb68-114">`>>=` 演算子は、まず変数またはプロパティの値に対して算術右シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="3fb68-114">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="3fb68-115">次に、この演算子はその演算の結果を変数またはプロパティに戻して代入します。</span><span class="sxs-lookup"><span data-stu-id="3fb68-115">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="3fb68-116">算術シフトは循環ではありません。つまり、結果の一方の端からシフトされたビットはもう一方の端には再入されません。</span><span class="sxs-lookup"><span data-stu-id="3fb68-116">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="3fb68-117">算術右シフトでは、右端のビット位置を超えてシフトされたビットは破棄され、左端ビットは左側の空いたビット位置に移されます。</span><span class="sxs-lookup"><span data-stu-id="3fb68-117">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="3fb68-118">したがって、`variableorproperty` に負の値がある場合、空いている位置は 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3fb68-118">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="3fb68-119">`variableorproperty` が正の場合、またはそのデータ型が符号なしの型の場合、空いている位置は 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3fb68-119">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3fb68-120">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="3fb68-120">Overloading</span></span>  

 <span data-ttu-id="3fb68-121">[>> 演算子](right-shift-operator.md)は "*オーバーロード*" できます。つまり、オペランドがクラスまたは構造体の型を持っているときに、クラスまたは構造体はその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="3fb68-121">The [>> Operator](right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3fb68-122">`>>` 演算子をオーバーロードすると、`>>=` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="3fb68-122">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="3fb68-123">コードで、`>>` をオーバーロードするクラスまたは構造体で `>>=` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3fb68-123">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3fb68-124">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fb68-124">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fb68-125">例</span><span class="sxs-lookup"><span data-stu-id="3fb68-125">Example</span></span>  

 <span data-ttu-id="3fb68-126">次の例では、`>>=` 演算子を使用して、`Integer` 変数のビット パターンを、指定された桁数だけ右にシフトし、結果をその変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="3fb68-126">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="3fb68-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fb68-127">See also</span></span>

- [<span data-ttu-id="3fb68-128">>> 演算子</span><span class="sxs-lookup"><span data-stu-id="3fb68-128">>> Operator</span></span>](right-shift-operator.md)
- [<span data-ttu-id="3fb68-129">代入演算子</span><span class="sxs-lookup"><span data-stu-id="3fb68-129">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="3fb68-130">ビット シフト演算子</span><span class="sxs-lookup"><span data-stu-id="3fb68-130">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="3fb68-131">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="3fb68-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="3fb68-132">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="3fb68-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="3fb68-133">ステートメント</span><span class="sxs-lookup"><span data-stu-id="3fb68-133">Statements</span></span>](../../programming-guide/language-features/statements.md)
