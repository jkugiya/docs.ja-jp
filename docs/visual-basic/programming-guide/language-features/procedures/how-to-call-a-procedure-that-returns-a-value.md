---
description: '詳細情報: 方法:値を返すプロシージャを呼び出す (Visual Basic)'
title: '方法: 値を返すプロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 74c7b6c9340537088ac631fc47f9ebf7b1a203cb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466745"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="21422-103">方法: 値を返すプロシージャを呼び出す (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21422-103">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="21422-104">`Function` プロシージャからは、呼び出し元のコードに値が返されます。</span><span class="sxs-lookup"><span data-stu-id="21422-104">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="21422-105">それを呼び出すには、その名前と引数を代入ステートメントの右辺に、または式に含めます。</span><span class="sxs-lookup"><span data-stu-id="21422-105">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="21422-106">式内で Function プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="21422-106">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="21422-107">`Function` プロシージャ名は、変数を使用する場合と同じ方法で使用します。</span><span class="sxs-lookup"><span data-stu-id="21422-107">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="21422-108">式内の変数または定数を使用できる場所であればどこでも、`Function` プロシージャ呼び出しを使用できます。</span><span class="sxs-lookup"><span data-stu-id="21422-108">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="21422-109">プロシージャ名の後にかっこを使用して引数リストを囲みます。</span><span class="sxs-lookup"><span data-stu-id="21422-109">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="21422-110">引数がない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="21422-110">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="21422-111">ただし、かっこを使用すると、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="21422-111">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="21422-112">引数リストの引数をコンマで区切ってかっこ内に配置します。</span><span class="sxs-lookup"><span data-stu-id="21422-112">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="21422-113">引数の指定は必ず、`Function` プロシージャで定義されている対応するパラメーターと同じ順序で行ってください。</span><span class="sxs-lookup"><span data-stu-id="21422-113">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="21422-114">または、1 つまたは複数の引数を名前で渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="21422-114">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="21422-115">詳細については、「[位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21422-115">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="21422-116">プロシージャから返される値は、変数または定数の値と同じように、式に含められます。</span><span class="sxs-lookup"><span data-stu-id="21422-116">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="21422-117">代入ステートメントで Function プロシージャを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="21422-117">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="21422-118">代入ステートメント内で等号 (`=`) の後に `Function` プロシージャ名を使用します。</span><span class="sxs-lookup"><span data-stu-id="21422-118">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="21422-119">プロシージャ名の後にかっこを使用して引数リストを囲みます。</span><span class="sxs-lookup"><span data-stu-id="21422-119">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="21422-120">引数がない場合は、必要に応じてかっこを省略できます。</span><span class="sxs-lookup"><span data-stu-id="21422-120">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="21422-121">ただし、かっこを使用すると、コードが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="21422-121">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="21422-122">引数リストの引数をコンマで区切ってかっこ内に配置します。</span><span class="sxs-lookup"><span data-stu-id="21422-122">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="21422-123">引数を名前で渡さない場合、それらは必ず、`Function` プロシージャで定義されている対応するパラメーターと同じ順序で指定してください。</span><span class="sxs-lookup"><span data-stu-id="21422-123">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="21422-124">プロシージャから返された値は、代入ステートメントの左側にある変数またはプロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="21422-124">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21422-125">例</span><span class="sxs-lookup"><span data-stu-id="21422-125">Example</span></span>  

 <span data-ttu-id="21422-126">次の例では、Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> を呼び出して、オペレーティング システムの環境変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="21422-126">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="21422-127">最初の行では式内で `Environ` が呼び出され、2 番目の行では代入ステートメントでそれが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="21422-127">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="21422-128">`Environ` では、その唯一の引数として変数名を取ります。</span><span class="sxs-lookup"><span data-stu-id="21422-128">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="21422-129">これにより、呼び出し元のコードに変数の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="21422-129">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="21422-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="21422-130">See also</span></span>

- [<span data-ttu-id="21422-131">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="21422-131">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="21422-132">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="21422-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="21422-133">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="21422-133">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="21422-134">方法: 値を返すプロシージャを作成する</span><span class="sxs-lookup"><span data-stu-id="21422-134">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="21422-135">方法: プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="21422-135">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="21422-136">方法: 値を返さないプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="21422-136">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
