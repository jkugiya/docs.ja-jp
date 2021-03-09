---
title: デッドロックのデバッグ - .NET Core
description: .NET Core でのロックに関する問題のデバッグについて説明するチュートリアルです。
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 0f5862c9acc4c1ae892caf29cea2ca484116cabf
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105585"
---
# <a name="debug-a-deadlock-in-net-core"></a><span data-ttu-id="d2775-103">.NET Core でデッドロックをデバッグする</span><span class="sxs-lookup"><span data-stu-id="d2775-103">Debug a deadlock in .NET Core</span></span>

<span data-ttu-id="d2775-104">**この記事の対象: ✔️** .NET Core 3.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="d2775-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="d2775-105">このチュートリアルでは、デッドロック シナリオをデバッグする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d2775-105">In this tutorial, you'll learn how to debug a deadlock scenario.</span></span> <span data-ttu-id="d2775-106">示されている例の [ASP.NET Core Web アプリ](/samples/dotnet/samples/diagnostic-scenarios) ソース コード リポジトリを使用して、デッドロックを意図的に発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="d2775-106">Using the provided example [ASP.NET Core web app](/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="d2775-107">エンドポイントでは、ハングとスレッドが蓄積します。</span><span class="sxs-lookup"><span data-stu-id="d2775-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="d2775-108">コア ダンプ、コア ダンプ分析、プロセス トレースなど、さまざまなツールを使用して問題を分析する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="d2775-108">You'll learn how you can use various tools to analyze the problem, such as core dumps, core dump analysis, and process tracing.</span></span>

<span data-ttu-id="d2775-109">このチュートリアルでは、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="d2775-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="d2775-110">アプリのハングを調査する</span><span class="sxs-lookup"><span data-stu-id="d2775-110">Investigate an app hang</span></span>
> - <span data-ttu-id="d2775-111">コア ダンプ ファイルを生成する</span><span class="sxs-lookup"><span data-stu-id="d2775-111">Generate a core dump file</span></span>
> - <span data-ttu-id="d2775-112">ダンプ ファイル内のプロセス スレッドを分析する</span><span class="sxs-lookup"><span data-stu-id="d2775-112">Analyze process threads in the dump file</span></span>
> - <span data-ttu-id="d2775-113">コールスタックと同期ブロックを分析する</span><span class="sxs-lookup"><span data-stu-id="d2775-113">Analyze callstacks and sync blocks</span></span>
> - <span data-ttu-id="d2775-114">デッドロックを診断して解決する</span><span class="sxs-lookup"><span data-stu-id="d2775-114">Diagnose and solve a deadlock</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2775-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d2775-115">Prerequisites</span></span>

<span data-ttu-id="d2775-116">このチュートリアルでは次のものを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2775-116">The tutorial uses:</span></span>

- <span data-ttu-id="d2775-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="d2775-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>
- <span data-ttu-id="d2775-118">シナリオをトリガーするための[サンプル デバッグ ターゲット - Web アプリ](/samples/dotnet/samples/diagnostic-scenarios)</span><span class="sxs-lookup"><span data-stu-id="d2775-118">[Sample debug target - web app](/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario</span></span>
- <span data-ttu-id="d2775-119">[dotnet-trace](dotnet-trace.md) を使ってプロセスを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="d2775-119">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="d2775-120">[dotnet-dump](dotnet-dump.md) を使ってダンプ ファイルを収集して分析する</span><span class="sxs-lookup"><span data-stu-id="d2775-120">[dotnet-dump](dotnet-dump.md) to collect, and analyze a dump file</span></span>

## <a name="core-dump-generation"></a><span data-ttu-id="d2775-121">コア ダンプ生成</span><span class="sxs-lookup"><span data-stu-id="d2775-121">Core dump generation</span></span>

<span data-ttu-id="d2775-122">アプリケーション無応答を調査するために、コア ダンプまたはメモリ ダンプを使用すると、そのスレッドの状態と、競合の問題が発生している可能性のあるすべてのロックを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="d2775-122">To investigate application unresponsiveness, a core dump or memory dump allows you to inspect the state of its threads and any possible locks that may have contention issues.</span></span> <span data-ttu-id="d2775-123">サンプルのルート ディレクトリから次のコマンドを使用して、[サンプル デバッグ](/samples/dotnet/samples/diagnostic-scenarios) アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="d2775-123">Run the [sample debug](/samples/dotnet/samples/diagnostic-scenarios) application using the following command from the sample root directory:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="d2775-124">このプロセス ID を検索するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2775-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="d2775-125">ご自分のコマンド出力からプロセス ID をメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="d2775-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="d2775-126">プロセス ID は `4807` でしたが、この ID は異なります。</span><span class="sxs-lookup"><span data-stu-id="d2775-126">Our process ID was `4807`, but yours will be different.</span></span> <span data-ttu-id="d2775-127">サンプル サイトの API エンドポイントである次の URL に移動します。</span><span class="sxs-lookup"><span data-stu-id="d2775-127">Navigate to the following URL, which is an API endpoint on the sample site:</span></span>

`https://localhost:5001/api/diagscenario/deadlock`

<span data-ttu-id="d2775-128">サイトへの API 要求がハングし、応答がありません。</span><span class="sxs-lookup"><span data-stu-id="d2775-128">The API request to the site will hang and not respond.</span></span> <span data-ttu-id="d2775-129">要求を約 10 から 15 秒間実行します。</span><span class="sxs-lookup"><span data-stu-id="d2775-129">Let the request run for about 10-15 seconds.</span></span> <span data-ttu-id="d2775-130">その後、次のコマンドを使用して、コア ダンプを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2775-130">Then create the core dump using the following command:</span></span>

### <a name="linux"></a>[<span data-ttu-id="d2775-131">Linux</span><span class="sxs-lookup"><span data-stu-id="d2775-131">Linux</span></span>](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[<span data-ttu-id="d2775-132">Windows</span><span class="sxs-lookup"><span data-stu-id="d2775-132">Windows</span></span>](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a><span data-ttu-id="d2775-133">コア ダンプを分析する</span><span class="sxs-lookup"><span data-stu-id="d2775-133">Analyze the core dump</span></span>

<span data-ttu-id="d2775-134">コア ダンプ分析を開始するには、次の `dotnet-dump analyze` コマンドを使用してコア ダンプを開きます。</span><span class="sxs-lookup"><span data-stu-id="d2775-134">To start the core dump analysis, open the core dump using the following `dotnet-dump analyze` command.</span></span> <span data-ttu-id="d2775-135">引数は、前に収集されたコア ダンプ ファイルへのパスです。</span><span class="sxs-lookup"><span data-stu-id="d2775-135">The argument is the path to the core dump file that was collected earlier.</span></span>

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

<span data-ttu-id="d2775-136">潜在的なハングを確認するため、プロセスのスレッド アクティビティの全体的な感触をつかむ必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2775-136">Since you're looking at a potential hang, you want an overall feel for the thread activity in the process.</span></span> <span data-ttu-id="d2775-137">次に示すように、`threads` コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2775-137">You can use the `threads` command as shown below:</span></span>

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

<span data-ttu-id="d2775-138">出力には、プロセスで現在実行中のすべてのスレッドが、関連付けられているデバッガーのスレッド ID およびオペレーティング システムのスレッド ID と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2775-138">The output shows all the threads currently running in the process with their associated debugger thread ID and operating system thread ID.</span></span> <span data-ttu-id="d2775-139">出力に基づいて、300 を超えるスレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="d2775-139">Based on the output, there are over 300 threads.</span></span>

<span data-ttu-id="d2775-140">次の手順では、各スレッドのコールスタックを取得することによって、スレッドがどのような処理を行っているかを正確に把握します。</span><span class="sxs-lookup"><span data-stu-id="d2775-140">The next step is to get a better understanding of what the threads are currently doing by getting each thread's callstack.</span></span> <span data-ttu-id="d2775-141">`clrstack` コマンドは、コールスタックを出力するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2775-141">The `clrstack` command can be used to output callstacks.</span></span> <span data-ttu-id="d2775-142">1 つのコールスタックまたはすべてのコールスタックを出力できます。</span><span class="sxs-lookup"><span data-stu-id="d2775-142">It can either output a single callstack or all the callstacks.</span></span> <span data-ttu-id="d2775-143">次のコマンドを使用して、プロセス内のすべてのスレッドのすべてのコールスタックを出力します。</span><span class="sxs-lookup"><span data-stu-id="d2775-143">Use the following command to output all the callstacks for all the threads in the process:</span></span>

```console
clrstack -all
```

<span data-ttu-id="d2775-144">出力の代表的な部分は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d2775-144">A representative portion of the output looks like:</span></span>

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

<span data-ttu-id="d2775-145">300 を超えるすべてのスレッドのコールスタックを観察すると、ほとんどのスレッドが共通のコールスタックを共有するパターンが示されます。</span><span class="sxs-lookup"><span data-stu-id="d2775-145">Observing the callstacks for all 300+ threads shows a pattern where a majority of the threads share a common callstack:</span></span>

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

<span data-ttu-id="d2775-146">コールスタックを見ると、要求がデッドロック メソッドに到達し、これによって `Monitor.ReliableEnter` が呼び出されているように見えます。</span><span class="sxs-lookup"><span data-stu-id="d2775-146">The callstack seems to show that the request arrived in our deadlock method that in turn makes a call to `Monitor.ReliableEnter`.</span></span> <span data-ttu-id="d2775-147">このメソッドは、スレッドによってモニター ロックが開始されようとしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="d2775-147">This method indicates that the threads are trying to enter a monitor lock.</span></span> <span data-ttu-id="d2775-148">これらは、ロックが利用可能になるのを待機しています。</span><span class="sxs-lookup"><span data-stu-id="d2775-148">They're waiting on the availability of the lock.</span></span> <span data-ttu-id="d2775-149">これは、別のスレッドによってロックされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d2775-149">It's likely locked by a different thread.</span></span>

<span data-ttu-id="d2775-150">次の手順では、実際にモニター ロックが保持されているスレッドを確認します。</span><span class="sxs-lookup"><span data-stu-id="d2775-150">The next step then is to find out which thread is actually holding the monitor lock.</span></span> <span data-ttu-id="d2775-151">通常、モニターではロック情報が同期ブロック テーブルに格納されるため、`syncblk` コマンドを使用して詳細情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d2775-151">Since monitors typically store lock information in the sync block table, we can use the `syncblk` command to get more information:</span></span>

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

<span data-ttu-id="d2775-152">2 つの興味深い列は、**MonitorHeld** と **Owning Thread Info** です。</span><span class="sxs-lookup"><span data-stu-id="d2775-152">The two interesting columns are **MonitorHeld** and **Owning Thread Info**.</span></span> <span data-ttu-id="d2775-153">**MonitorHeld** 列には、スレッドによってモニター ロックが取得されたかどうかと、待機中のスレッドの数が示されます。</span><span class="sxs-lookup"><span data-stu-id="d2775-153">The **MonitorHeld** column shows whether a monitor lock is acquired by a thread and the number of waiting threads.</span></span> <span data-ttu-id="d2775-154">**Owning Thread Info** 列には、モニター ロックが現在所有されているスレッドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2775-154">The **Owning Thread Info** column shows which thread currently owns the monitor lock.</span></span> <span data-ttu-id="d2775-155">スレッド情報には、3 つの異なるサブ列があります。</span><span class="sxs-lookup"><span data-stu-id="d2775-155">The thread info has three different subcolumns.</span></span> <span data-ttu-id="d2775-156">2 番目のサブ列には、オペレーティング システムのスレッド ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d2775-156">The second subcolumn shows operating system thread ID.</span></span>

<span data-ttu-id="d2775-157">この時点で、2 つの異なるスレッド (0x5634 と 0x51d4) にモニター ロックが保持されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="d2775-157">At this point, we know two different threads (0x5634 and 0x51d4) hold a monitor lock.</span></span> <span data-ttu-id="d2775-158">次の手順では、これらのスレッドによってどのような処理が行われているかを見ていきます。</span><span class="sxs-lookup"><span data-stu-id="d2775-158">The next step is to take a look at what those threads are doing.</span></span> <span data-ttu-id="d2775-159">それらにロックが保持されていて、無期限でスタックしているかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2775-159">We need to check if they're stuck indefinitely holding the lock.</span></span> <span data-ttu-id="d2775-160">`setthread` コマンドと `clrstack` コマンドを使用して各スレッドに切り替えて、コールスタックを表示してみましょう。</span><span class="sxs-lookup"><span data-stu-id="d2775-160">Let's use the `setthread` and `clrstack` commands to switch to each of the threads and display the callstacks.</span></span>

<span data-ttu-id="d2775-161">最初のスレッドを確認するには、`setthread` コマンドを実行し、0x5634 スレッドのインデックス (このインデックスは 28) を探します。</span><span class="sxs-lookup"><span data-stu-id="d2775-161">To look at the first thread, run the `setthread` command, and find the index of the 0x5634 thread (our index was 28).</span></span> <span data-ttu-id="d2775-162">デッドロック関数によってロックの取得が待機されていますが、既にロックが所有されています。</span><span class="sxs-lookup"><span data-stu-id="d2775-162">The deadlock function is waiting to acquire a lock, but it already owns the lock.</span></span> <span data-ttu-id="d2775-163">それは、既に保持されているロックを待機しているデッドロック内にあります。</span><span class="sxs-lookup"><span data-stu-id="d2775-163">It's in deadlock waiting for the lock it already holds.</span></span>

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

<span data-ttu-id="d2775-164">2 番目のスレッドも同様です。</span><span class="sxs-lookup"><span data-stu-id="d2775-164">The second thread is similar.</span></span> <span data-ttu-id="d2775-165">ここでも既に所有しているロックの取得が試みられています。</span><span class="sxs-lookup"><span data-stu-id="d2775-165">It's also trying to acquire a lock that it already owns.</span></span> <span data-ttu-id="d2775-166">待機中の 300 を超える残りのスレッドによっても、デッドロックの原因となったいずれかのロックが待機されている可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="d2775-166">The remaining 300+ threads that are all waiting are most likely also waiting on one of the locks that caused the deadlock.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2775-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2775-167">See also</span></span>

- <span data-ttu-id="d2775-168">[dotnet-trace](dotnet-trace.md) を使ってプロセスを一覧表示する</span><span class="sxs-lookup"><span data-stu-id="d2775-168">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="d2775-169">[dotnet-counters](dotnet-counters.md) を使ってマネージド メモリ使用量を確認する</span><span class="sxs-lookup"><span data-stu-id="d2775-169">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="d2775-170">[dotnet-dump](dotnet-dump.md) を使ってダンプ ファイルを収集して分析する</span><span class="sxs-lookup"><span data-stu-id="d2775-170">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="d2775-171">dotnet/診断</span><span class="sxs-lookup"><span data-stu-id="d2775-171">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="d2775-172">次の手順</span><span class="sxs-lookup"><span data-stu-id="d2775-172">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d2775-173">.NET Core で使用できる診断ツール</span><span class="sxs-lookup"><span data-stu-id="d2775-173">What diagnostic tools are available in .NET Core</span></span>](index.md)
