---
description: "詳細情報: BC42105:関数 '<procedurename>' すべてのコード パス上では値を返しません。"
title: 関数 '<procedurename>' すべてのコード パス上では値を返しません。
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 2d0fa99906606228595a0c0d45f58dae0b269b77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796172"
---
# <a name="bc42105-function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="1687d-103">BC42105:関数 '\<procedurename>' すべてのコード パス上では値を返しません。</span><span class="sxs-lookup"><span data-stu-id="1687d-103">BC42105: Function '\<procedurename>' doesn't return a value on all code paths</span></span>

<span data-ttu-id="1687d-104">関数 '\<procedurename>' がすべてのコード パス上では値を返しません。</span><span class="sxs-lookup"><span data-stu-id="1687d-104">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="1687d-105">'return' ステートメントが不足していませんか。</span><span class="sxs-lookup"><span data-stu-id="1687d-105">Are you missing a 'Return' statement?</span></span>

 <span data-ttu-id="1687d-106">`Function` プロシージャに、値を返さないコードのパスが少なくとも 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="1687d-106">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>

 <span data-ttu-id="1687d-107">次のいずれかの方法で、`Function` プロシージャから値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="1687d-107">You can return a value from a `Function` procedure in any of the following ways:</span></span>

- <span data-ttu-id="1687d-108">[return ステートメント](../statements/return-statement.md)に値を含めます。</span><span class="sxs-lookup"><span data-stu-id="1687d-108">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>

- <span data-ttu-id="1687d-109">`Function` プロシージャ名に値を代入して、`Exit Function` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="1687d-109">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>

- <span data-ttu-id="1687d-110">`Function` プロシージャ名に値を代入して、`End Function` ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="1687d-110">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>

 <span data-ttu-id="1687d-111">制御が `Exit Function` または `End Function` に渡され、プロシージャ名に何も値を代入していない場合、プロシージャでは、戻り値のデータ型の既定値が返されます。</span><span class="sxs-lookup"><span data-stu-id="1687d-111">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="1687d-112">詳細については、「[Function ステートメント](../statements/function-statement.md)」の "動作" に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1687d-112">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>

 <span data-ttu-id="1687d-113">既定では、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="1687d-113">By default, this message is a warning.</span></span> <span data-ttu-id="1687d-114">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1687d-114">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="1687d-115">**エラー ID:** BC42105</span><span class="sxs-lookup"><span data-stu-id="1687d-115">**Error ID:** BC42105</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1687d-116">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="1687d-116">To correct this error</span></span>

- <span data-ttu-id="1687d-117">制御フロー ロジックをチェックし、戻り値を返すすべてのステートメントの前に値を代入してください。</span><span class="sxs-lookup"><span data-stu-id="1687d-117">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>

     <span data-ttu-id="1687d-118">常に `Return` ステートメントを使用すれば、プロシージャからのすべての戻り値で、値が返されることを簡単に保証できます。</span><span class="sxs-lookup"><span data-stu-id="1687d-118">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="1687d-119">これを実行する場合、`End Function` の前の最後のステートメントは、`Return` ステートメントでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="1687d-119">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="1687d-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="1687d-120">See also</span></span>

- [<span data-ttu-id="1687d-121">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="1687d-121">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="1687d-122">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="1687d-122">Function Statement</span></span>](../statements/function-statement.md)
- <span data-ttu-id="1687d-123">[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="1687d-123">[Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)</span></span>
