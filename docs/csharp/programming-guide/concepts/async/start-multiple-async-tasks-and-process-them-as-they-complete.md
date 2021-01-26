---
title: 完了時の非同期タスクの処理
description: この例では、C# で Task.WhenAny を使用して複数のタスクを開始し、その結果を開始の順番で処理するのではなく、完了時に処理する方法を示します。
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 4cdd35af900863895911ea5c2c9772af362951ec
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615972"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a><span data-ttu-id="d3d21-103">完了時の非同期タスクの処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="d3d21-103">Process asynchronous tasks as they complete (C#)</span></span>

<span data-ttu-id="d3d21-104"><xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> を使用すると、複数のタスクを、開始された順番に処理するのでなく、同時に開始して完了するごとに 1 つずつ処理できます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they're completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="d3d21-105">クエリを使用して、タスクのコレクションを作成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="d3d21-106">各タスクは、指定された Web サイトのコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d3d21-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="d3d21-107">while ループの各反復で、待機されている <xref:System.Threading.Tasks.Task.WhenAny%2A> への呼び出しは、最初にダウンロードを終了するタスクのコレクションにあるタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-107">In each iteration of a while loop, an awaited call to <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="d3d21-108">タスクはコレクションから削除され、処理されます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="d3d21-109">ループは、コレクションのタスクがなくなるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-109">The loop repeats until the collection contains no more tasks.</span></span>

## <a name="create-example-application"></a><span data-ttu-id="d3d21-110">サンプル アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="d3d21-110">Create example application</span></span>

<span data-ttu-id="d3d21-111">新しい .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-111">Create a new .NET Core console application.</span></span> <span data-ttu-id="d3d21-112">[dotnet new console](../../../../core/tools/dotnet-new.md#console) コマンドを使用するか、[Visual Studio](/visualstudio/install/install-visual-studio) を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-112">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="d3d21-113">任意のコード エディターで *Program.cs* ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-113">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="d3d21-114">using ステートメントの置換</span><span class="sxs-lookup"><span data-stu-id="d3d21-114">Replace using statements</span></span>

<span data-ttu-id="d3d21-115">既存の using ステートメントを次の宣言に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-115">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="d3d21-116">フィールドを追加する</span><span class="sxs-lookup"><span data-stu-id="d3d21-116">Add fields</span></span>

<span data-ttu-id="d3d21-117">`Program` クラスの定義に、次の 2 つのフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-117">In the `Program` class definition, add the following two fields:</span></span>

```csharp
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

<span data-ttu-id="d3d21-118">`HttpClient` では、HTTP 要求を送信して HTTP 応答を受信する機能が公開されます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-118">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="d3d21-119">`s_urlList` には、このアプリケーションで処理を計画するすべての URL が格納されます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-119">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="d3d21-120">アプリケーション エントリ ポイントの更新</span><span class="sxs-lookup"><span data-stu-id="d3d21-120">Update application entry point</span></span>

<span data-ttu-id="d3d21-121">コンソール アプリケーションのメイン エントリ ポイントは、`Main` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d3d21-121">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="d3d21-122">既存のメソッドを以下に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-122">Replace the existing method with the following:</span></span>

```csharp
static Task Main() => SumPageSizesAsync();
```

<span data-ttu-id="d3d21-123">更新した `Main` メソッドは、[async main](../../../whats-new/csharp-7.md#async-main) と見なされるようになります。これにより、実行可能ファイルへの非同期エントリ ポイントが可能になります。</span><span class="sxs-lookup"><span data-stu-id="d3d21-123">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="d3d21-124">これは、`SumPageSizesAsync` の呼び出しを表しています。</span><span class="sxs-lookup"><span data-stu-id="d3d21-124">It is expressed a call to `SumPageSizesAsync`.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="d3d21-125">非同期の合計ページ サイズ メソッドの作成</span><span class="sxs-lookup"><span data-stu-id="d3d21-125">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="d3d21-126">`Main` メソッドの下に、`SumPageSizesAsync` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-126">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="d3d21-127">このメソッドを開始するには、<xref:System.Diagnostics.Stopwatch> をインスタンス化して開始します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-127">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="d3d21-128">それには、実行時にタスクのコレクションを作成するクエリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-128">It then includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="d3d21-129">次のコードの `ProcessUrlAsync` への各呼び出しは、`TResult` が整数である <xref:System.Threading.Tasks.Task%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-129">Each call to `ProcessUrlAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

<span data-ttu-id="d3d21-130">LINQ での[遅延実行](../../../../standard/linq/deferred-execution-example.md)のため、各タスクを開始するには <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-130">Due to [deferred execution](../../../../standard/linq/deferred-execution-example.md) with the LINQ, you call <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> to start each task.</span></span>

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

<span data-ttu-id="d3d21-131">`while` ループでは、コレクション内の各タスクに対して次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-131">The `while` loop performs the following steps for each task in the collection:</span></span>

1. <span data-ttu-id="d3d21-132">`WhenAny` への呼び出しを待機し、コレクション内で最初にダウンロードが終了したタスクを識別します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-132">Awaits a call to `WhenAny` to identify the first task in the collection that has finished its download.</span></span>

    ```csharp
    Task<int> finishedTask = await Task.WhenAny(downloadTasks);
    ```

1. <span data-ttu-id="d3d21-133">コレクションからそのタスクを削除します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-133">Removes that task from the collection.</span></span>

    ```csharp
    downloadTasks.Remove(finishedTask);
    ```

1. <span data-ttu-id="d3d21-134">`finishedTask` への呼び出しから返される、`ProcessUrlAsync` を待機します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-134">Awaits `finishedTask`, which is returned by a call to `ProcessUrlAsync`.</span></span> <span data-ttu-id="d3d21-135">`finishedTask` 変数は <xref:System.Threading.Tasks.Task%601> が整数である `TResult` です。</span><span class="sxs-lookup"><span data-stu-id="d3d21-135">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span> <span data-ttu-id="d3d21-136">次の例に示すように、タスクは既に完了していますが、ダウンロードした Web サイトの長さの取得を待機します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-136">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="d3d21-137">タスクが失敗した場合、`AggregateException` がスローされる <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> プロパティの読み取りとは異なり、`await` からは `AggregateException` に格納されている最初の子の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-137">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property, which would throw the `AggregateException`.</span></span>

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a><span data-ttu-id="d3d21-138">プロセス メソッドの追加</span><span class="sxs-lookup"><span data-stu-id="d3d21-138">Add process method</span></span>

<span data-ttu-id="d3d21-139">`SumPageSizesAsync` メソッドの下に次の `ProcessUrlAsync` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-139">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="d3d21-140">どの URL に対しても、このメソッドにより、提供される `client` インスタンスが使用され、応答が `byte[]` として取得されます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-140">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="d3d21-141">URL と長さがコンソールに出力された後、長さが返されます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-141">The length is returned after the URL and length is written to the console.</span></span>

<span data-ttu-id="d3d21-142">ダウンロードされた長さが常に同じ順序では表示されないことを確認するために、プログラムを複数回実行します。</span><span class="sxs-lookup"><span data-stu-id="d3d21-142">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="d3d21-143">ループで `WhenAny` を使って、例に示すように、いくつかのタスクを格納する問題を解決できます。</span><span class="sxs-lookup"><span data-stu-id="d3d21-143">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="d3d21-144">ただし、多数のタスクが処理する場合、他のアプローチがより効率的です。</span><span class="sxs-lookup"><span data-stu-id="d3d21-144">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="d3d21-145">詳細と例については、「[Processing Tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete)」 (完了したタスクを処理する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3d21-145">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span></span>

## <a name="complete-example"></a><span data-ttu-id="d3d21-146">コード例全体</span><span class="sxs-lookup"><span data-stu-id="d3d21-146">Complete example</span></span>

<span data-ttu-id="d3d21-147">次のコードは、この例の *Program.cs* ファイルの完全なテキストです。</span><span class="sxs-lookup"><span data-stu-id="d3d21-147">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="d3d21-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3d21-148">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="d3d21-149">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="d3d21-149">Asynchronous programming with async and await (C#)</span></span>](index.md)
