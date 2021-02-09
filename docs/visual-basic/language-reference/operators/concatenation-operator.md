---
description: '詳細情報: &amp; 演算子 (Visual Basic)'
title: '&amp; 演算子'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: ba7c94805e805c841d05241fef557ca972a19ae9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774097"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="abf5c-103">&amp; 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abf5c-103">&amp; Operator (Visual Basic)</span></span>

<span data-ttu-id="abf5c-104">2 つの式の文字列連結を生成します。</span><span class="sxs-lookup"><span data-stu-id="abf5c-104">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abf5c-105">構文</span><span class="sxs-lookup"><span data-stu-id="abf5c-105">Syntax</span></span>  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="abf5c-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="abf5c-106">Parts</span></span>  

 `result`  
 <span data-ttu-id="abf5c-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="abf5c-107">Required.</span></span> <span data-ttu-id="abf5c-108">任意の `String` または `Object` 変数。</span><span class="sxs-lookup"><span data-stu-id="abf5c-108">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="abf5c-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="abf5c-109">Required.</span></span> <span data-ttu-id="abf5c-110">`String` に拡大変換されるデータ型を持つ任意の式。</span><span class="sxs-lookup"><span data-stu-id="abf5c-110">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="abf5c-111">必須です。</span><span class="sxs-lookup"><span data-stu-id="abf5c-111">Required.</span></span> <span data-ttu-id="abf5c-112">`String` に拡大変換されるデータ型を持つ任意の式。</span><span class="sxs-lookup"><span data-stu-id="abf5c-112">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abf5c-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="abf5c-113">Remarks</span></span>  

 <span data-ttu-id="abf5c-114">`expression1` または `expression2` のデータ型が `String` ではなく `String` に拡大変換される場合は、`String` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="abf5c-114">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="abf5c-115">いずれのデータ型も `String` に拡大変換されない場合、コンパイラはエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="abf5c-115">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="abf5c-116">`result` のデータ型は `String` です。</span><span class="sxs-lookup"><span data-stu-id="abf5c-116">The data type of `result` is `String`.</span></span> <span data-ttu-id="abf5c-117">いずれかまたは両方の式が [Nothing](../nothing.md) に評価される場合、または値が <xref:System.DBNull.Value?displayProperty=nameWithType> の場合は、"" の値を持つ文字列として扱われます。</span><span class="sxs-lookup"><span data-stu-id="abf5c-117">If one or both expressions evaluate to [Nothing](../nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abf5c-118">`&` 演算子は "*オーバーロード*" できます。つまり、オペランドの型がクラスまたは構造体であるとき、そのクラスまたは構造体でその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="abf5c-118">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="abf5c-119">コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="abf5c-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="abf5c-120">詳細については、「 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abf5c-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abf5c-121">アンパサンド (&) 文字は `Long` 型として変数を識別するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="abf5c-121">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="abf5c-122">詳細については、「[型文字](../../programming-guide/language-features/data-types/type-characters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abf5c-122">For more information, see [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf5c-123">例</span><span class="sxs-lookup"><span data-stu-id="abf5c-123">Example</span></span>  

 <span data-ttu-id="abf5c-124">この例では、`&` 演算子を使用して、文字列の連結を強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="abf5c-124">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="abf5c-125">結果は、2 つの文字列オペランドの連結を表す文字列値になります。</span><span class="sxs-lookup"><span data-stu-id="abf5c-125">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="abf5c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="abf5c-126">See also</span></span>

- [<span data-ttu-id="abf5c-127">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="abf5c-127">&= Operator</span></span>](and-assignment-operator.md)
- [<span data-ttu-id="abf5c-128">連結演算子</span><span class="sxs-lookup"><span data-stu-id="abf5c-128">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="abf5c-129">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="abf5c-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="abf5c-130">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="abf5c-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="abf5c-131">Visual Basic の連結演算子</span><span class="sxs-lookup"><span data-stu-id="abf5c-131">Concatenation Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
