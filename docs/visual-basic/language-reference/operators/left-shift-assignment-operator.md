---
description: '詳細情報: <<= 演算子 (Visual Basic)'
title: <<= 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 40d0b69c3af672383230db5beadbcd3f3391db7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665641"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3cd99-103">\<\<= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cd99-103">\<\<= Operator (Visual Basic)</span></span>

<span data-ttu-id="3cd99-104">変数またはプロパティの値に算術左シフトを実行し、結果をその変数またはプロパティに戻して代入します。</span><span class="sxs-lookup"><span data-stu-id="3cd99-104">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cd99-105">構文</span><span class="sxs-lookup"><span data-stu-id="3cd99-105">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="3cd99-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="3cd99-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="3cd99-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="3cd99-107">Required.</span></span> <span data-ttu-id="3cd99-108">整数型の変数またはプロパティ (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="3cd99-108">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="3cd99-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="3cd99-109">Required.</span></span> <span data-ttu-id="3cd99-110">`Integer` に拡大されるデータ型の数値式。</span><span class="sxs-lookup"><span data-stu-id="3cd99-110">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cd99-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="3cd99-111">Remarks</span></span>  

 <span data-ttu-id="3cd99-112">`<<=` 演算子の左側の要素には、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3cd99-112">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="3cd99-113">変数またはプロパティを [ReadOnly](../modifiers/readonly.md) にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3cd99-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="3cd99-114">`<<=` 演算子は、まず変数またはプロパティの値に対して算術左シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="3cd99-114">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="3cd99-115">次に、この演算子はその演算の結果をその変数またはプロパティに戻して代入します。</span><span class="sxs-lookup"><span data-stu-id="3cd99-115">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="3cd99-116">算術シフトは循環ではありません。つまり、結果の一方の端からシフトされたビットはもう一方の端には再入されません。</span><span class="sxs-lookup"><span data-stu-id="3cd99-116">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="3cd99-117">算術左シフトでは、結果のデータ型の範囲を超えてシフトされたビットは破棄され、右側に空いたビット位置は 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3cd99-117">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3cd99-118">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="3cd99-118">Overloading</span></span>  

 <span data-ttu-id="3cd99-119">[<< 演算子](left-shift-operator.md)は "*オーバーロード*" できます。つまり、オペランドがあるクラスまたは構造体の型を持っているときに、そのクラスまたは構造体がその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="3cd99-119">The [<< Operator](left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3cd99-120">`<<` 演算子をオーバーロードすると、`<<=` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="3cd99-120">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="3cd99-121">コードで、`<<` をオーバーロードするクラスまたは構造体で `<<=` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3cd99-121">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3cd99-122">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cd99-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cd99-123">例</span><span class="sxs-lookup"><span data-stu-id="3cd99-123">Example</span></span>  

 <span data-ttu-id="3cd99-124">次の例では、`<<=` 演算子を使用して、`Integer` 変数のビット パターンを、指定された桁数だけ左にシフトし、結果をその変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="3cd99-124">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="3cd99-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cd99-125">See also</span></span>

- [<span data-ttu-id="3cd99-126"><< 演算子</span><span class="sxs-lookup"><span data-stu-id="3cd99-126"><< Operator</span></span>](left-shift-operator.md)
- [<span data-ttu-id="3cd99-127">代入演算子</span><span class="sxs-lookup"><span data-stu-id="3cd99-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="3cd99-128">ビット シフト演算子</span><span class="sxs-lookup"><span data-stu-id="3cd99-128">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="3cd99-129">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="3cd99-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="3cd99-130">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="3cd99-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="3cd99-131">ステートメント</span><span class="sxs-lookup"><span data-stu-id="3cd99-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
