---
title: ログとトレース - .NET Core
description: .NET Core のログとトレースの概要について説明します。
ms.date: 10/12/2020
ms.openlocfilehash: a8c6d82ddb7bc3f8b4cc9eae9dd7aaf65732a0b8
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548396"
---
# <a name="net-core-logging-and-tracing"></a><span data-ttu-id="7cafb-103">.NET Core のログとトレース</span><span class="sxs-lookup"><span data-stu-id="7cafb-103">.NET Core logging and tracing</span></span>

<span data-ttu-id="7cafb-104">ログとトレースは、実際には同じ手法の 2 つの名前です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-104">Logging and tracing are really two names for the same technique.</span></span> <span data-ttu-id="7cafb-105">コンピューターの初期の頃から、単純な手法が使用されています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-105">The simple technique has been used since the early days of computers.</span></span> <span data-ttu-id="7cafb-106">アプリケーションをインストルメント化して、後で使用するために出力を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-106">It simply involves instrumenting an application to write output to be consumed later.</span></span>

## <a name="reasons-to-use-logging-and-tracing"></a><span data-ttu-id="7cafb-107">ログとトレースを使用する理由</span><span class="sxs-lookup"><span data-stu-id="7cafb-107">Reasons to use logging and tracing</span></span>

<span data-ttu-id="7cafb-108">この単純な手法は、驚くほど強力です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-108">This simple technique is surprisingly powerful.</span></span> <span data-ttu-id="7cafb-109">これは、次のようなデバッガーでは対応できない場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-109">It can be used in situations where a debugger fails:</span></span>

- <span data-ttu-id="7cafb-110">長期間にわたって発生する問題は、従来のデバッガーでデバッグするのが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7cafb-110">Issues occurring over long periods of time, can be difficult to debug with a traditional debugger.</span></span> <span data-ttu-id="7cafb-111">ログを使用すると、長期間にわたる詳細な事後分析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-111">Logs allow for detailed post-mortem review spanning long periods of time.</span></span> <span data-ttu-id="7cafb-112">これに対し、デバッガーはリアルタイム分析に制約されます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-112">In contrast, debuggers are constrained to real-time analysis.</span></span>
- <span data-ttu-id="7cafb-113">多くの場合、マルチスレッド アプリケーションと分散アプリケーションはデバッグが困難です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-113">Multi-threaded applications and distributed applications are often difficult to debug.</span></span>  <span data-ttu-id="7cafb-114">デバッガーをアタッチすると、動作が変更される傾向があります。</span><span class="sxs-lookup"><span data-stu-id="7cafb-114">Attaching a debugger tends to modify behaviors.</span></span> <span data-ttu-id="7cafb-115">必要に応じて詳細ログを分析することで、複雑なシステムを理解できます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-115">Detailed logs can be analyzed as needed to understand complex systems.</span></span>
- <span data-ttu-id="7cafb-116">分散アプリケーションの問題は、多くのコンポーネント間の複雑な相互作用によって生じる可能性があり、デバッガーをシステムのすべての部分に接続するのは合理的でない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7cafb-116">Issues in distributed applications may arise from a complex interaction between many components and it may not be reasonable to connect a debugger to every part of the system.</span></span>
- <span data-ttu-id="7cafb-117">多くのサービスは停止することができません。</span><span class="sxs-lookup"><span data-stu-id="7cafb-117">Many services shouldn't be stalled.</span></span> <span data-ttu-id="7cafb-118">デバッガーをアタッチすると、多くの場合、タイムアウト エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7cafb-118">Attaching a debugger often causes timeout failures.</span></span>
- <span data-ttu-id="7cafb-119">問題は常に予測できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="7cafb-119">Issues aren't always foreseen.</span></span> <span data-ttu-id="7cafb-120">ログとトレースは、問題が発生した場合に備えてプログラムで常に記録できるように、オーバーヘッドが低くなるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-120">Logging and tracing are designed for low overhead so that programs can always be recording in case an issue occurs.</span></span>

## <a name="net-core-apis"></a><span data-ttu-id="7cafb-121">.NET Core API</span><span class="sxs-lookup"><span data-stu-id="7cafb-121">.NET Core APIs</span></span>

### <a name="print-style-apis"></a><span data-ttu-id="7cafb-122">出力スタイルの API</span><span class="sxs-lookup"><span data-stu-id="7cafb-122">Print style APIs</span></span>

<span data-ttu-id="7cafb-123"><xref:System.Console?displayProperty=nameWithType>、<xref:System.Diagnostics.Trace?displayProperty=nameWithType>、および <xref:System.Diagnostics.Debug?displayProperty=nameWithType> クラスはそれぞれ、ログ記録に便利な出力スタイルの API を備えています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-123">The <xref:System.Console?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes each provide similar print style APIs convenient for logging.</span></span>

<span data-ttu-id="7cafb-124">どの出力スタイル API を使用するかは、ユーザーが決定します。</span><span class="sxs-lookup"><span data-stu-id="7cafb-124">The choice of which print style API to use is up to you.</span></span> <span data-ttu-id="7cafb-125">主な違いを次に示します。</span><span class="sxs-lookup"><span data-stu-id="7cafb-125">The key differences are:</span></span>

- <xref:System.Console?displayProperty=nameWithType>
  - <span data-ttu-id="7cafb-126">常に有効であり、常にコンソールに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-126">Always enabled and always writes to the console.</span></span>
  - <span data-ttu-id="7cafb-127">顧客がリリースで参照する必要のある情報の場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-127">Useful for information that your customer may need to see in the release.</span></span>
  - <span data-ttu-id="7cafb-128">最も簡単な方法であるため、アドホックな一時デバッグによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-128">Because it's the simplest approach, it's often used for ad-hoc temporary debugging.</span></span> <span data-ttu-id="7cafb-129">このデバッグ コードは、多くの場合、ソース管理にチェックインされません。</span><span class="sxs-lookup"><span data-stu-id="7cafb-129">This debug code is often never checked in to source control.</span></span>
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - <span data-ttu-id="7cafb-130">ソースに `#define TRACE` を追加するか、コンパイル時、オプション `/d:TRACE` を指定することで `TRACE` が定義されたときにのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-130">Only enabled when `TRACE` is defined by adding `#define TRACE` to your source or specifying the option `/d:TRACE` when compiling.</span></span>
  - <span data-ttu-id="7cafb-131">アタッチされている <xref:System.Diagnostics.Trace.Listeners> (既定では <xref:System.Diagnostics.DefaultTraceListener>) に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-131">Writes to attached <xref:System.Diagnostics.Trace.Listeners>, by default the <xref:System.Diagnostics.DefaultTraceListener>.</span></span>
  - <span data-ttu-id="7cafb-132">ほとんどのビルドで有効になるログを作成するときに、この API を使用します。</span><span class="sxs-lookup"><span data-stu-id="7cafb-132">Use this API when creating logs that will be enabled in most builds.</span></span>
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - <span data-ttu-id="7cafb-133">ソースに `#define DEBUG` を追加するか、コンパイル時、オプション `/d:DEBUG` を指定することで `DEBUG` が定義されたときにのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-133">Only enabled when `DEBUG` is defined by adding `#define DEBUG` to your source or specifying the option `/d:DEBUG` when compiling.</span></span>
  - <span data-ttu-id="7cafb-134">アタッチされたデバッガーに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-134">Writes to an attached debugger.</span></span>
  - <span data-ttu-id="7cafb-135">`*nix` では、`COMPlus_DebugWriteToStdErr` が設定されている場合は stderr に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-135">On `*nix` writes to stderr if `COMPlus_DebugWriteToStdErr` is set.</span></span>
  - <span data-ttu-id="7cafb-136">デバッグ ビルドでのみ有効になるログを作成するときに、この API を使用します。</span><span class="sxs-lookup"><span data-stu-id="7cafb-136">Use this API when creating logs that will be enabled only in debug builds.</span></span>

### <a name="logging-events"></a><span data-ttu-id="7cafb-137">イベントのログ記録</span><span class="sxs-lookup"><span data-stu-id="7cafb-137">Logging events</span></span>

<span data-ttu-id="7cafb-138">次の API は、よりイベント指向です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-138">The following APIs are more event oriented.</span></span> <span data-ttu-id="7cafb-139">単純な文字列をログに記録するのではなく、イベント オブジェクトをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="7cafb-139">Rather than logging simple strings they log event objects.</span></span>

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - <span data-ttu-id="7cafb-140">EventSource は、プライマリ ルートの .NET Core トレース API です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-140">EventSource is the primary root .NET Core tracing API.</span></span>
  - <span data-ttu-id="7cafb-141">すべての .NET Standard バージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-141">Available in all .NET Standard versions.</span></span>
  - <span data-ttu-id="7cafb-142">シリアル化可能なオブジェクトのみをトレースできます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-142">Only allows tracing serializable objects.</span></span>
  - <span data-ttu-id="7cafb-143">EventSource を使用するように構成されている [EventListener](xref:System.Diagnostics.Tracing.EventListener) インスタンスを介してインプロセスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-143">Can be consumed in-process via any [EventListener](xref:System.Diagnostics.Tracing.EventListener) instances configured to consume the EventSource.</span></span>
  - <span data-ttu-id="7cafb-144">次を介してアウトプロセスで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-144">Can be consumed out-of-process via:</span></span>
    - <span data-ttu-id="7cafb-145">すべてのプラットフォームでの [.NET Core の EventPipe](./eventpipe.md)</span><span class="sxs-lookup"><span data-stu-id="7cafb-145">[.NET Core's EventPipe](./eventpipe.md) on all platforms</span></span>
    - [<span data-ttu-id="7cafb-146">Windows イベント トレーシング (ETW)</span><span class="sxs-lookup"><span data-stu-id="7cafb-146">Event Tracing for Windows (ETW)</span></span>](/windows/win32/etw/event-tracing-portal)
    - [<span data-ttu-id="7cafb-147">Linux 用 LTTng トレース フレームワーク</span><span class="sxs-lookup"><span data-stu-id="7cafb-147">LTTng tracing framework for Linux</span></span>](https://lttng.org/)
      - <span data-ttu-id="7cafb-148">チュートリアル: [PerfCollect を使用して LTTng トレースを収集する](trace-perfcollect-lttng.md)。</span><span class="sxs-lookup"><span data-stu-id="7cafb-148">Walkthrough: [Collect an LTTng trace using PerfCollect](trace-perfcollect-lttng.md).</span></span>

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - <span data-ttu-id="7cafb-149">.NET Core に含まれており、.NET Framework の [NuGet パッケージ](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource)として提供されています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-149">Included in .NET Core and as a [NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) for .NET Framework.</span></span>
  - <span data-ttu-id="7cafb-150">シリアル化できないオブジェクトのインプロセス トレースを可能にします。</span><span class="sxs-lookup"><span data-stu-id="7cafb-150">Allows in-process tracing of non-serializable objects.</span></span>
  - <span data-ttu-id="7cafb-151">ログ対象オブジェクトの選択したフィールドを <xref:System.Diagnostics.Tracing.EventSource> に書き込むことができるようにするブリッジが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-151">Includes a bridge to allow selected fields of logged objects to be written to an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - <span data-ttu-id="7cafb-152">特定のアクティビティまたはトランザクションによって生成されたログ メッセージを明確に識別する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="7cafb-152">Provides a definitive way to identify log messages resulting from a specific activity or transaction.</span></span> <span data-ttu-id="7cafb-153">このオブジェクトを使用すると、さまざまなサービス間でログを相互に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-153">This object can be used to correlate logs across different services.</span></span>

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - <span data-ttu-id="7cafb-154">Windows のみ。</span><span class="sxs-lookup"><span data-stu-id="7cafb-154">Windows only.</span></span>
  - <span data-ttu-id="7cafb-155">Windows イベント ログにメッセージを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-155">Writes messages to the Windows Event Log.</span></span>
  - <span data-ttu-id="7cafb-156">システム管理者は、致命的なアプリケーション エラー メッセージが Windows イベントログに記録されることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-156">System administrators expect fatal application error messages to appear in the Windows Event Log.</span></span>

## <a name="distributed-tracing"></a><span data-ttu-id="7cafb-157">分散トレース</span><span class="sxs-lookup"><span data-stu-id="7cafb-157">Distributed Tracing</span></span>

<span data-ttu-id="7cafb-158">[分散トレース](./distributed-tracing.md)は、分散システムでトレース データを発行して監視する方法です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-158">[Distributed Tracing](./distributed-tracing.md) is the way to publish and observe the tracing data in a distributed system.</span></span>

## <a name="ilogger-and-logging-frameworks"></a><span data-ttu-id="7cafb-159">ILogger とログ記録フレームワーク</span><span class="sxs-lookup"><span data-stu-id="7cafb-159">ILogger and logging frameworks</span></span>

<span data-ttu-id="7cafb-160">低レベルの API は、ログ記録のニーズに適しているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="7cafb-160">The low-level APIs may not be the right choice for your logging needs.</span></span> <span data-ttu-id="7cafb-161">ログ記録フレームワークを検討することもできます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-161">You may want to consider a logging framework.</span></span>

<span data-ttu-id="7cafb-162"><xref:Microsoft.Extensions.Logging.ILogger> インターフェイスは、依存関係の挿入を通じてロガーを挿入できる共通のログ インターフェイスを作成するために使用されています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-162">The <xref:Microsoft.Extensions.Logging.ILogger> interface has been used to create a common logging interface where the loggers can be inserted through dependency injection.</span></span>

<span data-ttu-id="7cafb-163">たとえば、アプリケーションに最適な選択を可能にするために、.NET では、組み込みおよびサード パーティのフレームワークのサポートが提供されています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-163">For instance, to allow you to make the best choice for your application .NET offers support for a selection of built-in and third-party frameworks:</span></span>

- [<span data-ttu-id="7cafb-164">.NET の組み込みのログ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="7cafb-164">.NET Built-in logging providers</span></span>](../extensions/logging-providers.md#built-in-logging-providers)
- [<span data-ttu-id="7cafb-165">.NET のサード パーティ製のログ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="7cafb-165">.NET Third-party logging providers</span></span>](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a><span data-ttu-id="7cafb-166">ログ関連の参照</span><span class="sxs-lookup"><span data-stu-id="7cafb-166">Logging related references</span></span>

- [<span data-ttu-id="7cafb-167">方法 : トレースとデバッグを指定して条件付きコンパイルを実行する</span><span class="sxs-lookup"><span data-stu-id="7cafb-167">How to: Compile Conditionally with Trace and Debug</span></span>](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [<span data-ttu-id="7cafb-168">方法 : アプリケーション コードにトレース ステートメントを追加する</span><span class="sxs-lookup"><span data-stu-id="7cafb-168">How to: Add Trace Statements to Application Code</span></span>](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- <span data-ttu-id="7cafb-169">「[.NET のログ記録](../extensions/logging.md)」では、サポートしているログ記録技法の概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="7cafb-169">[Logging in .NET](../extensions/logging.md) provides an overview of the logging techniques it supports.</span></span>

- <span data-ttu-id="7cafb-170">[C# の文字列補間](../../csharp/language-reference/tokens/interpolated.md)を使用すると、ログ記録コードを簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-170">[C# string interpolation](../../csharp/language-reference/tokens/interpolated.md) can simplify writing logging code.</span></span>

- [<span data-ttu-id="7cafb-171">ランタイム プロバイダー イベント一覧</span><span class="sxs-lookup"><span data-stu-id="7cafb-171">Runtime Provider Event List</span></span>](../../fundamentals/diagnostics/runtime-events.md)

- [<span data-ttu-id="7cafb-172">.NET の既知のイベント プロバイダー</span><span class="sxs-lookup"><span data-stu-id="7cafb-172">Well-known Event Providers in .NET</span></span>](well-known-event-providers.md)

- <span data-ttu-id="7cafb-173"><xref:System.Exception.Message?displayProperty=nameWithType> プロパティは、例外をログに記録する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7cafb-173">The <xref:System.Exception.Message?displayProperty=nameWithType> property is useful for logging exceptions.</span></span>

- <span data-ttu-id="7cafb-174"><xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> クラスは、ログにスタック情報を提供するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7cafb-174">The <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> class can be useful to provide stack info in your logs.</span></span>

## <a name="performance-considerations"></a><span data-ttu-id="7cafb-175">パフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="7cafb-175">Performance considerations</span></span>

<span data-ttu-id="7cafb-176">文字列を書式設定すると、CPU 処理時間が著しく長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7cafb-176">String formatting can take noticeable CPU processing time.</span></span>

<span data-ttu-id="7cafb-177">パフォーマンス クリティカルなアプリケーションでは、次のことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7cafb-177">In performance critical applications, it's recommended that you:</span></span>

- <span data-ttu-id="7cafb-178">リッスンしているものがない場合は、大量のログを記録しないようにします。</span><span class="sxs-lookup"><span data-stu-id="7cafb-178">Avoid lots of logging when no one is listening.</span></span> <span data-ttu-id="7cafb-179">最初にログ記録が有効かどうかを確認することで、負荷の高いログ メッセージを作成しないようにします。</span><span class="sxs-lookup"><span data-stu-id="7cafb-179">Avoid constructing costly logging messages by checking if logging is enabled first.</span></span>
- <span data-ttu-id="7cafb-180">役に立つものだけをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="7cafb-180">Only log what's useful.</span></span>
- <span data-ttu-id="7cafb-181">凝ったフォーマット設定は分析ステージで行います。</span><span class="sxs-lookup"><span data-stu-id="7cafb-181">Defer fancy formatting to the analysis stage.</span></span>
