---
title: タスクの一覧をキャンセルする (C#)
description: キャンセル トークンを使用して、タスクの一覧にキャンセル要求を通知する方法について説明します。
ms.date: 02/03/2021
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 532c61ab6499583620ba2ee5c710c58f7886f89d
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585742"
---
# <a name="cancel-a-list-of-tasks-c"></a><span data-ttu-id="2dea3-103">タスクの一覧をキャンセルする (C#)</span><span class="sxs-lookup"><span data-stu-id="2dea3-103">Cancel a list of tasks (C#)</span></span>

<span data-ttu-id="2dea3-104">非同期のコンソール アプリケーションは、終了まで待機しない場合にキャンセルすることができます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-104">You can cancel an async console application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="2dea3-105">このトピックの例に従うと、Web サイトの一覧のコンテンツをダウンロードするアプリケーションにキャンセルを追加できます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-105">By following the example in this topic, you can add a cancellation to an application that downloads the contents of a list of websites.</span></span> <span data-ttu-id="2dea3-106">各タスクに <xref:System.Threading.CancellationTokenSource> インスタンスを関連付けると、多くのタスクをキャンセルすることができます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-106">You can cancel many tasks by associating the <xref:System.Threading.CancellationTokenSource> instance with each task.</span></span> <span data-ttu-id="2dea3-107"><kbd>Enter</kbd> キーを選択すると、完了していないすべてのタスクがキャンセルされます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-107">If you select the <kbd>Enter</kbd> key, you cancel all tasks that aren't yet complete.</span></span>

<span data-ttu-id="2dea3-108">このチュートリアルの内容:</span><span class="sxs-lookup"><span data-stu-id="2dea3-108">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="2dea3-109">.NET コンソール アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="2dea3-109">Creating a .NET console application</span></span>
> - <span data-ttu-id="2dea3-110">キャンセルをサポートする非同期アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="2dea3-110">Writing an async application that supports cancellation</span></span>
> - <span data-ttu-id="2dea3-111">キャンセル通知のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="2dea3-111">Demonstrating signaling cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2dea3-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="2dea3-112">Prerequisites</span></span>

<span data-ttu-id="2dea3-113">このチュートリアルには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="2dea3-113">This tutorial requires the following:</span></span>

- [<span data-ttu-id="2dea3-114">.NET 5.0 以降の SDK</span><span class="sxs-lookup"><span data-stu-id="2dea3-114">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="2dea3-115">統合開発環境 (IDE)</span><span class="sxs-lookup"><span data-stu-id="2dea3-115">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="2dea3-116">Visual Studio、Visual Studio Code、または Visual Studio for Mac をお勧めします</span><span class="sxs-lookup"><span data-stu-id="2dea3-116">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a><span data-ttu-id="2dea3-117">サンプル アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="2dea3-117">Create example application</span></span>

<span data-ttu-id="2dea3-118">新しい .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="2dea3-118">Create a new .NET Core console application.</span></span> <span data-ttu-id="2dea3-119">[`dotnet new console`](../../../../core/tools/dotnet-new.md#console) コマンドを使用するか、[Visual Studio](/visualstudio/install/install-visual-studio) から作成できます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-119">You can create one by using the [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="2dea3-120">任意のコード エディターで *Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-120">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="2dea3-121">using ステートメントの置換</span><span class="sxs-lookup"><span data-stu-id="2dea3-121">Replace using statements</span></span>

<span data-ttu-id="2dea3-122">既存の using ステートメントを次の宣言に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-122">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="2dea3-123">フィールドを追加する</span><span class="sxs-lookup"><span data-stu-id="2dea3-123">Add fields</span></span>

<span data-ttu-id="2dea3-124">`Program` クラス定義で、次の 3 つのフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="2dea3-124">In the `Program` class definition, add these three fields:</span></span>

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

<span data-ttu-id="2dea3-125"><xref:System.Threading.CancellationTokenSource> は、要求されるキャンセルを <xref:System.Threading.CancellationToken> に通知するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-125">The <xref:System.Threading.CancellationTokenSource> is used to signal a requested cancellation to a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="2dea3-126">`HttpClient` では、HTTP 要求を送信して HTTP 応答を受信する機能が公開されます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-126">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="2dea3-127">`s_urlList` には、このアプリケーションで処理を計画するすべての URL が格納されます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-127">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="2dea3-128">アプリケーション エントリ ポイントの更新</span><span class="sxs-lookup"><span data-stu-id="2dea3-128">Update application entry point</span></span>

<span data-ttu-id="2dea3-129">コンソール アプリケーションのメイン エントリ ポイントは、`Main` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2dea3-129">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="2dea3-130">既存のメソッドを以下に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-130">Replace the existing method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="2dea3-131">更新した `Main` メソッドは、[async main](../../../whats-new/csharp-7.md#async-main) と見なされるようになります。これにより、実行可能ファイルへの非同期エントリ ポイントが可能になります。</span><span class="sxs-lookup"><span data-stu-id="2dea3-131">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="2dea3-132">いくつかの指示メッセージがコンソールに出力され、次に `cancelTask` という名前の <xref:System.Threading.Tasks.Task> インスタンスが宣言されます。これにより、コンソールのキー ストロークが読み取られるようになります。</span><span class="sxs-lookup"><span data-stu-id="2dea3-132">It writes a few instructional messages to the console, then declares a <xref:System.Threading.Tasks.Task> instance named `cancelTask`, which will read console key strokes.</span></span> <span data-ttu-id="2dea3-133"><kbd>Enter</kbd> キーが押されると、<xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> の呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-133">If the <kbd>Enter</kbd> key is pressed, a call to <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> is made.</span></span> <span data-ttu-id="2dea3-134">これにより、キャンセルが通知されるようになります。</span><span class="sxs-lookup"><span data-stu-id="2dea3-134">This will signal cancellation.</span></span> <span data-ttu-id="2dea3-135">次に、`sumPageSizesTask` 変数が `SumPageSizesAsync` メソッドから割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="2dea3-135">Next, the `sumPageSizesTask` variable is assigned from the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="2dea3-136">両方のタスクは次に <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> に渡され、2 つのタスクのいずれかが完了したときに続行されるようになります。</span><span class="sxs-lookup"><span data-stu-id="2dea3-136">Both tasks are then passed to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, which will continue when any of the two tasks have completed.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="2dea3-137">非同期の合計ページ サイズ メソッドの作成</span><span class="sxs-lookup"><span data-stu-id="2dea3-137">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="2dea3-138">`Main` メソッドの下に、`SumPageSizesAsync` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="2dea3-138">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="2dea3-139">このメソッドを開始するには、<xref:System.Diagnostics.Stopwatch> をインスタンス化して開始します。</span><span class="sxs-lookup"><span data-stu-id="2dea3-139">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="2dea3-140">次に、`s_urlList` 内の各 URL をループし、`ProcessUrlAsync` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2dea3-140">It then loops through each URL in the `s_urlList` and calls `ProcessUrlAsync`.</span></span> <span data-ttu-id="2dea3-141">反復処理のたびに、`s_cts.Token` が `ProcessUrlAsync` メソッドに渡され、コードから <xref:System.Threading.Tasks.Task%601> が返されます。`TResult` は整数です。</span><span class="sxs-lookup"><span data-stu-id="2dea3-141">With each iteration, the `s_cts.Token` is passed into the `ProcessUrlAsync` method and the code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a><span data-ttu-id="2dea3-142">プロセス メソッドの追加</span><span class="sxs-lookup"><span data-stu-id="2dea3-142">Add process method</span></span>

<span data-ttu-id="2dea3-143">`SumPageSizesAsync` メソッドの下に次の `ProcessUrlAsync` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="2dea3-143">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="2dea3-144">どの URL に対しても、このメソッドにより、提供される `client` インスタンスが使用され、応答が `byte[]` として取得されます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-144">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="2dea3-145"><xref:System.Threading.CancellationToken> インスタンスは、<xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> および <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-145">The <xref:System.Threading.CancellationToken> instance is passed into the <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> and <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="2dea3-146">`token` は、要求されるキャンセルの登録に使用されます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-146">The `token` is used to register for requested cancellation.</span></span> <span data-ttu-id="2dea3-147">URL と長さがコンソールに出力された後、長さが返されます。</span><span class="sxs-lookup"><span data-stu-id="2dea3-147">The length is returned after the URL and length is written to the console.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="2dea3-148">アプリケーション出力の例</span><span class="sxs-lookup"><span data-stu-id="2dea3-148">Example application output</span></span>

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="2dea3-149">コード例全体</span><span class="sxs-lookup"><span data-stu-id="2dea3-149">Complete example</span></span>

<span data-ttu-id="2dea3-150">次のコードは、この例の *Program.cs* ファイルの完全なテキストです。</span><span class="sxs-lookup"><span data-stu-id="2dea3-150">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="2dea3-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="2dea3-151">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="2dea3-152">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="2dea3-152">Asynchronous programming with async and await (C#)</span></span>](index.md)

## <a name="next-steps"></a><span data-ttu-id="2dea3-153">次の手順</span><span class="sxs-lookup"><span data-stu-id="2dea3-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2dea3-154">指定した時間の経過後の非同期タスクのキャンセル (C#)</span><span class="sxs-lookup"><span data-stu-id="2dea3-154">Cancel async tasks after a period of time (C#)</span></span>](cancel-async-tasks-after-a-period-of-time.md)
