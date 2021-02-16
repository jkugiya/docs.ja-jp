---
description: '詳細情報: Visual Basic の Main プロシージャ'
title: メインのプロシージャ
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: b25190ef216fe4219923a27d6bbe0acff4536685
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432807"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="cda88-103">Visual Basic の Main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="cda88-103">Main Procedure in Visual Basic</span></span>

<span data-ttu-id="cda88-104">すべての Visual Basic アプリケーションには、`Main` と呼ばれるプロシージャが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cda88-104">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="cda88-105">このプロシージャは、アプリケーションの開始点となり、アプリケーションの全体的な制御を行います。</span><span class="sxs-lookup"><span data-stu-id="cda88-105">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="cda88-106">.NET Framework では、アプリケーションが読み込まれ、制御を渡す準備ができると、`Main` プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cda88-106">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="cda88-107">Windows フォーム アプリケーションを作成する場合を除き、単独で実行されるアプリケーションでは、`Main` プロシージャを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cda88-107">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="cda88-108">`Main` には、最初に実行されるコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cda88-108">`Main` contains the code that runs first.</span></span> <span data-ttu-id="cda88-109">`Main` では、プログラムの起動時に最初に読み込まれるフォームを決定したり、アプリケーションのコピーがシステムで既に実行されているかどうかを確認したりできます。また、アプリケーションの一連の変数を確立したり、アプリケーションに必要なデータベースを開いたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cda88-109">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="cda88-110">Main プロシージャの要件</span><span class="sxs-lookup"><span data-stu-id="cda88-110">Requirements for the Main Procedure</span></span>

 <span data-ttu-id="cda88-111">単独で実行されるファイル (通常は拡張子が .exe) には、`Main` プロシージャが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cda88-111">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="cda88-112">ライブラリ (拡張子.dll など) は単独では実行されないので、`Main` プロシージャは不要です。</span><span class="sxs-lookup"><span data-stu-id="cda88-112">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="cda88-113">作成できるさまざまな種類のプロジェクトの要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cda88-113">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="cda88-114">コンソール アプリケーションは単独で実行されるので、少なくとも 1 つの `Main` プロシージャを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cda88-114">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="cda88-115">Windows フォーム アプリケーションは単独で実行されます。</span><span class="sxs-lookup"><span data-stu-id="cda88-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="cda88-116">ただし、このようなアプリケーションの `Main` プロシージャは、Visual Basic コンパイラによって自動的に生成されるので、記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cda88-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="cda88-117">クラス ライブラリには、`Main` プロシージャは不要です。</span><span class="sxs-lookup"><span data-stu-id="cda88-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="cda88-118">これには、Windows コントロール ライブラリや Web コントロール ライブラリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cda88-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="cda88-119">Web アプリケーションは、クラス ライブラリとして展開されます。</span><span class="sxs-lookup"><span data-stu-id="cda88-119">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="cda88-120">Main プロシージャの宣言</span><span class="sxs-lookup"><span data-stu-id="cda88-120">Declaring the Main Procedure</span></span>

 <span data-ttu-id="cda88-121">`Main` プロシージャを宣言するには、4 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="cda88-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="cda88-122">引数を受け取ることも、受け取らないこともできます。また、値を返すことも返さないこともできます。</span><span class="sxs-lookup"><span data-stu-id="cda88-122">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="cda88-123">`Main` をクラスで宣言する場合は、`Shared` キーワードを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cda88-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="cda88-124">モジュールでは、`Main` は `Shared` である必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cda88-124">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="cda88-125">最も簡単な方法は、引数を受け取らず、値を返さない `Sub` プロシージャを宣言することです。</span><span class="sxs-lookup"><span data-stu-id="cda88-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="cda88-126">`Main` では、オペレーティング システムがプログラムの終了コードとして使用する `Integer` 値を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="cda88-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="cda88-127">他のプログラムは Windows の ERRORLEVEL 値を調べることで、このコードをテストできます。</span><span class="sxs-lookup"><span data-stu-id="cda88-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="cda88-128">終了コードを返すには、`Sub` プロシージャではなく、`Function` プロシージャとして `Main` を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cda88-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
    Module mainModule
        Function Main() As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="cda88-129">`Main` では、引数として `String` 配列を受け取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="cda88-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="cda88-130">配列内の各文字列には、プログラムの呼び出しに使用されるコマンド ライン引数の 1 つが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cda88-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="cda88-131">値に応じてさまざまなアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="cda88-131">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="cda88-132">次のように、コマンド ライン引数を調べ、終了コードは返さないように、`Main` を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="cda88-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="cda88-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="cda88-133">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="cda88-134">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="cda88-134">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="cda88-135">-main</span><span class="sxs-lookup"><span data-stu-id="cda88-135">-main</span></span>](../../reference/command-line-compiler/main.md)
- [<span data-ttu-id="cda88-136">Shared</span><span class="sxs-lookup"><span data-stu-id="cda88-136">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="cda88-137">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="cda88-137">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="cda88-138">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="cda88-138">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="cda88-139">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="cda88-139">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="cda88-140">String データ型</span><span class="sxs-lookup"><span data-stu-id="cda88-140">String Data Type</span></span>](../../language-reference/data-types/string-data-type.md)
