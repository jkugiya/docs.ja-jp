---
description: '詳細情報: 方法:演算子を定義する (Visual Basic)'
title: '方法: 演算子を定義する'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: ead96a302426c6f5b1667bb030aab56afe3284c8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462712"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="a0972-103">方法: 演算子を定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0972-103">How to: Define an Operator (Visual Basic)</span></span>

<span data-ttu-id="a0972-104">クラスまたは構造体を定義している場合、一方または両方のオペランドがクラスまたは構造体の型である場合の標準演算子 (`*`、`<>`、または `And` など) の動作を定義できます。</span><span class="sxs-lookup"><span data-stu-id="a0972-104">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="a0972-105">標準演算子をクラスまたは構造体内の演算子プロシージャとして定義します。</span><span class="sxs-lookup"><span data-stu-id="a0972-105">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="a0972-106">すべての演算子プロシージャは、`Public` `Shared` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0972-106">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="a0972-107">クラスまたは構造体での演算子の定義は、演算子の "*オーバーロード*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a0972-107">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0972-108">例</span><span class="sxs-lookup"><span data-stu-id="a0972-108">Example</span></span>  

 <span data-ttu-id="a0972-109">次の例では、`height` という構造体の `+` 演算子を定義しています。</span><span class="sxs-lookup"><span data-stu-id="a0972-109">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="a0972-110">この構造体では、フィートとインチで計測された高さを使用します。</span><span class="sxs-lookup"><span data-stu-id="a0972-110">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="a0972-111">1 "*インチ*" は 2.54 センチメートルであり、1 "*フィート*" は 12 インチです。</span><span class="sxs-lookup"><span data-stu-id="a0972-111">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="a0972-112">正規化された値 (インチ < 12.0) を確保するために、コンストラクターでは "*剰余*" 12 演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a0972-112">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="a0972-113">`+` 演算子では、コンストラクターを使用して正規化された値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a0972-113">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="a0972-114">次のコードで構造体 `height` をテストできます。</span><span class="sxs-lookup"><span data-stu-id="a0972-114">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  

## <a name="see-also"></a><span data-ttu-id="a0972-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0972-115">See also</span></span>

- [<span data-ttu-id="a0972-116">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a0972-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a0972-117">方法: 変換演算子を定義する</span><span class="sxs-lookup"><span data-stu-id="a0972-117">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="a0972-118">方法: 演算子プロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="a0972-118">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="a0972-119">方法: 演算子を定義するクラスを使用する</span><span class="sxs-lookup"><span data-stu-id="a0972-119">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="a0972-120">Operator ステートメント</span><span class="sxs-lookup"><span data-stu-id="a0972-120">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a0972-121">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="a0972-121">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="a0972-122">方法: 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="a0972-122">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a0972-123">Mod 演算子</span><span class="sxs-lookup"><span data-stu-id="a0972-123">Mod Operator</span></span>](../../../language-reference/operators/mod-operator.md)
