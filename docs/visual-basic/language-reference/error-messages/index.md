---
description: '詳細情報: Visual Basic のエラー メッセージ'
title: Visual Basic のエラー メッセージ
titleSuffix: ''
ms.date: 10/13/2020
helpviewer_keywords:
- errors [Visual Basic]
- error messages
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 28e59a47c47ff7905dfec93b057f7cb534842b91
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796068"
---
# <a name="error-messages-in-visual-basic"></a><span data-ttu-id="ba291-103">Visual Basic のエラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="ba291-103">Error messages in Visual Basic</span></span>

<span data-ttu-id="ba291-104">Visual Basic アプリケーションをコンパイルまたは実行する際は、次の種類のエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba291-104">When you compile or run a Visual Basic application, the following types of errors can occur:</span></span>

- <span data-ttu-id="ba291-105">コンパイル時エラー。アプリケーションをコンパイルするときに発生します。</span><span class="sxs-lookup"><span data-stu-id="ba291-105">Compile-time errors, which occur when you compile an application.</span></span>

- <span data-ttu-id="ba291-106">実行時エラー。アプリケーションの実行中に発生します。</span><span class="sxs-lookup"><span data-stu-id="ba291-106">Run-time errors, which occur when an application is running.</span></span>

<span data-ttu-id="ba291-107">特定のエラーのトラブルシューティング方法については、「[Visual Basic プログラマのための追加リソース](../../getting-started/additional-resources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba291-107">For information about how to troubleshoot a specific error, see [Additional Resources for Visual Basic Programmers](../../getting-started/additional-resources.md).</span></span>

## <a name="run-time-errors"></a><span data-ttu-id="ba291-108">実行時エラー</span><span class="sxs-lookup"><span data-stu-id="ba291-108">Run-time errors</span></span>

<span data-ttu-id="ba291-109">Visual Basic アプリケーションがシステムで実行できないアクションを実行しようとすると、実行時エラーが発生し、Visual Basic によって <xref:System.Exception> オブジェクトがスローされます。</span><span class="sxs-lookup"><span data-stu-id="ba291-109">If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and Visual Basic throws an <xref:System.Exception> object.</span></span> <span data-ttu-id="ba291-110">Visual Basic では、`Throw` ステートメントを使用することで、`Exception` オブジェクトを含む任意のデータ型のカスタム エラーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ba291-110">Visual Basic can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement.</span></span> <span data-ttu-id="ba291-111">アプリケーションは、キャッチされた例外のエラー番号とメッセージを表示して、エラーを識別できます。</span><span class="sxs-lookup"><span data-stu-id="ba291-111">An application can identify the error by displaying the error number and message of a caught exception.</span></span> <span data-ttu-id="ba291-112">エラーがキャッチされない場合、アプリケーションは終了します。</span><span class="sxs-lookup"><span data-stu-id="ba291-112">If an error isn't caught, the application ends.</span></span>

<span data-ttu-id="ba291-113">実行時エラーはコードでトラップして調べることができます。</span><span class="sxs-lookup"><span data-stu-id="ba291-113">The code can trap and examine run-time errors.</span></span> <span data-ttu-id="ba291-114">エラーが発生するコードを `Try` ブロックで囲むと、スローされたエラーを対応する `Catch` ブロック内でキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="ba291-114">If you enclose the code that produces the error in a `Try` block, you can catch any thrown error within a matching `Catch` block.</span></span> <span data-ttu-id="ba291-115">実行時にエラーをトラップしてコードで対処する方法については、「[Try...Catch...Finally ステートメント](../statements/try-catch-finally-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba291-115">For information about how to trap errors at run time and respond to them in your code, see [Try...Catch...Finally Statement](../statements/try-catch-finally-statement.md).</span></span>

## <a name="compile-time-errors"></a><span data-ttu-id="ba291-116">コンパイル時のエラー</span><span class="sxs-lookup"><span data-stu-id="ba291-116">Compile-time errors</span></span>

<span data-ttu-id="ba291-117">Visual Basic コンパイラがコード内で問題を検出すると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ba291-117">If the Visual Basic compiler encounters a problem in the code, a compile-time error occurs.</span></span> <span data-ttu-id="ba291-118">Visual Studio コード エディターでは、エラーの原因となったコード行の下に波線が表示されるため、簡単にその行を特定できます。</span><span class="sxs-lookup"><span data-stu-id="ba291-118">In the Visual Studio code editor, you can easily identify which line of code caused the error because a wavy line appears under that line of code.</span></span> <span data-ttu-id="ba291-119">波線をポイントするか **エラー一覧** を開くと、エラー メッセージが表示されます。エラー一覧には他のメッセージも表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba291-119">The error message appears if you either point to the wavy underline or open the **Error List**, which also shows other messages.</span></span>

<span data-ttu-id="ba291-120">識別子の下に波線があり、右端の文字の下に短い下線が表示されている場合は、クラス、コンストラクター、メソッド、プロパティ、フィールド、または列挙型のスタブを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ba291-120">If an identifier has a wavy underline and a short underline appears under the rightmost character, you can generate a stub for the class, constructor, method, property, field, or enum.</span></span> <span data-ttu-id="ba291-121">詳細については、[使用法からの生成 (Visual Studio)](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba291-121">For more information, see [Generate From Usage (Visual Studio)](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span></span>

<span data-ttu-id="ba291-122">Visual Basic コンパイラからのエラーを解決することにより、高速に実行されるバグの少ないコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ba291-122">By resolving warnings from the Visual Basic compiler, you might be able to write code that runs faster and has fewer bugs.</span></span> <span data-ttu-id="ba291-123">これらの警告では、アプリケーションの実行時にエラーを発生させるコードが示されます。</span><span class="sxs-lookup"><span data-stu-id="ba291-123">These warnings identify code that may cause errors when the application is run.</span></span> <span data-ttu-id="ba291-124">たとえば、ユーザーが、割り当てが行われていないオブジェクト変数のメンバーを呼び出そうとしたり、戻り値を設定せずに関数から戻ろうとしたり、例外をキャッチするロジックにエラーがある `Try` ブロックを実行しようとしたりすると、コンパイラは警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="ba291-124">For example, the compiler warns you if you try to invoke a member of an unassigned object variable, return from a function without setting the return value, or execute a `Try` block with errors in the logic to catch exceptions.</span></span> <span data-ttu-id="ba291-125">警告の表示/非表示を切り替える方法など、警告の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba291-125">For more information about warnings, including how to turn them on and off, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>
