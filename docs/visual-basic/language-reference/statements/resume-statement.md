---
description: '詳細情報: Resume ステートメント'
title: Resume ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: fd3a02fc2606355d7e3a34f5c0d69eef577809de
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741186"
---
# <a name="resume-statement"></a><span data-ttu-id="11e25-103">Resume ステートメント</span><span class="sxs-lookup"><span data-stu-id="11e25-103">Resume Statement</span></span>

<span data-ttu-id="11e25-104">エラー処理ルーチンが終了した後、実行を再開します。</span><span class="sxs-lookup"><span data-stu-id="11e25-104">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="11e25-105">コードでは、非構造化例外処理と `On Error` および `Resume` ステートメントを使用するのではなく、可能な限り、構造化例外処理を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11e25-105">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="11e25-106">詳しくは、「[Try...Catch...Finally ステートメント](try-catch-finally-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11e25-106">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e25-107">構文</span><span class="sxs-lookup"><span data-stu-id="11e25-107">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="11e25-108">指定項目</span><span class="sxs-lookup"><span data-stu-id="11e25-108">Parts</span></span>  

 `Resume`  
 <span data-ttu-id="11e25-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="11e25-109">Required.</span></span> <span data-ttu-id="11e25-110">エラー ハンドラーと同じプロシージャでエラーが発生した場合は、エラーの原因となったステートメントを使用して実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="11e25-110">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="11e25-111">呼び出されたプロシージャでエラーが発生した場合、エラー処理ルーチンを含むプロシージャから最後に呼び出されたステートメントで実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="11e25-111">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="11e25-112">任意。</span><span class="sxs-lookup"><span data-stu-id="11e25-112">Optional.</span></span> <span data-ttu-id="11e25-113">エラー ハンドラーと同じプロシージャでエラーが発生した場合は、エラーの原因となったステートメントの直後のステートメントを使用して実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="11e25-113">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="11e25-114">呼び出されたプロシージャでエラーが発生した場合、エラー処理ルーチン (または `On Error Resume Next` ステートメント) を含むプロシージャから最後に呼び出されたステートメントの直後のステートメントを使用して、実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="11e25-114">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="11e25-115">任意。</span><span class="sxs-lookup"><span data-stu-id="11e25-115">Optional.</span></span> <span data-ttu-id="11e25-116">実行は、必須の引数 `line` で指定した行で再開されます。</span><span class="sxs-lookup"><span data-stu-id="11e25-116">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="11e25-117">`line` 引数は、行ラベルまたは行番号であり、エラー ハンドラーと同じプロシージャ内にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="11e25-117">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11e25-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="11e25-118">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11e25-119">コードでは、非構造化例外処理と `On Error` および `Resume` ステートメントを使用するのではなく、可能な限り、構造化例外処理を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11e25-119">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="11e25-120">詳しくは、「[Try...Catch...Finally ステートメント](try-catch-finally-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="11e25-120">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="11e25-121">エラー処理ルーチン以外の場所で `Resume` ステートメントを使用すると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="11e25-121">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="11e25-122">`Resume` ステートメントは、`Try...Catch...Finally` ステートメントを含むプロシージャ内では使用できません。</span><span class="sxs-lookup"><span data-stu-id="11e25-122">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11e25-123">例</span><span class="sxs-lookup"><span data-stu-id="11e25-123">Example</span></span>  

 <span data-ttu-id="11e25-124">この例では、`Resume` ステートメントを使用してプロシージャのエラー処理を終了し、エラーの原因となったステートメントを使用して実行を再開します。</span><span class="sxs-lookup"><span data-stu-id="11e25-124">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="11e25-125">`Resume` ステートメントの使用方法を示すために、エラー番号 55 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="11e25-125">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="11e25-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="11e25-126">Requirements</span></span>  

 <span data-ttu-id="11e25-127">**名前空間:** [Microsoft.VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="11e25-127">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="11e25-128">**アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="11e25-128">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e25-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="11e25-129">See also</span></span>

- [<span data-ttu-id="11e25-130">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="11e25-130">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="11e25-131">Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="11e25-131">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="11e25-132">On Error ステートメント</span><span class="sxs-lookup"><span data-stu-id="11e25-132">On Error Statement</span></span>](on-error-statement.md)
