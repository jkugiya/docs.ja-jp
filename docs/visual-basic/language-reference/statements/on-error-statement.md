---
description: '詳細情報: On Error ステートメント (Visual Basic)'
title: On Error ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 593e90b07101d08d18a0db127bcb74cf6509f317
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768832"
---
# <a name="on-error-statement-visual-basic"></a><span data-ttu-id="e4134-103">On Error ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4134-103">On Error Statement (Visual Basic)</span></span>

<span data-ttu-id="e4134-104">エラー処理ルーチンを有効にし、プロシージャ内のルーチンの場所を指定します。エラー処理ルーチンを無効にするためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4134-104">Enables an error-handling routine and specifies the location of the routine within a procedure; can also be used to disable an error-handling routine.</span></span> <span data-ttu-id="e4134-105">`On Error` ステートメントは、非構造化エラー処理で使用し、構造化例外処理の代わりに使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4134-105">The `On Error` statement is used in unstructured error handling and can be used instead of structured exception handling.</span></span> <span data-ttu-id="e4134-106">[構造化例外処理](../../../standard/exceptions/index.md)は .NET に組み込まれており、一般に効率的であるため、アプリケーションで実行時エラーを処理する場合に推奨されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-106">[Structured exception handling](../../../standard/exceptions/index.md) is built into .NET, is generally more efficient, and so is recommended when handling runtime errors in your application.</span></span>

 <span data-ttu-id="e4134-107">エラー処理または例外処理を使用しない場合、発生したすべての実行時エラーが致命的になります。エラーメッセージが表示され、実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="e4134-107">Without error handling or exception handling, any run-time error that occurs is fatal: an error message is displayed, and execution stops.</span></span>

> [!NOTE]
> <span data-ttu-id="e4134-108">`Error` キーワードは、下位互換性のためにサポートされている [Error ステートメント](error-statement.md)でも使用します。</span><span class="sxs-lookup"><span data-stu-id="e4134-108">The `Error` keyword is also used in the [Error Statement](error-statement.md), which is supported for backward compatibility.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4134-109">構文</span><span class="sxs-lookup"><span data-stu-id="e4134-109">Syntax</span></span>

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a><span data-ttu-id="e4134-110">指定項目</span><span class="sxs-lookup"><span data-stu-id="e4134-110">Parts</span></span>

|<span data-ttu-id="e4134-111">用語</span><span class="sxs-lookup"><span data-stu-id="e4134-111">Term</span></span>|<span data-ttu-id="e4134-112">定義</span><span class="sxs-lookup"><span data-stu-id="e4134-112">Definition</span></span>|
|---|---|
|<span data-ttu-id="e4134-113">`GoTo` *line*</span><span class="sxs-lookup"><span data-stu-id="e4134-113">`GoTo` *line*</span></span>|<span data-ttu-id="e4134-114">必須の *line* 引数に指定された行から始まるエラー処理ルーチンを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e4134-114">Enables the error-handling routine that starts at the line specified in the required *line* argument.</span></span> <span data-ttu-id="e4134-115">*line* 引数は、任意の行ラベルまたは行番号です。</span><span class="sxs-lookup"><span data-stu-id="e4134-115">The *line* argument is any line label or line number.</span></span> <span data-ttu-id="e4134-116">実行時エラーが発生した場合、制御が指定された行に分岐し、エラー ハンドラーがアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="e4134-116">If a run-time error occurs, control branches to the specified line, making the error handler active.</span></span> <span data-ttu-id="e4134-117">指定した行は、`On Error` ステートメントと同じプロシージャ内に存在する必要があります。さもないと、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e4134-117">The specified line must be in the same procedure as the `On Error` statement or a compile-time error will occur.</span></span>|
|`GoTo 0`|<span data-ttu-id="e4134-118">現在のプロシージャで有効になっているエラー ハンドラーを無効にし、`Nothing` にリセットします。</span><span class="sxs-lookup"><span data-stu-id="e4134-118">Disables enabled error handler in the current procedure and resets it to `Nothing`.</span></span>|
|`GoTo -1`|<span data-ttu-id="e4134-119">現在のプロシージャで有効になっている例外を無効にし、`Nothing` にリセットします。</span><span class="sxs-lookup"><span data-stu-id="e4134-119">Disables enabled exception in the current procedure and resets it to `Nothing`.</span></span>|
|`Resume Next`|<span data-ttu-id="e4134-120">実行時エラーが発生したときに、エラーが発生したステートメントの直後のステートメントに制御を移動し、そのポイントから実行を続行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4134-120">Specifies that when a run-time error occurs, control goes to the statement immediately following the statement where the error occurred, and execution continues from that point.</span></span> <span data-ttu-id="e4134-121">オブジェクトにアクセスする場合は、`On Error GoTo` ではなく、この形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4134-121">Use this form rather than `On Error GoTo` when accessing objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4134-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="e4134-122">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="e4134-123">コードでは、非構造化例外処理と `On Error` ステートメントを使用するのではなく、可能な限り、構造化例外処理を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e4134-123">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` statement.</span></span> <span data-ttu-id="e4134-124">詳しくは、「[Try...Catch...Finally ステートメント](try-catch-finally-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e4134-124">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>

 <span data-ttu-id="e4134-125">"有効な" エラー ハンドラーは、`On Error` ステートメントによって有効にされるものです。</span><span class="sxs-lookup"><span data-stu-id="e4134-125">An "enabled" error handler is one that is turned on by an `On Error` statement.</span></span> <span data-ttu-id="e4134-126">"アクティブな" エラー ハンドラーは、エラーの処理中に有効にされているハンドラーです。</span><span class="sxs-lookup"><span data-stu-id="e4134-126">An "active" error handler is an enabled handler that is in the process of handling an error.</span></span>

 <span data-ttu-id="e4134-127">エラー ハンドラーがアクティブになっている間 (エラーの発生と、`Resume`、`Exit Sub`、`Exit Function`、または `Exit Property` ステートメントの間) にエラーが発生した場合、現在のプロシージャのエラー ハンドラーではエラーを処理できません。</span><span class="sxs-lookup"><span data-stu-id="e4134-127">If an error occurs while an error handler is active (between the occurrence of the error and a `Resume`, `Exit Sub`, `Exit Function`, or `Exit Property` statement), the current procedure's error handler cannot handle the error.</span></span> <span data-ttu-id="e4134-128">呼び出し元のプロシージャに制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="e4134-128">Control returns to the calling procedure.</span></span>
  
 <span data-ttu-id="e4134-129">呼び出し元のプロシージャに有効なエラー ハンドラーがある場合、エラーを処理するために、それがアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-129">If the calling procedure has an enabled error handler, it is activated to handle the error.</span></span> <span data-ttu-id="e4134-130">呼び出し元のプロシージャのエラー ハンドラーもアクティブな場合は、有効だが非アクティブなエラー ハンドラーが見つかるまで、前の呼び出し元プロシージャをさかのぼって、制御が戻されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-130">If the calling procedure's error handler is also active, control passes back through previous calling procedures until an enabled, but inactive, error handler is found.</span></span> <span data-ttu-id="e4134-131">そのようなエラー ハンドラーが見つからない場合、エラーは実際に発生した時点で致命的になります。</span><span class="sxs-lookup"><span data-stu-id="e4134-131">If no such error handler is found, the error is fatal at the point at which it actually occurred.</span></span>
  
 <span data-ttu-id="e4134-132">エラー ハンドラーによって呼び出し元のプロシージャに制御が戻されるたびに、そのプロシージャが現在のプロシージャになります。</span><span class="sxs-lookup"><span data-stu-id="e4134-132">Each time the error handler passes control back to a calling procedure, that procedure becomes the current procedure.</span></span> <span data-ttu-id="e4134-133">いずれかのプロシージャのエラーハンドラーによってエラーが処理されると、`Resume` ステートメントで指定されたポイントにある現在のプロシージャで、実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-133">Once an error is handled by an error handler in any procedure, execution resumes in the current procedure at the point designated by the `Resume` statement.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e4134-134">エラー処理ルーチンは、`Sub` プロシージャや `Function` プロシージャではありません。</span><span class="sxs-lookup"><span data-stu-id="e4134-134">An error-handling routine is not a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="e4134-135">それは、行ラベルまたは行番号でマークされたコードのセクションです。</span><span class="sxs-lookup"><span data-stu-id="e4134-135">It is a section of code marked by a line label or a line number.</span></span>
  
## <a name="number-property"></a><span data-ttu-id="e4134-136">Number プロパティ</span><span class="sxs-lookup"><span data-stu-id="e4134-136">Number Property</span></span>

 <span data-ttu-id="e4134-137">エラー処理ルーチンでは、エラーの原因を特定するために、`Err` オブジェクトの `Number` プロパティの値に依存しています。</span><span class="sxs-lookup"><span data-stu-id="e4134-137">Error-handling routines rely on the value in the `Number` property of the `Err` object to determine the cause of the error.</span></span> <span data-ttu-id="e4134-138">ルーチンでは、他のエラーが発生する可能性がある前、またはエラーが発生する可能性のあるプロシージャが呼び出される前に、`Err` オブジェクトの関連するプロパティ値をテストまたは保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4134-138">The routine should test or save relevant property values in the `Err` object before any other error can occur or before a procedure that might cause an error is called.</span></span> <span data-ttu-id="e4134-139">`Err` オブジェクトのプロパティ値は、最新のエラーだけを反映しています。</span><span class="sxs-lookup"><span data-stu-id="e4134-139">The property values in the `Err` object reflect only the most recent error.</span></span> <span data-ttu-id="e4134-140">`Err.Number` に関連付けられたエラー メッセージは `Err.Description` に含まれています。</span><span class="sxs-lookup"><span data-stu-id="e4134-140">The error message associated with `Err.Number` is contained in `Err.Description`.</span></span>  
  
## <a name="throw-statement"></a><span data-ttu-id="e4134-141">Throw ステートメント</span><span class="sxs-lookup"><span data-stu-id="e4134-141">Throw Statement</span></span>  

 <span data-ttu-id="e4134-142">`Err.Raise` メソッドで発生したエラーによって、`Exception` プロパティが <xref:System.Exception> クラスの新しく作成されたインスタンスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-142">An error that is raised with the `Err.Raise` method sets the `Exception` property to a newly created instance of the <xref:System.Exception> class.</span></span> <span data-ttu-id="e4134-143">派生した例外の種類の例外の発生をサポートするために、その言語で `Throw` ステートメントがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e4134-143">In order to support the raising of exceptions of derived exception types, a `Throw` statement is supported in the language.</span></span> <span data-ttu-id="e4134-144">これは、スローされる例外インスタンスである 1 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e4134-144">This takes a single parameter that is the exception instance to be thrown.</span></span> <span data-ttu-id="e4134-145">次の例に、これらの機能を既存の例外処理サポートと共に使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e4134-145">The following example shows how these features can be used with the existing exception handling support:</span></span>

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 <span data-ttu-id="e4134-146">`On Error GoTo` ステートメントでは、例外クラスに関係なく、すべてのエラーがトラップされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e4134-146">Notice that the `On Error GoTo` statement traps all errors, regardless of the exception class.</span></span>
  
## <a name="on-error-resume-next"></a><span data-ttu-id="e4134-147">On Error Resume Next</span><span class="sxs-lookup"><span data-stu-id="e4134-147">On Error Resume Next</span></span>

 <span data-ttu-id="e4134-148">`On Error Resume Next` によって、実行時エラーが発生したステートメントの直後のステートメント、または `On Error Resume Next` ステートメントを含むプロシージャからの最新の呼び出しの直後のステートメントから、実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-148">`On Error Resume Next` causes execution to continue with the statement immediately following the statement that caused the run-time error, or with the statement immediately following the most recent call out of the procedure containing the `On Error Resume Next` statement.</span></span> <span data-ttu-id="e4134-149">このステートメントを使用すると、実行時エラーが発生しても実行を続行できます。</span><span class="sxs-lookup"><span data-stu-id="e4134-149">This statement allows execution to continue despite a run-time error.</span></span> <span data-ttu-id="e4134-150">プロシージャ内の別の場所に制御を移すのではなく、エラーが発生しそうな場所に、エラー処理ルーチンを配置できます。</span><span class="sxs-lookup"><span data-stu-id="e4134-150">You can place the error-handling routine where the error would occur rather than transferring control to another location within the procedure.</span></span> <span data-ttu-id="e4134-151">別のプロシージャが呼び出されると、`On Error Resume Next` ステートメントは非アクティブになります。そのため、ルーチン内にエラー処理を埋め込む場合に、呼び出される各ルーチンで `On Error Resume Next` ステートメントを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4134-151">An `On Error Resume Next` statement becomes inactive when another procedure is called, so you should execute an `On Error Resume Next` statement in each called routine if you want inline error handling within that routine.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e4134-152">他のオブジェクトへのアクセス中に生成されたエラーを処理する場合は、`On Error Resume Next` コンストラクトの方が、`On Error GoTo` より推奨されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-152">The `On Error Resume Next` construct may be preferable to `On Error GoTo` when handling errors generated during access to other objects.</span></span> <span data-ttu-id="e4134-153">オブジェクトの操作のたびに `Err` をチェックすることで、コードによってアクセスされたオブジェクトについてのあいまいさがなくなります。</span><span class="sxs-lookup"><span data-stu-id="e4134-153">Checking `Err` after each interaction with an object removes ambiguity about which object was accessed by the code.</span></span> <span data-ttu-id="e4134-154">`Err.Number` にエラーコードを配置したオブジェクトのほか、最初にエラーを生成したオブジェクト (`Err.Source` に指定されたオブジェクト) を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e4134-154">You can be sure which object placed the error code in `Err.Number`, as well as which object originally generated the error (the object specified in `Err.Source`).</span></span>

## <a name="on-error-goto-0"></a><span data-ttu-id="e4134-155">On Error GoTo 0</span><span class="sxs-lookup"><span data-stu-id="e4134-155">On Error GoTo 0</span></span>

 <span data-ttu-id="e4134-156">`On Error GoTo 0` によって、現在のプロシージャのエラー処理が無効になります。</span><span class="sxs-lookup"><span data-stu-id="e4134-156">`On Error GoTo 0` disables error handling in the current procedure.</span></span> <span data-ttu-id="e4134-157">プロシージャに 0 番の行が含まれている場合でも、エラー処理コードの開始として行 0 は指定されません。</span><span class="sxs-lookup"><span data-stu-id="e4134-157">It doesn't specify line 0 as the start of the error-handling code, even if the procedure contains a line numbered 0.</span></span> <span data-ttu-id="e4134-158">`On Error GoTo 0` ステートメントを使用しない場合、プロシージャが終了すると、エラー ハンドラーが自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="e4134-158">Without an `On Error GoTo 0` statement, an error handler is automatically disabled when a procedure is exited.</span></span>

## <a name="on-error-goto--1"></a><span data-ttu-id="e4134-159">On Error GoTo -1</span><span class="sxs-lookup"><span data-stu-id="e4134-159">On Error GoTo -1</span></span>

 <span data-ttu-id="e4134-160">`On Error GoTo -1` によって、現在のプロシージャの例外が無効になります。</span><span class="sxs-lookup"><span data-stu-id="e4134-160">`On Error GoTo -1` disables the exception in the current procedure.</span></span> <span data-ttu-id="e4134-161">プロシージャに -1 番の行が含まれている場合でも、エラー処理コードの開始として行 -1 は指定されません。</span><span class="sxs-lookup"><span data-stu-id="e4134-161">It does not specify line -1 as the start of the error-handling code, even if the procedure contains a line numbered -1.</span></span> <span data-ttu-id="e4134-162">`On Error GoTo -1` ステートメントを使用しない場合、プロシージャが終了すると、例外が自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="e4134-162">Without an `On Error GoTo -1` statement, an exception is automatically disabled when a procedure is exited.</span></span>

 <span data-ttu-id="e4134-163">エラーが発生しなかったときに、エラー処理コードが実行されないようにするには、次のフラグメントのように、エラー処理ルーチンの直前に、`Exit Sub`、`Exit Function`、または `Exit Property` ステートメントを配置します。</span><span class="sxs-lookup"><span data-stu-id="e4134-163">To prevent error-handling code from running when no error has occurred, place an `Exit Sub`, `Exit Function`, or `Exit Property` statement immediately before the error-handling routine, as in the following fragment:</span></span>

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 <span data-ttu-id="e4134-164">ここで、エラー処理コードは、`Exit Sub` ステートメントの後、`End Sub` ステートメントの前に置いて、プロシージャ フローから分離します。</span><span class="sxs-lookup"><span data-stu-id="e4134-164">Here, the error-handling code follows the `Exit Sub` statement and precedes the `End Sub` statement to separate it from the procedure flow.</span></span> <span data-ttu-id="e4134-165">エラー処理コードは、プロシージャ内の任意の場所に配置できます。</span><span class="sxs-lookup"><span data-stu-id="e4134-165">You can place error-handling code anywhere in a procedure.</span></span>

## <a name="untrapped-errors"></a><span data-ttu-id="e4134-166">トラップされないエラー</span><span class="sxs-lookup"><span data-stu-id="e4134-166">Untrapped Errors</span></span>

 <span data-ttu-id="e4134-167">オブジェクトが実行可能ファイルとして実行されている場合に、オブジェクトのトラップされないエラーが制御元のアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-167">Untrapped errors in objects are returned to the controlling application when the object is running as an executable file.</span></span> <span data-ttu-id="e4134-168">開発環境では、適切なオプションが設定されている場合にのみ、トラップされないエラーが制御元のアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-168">Within the development environment, untrapped errors are returned to the controlling application only if the proper options are set.</span></span> <span data-ttu-id="e4134-169">デバッグ時に設定すべきオプション、それらの設定方法、およびホストでクラスを作成できるかどうかの説明については、ホスト アプリケーションのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4134-169">See your host application's documentation for a description of which options should be set during debugging, how to set them, and whether the host can create classes.</span></span>

 <span data-ttu-id="e4134-170">他のオブジェクトにアクセスするオブジェクトを作成する場合は、返されたハンドルされないエラーの処理を試みる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4134-170">If you create an object that accesses other objects, you should try to handle any unhandled errors they pass back.</span></span> <span data-ttu-id="e4134-171">できない場合、`Err.Number` のエラー コードを独自のエラーのいずれかにマップし、次にそれらをオブジェクトの呼び出し元に渡します。</span><span class="sxs-lookup"><span data-stu-id="e4134-171">If you cannot, map the error codes in `Err.Number` to one of your own errors and then pass them back to the caller of your object.</span></span> <span data-ttu-id="e4134-172">独自のエラーを指定するには、エラー コードを `VbObjectError` 定数に追加します。</span><span class="sxs-lookup"><span data-stu-id="e4134-172">You should specify your error by adding your error code to the `VbObjectError` constant.</span></span> <span data-ttu-id="e4134-173">たとえば、エラー コードが 1052 の場合は、それを次のように割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e4134-173">For example, if your error code is 1052, assign it as follows:</span></span>

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> <span data-ttu-id="e4134-174">Windows ダイナミックリンク ライブラリ (DLL) の呼び出し時のシステム エラーでは、例外が発生せず、Visual Basic エラー トラップでトラップできません。</span><span class="sxs-lookup"><span data-stu-id="e4134-174">System errors during calls to Windows dynamic-link libraries (DLLs) do not raise exceptions and cannot be trapped with Visual Basic error trapping.</span></span> <span data-ttu-id="e4134-175">DLL 関数を呼び出すときは、API 仕様に従って、各戻り値の成功または失敗を確認し、失敗の場合は `Err` オブジェクトの `LastDLLError` プロパティの値を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4134-175">When calling DLL functions, you should check each return value for success or failure (according to the API specifications), and in the event of a failure, check the value in the `Err` object's `LastDLLError` property.</span></span>

## <a name="example"></a><span data-ttu-id="e4134-176">例</span><span class="sxs-lookup"><span data-stu-id="e4134-176">Example</span></span>

 <span data-ttu-id="e4134-177">この例では、最初に `On Error GoTo` ステートメントを使用して、プロシージャ内のエラー処理ルーチンの場所を指定しています。</span><span class="sxs-lookup"><span data-stu-id="e4134-177">This example first uses the `On Error GoTo` statement to specify the location of an error-handling routine within a procedure.</span></span> <span data-ttu-id="e4134-178">例では、0 で除算しようとしてエラー番号 6 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-178">In the example, an attempt to divide by zero generates error number 6.</span></span> <span data-ttu-id="e4134-179">エラー処理ルーチンでエラーが処理され、エラーが発生したステートメントに制御が返されます。</span><span class="sxs-lookup"><span data-stu-id="e4134-179">The error is handled in the error-handling routine, and control is then returned to the statement that caused the error.</span></span> <span data-ttu-id="e4134-180">`On Error GoTo 0` ステートメントによって、エラー トラップがオフになります。</span><span class="sxs-lookup"><span data-stu-id="e4134-180">The `On Error GoTo 0` statement turns off error trapping.</span></span> <span data-ttu-id="e4134-181">さらに、次のステートメントによって生成されるエラーのコンテキストを確実に認識できるように、`On Error Resume Next` ステートメントを使用して、エラー トラップを遅延します。</span><span class="sxs-lookup"><span data-stu-id="e4134-181">Then the `On Error Resume Next` statement is used to defer error trapping so that the context for the error generated by the next statement can be known for certain.</span></span> <span data-ttu-id="e4134-182">`Err.Clear` を使用して、エラーが処理された後に `Err` オブジェクトのプロパティがクリアされていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="e4134-182">Note that `Err.Clear` is used to clear the `Err` object's properties after the error is handled.</span></span>

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a><span data-ttu-id="e4134-183">必要条件</span><span class="sxs-lookup"><span data-stu-id="e4134-183">Requirements</span></span>

 <span data-ttu-id="e4134-184">**名前空間:** [Microsoft.VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="e4134-184">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>

 <span data-ttu-id="e4134-185">**アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="e4134-185">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>

## <a name="see-also"></a><span data-ttu-id="e4134-186">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4134-186">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [<span data-ttu-id="e4134-187">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="e4134-187">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="e4134-188">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="e4134-188">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="e4134-189">Resume ステートメント</span><span class="sxs-lookup"><span data-stu-id="e4134-189">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="e4134-190">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="e4134-190">Error Messages</span></span>](../error-messages/index.md)
- [<span data-ttu-id="e4134-191">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="e4134-191">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
