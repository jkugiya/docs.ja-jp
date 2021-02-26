---
title: EventPipe の概要
description: EventPipe について、およびそれを使用して .NET アプリケーションをトレースし、パフォーマンスの問題を診断する方法について説明します。
ms.date: 11/09/2020
ms.topic: overview
ms.openlocfilehash: f315beafabbd99bf78647b3f714fd76d93fcac28
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2021
ms.locfileid: "100582978"
---
# <a name="eventpipe"></a><span data-ttu-id="37996-103">EventPipe</span><span class="sxs-lookup"><span data-stu-id="37996-103">EventPipe</span></span>

<span data-ttu-id="37996-104">EventPipe は、ETW や LTTng と同様に、トレース データを収集するために使用できるランタイム コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="37996-104">EventPipe is a runtime component that can be used to collect tracing data, similar to ETW or LTTng.</span></span> <span data-ttu-id="37996-105">EventPipe の目的は、.NET 開発者が、ETW や LTTng などのプラットフォーム固有の OS ネイティブ コンポーネントに依存することなく、簡単に .NET アプリケーションをトレースできるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="37996-105">The goal of EventPipe is to allow .NET developers to easily trace their .NET applications without having to rely on platform-specific OS-native components such as ETW or LTTng.</span></span>

<span data-ttu-id="37996-106">EventPipe は多くの診断ツールの背後にあるメカニズムです。これを使用することで、ランタイムによって生成されたイベントや、[EventSource](xref:System.Diagnostics.Tracing.EventSource) で記述されたカスタム イベントを利用できます。</span><span class="sxs-lookup"><span data-stu-id="37996-106">EventPipe is the mechanism behind many of the diagnostic tools and can be used for consuming events emitted by the runtime as well as custom events written with [EventSource](xref:System.Diagnostics.Tracing.EventSource).</span></span>

<span data-ttu-id="37996-107">この記事では、EventPipe の概要を示します。EventPipe をどのような場合にどのような方法で使用するか、および実際のニーズに合わせて最適に構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="37996-107">This article is a high-level overview of EventPipe describing when and how to use EventPipe, and how to configure it to best suit your needs.</span></span>

## <a name="eventpipe-basics"></a><span data-ttu-id="37996-108">EventPipe の基本</span><span class="sxs-lookup"><span data-stu-id="37996-108">EventPipe basics</span></span>

<span data-ttu-id="37996-109">EventPipe により、ランタイム コンポーネント (たとえば、Just-In-Time コンパイラまたはガベージ コレクター) によって生成されたイベントと、ライブラリおよびユーザー コード内の [EventSource](xref:System.Diagnostics.Tracing.EventSource) インスタンスから書き込まれたイベントが集約されます。</span><span class="sxs-lookup"><span data-stu-id="37996-109">EventPipe aggregates events emitted by runtime components - for example, the Just-In-Time compiler or the garbage collector - and events written from [EventSource](xref:System.Diagnostics.Tracing.EventSource) instances in the libraries and user code.</span></span>

<span data-ttu-id="37996-110">その後、イベントはシリアル化され、ファイルに直接書き込むか、診断ポートを介してアウトプロセスから利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="37996-110">The events are then serialized and can be written directly to a file or consumed through a Diagnostics Port from out-of-proces.</span></span> <span data-ttu-id="37996-111">Windows では、診断ポートは `NamedPipe` として実装されます。</span><span class="sxs-lookup"><span data-stu-id="37996-111">On Windows, Diagnostic Ports are implemented as `NamedPipe`s.</span></span> <span data-ttu-id="37996-112">Linux や macOS など、Windows 以外のプラットフォームでは、Unix ドメイン ソケットを使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="37996-112">On non-Windows platforms, such as Linux or macOS, it is implemented using Unix Domain Sockets.</span></span> <span data-ttu-id="37996-113">診断ポートと、カスタムのプロセス間通信プロトコルを使用してそれを操作する方法の詳細については、[診断 IPC プロトコルのドキュメント](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37996-113">For more information about the Diagnostics Port and how to interact with it via its custom inter-process communication protocol, see the [diagnostics IPC protocol documentation](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).</span></span>

<span data-ttu-id="37996-114">次に、シリアル化されたイベントが、EventPipe によって `.nettrace` ファイル形式で (診断ポートを介してストリームとして、またはファイルへの直接書き込みで) 書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="37996-114">EventPipe then writes the serialized events in the `.nettrace` file format, either as a stream via Diagnostic Ports or directly to a file.</span></span> <span data-ttu-id="37996-115">EventPipe のシリアル化形式の詳細については、[EventPipe 形式のドキュメント](https://github.com/microsoft/perfview/blob/master/src/TraceEvent/EventPipe/EventPipeFormat.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37996-115">To learn more about the EventPipe serialization format, refer to the [EventPipe format documentation](https://github.com/microsoft/perfview/blob/master/src/TraceEvent/EventPipe/EventPipeFormat.md).</span></span>

## <a name="eventpipe-vs-etwlttng"></a><span data-ttu-id="37996-116">EventPipe と、ETW または LTTng</span><span class="sxs-lookup"><span data-stu-id="37996-116">EventPipe vs. ETW/LTTng</span></span>

<span data-ttu-id="37996-117">EventPipe は .NET ランタイム (CoreCLR) の一部であり、.NET Core でサポートされるすべてのプラットフォームで同じように動作するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="37996-117">EventPipe is part of the .NET runtime (CoreCLR) and is designed to work the same way across all the platforms .NET Core supports.</span></span> <span data-ttu-id="37996-118">これにより複数のプラットフォーム間で、`dotnet-counters`、`dotnet-gcdump`、`dotnet-trace` などの EventPipe に基づくトレース ツールのシームレスな動作が実現します。</span><span class="sxs-lookup"><span data-stu-id="37996-118">This allows tracing tools based on EventPipe, such as `dotnet-counters`, `dotnet-gcdump`, and `dotnet-trace`, to work seamlessly across platforms.</span></span>

<span data-ttu-id="37996-119">ただし、EventPipe はランタイムの組み込みコンポーネントであるため、そのスコープはマネージド コードとランタイム自体に限定されます。</span><span class="sxs-lookup"><span data-stu-id="37996-119">However, because EventPipe is a runtime built-in component, its scope is limited to managed code and the runtime itself.</span></span> <span data-ttu-id="37996-120">EventPipe は、ネイティブ コード スタックの解決やさまざまなカーネル イベントの取得といった下位レベルのイベントの追跡には使用できません。</span><span class="sxs-lookup"><span data-stu-id="37996-120">EventPipe cannot be used for tracking some lower-level events, such as resolving native code stack or getting various kernel events.</span></span> <span data-ttu-id="37996-121">アプリで C または C++ の interop を使用するか、ランタイム自体 (C++ で記述されたもの) をトレースするか、カーネル イベント (つまり、ネイティブ スレッドのコンテキスト切り替えイベント) を必要とするアプリの動作についてより詳細な診断が必要な場合は、ETW、[perf、LTTng](./trace-perfcollect-lttng.md) のいずれかを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="37996-121">If you use C/C++ interop in your app or you want to trace the runtime itself (which is written in C++), or want deeper diagnostics into the behavior of the app that requires kernel events (that is, native-thread context-switching events) you should use ETW or [perf/LTTng](./trace-perfcollect-lttng.md).</span></span>

<span data-ttu-id="37996-122">EventPipe と、ETW または LTTng とのもう 1 つの大きな違いは、管理者または root の特権の要件です。</span><span class="sxs-lookup"><span data-stu-id="37996-122">Another major difference between EventPipe and ETW/LTTng is admin/root privilege requirement.</span></span> <span data-ttu-id="37996-123">ETW または LTTng を使用してアプリケーションをトレースするには、管理者または root である必要があります。</span><span class="sxs-lookup"><span data-stu-id="37996-123">To trace an application using ETW or LTTng you need to be an admin/root.</span></span> <span data-ttu-id="37996-124">EventPipe を使用すると、トレーサー (`dotnet-trace` など) が、アプリケーションを起動したユーザーと同じユーザーとして実行されている限り、アプリケーションをトレースできます。</span><span class="sxs-lookup"><span data-stu-id="37996-124">Using EventPipe, you can trace applications as long as the tracer (for example, `dotnet-trace`) is run as the same user as the user that launched the application.</span></span>

<span data-ttu-id="37996-125">次の表に、EventPipe、ETW、LTTng の違いの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="37996-125">The following table is a summary of the differences between EventPipe and ETW/LTTng.</span></span>

|<span data-ttu-id="37996-126">機能</span><span class="sxs-lookup"><span data-stu-id="37996-126">Feature</span></span>|<span data-ttu-id="37996-127">EventPipe</span><span class="sxs-lookup"><span data-stu-id="37996-127">EventPipe</span></span>|<span data-ttu-id="37996-128">ETW</span><span class="sxs-lookup"><span data-stu-id="37996-128">ETW</span></span>|<span data-ttu-id="37996-129">LTTng</span><span class="sxs-lookup"><span data-stu-id="37996-129">LTTng</span></span>|
|-------|---------|---|-----------|
|<span data-ttu-id="37996-130">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="37996-130">Cross-platform</span></span>|<span data-ttu-id="37996-131">はい</span><span class="sxs-lookup"><span data-stu-id="37996-131">Yes</span></span>|<span data-ttu-id="37996-132">いいえ (Windows のみ)</span><span class="sxs-lookup"><span data-stu-id="37996-132">No (only on Windows)</span></span>|<span data-ttu-id="37996-133">いいえ (サポートされている Linux ディストリビューションのみ)</span><span class="sxs-lookup"><span data-stu-id="37996-133">No (only on supported Linux distros)</span></span>|
|<span data-ttu-id="37996-134">管理者または root の特権が必要</span><span class="sxs-lookup"><span data-stu-id="37996-134">Require admin/root privilege</span></span>|<span data-ttu-id="37996-135">いいえ</span><span class="sxs-lookup"><span data-stu-id="37996-135">No</span></span>|<span data-ttu-id="37996-136">はい</span><span class="sxs-lookup"><span data-stu-id="37996-136">Yes</span></span>|<span data-ttu-id="37996-137">はい</span><span class="sxs-lookup"><span data-stu-id="37996-137">Yes</span></span>|
|<span data-ttu-id="37996-138">OS またはカーネル イベントを取得できる</span><span class="sxs-lookup"><span data-stu-id="37996-138">Can get OS/kernel events</span></span>|<span data-ttu-id="37996-139">いいえ</span><span class="sxs-lookup"><span data-stu-id="37996-139">No</span></span>|<span data-ttu-id="37996-140">はい</span><span class="sxs-lookup"><span data-stu-id="37996-140">Yes</span></span>|<span data-ttu-id="37996-141">はい</span><span class="sxs-lookup"><span data-stu-id="37996-141">Yes</span></span>|
|<span data-ttu-id="37996-142">ネイティブの呼び出し履歴を解決できる</span><span class="sxs-lookup"><span data-stu-id="37996-142">Can resolve native callstacks</span></span>|<span data-ttu-id="37996-143">いいえ</span><span class="sxs-lookup"><span data-stu-id="37996-143">No</span></span>|<span data-ttu-id="37996-144">はい</span><span class="sxs-lookup"><span data-stu-id="37996-144">Yes</span></span>|<span data-ttu-id="37996-145">はい</span><span class="sxs-lookup"><span data-stu-id="37996-145">Yes</span></span>|

## <a name="use-eventpipe-to-trace-your-net-application"></a><span data-ttu-id="37996-146">EventPipe を使用して .NET アプリケーションをトレースする</span><span class="sxs-lookup"><span data-stu-id="37996-146">Use EventPipe to trace your .NET application</span></span>

<span data-ttu-id="37996-147">EventPipe を使用すると、さまざまな方法で .NET アプリケーションをトレースできます。</span><span class="sxs-lookup"><span data-stu-id="37996-147">You can use EventPipe to trace your .NET application in many ways:</span></span>

* <span data-ttu-id="37996-148">EventPipe の上に構築された[診断ツール](#tools-that-use-eventpipe)のどれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="37996-148">Use one of the [diagnostics tools](#tools-that-use-eventpipe) that are built on top of EventPipe.</span></span>

* <span data-ttu-id="37996-149">[Microsoft.Diagnostics.NETCore.Client](https://github.com/dotnet/diagnostics/blob/master/documentation/diagnostics-client-library-instructions.md) ライブラリを使用して、EventPipe セッションを構成して開始するための独自のツールを自分で作成します。</span><span class="sxs-lookup"><span data-stu-id="37996-149">Use [Microsoft.Diagnostics.NETCore.Client](https://github.com/dotnet/diagnostics/blob/master/documentation/diagnostics-client-library-instructions.md) library to write your own tool to configure and start EventPipe sessions yourself.</span></span>

* <span data-ttu-id="37996-150">[環境変数](#trace-using-environment-variables)を使用して EventPipe を開始します。</span><span class="sxs-lookup"><span data-stu-id="37996-150">Use [environment variables](#trace-using-environment-variables) to start EventPipe.</span></span>

<span data-ttu-id="37996-151">EventPipe イベントを含む `nettrace` ファイルを作成した後、[`PerfView`](https://github.com/Microsoft/perfview#perfview-overview) または Visual Studio でそのファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="37996-151">After you've produced a `nettrace` file that contains your EventPipe events, you can view the file in [`PerfView`](https://github.com/Microsoft/perfview#perfview-overview) or Visual Studio.</span></span> <span data-ttu-id="37996-152">Windows 以外のプラットフォームでは、[`dotnet-trace convert`](./dotnet-trace.md#dotnet-trace-convert) コマンドを使用して `nettrace` ファイルを `speedscope` または `Chromium` トレース形式に変換し、[`speedscope`](https://www.speedscope.app/) または Chrome DevTools を使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="37996-152">On non-Windows platforms, you can convert the `nettrace` file to a `speedscope` or `Chromium` trace format by using [`dotnet-trace convert`](./dotnet-trace.md#dotnet-trace-convert) command and view it with [`speedscope`](https://www.speedscope.app/) or Chrome DevTools.</span></span>

<span data-ttu-id="37996-153">[TraceEvent](https://github.com/Microsoft/perfview/blob/master/documentation/TraceEvent/TraceEventLibrary.md) を使用してプログラムで EventPipe トレースを分析することもできます。</span><span class="sxs-lookup"><span data-stu-id="37996-153">You can also analyze EventPipe traces programmatically with [TraceEvent](https://github.com/Microsoft/perfview/blob/master/documentation/TraceEvent/TraceEventLibrary.md).</span></span>

### <a name="tools-that-use-eventpipe"></a><span data-ttu-id="37996-154">EventPipe を使用するツール</span><span class="sxs-lookup"><span data-stu-id="37996-154">Tools that use EventPipe</span></span>

<span data-ttu-id="37996-155">これは EventPipe を使用してアプリケーションをトレースする最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="37996-155">This is the easiest way to use EventPipe to trace your application.</span></span> <span data-ttu-id="37996-156">これらの各ツールの使用方法の詳細については、各ツールのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37996-156">To learn more about how to use each of these tools, refer to each tool's documentation.</span></span>

* <span data-ttu-id="37996-157">[dotnet-counters](./dotnet-counters.md) を使用すると、.NET ランタイムとコア ライブラリによって生成されるさまざまなメトリックに加えて、自分で作成できるカスタム メトリックを監視および収集することができます。</span><span class="sxs-lookup"><span data-stu-id="37996-157">[dotnet-counters](./dotnet-counters.md) lets you monitor and collect various metrics emitted by the .NET runtime and core libraries, as well as custom metrics you can write.</span></span>

* <span data-ttu-id="37996-158">[dotnet-gcdump](./dotnet-gcdump.md) を使用すると、アプリケーションのマネージド ヒープを分析するためにライブ プロセスの GC ヒープ ダンプを収集できます。</span><span class="sxs-lookup"><span data-stu-id="37996-158">[dotnet-gcdump](./dotnet-gcdump.md) lets you collect GC heap dumps of live processes for analyzing an application's managed heap.</span></span>

* <span data-ttu-id="37996-159">[dotnet-trace](./dotnet-trace.md) を使用すると、パフォーマンスを分析するためにアプリケーションのトレースを収集できます。</span><span class="sxs-lookup"><span data-stu-id="37996-159">[dotnet-trace](./dotnet-trace.md) lets you collect traces of applications to analyze for performance.</span></span>

## <a name="trace-using-environment-variables"></a><span data-ttu-id="37996-160">環境変数を使用したトレース</span><span class="sxs-lookup"><span data-stu-id="37996-160">Trace using environment variables</span></span>

<span data-ttu-id="37996-161">EventPipe を使用する場合の好ましい方法は、`dotnet-trace` または `Microsoft.Diagnostics.NETCore.Client` ライブラリを使用することです。</span><span class="sxs-lookup"><span data-stu-id="37996-161">The preferred mechanism for using EventPipe is to use `dotnet-trace` or the `Microsoft.Diagnostics.NETCore.Client` library.</span></span>

<span data-ttu-id="37996-162">ただし、次の環境変数を使用すると、アプリで EventPipe セッションを設定し、それによってトレースをファイルに直接書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="37996-162">However, you can use the following environment variables to set up an EventPipe session on an app and have it write the trace directly to a file.</span></span> <span data-ttu-id="37996-163">トレースを停止するには、アプリケーションを終了します。</span><span class="sxs-lookup"><span data-stu-id="37996-163">To stop tracing, exit the application.</span></span>

* <span data-ttu-id="37996-164">`COMPlus_EnableEventPipe`: ファイルに直接書き込む EventPipe セッションを開始するには、これを `1` に設定します。</span><span class="sxs-lookup"><span data-stu-id="37996-164">`COMPlus_EnableEventPipe`: Set this to `1` to start an EventPipe session that writes directly to a file.</span></span> <span data-ttu-id="37996-165">既定値は `0` です。</span><span class="sxs-lookup"><span data-stu-id="37996-165">The default value is `0`.</span></span>

* <span data-ttu-id="37996-166">`COMPlus_EventPipeOutputPath`: EventPipe が `COMPlus_EnableEventPipe` を介して実行するように構成されている場合に、その出力となるトレース ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="37996-166">`COMPlus_EventPipeOutputPath`: The path to the output EventPipe trace file when it's configured to run via `COMPlus_EnableEventPipe`.</span></span> <span data-ttu-id="37996-167">既定値は `trace.nettrace` です。これは、アプリが実行されているのと同じディレクトリに作成されます。</span><span class="sxs-lookup"><span data-stu-id="37996-167">The default value is `trace.nettrace`, which will be created in the same directory that the app is running from.</span></span>

* <span data-ttu-id="37996-168">`COMPlus_CircularBufferMB`: EventPipe が `COMPlus_EnableEventPipe` を介して実行するように構成されている場合に使用される内部バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="37996-168">`COMPlus_CircularBufferMB`: The size of the internal buffer that is used by EventPipe when it's configured to run via `COMPlus_EnableEventPipe`.</span></span>

* <span data-ttu-id="37996-169">`COMPlus_EventPipeConfig`: `COMPlus_EnableEventPipe` を使用して EventPipe セッションを開始するときに、EventPipe セッション構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="37996-169">`COMPlus_EventPipeConfig`: Sets up the EventPipe session configuration when starting an EventPipe session with `COMPlus_EnableEventPipe`.</span></span>

  <span data-ttu-id="37996-170">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="37996-170">The syntax is as follows:</span></span>

  `<provider>:<keyword>:<level>`

  <span data-ttu-id="37996-171">コンマで連結することによって複数のプロバイダーを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="37996-171">You can also specify multiple providers by concatenating them with a comma:</span></span>

  `<provider1>:<keyword1>:<level1>,<provider2>:<keyword2>:<level2>`

  <span data-ttu-id="37996-172">この環境変数が設定されていないが、EventPipe が `COMPlus_EnableEventPipe` によって有効になる場合は、次に示すキーワードとレベルを使用して次のプロバイダーを有効にすることでトレースが開始されます。</span><span class="sxs-lookup"><span data-stu-id="37996-172">If this environment variable is not set but EventPipe is enabled by `COMPlus_EnableEventPipe`, it will start tracing by enabling the following providers with the following keywords and levels:</span></span>

  - `Microsoft-Windows-DotNETRuntime:4c14fccbd:5`
  - `Microsoft-Windows-DotNETRuntimePrivate:4002000b:5`
  - `Microsoft-DotNETCore-SampleProfiler:0:5`

  <span data-ttu-id="37996-173">.NET でのいくつかの既知のプロバイダーの詳細については、[既知のイベント プロバイダー](./well-known-event-providers.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37996-173">To learn more about some of the well-known providers in .NET, refer to [Well-known Event Providers](./well-known-event-providers.md).</span></span>
