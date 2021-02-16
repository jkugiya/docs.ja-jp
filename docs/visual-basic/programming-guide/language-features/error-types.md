---
description: '詳細情報: エラーの種類 (Visual Basic)'
title: エラーの種類
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
ms.openlocfilehash: cc4fce5e0ce77a4e402ba832fd6f4e36e6feed07
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423772"
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="e2aea-103">エラーの種類 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2aea-103">Error Types (Visual Basic)</span></span>

<span data-ttu-id="e2aea-104">Visual Basic では、エラーは構文エラー、実行時エラー、論理エラーという 3 つのカテゴリのいずれかに分類されます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-104">In Visual Basic, errors fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>

## <a name="syntax-errors"></a><span data-ttu-id="e2aea-105">構文エラー</span><span class="sxs-lookup"><span data-stu-id="e2aea-105">Syntax Errors</span></span>

 <span data-ttu-id="e2aea-106">"*構文エラー*" は、コードの記述時に表示されるエラーです。</span><span class="sxs-lookup"><span data-stu-id="e2aea-106">*Syntax errors* are those that appear while you write code.</span></span> <span data-ttu-id="e2aea-107">Visual Studio を使用している場合は、**コード エディター** ウィンドウでコードを入力すると Visual Basic でコードが確認され、単語のスペルミスや言語要素の不適切な使用などの誤りがあった場合は警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-107">If you're using Visual Studio, Visual Basic checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="e2aea-108">コマンド ラインからコンパイルすると、Visual Basic にはコンパイラ エラーが、構文エラーに関する情報とともに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-108">If you compile from the command line, Visual Basic displays a compiler error with information about the syntax error.</span></span> <span data-ttu-id="e2aea-109">構文エラーは、最も一般的なエラーの種類です。</span><span class="sxs-lookup"><span data-stu-id="e2aea-109">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="e2aea-110">コーディング環境では、発生したらすぐに、簡単に修正できます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-110">You can fix them easily in the coding environment as soon as they occur.</span></span>

> [!NOTE]
> <span data-ttu-id="e2aea-111">`Option Explicit` ステートメントは、構文エラーを回避するための 1 つの手段です。</span><span class="sxs-lookup"><span data-stu-id="e2aea-111">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="e2aea-112">これにより、アプリケーションで使用するすべての変数を事前に宣言することが強制されます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-112">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="e2aea-113">そのため、それらの変数をコード内で使用するときは、あらゆる表記エラーを即座に見つけて修正することができます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-113">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>

## <a name="run-time-errors"></a><span data-ttu-id="e2aea-114">実行時エラー</span><span class="sxs-lookup"><span data-stu-id="e2aea-114">Run-Time Errors</span></span>

 <span data-ttu-id="e2aea-115">"*実行時エラー*" は、コードをコンパイルして実行した後でのみ表示されるエラーです。</span><span class="sxs-lookup"><span data-stu-id="e2aea-115">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="e2aea-116">これには、構文エラーがなく正しく見えるにもかかわらず、実行できないコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-116">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="e2aea-117">たとえば、ファイルを開くためのコード行を正しく記述したとします。</span><span class="sxs-lookup"><span data-stu-id="e2aea-117">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="e2aea-118">しかし、そのファイルが存在しない場合は、アプリケーションでファイルを開くことができず、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-118">But if the file does not exist, the application cannot open the file, and it throws an exception.</span></span> <span data-ttu-id="e2aea-119">ほとんどの実行時エラーは、問題のあるコードを書き直すか、[例外処理](../../language-reference/statements/try-catch-finally-statement.md)を使用して、再コンパイル後に再実行することによって修正できます。</span><span class="sxs-lookup"><span data-stu-id="e2aea-119">You can fix most run-time errors by rewriting the faulty code or by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md), and then recompiling and rerunning it.</span></span>
  
## <a name="logic-errors"></a><span data-ttu-id="e2aea-120">論理エラー</span><span class="sxs-lookup"><span data-stu-id="e2aea-120">Logic Errors</span></span>

 <span data-ttu-id="e2aea-121">"*論理エラー*" は、アプリケーションの使用中に表示されるエラーです。</span><span class="sxs-lookup"><span data-stu-id="e2aea-121">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="e2aea-122">ほとんどの場合は、開発者による想定の誤り、またはユーザーの操作に対する応答として望ましくないか、予期しない結果です。</span><span class="sxs-lookup"><span data-stu-id="e2aea-122">They are most often faulty assumptions made by the developer, or unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="e2aea-123">たとえば、キーの誤入力によってメソッドに誤った情報が提供されることがあります。そうでない場合は、常に有効な値がメソッドに渡されるという、想定をしている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e2aea-123">For example, a mistyped key might provide incorrect information to a method, or you may assume that a valid value is always supplied to a method when that is not the case.</span></span> <span data-ttu-id="e2aea-124">論理エラーは[例外処理](../../language-reference/statements/try-catch-finally-statement.md)を使用して処理できますが (たとえば、引数が `Nothing` であるかどうかをテストし、<xref:System.ArgumentNullException> をスローするなど)、ほとんどの場合、ロジックのエラーを修正し、アプリケーションを再コンパイルして対処する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2aea-124">Although logic errors can be handled by using [exception handling](../../language-reference/statements/try-catch-finally-statement.md) (for example, by testing whether an argument is `Nothing` and throwing an <xref:System.ArgumentNullException>), most commonly they should be addressed by correcting the error in logic and recompiling the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2aea-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2aea-125">See also</span></span>

- [<span data-ttu-id="e2aea-126">Try...Catch...Finally ステートメント</span><span class="sxs-lookup"><span data-stu-id="e2aea-126">Try...Catch...Finally Statement</span></span>](../../language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="e2aea-127">デバッガーの基本事項</span><span class="sxs-lookup"><span data-stu-id="e2aea-127">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
