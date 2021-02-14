---
title: アセンブリの読み込みに関する詳細情報の収集 - .NET Core
description: .NET Core でアセンブリの読み込み情報を収集する方法の説明
author: elinor-fung
ms.author: elfung
ms.date: 11/17/2020
ms.openlocfilehash: b121982995b440ade6d72190f44f9b9d237c8af6
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506505"
---
# <a name="collect-detailed-assembly-loading-information"></a><span data-ttu-id="31394-103">アセンブリの読み込みに関する詳細情報の収集</span><span class="sxs-lookup"><span data-stu-id="31394-103">Collect detailed assembly loading information</span></span>

<span data-ttu-id="31394-104">.NET 5.0 以降、ランタイムを使用して、`EventPipe` を介して[マネージド アセンブリの読み込み](loading-managed.md)に関する詳細情報を含むイベントを発行し、アセンブリの読み込みに関する問題の診断に役立てることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="31394-104">Starting with .NET 5.0, the runtime can emit events through `EventPipe` with detailed information about [managed assembly loading](loading-managed.md) to aid in diagnosing assembly loading issues.</span></span> <span data-ttu-id="31394-105">これらの[イベント](../../fundamentals/diagnostics/runtime-loader-binder-events.md)は、`AssemblyLoader` キーワード (`0x4`) に従い `Microsoft-Windows-DotNETRuntime` プロバイダーによって発行されます。</span><span class="sxs-lookup"><span data-stu-id="31394-105">These [events](../../fundamentals/diagnostics/runtime-loader-binder-events.md) are emitted by the `Microsoft-Windows-DotNETRuntime` provider under the `AssemblyLoader` keyword (`0x4`).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31394-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="31394-106">Prerequisites</span></span>

- <span data-ttu-id="31394-107">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="31394-107">[.NET 5.0 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="31394-108">[dotnet-trace](../diagnostics/dotnet-trace.md) ツール。</span><span class="sxs-lookup"><span data-stu-id="31394-108">[dotnet-trace](../diagnostics/dotnet-trace.md) tool.</span></span>

## <a name="collect-a-trace-with-assembly-loading-events"></a><span data-ttu-id="31394-109">アセンブリの読み込みイベントを使用してトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="31394-109">Collect a trace with assembly loading events</span></span>

<span data-ttu-id="31394-110">ランタイムでアセンブリの読み込みイベントを有効にし、それらのトレースを収集するには、次のコマンドで `dotnet-trace` を使用します。</span><span class="sxs-lookup"><span data-stu-id="31394-110">To enable assembly loading events in the runtime and collect a trace of them, use `dotnet-trace` with the following command:</span></span>

```console
dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id <pid>
```

<span data-ttu-id="31394-111">これにより、`Microsoft-Windows-DotNETRuntime` プロバイダーで `AssemblyLoader` イベントが有効になり、指定された `<pid>` のトレースが収集されます。</span><span class="sxs-lookup"><span data-stu-id="31394-111">This will collect a trace of the specified `<pid>`, enabling the `AssemblyLoader` events in the `Microsoft-Windows-DotNETRuntime` provider.</span></span> <span data-ttu-id="31394-112">結果は `.nettrace` ファイルになります。</span><span class="sxs-lookup"><span data-stu-id="31394-112">The result is a `.nettrace` file.</span></span>

## <a name="view-a-trace"></a><span data-ttu-id="31394-113">トレースを表示する</span><span class="sxs-lookup"><span data-stu-id="31394-113">View a trace</span></span>

<span data-ttu-id="31394-114">収集されたトレース ファイルは、Windows 上で [PerfView](https://github.com/microsoft/perfview) の [Events]\(イベント\) ビューを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="31394-114">The collected trace file can be viewed on Windows using the Events view in [PerfView](https://github.com/microsoft/perfview).</span></span> <span data-ttu-id="31394-115">すべてのアセンブリの読み込みイベントには、`Microsoft-Windows-DotNETRuntime/AssemblyLoader` というプレフィックスが付きます。</span><span class="sxs-lookup"><span data-stu-id="31394-115">All the assembly loading events will be prefixed with `Microsoft-Windows-DotNETRuntime/AssemblyLoader`.</span></span>

## <a name="example-on-windows"></a><span data-ttu-id="31394-116">例 (Windows の場合)</span><span class="sxs-lookup"><span data-stu-id="31394-116">Example (on Windows)</span></span>

<span data-ttu-id="31394-117">この例では、[アセンブリの読み込み拡張ポイントのサンプル](https://github.com/dotnet/samples/tree/master/core/extensions/AssemblyLoading)を使用します。</span><span class="sxs-lookup"><span data-stu-id="31394-117">This example uses the [assembly loading extension points sample](https://github.com/dotnet/samples/tree/master/core/extensions/AssemblyLoading).</span></span> <span data-ttu-id="31394-118">このアプリケーションにより、アセンブリ `MyLibrary` (アプリケーションから参照されていないアセンブリ) の読み込みが試行されます。そのため、正常に読み込むには、アセンブリの読み込み拡張ポイントでの処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="31394-118">The application attempts to load an assembly `MyLibrary` - an assembly that is not referenced by the application and thus requires handling in an assembly loading extension point to be successfully loaded.</span></span>

### <a name="collect-the-trace"></a><span data-ttu-id="31394-119">トレースを収集する</span><span class="sxs-lookup"><span data-stu-id="31394-119">Collect the trace</span></span>

01. <span data-ttu-id="31394-120">ダウンロードしたサンプルのあるディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="31394-120">Navigate to the directory with the downloaded sample.</span></span> <span data-ttu-id="31394-121">次を使用してアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="31394-121">Build the application with:</span></span>

    ```console
    dotnet build
    ```

01. <span data-ttu-id="31394-122">一時停止する必要があることを示す引数を指定してアプリケーションを起動し、キーの押下を待機します。</span><span class="sxs-lookup"><span data-stu-id="31394-122">Launch the application with arguments indicating that it should pause, waiting for a key press.</span></span> <span data-ttu-id="31394-123">再開すると、既定の `AssemblyLoadContext` でアセンブリの読み込みが試行されます。正常に読み込むために必要な処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="31394-123">On resuming, it will attempt to load the assembly in the default `AssemblyLoadContext` - without the handling necessary for a successful load.</span></span> <span data-ttu-id="31394-124">出力ディレクトリに移動し、次を実行します。</span><span class="sxs-lookup"><span data-stu-id="31394-124">Navigate to the output directory and run:</span></span>

    ```console
    AssemblyLoading.exe /d default
    ```

01. <span data-ttu-id="31394-125">アプリケーションのプロセス ID を見つけます。</span><span class="sxs-lookup"><span data-stu-id="31394-125">Find the application's process ID.</span></span>

    ```console
    dotnet-trace ps
    ```

    <span data-ttu-id="31394-126">出力には、使用できるプロセスが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="31394-126">The output will list the available processes.</span></span> <span data-ttu-id="31394-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="31394-127">For example:</span></span>

    ```console
    35832 AssemblyLoading C:\src\AssemblyLoading\bin\Debug\net5.0\AssemblyLoading.exe
    ```

01. <span data-ttu-id="31394-128">実行中のアプリケーションに `dotnet-trace` をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="31394-128">Attach `dotnet-trace` to the running application.</span></span>

    ```console
    dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id 35832
    ```

01. <span data-ttu-id="31394-129">アプリケーションを実行しているウィンドウで、任意のキーを押してプログラムを続行します。</span><span class="sxs-lookup"><span data-stu-id="31394-129">In the window running the application, press any key to let the program continue.</span></span> <span data-ttu-id="31394-130">アプリケーションが終了すると、トレースは自動的に停止します。</span><span class="sxs-lookup"><span data-stu-id="31394-130">Tracing will automatically stop once the application exits.</span></span>

### <a name="view-the-trace"></a><span data-ttu-id="31394-131">トレースを表示する</span><span class="sxs-lookup"><span data-stu-id="31394-131">View the trace</span></span>

<span data-ttu-id="31394-132">収集したトレースを [PerfView](https://github.com/microsoft/perfview) で開き、[Events]\(イベント\) ビューを開きます。</span><span class="sxs-lookup"><span data-stu-id="31394-132">Open the collected trace in [PerfView](https://github.com/microsoft/perfview) and open the Events view.</span></span> <span data-ttu-id="31394-133">イベント一覧をフィルター処理して `Microsoft-Windows-DotNETRuntime/AssemblyLoader` イベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="31394-133">Filter the events list to `Microsoft-Windows-DotNETRuntime/AssemblyLoader` events.</span></span>

:::image type="content" source="media/collect-details/assembly-loader-filter.png" alt-text="PerfView のアセンブリ ローダーのフィルターの画像":::

<span data-ttu-id="31394-135">トレースの開始後にアプリケーションで発生したすべてのアセンブリの読み込みが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31394-135">All assembly loads that occurred in the application after tracing started will be shown.</span></span> <span data-ttu-id="31394-136">この例 (`MyLibrary`) の対象となるアセンブリの読み込み操作を調べるために、さらにフィルター処理を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="31394-136">To inspect the load operation for the assembly of interest for this example - `MyLibrary`, we can do some more filtering.</span></span>

### <a name="assembly-loads"></a><span data-ttu-id="31394-137">アセンブリの読み込み</span><span class="sxs-lookup"><span data-stu-id="31394-137">Assembly loads</span></span>

<span data-ttu-id="31394-138">左側のイベント一覧を使用し、ビューをフィルター処理して `Microsoft-Windows-DotNETRuntime/AssemblyLoader` 以下の [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) および [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) イベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="31394-138">Filter the view to the [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) and [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) events under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="31394-139">列 `AssemblyName`、`ActivityID`、および `Success` をビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="31394-139">Add the columns `AssemblyName`, `ActivityID`, and `Success` to the view.</span></span> <span data-ttu-id="31394-140">フィルター処理して `MyLibrary` を含むイベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="31394-140">Filter to events containing `MyLibrary`.</span></span>

:::image type="content" source="media/collect-details/start-stop.png" alt-text="PerfView の開始および終了イベントの画像":::

| <span data-ttu-id="31394-142">イベント名</span><span class="sxs-lookup"><span data-stu-id="31394-142">Event Name</span></span>             | <span data-ttu-id="31394-143">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31394-143">AssemblyName</span></span>                                      | <span data-ttu-id="31394-144">ActivityID</span><span class="sxs-lookup"><span data-stu-id="31394-144">ActivityID</span></span> | <span data-ttu-id="31394-145">成功</span><span class="sxs-lookup"><span data-stu-id="31394-145">Success</span></span> |
| ---------------------- | ------------------------------------------------- | ---------- | ------- |
| `AssemblyLoader/Start` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31394-146">//1/2/</span><span class="sxs-lookup"><span data-stu-id="31394-146">//1/2/</span></span>     |         |
| `AssemblyLoader/Stop`  | `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31394-147">//1/2/</span><span class="sxs-lookup"><span data-stu-id="31394-147">//1/2/</span></span>     | <span data-ttu-id="31394-148">False</span><span class="sxs-lookup"><span data-stu-id="31394-148">False</span></span>   |

<span data-ttu-id="31394-149">`Stop` イベントに 1 つの `Start`/`Stop` ペアと `Success=False` があります。これは、読み込み操作が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="31394-149">You should see one `Start`/`Stop` pair with `Success=False` on the `Stop` event, indicating the load operation failed.</span></span> <span data-ttu-id="31394-150">2 つのイベントのアクティビティ ID が同じであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="31394-150">Note that the two events have the same activity ID.</span></span> <span data-ttu-id="31394-151">アクティビティ ID を使用すると、他のすべてのアセンブリ ローダー イベントを、この読み込み操作に対応するイベントのみにフィルター処理することができます。</span><span class="sxs-lookup"><span data-stu-id="31394-151">The activity ID can be used to filter all the other assembly loader events to just the ones corresponding to this load operation.</span></span>

### <a name="breakdown-of-attempt-to-load"></a><span data-ttu-id="31394-152">読み込みの試行の内訳</span><span class="sxs-lookup"><span data-stu-id="31394-152">Breakdown of attempt to load</span></span>

<span data-ttu-id="31394-153">読み込み操作の詳細な内訳については、左側のイベント一覧を使用し、ビューをフィルター処理して `Microsoft-Windows-DotNETRuntime/AssemblyLoader` 以下の [`ResolutionAttempted` イベント](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event)を表示します。</span><span class="sxs-lookup"><span data-stu-id="31394-153">For a more detailed breakdown of the load operation, filter the view to the [`ResolutionAttempted` events](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event) under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="31394-154">列 `AssemblyName`、`Stage`、および `Result` をビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="31394-154">Add the columns `AssemblyName`, `Stage`, and `Result` to the view.</span></span> <span data-ttu-id="31394-155">フィルター処理して、`Start`/`Stop` ペアのうち、そのアクティビティ ID を持つイベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="31394-155">Filter to events with the activity ID from the `Start`/`Stop` pair.</span></span>

:::image type="content" source="media/collect-details/resolution-attempted.png" alt-text="PerfView の ResolutionAttempted イベントの画像":::

| <span data-ttu-id="31394-157">イベント名</span><span class="sxs-lookup"><span data-stu-id="31394-157">Event Name</span></span>                           | <span data-ttu-id="31394-158">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31394-158">AssemblyName</span></span>                                      | <span data-ttu-id="31394-159">段階</span><span class="sxs-lookup"><span data-stu-id="31394-159">Stage</span></span>                               | <span data-ttu-id="31394-160">結果</span><span class="sxs-lookup"><span data-stu-id="31394-160">Result</span></span>             |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AppDomainAssemblyResolveEvent`     | `AssemblyNotFound` |

<span data-ttu-id="31394-161">上記のイベントは、アセンブリ ローダーによって、現在の読み込みコンテキストが確認され、マネージド アプリケーション アセンブリの既定のプローブ ロジックが実行され、<xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> イベントのハンドラーが呼び出され、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> のハンドラーを呼び出されるという手順で、アセンブリの解決が試行されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="31394-161">The events above indicate that the assembly loader attempted to resolve the assembly by looking in the current load context, running the default probing logic for managed application assemblies, invoking handlers for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event, and invoking handlers for the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.</span></span> <span data-ttu-id="31394-162">これらすべての手順を実行しても、アセンブリは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="31394-162">For all of these steps, the assembly was not found.</span></span>

### <a name="extension-points"></a><span data-ttu-id="31394-163">拡張ポイント</span><span class="sxs-lookup"><span data-stu-id="31394-163">Extension points</span></span>

<span data-ttu-id="31394-164">呼び出された拡張ポイントを確認するには、左側のイベント一覧を使用し、ビューをフィルター処理して `Microsoft-Windows-DotNETRuntime/AssemblyLoader` 以下の [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) および [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) を表示します。</span><span class="sxs-lookup"><span data-stu-id="31394-164">To see which extension points were invoked, filter the view to the [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) and [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) under `Microsoft-Windows-DotNETRuntime/AssemblyLoader` using the event list on the left.</span></span> <span data-ttu-id="31394-165">列 `AssemblyName` および `HandlerName` をビューに追加します。</span><span class="sxs-lookup"><span data-stu-id="31394-165">Add the columns `AssemblyName` and `HandlerName` to the view.</span></span> <span data-ttu-id="31394-166">フィルター処理して、`Start`/`Stop` ペアのうち、そのアクティビティ ID を持つイベントを表示します。</span><span class="sxs-lookup"><span data-stu-id="31394-166">Filter to events with the activity ID from the `Start`/`Stop` pair.</span></span>

:::image type="content" source="media/collect-details/extension-point.png" alt-text="PerfView の拡張ポイント イベントの画像":::

| <span data-ttu-id="31394-168">イベント名</span><span class="sxs-lookup"><span data-stu-id="31394-168">Event Name</span></span>                                                  | <span data-ttu-id="31394-169">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31394-169">AssemblyName</span></span>                                      | <span data-ttu-id="31394-170">HandlerName</span><span class="sxs-lookup"><span data-stu-id="31394-170">HandlerName</span></span>                      |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` |
| `AssemblyLoader/AppDomainAssemblyResolveHandlerInvoked`     | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAppDomainAssemblyResolve`     |

<span data-ttu-id="31394-171">上記のイベントは、`OnAssemblyLoadContextResolving` という名前のハンドラーが <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> イベントに対して呼び出され、`OnAppDomainAssemblyResolve` という名前のハンドラーが <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> イベントに対して呼び出されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="31394-171">The events above indicate that a handler named `OnAssemblyLoadContextResolving` was invoked for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event and a handler named `OnAppDomainAssemblyResolve` was invoked for the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

### <a name="collect-another-trace"></a><span data-ttu-id="31394-172">別のトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="31394-172">Collect another trace</span></span>

<span data-ttu-id="31394-173"><xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> イベントのハンドラーによって `MyLibrary` アセンブリが読み込まれるように、引数を指定してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="31394-173">Run the application with arguments such that its handler for the <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> event will load the `MyLibrary` assembly.</span></span>

```console
AssemblyLoading /d default alc-resolving
```

<span data-ttu-id="31394-174">[上記の手順](#collect-the-trace)を使用して、別の `.nettrace` ファイルを収集して開きます。</span><span class="sxs-lookup"><span data-stu-id="31394-174">Collect and open another `.nettrace` file using the [steps from above](#collect-the-trace).</span></span>

<span data-ttu-id="31394-175">フィルター処理して `MyLibrary` の `Start` および `Stop` イベントをもう一度表示します。</span><span class="sxs-lookup"><span data-stu-id="31394-175">Filter to the `Start` and `Stop` events for `MyLibrary` again.</span></span> <span data-ttu-id="31394-176">`Start`/`Stop` のペアとその間に別の `Start`/`Stop` があります。</span><span class="sxs-lookup"><span data-stu-id="31394-176">You should see a `Start`/`Stop` pair with another `Start`/`Stop` between them.</span></span> <span data-ttu-id="31394-177">内側にある読み込み操作は、<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType> が呼び出されたときに <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> のハンドラーによってトリガーされた読み込みを表します。</span><span class="sxs-lookup"><span data-stu-id="31394-177">The inner load operation represents the load triggered by the handler for <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> when it called <xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="31394-178">今回は、`Stop` イベントに `Success=True` があります。これは読み込み操作が成功したことを示しています。</span><span class="sxs-lookup"><span data-stu-id="31394-178">This time, you should see `Success=True` on the `Stop` event, indicating the load operation succeeded.</span></span> <span data-ttu-id="31394-179">`ResultAssemblyPath` フィールドには、結果のアセンブリのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31394-179">The `ResultAssemblyPath` field shows the path of the resulting assembly.</span></span>

:::image type="content" source="media/collect-details/start-stop-success.png" alt-text="PerfView の成功した開始および停止イベントの画像":::

| <span data-ttu-id="31394-181">イベント名</span><span class="sxs-lookup"><span data-stu-id="31394-181">Event Name</span></span>             | <span data-ttu-id="31394-182">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31394-182">AssemblyName</span></span>                                                       | <span data-ttu-id="31394-183">ActivityID</span><span class="sxs-lookup"><span data-stu-id="31394-183">ActivityID</span></span> | <span data-ttu-id="31394-184">成功</span><span class="sxs-lookup"><span data-stu-id="31394-184">Success</span></span> | <span data-ttu-id="31394-185">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="31394-185">ResultAssemblyPath</span></span>                                      |
| ---------------------- | ------------------------------------------------------------------ |------------|---------| ------------------------------------------------------- |
| `AssemblyLoader/Start` |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31394-186">//1/2/</span><span class="sxs-lookup"><span data-stu-id="31394-186">//1/2/</span></span>     |         |                                                         |
| `AssemblyLoader/Start` | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31394-187">//1/2/1/</span><span class="sxs-lookup"><span data-stu-id="31394-187">//1/2/1/</span></span>   |         |                                                         |
| `AssemblyLoader/Stop`  | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31394-188">//1/2/1/</span><span class="sxs-lookup"><span data-stu-id="31394-188">//1/2/1/</span></span>   | <span data-ttu-id="31394-189">True</span><span class="sxs-lookup"><span data-stu-id="31394-189">True</span></span>    | <span data-ttu-id="31394-190">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="31394-190">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |
| `AssemblyLoader/Stop`  |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | <span data-ttu-id="31394-191">//1/2/</span><span class="sxs-lookup"><span data-stu-id="31394-191">//1/2/</span></span>     | <span data-ttu-id="31394-192">True</span><span class="sxs-lookup"><span data-stu-id="31394-192">True</span></span>    | <span data-ttu-id="31394-193">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="31394-193">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="31394-194">次に、外側の読み込みのアクティビティ ID を持つ `ResolutionAttempted` イベントを調べて、アセンブリが正常に解決されたステップを判断できます。</span><span class="sxs-lookup"><span data-stu-id="31394-194">We can then look at the `ResolutionAttempted` events with the activity ID from the outer load to determine the step at which the assembly was successfully resolved.</span></span> <span data-ttu-id="31394-195">今回のイベントでは、`AssemblyLoadContextResolvingEvent` ステージが成功したことが示されます。</span><span class="sxs-lookup"><span data-stu-id="31394-195">This time, the events will show that the `AssemblyLoadContextResolvingEvent` stage was successful.</span></span> <span data-ttu-id="31394-196">`ResultAssemblyPath` フィールドには、結果のアセンブリのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31394-196">The `ResultAssemblyPath` field shows the path of the resulting assembly.</span></span>

:::image type="content" source="media/collect-details/resolution-attempted-success.png" alt-text="PerfView の成功した ResolutionAttempted イベントの画像":::

| <span data-ttu-id="31394-198">イベント名</span><span class="sxs-lookup"><span data-stu-id="31394-198">Event Name</span></span>                           | <span data-ttu-id="31394-199">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31394-199">AssemblyName</span></span>                                      | <span data-ttu-id="31394-200">段階</span><span class="sxs-lookup"><span data-stu-id="31394-200">Stage</span></span>                               | <span data-ttu-id="31394-201">結果</span><span class="sxs-lookup"><span data-stu-id="31394-201">Result</span></span>             | <span data-ttu-id="31394-202">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="31394-202">ResultAssemblyPath</span></span> |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `Success`          | <span data-ttu-id="31394-203">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="31394-203">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="31394-204">`AssemblyLoadContextResolvingHandlerInvoked` イベントを見ると、`OnAssemblyLoadContextResolving` という名前のハンドラーが呼び出されたことがわかります。</span><span class="sxs-lookup"><span data-stu-id="31394-204">Looking at `AssemblyLoadContextResolvingHandlerInvoked` events will show that the handler named `OnAssemblyLoadContextResolving` was invoked.</span></span> <span data-ttu-id="31394-205">`ResultAssemblyPath` フィールドには、ハンドラーから返されたアセンブリのパスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31394-205">The `ResultAssemblyPath` field shows the path of the assembly returned by the handler.</span></span>

:::image type="content" source="media/collect-details/extension-point-success.png" alt-text="PerfView の成功した拡張ポイント イベントの画像":::

| <span data-ttu-id="31394-207">イベント名</span><span class="sxs-lookup"><span data-stu-id="31394-207">Event Name</span></span>                                                  | <span data-ttu-id="31394-208">AssemblyName</span><span class="sxs-lookup"><span data-stu-id="31394-208">AssemblyName</span></span>                                      | <span data-ttu-id="31394-209">HandlerName</span><span class="sxs-lookup"><span data-stu-id="31394-209">HandlerName</span></span>                      | <span data-ttu-id="31394-210">ResultAssemblyPath</span><span class="sxs-lookup"><span data-stu-id="31394-210">ResultAssemblyPath</span></span> |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- | ------------------ |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` | <span data-ttu-id="31394-211">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span><span class="sxs-lookup"><span data-stu-id="31394-211">*C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll*</span></span> |

<span data-ttu-id="31394-212"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> イベントを発生させる読み込みアルゴリズムのステップに到達する前にアセンブリが正常に読み込まれたため、`AppDomainAssemblyResolveEvent` ステージまたは `AppDomainAssemblyResolveHandlerInvoked` イベントを伴う `ResolutionAttempted` イベントは存在しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="31394-212">Note that there is no longer a `ResolutionAttempted` event with the `AppDomainAssemblyResolveEvent` stage or any `AppDomainAssemblyResolveHandlerInvoked` events, as the assembly was successfully loaded before reaching the step of the loading algorithm that raises the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>

## <a name="see-also"></a><span data-ttu-id="31394-213">関連項目</span><span class="sxs-lookup"><span data-stu-id="31394-213">See also</span></span>

- [<span data-ttu-id="31394-214">アセンブリ ローダーのイベント</span><span class="sxs-lookup"><span data-stu-id="31394-214">Assembly loader events</span></span>](../../fundamentals/diagnostics/runtime-loader-binder-events.md)
- [<span data-ttu-id="31394-215">dotnet-トレース</span><span class="sxs-lookup"><span data-stu-id="31394-215">dotnet-trace</span></span>](../diagnostics/dotnet-trace.md)
- [<span data-ttu-id="31394-216">PerfView</span><span class="sxs-lookup"><span data-stu-id="31394-216">PerfView</span></span>](https://github.com/microsoft/perfview)
