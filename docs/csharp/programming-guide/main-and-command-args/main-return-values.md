---
title: Main() の戻り値 - C# プログラミング ガイド
description: Main() の戻り値について説明します。 コード例とコンパイラにより生成されたコードを参照し、使用可能なその他のリソースを確認してください。
ms.date: 03/11/2021
helpviewer_keywords:
- Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
ms.openlocfilehash: 6f4001ecd490d5627d3a1ec74ecf7d593451e104
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190360"
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="44c79-104">Main() の戻り値 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="44c79-104">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="44c79-105">次のいずれかの方法でメソッドを定義することで、`Main` メソッドから `int` を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="44c79-105">You can return an `int` from the `Main` method by defining the method in one of the following ways:</span></span>

| <span data-ttu-id="44c79-106">`Main` メソッド コード</span><span class="sxs-lookup"><span data-stu-id="44c79-106">`Main` method code</span></span>             | <span data-ttu-id="44c79-107">`Main` シグネチャ</span><span class="sxs-lookup"><span data-stu-id="44c79-107">`Main` signature</span></span>                             |
|--------------------------------|----------------------------------------------|
| <span data-ttu-id="44c79-108">`args` と `await` は使用しない</span><span class="sxs-lookup"><span data-stu-id="44c79-108">No use of `args` or `await`</span></span>    | `static int Main()`                          |
| <span data-ttu-id="44c79-109">`args` を使用し、`await` を使用しない</span><span class="sxs-lookup"><span data-stu-id="44c79-109">Uses `args`, no use of `await`</span></span> | `static int Main(string[] args)`             |
| <span data-ttu-id="44c79-110">`args` を使用せず、`await` を使用する</span><span class="sxs-lookup"><span data-stu-id="44c79-110">No use of `args`, uses `await`</span></span> | `static async Task<int> Main()`              |
| <span data-ttu-id="44c79-111">`args` と `await` を使用する</span><span class="sxs-lookup"><span data-stu-id="44c79-111">Uses `args` and `await`</span></span>        | `static async Task<int> Main(string[] args)` |

<span data-ttu-id="44c79-112">`Main` からの戻り値を使用しない場合、`void` か `Task` を返すと少し簡単なコードにすることができます。</span><span class="sxs-lookup"><span data-stu-id="44c79-112">If the return value from `Main` is not used, returning `void` or `Task` allows for slightly simpler code.</span></span>

| <span data-ttu-id="44c79-113">`Main` メソッド コード</span><span class="sxs-lookup"><span data-stu-id="44c79-113">`Main` method code</span></span>             | <span data-ttu-id="44c79-114">`Main` シグネチャ</span><span class="sxs-lookup"><span data-stu-id="44c79-114">`Main` signature</span></span>                        |
|--------------------------------|-----------------------------------------|
| <span data-ttu-id="44c79-115">`args` と `await` は使用しない</span><span class="sxs-lookup"><span data-stu-id="44c79-115">No use of `args` or `await`</span></span>    | `static void Main()`                    |
| <span data-ttu-id="44c79-116">`args` を使用し、`await` を使用しない</span><span class="sxs-lookup"><span data-stu-id="44c79-116">Uses `args`, no use of `await`</span></span> | `static void Main(string[] args)`       |
| <span data-ttu-id="44c79-117">`args` を使用せず、`await` を使用する</span><span class="sxs-lookup"><span data-stu-id="44c79-117">No use of `args`, uses `await`</span></span> | `static async Task Main()`              |
| <span data-ttu-id="44c79-118">`args` と `await` を使用する</span><span class="sxs-lookup"><span data-stu-id="44c79-118">Uses `args` and `await`</span></span>        | `static async Task Main(string[] args)` |

<span data-ttu-id="44c79-119">ただし、`int` か `Task<int>` を返すことによって、プログラムが状態の情報を、実行可能ファイルを呼び出す他のプログラムまたはスクリプトに伝達することができます。</span><span class="sxs-lookup"><span data-stu-id="44c79-119">However, returning `int` or `Task<int>` enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span>

<span data-ttu-id="44c79-120">次の例からは、プロセスの終了コードにアクセスする方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="44c79-120">The following example shows how the exit code for the process can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="44c79-121">例</span><span class="sxs-lookup"><span data-stu-id="44c79-121">Example</span></span>

<span data-ttu-id="44c79-122">この例では、[.NET Core](../../../core/introduction.md) コマンドライン ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="44c79-122">This example uses [.NET Core](../../../core/introduction.md) command-line tools.</span></span> <span data-ttu-id="44c79-123">.NET Core コマンドライン ツールに慣れていない場合は、この[概要の記事](../../../core/tutorials/with-visual-studio-code.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44c79-123">If you are unfamiliar with .NET Core command-line tools, you can learn about them in this [get-started article](../../../core/tutorials/with-visual-studio-code.md).</span></span>

<span data-ttu-id="44c79-124">*program.cs* の `Main` メソッドを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="44c79-124">Modify the `Main` method in *program.cs* as follows:</span></span>

 [!code-csharp[csProgGuideMain#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#14)]

<span data-ttu-id="44c79-125">プログラムを Windows で実行する場合、`Main` 関数からの戻り値はすべて 1 つの環境変数に格納されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-125">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="44c79-126">この環境変数を取得するには、バッチ ファイルから `ERRORLEVEL` を使用するか、PowerShell から `$LastExitCode` を使用します。</span><span class="sxs-lookup"><span data-stu-id="44c79-126">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from PowerShell.</span></span>

<span data-ttu-id="44c79-127">[dotnet CLI](../../../core/tools/dotnet.md) の `dotnet build` コマンドを使用してアプリケーションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="44c79-127">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="44c79-128">次に、アプリケーションを実行して結果を表示する PowerShell スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="44c79-128">Next, create a PowerShell script to run the application and display the result.</span></span> <span data-ttu-id="44c79-129">次のコードをテキスト ファイルに貼り付け、プロジェクトが保存されているフォルダーに `test.ps1` として保存します。</span><span class="sxs-lookup"><span data-stu-id="44c79-129">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="44c79-130">PowerShell プロンプトに「`test.ps1`」と入力して PowerShell スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="44c79-130">Run the PowerShell script by typing `test.ps1` at the PowerShell prompt.</span></span>

<span data-ttu-id="44c79-131">コードがゼロを返すため、バッチ ファイルで成功が報告されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-131">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="44c79-132">ただし、MainReturnValTest.cs が 0 以外の値を返すように変更して、プログラムを再コンパイルする場合、PowerShell スクリプトの後続の実行では失敗が報告されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-132">However, if you change MainReturnValTest.cs to return a non-zero value and then recompile the program, subsequent execution of the PowerShell script will report failure.</span></span>

```dotnetcli
dotnet run
```

```powershell
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="44c79-133">出力例</span><span class="sxs-lookup"><span data-stu-id="44c79-133">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="44c79-134">非同期 Main の戻り値</span><span class="sxs-lookup"><span data-stu-id="44c79-134">Async Main return values</span></span>

<span data-ttu-id="44c79-135">非同期 Main の戻り値によって、`Main` 内の非同期メソッドを呼び出すために必要な定型コードを、コンパイラで生成されるコードに移動します。</span><span class="sxs-lookup"><span data-stu-id="44c79-135">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="44c79-136">以前のバージョンでは、このコンストラクトを出力して非同期コードを呼び出し、非同期操作が完了するまでプログラムが実行されるようにする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="44c79-136">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="44c79-137">現在のバージョンでは、以下のように書き換えられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="44c79-137">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="44c79-138">新しい構文を使用すると、コンパイラから常に正しいコードが生成されるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="44c79-138">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="44c79-139">コンパイラで生成されたコード</span><span class="sxs-lookup"><span data-stu-id="44c79-139">Compiler-generated code</span></span>

<span data-ttu-id="44c79-140">アプリケーションのエントリ ポイントから `Task` または `Task<int>` が返されると、コンパイラによって、アプリケーション コードで宣言されたエントリ ポイント メソッドを呼び出す新しいエントリ ポイントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-140">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="44c79-141">このエントリ ポイント名が `$GeneratedMain` だとすると、これらのエントリ ポイントについて次のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-141">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="44c79-142">`static Task Main()` の結果、`private static void $GeneratedMain() => Main().GetAwaiter().GetResult();` と同等のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-142">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="44c79-143">`static Task Main(string[])` の結果、`private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` と同等のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-143">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="44c79-144">`static Task<int> Main()` の結果、`private static int $GeneratedMain() => Main().GetAwaiter().GetResult();` と同等のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-144">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="44c79-145">`static Task<int> Main(string[])` の結果、`private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();` と同等のコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-145">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="44c79-146">この例の `Main` メソッドで `async` 修飾子を使用した場合、同じコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="44c79-146">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="44c79-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="44c79-147">See also</span></span>

- [<span data-ttu-id="44c79-148">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="44c79-148">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="44c79-149">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="44c79-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="44c79-150">Main() とコマンドライン引数</span><span class="sxs-lookup"><span data-stu-id="44c79-150">Main() and Command-Line Arguments</span></span>](index.md)
- [<span data-ttu-id="44c79-151">コマンド ライン引数を表示する方法</span><span class="sxs-lookup"><span data-stu-id="44c79-151">How to display command line arguments</span></span>](./how-to-display-command-line-arguments.md)
