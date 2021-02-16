---
description: '詳細情報: 方法:値を返すプロシージャを作成する (Visual Basic)'
title: '方法: 値を返すプロシージャを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: fa2ea50febd1cc4e7aecf1e6f5cca671789b36fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467057"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="f2daf-103">方法: 値を返すプロシージャを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2daf-103">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="f2daf-104">`Function` プロシージャを使用して、呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="f2daf-104">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="f2daf-105">値を返すプロシージャを作成するには</span><span class="sxs-lookup"><span data-stu-id="f2daf-105">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="f2daf-106">他のプロシージャの外部で、`Function` ステートメントを使用し、その後に `End Function` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f2daf-106">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="f2daf-107">`Function` ステートメントで、`Function` キーワードの後にプロシージャの名前を指定し、その後にかっこで囲んだパラメーター リストを指定します。</span><span class="sxs-lookup"><span data-stu-id="f2daf-107">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="f2daf-108">かっこの後に `As` 句を入力して、戻り値のデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="f2daf-108">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="f2daf-109">`Function` ステートメントと `End Function` ステートメントの間に、プロシージャのコード ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="f2daf-109">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="f2daf-110">`Return` ステートメントを使用して、呼び出し元のコードに値を返します。</span><span class="sxs-lookup"><span data-stu-id="f2daf-110">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="f2daf-111">次の `Function` プロシージャは、他の 2 つの辺の値を指定して、直角三角形の最も長い辺 (斜辺) を計算します。</span><span class="sxs-lookup"><span data-stu-id="f2daf-111">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="f2daf-112">次の例は、`hypotenuse` の一般的な呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="f2daf-112">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="f2daf-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2daf-113">See also</span></span>

- [<span data-ttu-id="f2daf-114">手順</span><span class="sxs-lookup"><span data-stu-id="f2daf-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f2daf-115">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f2daf-115">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="f2daf-116">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f2daf-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="f2daf-117">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f2daf-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="f2daf-118">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="f2daf-118">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f2daf-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="f2daf-119">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="f2daf-120">方法: プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="f2daf-120">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="f2daf-121">方法: 値を返すプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="f2daf-121">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
