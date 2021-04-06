---
title: 分散トレース インストルメンテーションを追加する - .NET
description: .NET アプリケーションで分散トレースをインストルメント化するためのチュートリアル
ms.topic: tutorial
ms.date: 03/14/2021
ms.openlocfilehash: 4eb791499855a1479393ef2e00d86316a81409a1
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231154"
---
# <a name="adding-distributed-tracing-instrumentation"></a><span data-ttu-id="7e9e8-103">分散トレース インストルメンテーションの追加</span><span class="sxs-lookup"><span data-stu-id="7e9e8-103">Adding distributed tracing instrumentation</span></span>

<span data-ttu-id="7e9e8-104">**この記事の対象: ✔️** .NET Core 2.1 以降のバージョン **および** .NET Framework 4.5 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="7e9e8-104">**This article applies to: ✔️** .NET Core 2.1 and later versions **and** .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="7e9e8-105">.NET アプリケーションを <xref:System.Diagnostics.Activity?displayProperty=nameWithType> API を使用してインストルメント化し、分散トレース テレメトリを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-105">.NET applications can be instrumented using the <xref:System.Diagnostics.Activity?displayProperty=nameWithType> API to produce distributed tracing telemetry.</span></span> <span data-ttu-id="7e9e8-106">一部のインストルメンテーションは標準の .NET ライブラリに組み込まれていますが、さらに追加してコードをより簡単に診断できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-106">Some instrumentation is built-in to standard .NET libraries but you may want to add more to make your code more easily diagnosable.</span></span> <span data-ttu-id="7e9e8-107">このチュートリアルでは、新しいカスタム分散トレース インストルメンテーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-107">In this tutorial you will add new custom distributed tracing instrumentation.</span></span> <span data-ttu-id="7e9e8-108">このインストルメンテーションによって生成されるテレメトリの記録の詳細については、[コレクションのチュートリアル](distributed-tracing-instrumentation-walkthroughs.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-108">See [the collection tutorial](distributed-tracing-instrumentation-walkthroughs.md) to learn more about recording the telemetry produced by this instrumentation.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7e9e8-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="7e9e8-109">Prerequisites</span></span>

- <span data-ttu-id="7e9e8-110">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="7e9e8-110">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download/dotnet) or a later version</span></span>

## <a name="an-initial-app"></a><span data-ttu-id="7e9e8-111">最初のアプリ</span><span class="sxs-lookup"><span data-stu-id="7e9e8-111">An initial app</span></span>

<span data-ttu-id="7e9e8-112">最初に、OpenTelemetry を使用してテレメトリを収集するサンプル アプリを作成しますが、インストルメンテーションはまだありません。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-112">First you will create a sample app that collects telemetry using OpenTelemetry, but doesn't yet have any instrumentation.</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="7e9e8-113">.NET 5 以降をターゲットとするアプリケーションには、必要な分散トレース API が既に含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-113">Applications that target .NET 5 and later already have the necessary distributed tracing APIs included.</span></span> <span data-ttu-id="7e9e8-114">以前のバージョンの .NET をターゲットとするアプリの場合は、[System.Diagnostics.DiagnosticSource NuGet パッケージ](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) バージョン 5 以降を追加します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-114">For apps targeting older .NET versions add the [System.Diagnostics.DiagnosticSource NuGet package](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource/) version 5 or greater.</span></span>

```dotnetcli
dotnet add package System.Diagnostics.DiagnosticSource
```

<span data-ttu-id="7e9e8-115">テレメトリを収集するために使用される [OpenTelemetry](https://www.nuget.org/packages/OpenTelemetry/) および [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-115">Add the [OpenTelemetry](https://www.nuget.org/packages/OpenTelemetry/) and [OpenTelemetry.Exporter.Console](https://www.nuget.org/packages/OpenTelemetry.Exporter.Console/) NuGet packages which will be used to collect the telemetry.</span></span>

```dotnetcli
dotnet add package OpenTelemetry
dotnet add package OpenTelemetry.Exporter.Console
```

<span data-ttu-id="7e9e8-116">生成された Program.cs の内容を次のソース例に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-116">Replace the contents of the generated Program.cs with this example source:</span></span>

```C#
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        static async Task Main(string[] args)
        {
            using var tracerProvider = Sdk.CreateTracerProviderBuilder()
                .SetResourceBuilder(ResourceBuilder.CreateDefault().AddService("MySample"))
                .AddSource("Sample.DistributedTracing")
                .AddConsoleExporter()
                .Build();

            await DoSomeWork("banana", 8);
            Console.WriteLine("Example work done");
        }

        // All the functions below simulate doing some arbitrary work
        static async Task DoSomeWork(string foo, int bar)
        {
            await StepOne();
            await StepTwo();
        }

        static async Task StepOne()
        {
            await Task.Delay(500);
        }

        static async Task StepTwo()
        {
            await Task.Delay(1000);
        }
    }
}
```

<span data-ttu-id="7e9e8-117">アプリにはまだインストルメンテーションがないため、表示されるトレース情報はありません。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-117">The app has no instrumentation yet so there is no trace information to display:</span></span>

```dotnetcli
> dotnet run
Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="7e9e8-118">推奨する運用方法</span><span class="sxs-lookup"><span data-stu-id="7e9e8-118">Best Practices</span></span>

<span data-ttu-id="7e9e8-119">この例の OpenTelemetry など、分散トレース テレメトリを収集するためにオプションのサード パーティ ライブラリを参照する必要があるのは、アプリ開発者のみです。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-119">Only app developers need to reference an optional 3rd party library for collecting the distributed trace telemetry, such as OpenTelemetry in this example.</span></span> <span data-ttu-id="7e9e8-120">.NET ライブラリの作成者は、.NET ランタイムの一部である System.Diagnostics.DiagnosticSource 内の API にのみ依存できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-120">.NET library authors can exclusively rely on APIs in System.Diagnostics.DiagnosticSource which is part of .NET runtime.</span></span> <span data-ttu-id="7e9e8-121">これにより、テレメトリの収集に使用するライブラリまたはベンダーに関するアプリ開発者の設定に関係なく、さまざまな .NET アプリでライブラリが確実に実行されるようになります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-121">This ensures that libraries will run in a wide range of .NET apps, regardless of the app developer's preferences about which library or vendor to use for collecting telemetry.</span></span>

## <a name="adding-basic-instrumentation"></a><span data-ttu-id="7e9e8-122">基本インストルメンテーションの追加</span><span class="sxs-lookup"><span data-stu-id="7e9e8-122">Adding Basic Instrumentation</span></span>

<span data-ttu-id="7e9e8-123">アプリケーションとライブラリでは、<xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> および <xref:System.Diagnostics.Activity?displayProperty=nameWithType> クラスを使用して分散トレース インストルメンテーションが追加されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-123">Applications and libraries add distributed tracing instrumentation using the <xref:System.Diagnostics.ActivitySource?displayProperty=nameWithType> and <xref:System.Diagnostics.Activity?displayProperty=nameWithType> classes.</span></span>

### <a name="activitysource"></a><span data-ttu-id="7e9e8-124">ActivitySource</span><span class="sxs-lookup"><span data-stu-id="7e9e8-124">ActivitySource</span></span>

<span data-ttu-id="7e9e8-125">まず ActivitySource のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-125">First create an instance of ActivitySource.</span></span> <span data-ttu-id="7e9e8-126">ActivitySource により、アクティビティ オブジェクトを作成および開始するための API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-126">ActivitySource provides APIs to create and start Activity objects.</span></span> <span data-ttu-id="7e9e8-127">Main() および `using System.Diagnostics;` の上の静的 ActivitySource 変数を using ステートメントに追加します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-127">Add the static ActivitySource variable above Main() and `using System.Diagnostics;` to the using statements.</span></span>

```csharp
using OpenTelemetry;
using OpenTelemetry.Resources;
using OpenTelemetry.Trace;
using System;
using System.Diagnostics;
using System.Threading.Tasks;

namespace Sample.DistributedTracing
{
    class Program
    {
        private static ActivitySource source = new ActivitySource("Sample.DistributedTracing", "1.0.0");

        static async Task Main(string[] args)
        {
            ...
```

#### <a name="best-practices"></a><span data-ttu-id="7e9e8-128">推奨する運用方法</span><span class="sxs-lookup"><span data-stu-id="7e9e8-128">Best Practices</span></span>

- <span data-ttu-id="7e9e8-129">ActivitySource を一度作成し、静的変数に格納し、必要に応じてそのインスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-129">Create the ActivitySource once, store it in a static variable and use that instance as long as needed.</span></span>
<span data-ttu-id="7e9e8-130">各ライブラリまたはライブラリのサブコンポーネントでは、独自のソースを作成することができます (多くの場合、そうする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-130">Each library or library sub-component can (and often should) create its own source.</span></span> <span data-ttu-id="7e9e8-131">アプリ開発者がソース内のアクティビティ テレメトリを個別に有効または無効にできることが予想される場合は、既存のソースを再利用するのではなく、新しいものを作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-131">Consider creating a new source rather than re-using an existing one if you anticipate app developers would appreciate being able to enable and disable the Activity telemetry in the sources independently.</span></span>

- <span data-ttu-id="7e9e8-132">コンストラクターに渡されるソース名は、他のソースと競合しないように一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-132">The source name passed to the constructor has to be unique to avoid the conflicts with any other sources.</span></span>
<span data-ttu-id="7e9e8-133">同じアセンブリ内に複数のソースが存在する場合は、アセンブリ名を含む階層名と、必要に応じてコンポーネント名を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-133">It is recommended to use a hierarchical name that contains the assembly name and optionally a component name if there are multiple sources within the same assembly.</span></span> <span data-ttu-id="7e9e8-134">たとえば、「 `Microsoft.AspNetCore.Hosting` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-134">For example, `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="7e9e8-135">アセンブリで 2 番目の独立したアセンブリにコードのインストルメンテーションを追加する場合、その名前は、コードがインストルメント化されるアセンブリではなく、ActivitySource を定義するアセンブリに基づいている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-135">If an assembly is adding instrumentation for code in a 2nd independent assembly, the name should be based on the assembly that defines the ActivitySource, not the assembly whose code is being instrumented.</span></span>

- <span data-ttu-id="7e9e8-136">バージョン パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-136">The version parameter is optional.</span></span> <span data-ttu-id="7e9e8-137">複数のバージョンのライブラリをリリースし、インストルメント化されたテレメトリに変更を加える場合は、バージョンを指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-137">It is recommended to provide the version in case you release multiple versions of the library and make changes to the instrumented telemetry.</span></span>

> [!NOTE]
> <span data-ttu-id="7e9e8-138">OpenTelemetry では、代替用語である "トレーサー" と "スパン" を使用します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-138">OpenTelemetry uses alternate terms 'Tracer' and 'Span'.</span></span> <span data-ttu-id="7e9e8-139">.NET では、"ActivitySource" はトレーサーの実装であり、アクティビティは "スパン" の実装です。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-139">In .NET 'ActivitySource' is the implementation of Tracer and Activity is the implementation of 'Span'.</span></span> <span data-ttu-id="7e9e8-140">.NET の long 型のアクティビティは OpenTelemetry 仕様より前のものであり、.NET エコシステム内の一貫性および .NET アプリケーションの互換性のために元の .NET の名前付けが保持されています。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-140">.NET's Activity type long pre-dates the OpenTelemetry specification and the original .NET naming has been preserved for consistency within the .NET ecosystem and .NET application compatibility.</span></span>

### <a name="activity-creation"></a><span data-ttu-id="7e9e8-141">Activity の作成</span><span class="sxs-lookup"><span data-stu-id="7e9e8-141">Activity Creation</span></span>

<span data-ttu-id="7e9e8-142">ActivitySource オブジェクトを使用し、意味のある作業単位に基づいてアクティビティ オブジェクトを開始および停止します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-142">Use the ActivitySource object to Start and Stop Activity objects around meaningful units of work.</span></span> <span data-ttu-id="7e9e8-143">ここに示すコードで DoSomeWork() を更新します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-143">Update DoSomeWork() with the code shown here:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                await StepOne();
                await StepTwo();
            }
        }
```

<span data-ttu-id="7e9e8-144">これで、アプリを実行すると、ログに記録される新しいアクティビティが表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-144">Running the app now shows the new Activity being logged:</span></span>

```dotnetcli
> dotnet run
Activity.Id:          00-f443e487a4998c41a6fd6fe88bae644e-5b7253de08ed474f-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:36:51.4720202Z
Activity.Duration:    00:00:01.5025842
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 067f4bb5-a5a8-4898-a288-dec569d6dbef
```

#### <a name="notes"></a><span data-ttu-id="7e9e8-145">Notes</span><span class="sxs-lookup"><span data-stu-id="7e9e8-145">Notes</span></span>

- <span data-ttu-id="7e9e8-146"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> では、アクティビティを同時に作成して開始します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-146"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> creates and starts the activity at the same time.</span></span> <span data-ttu-id="7e9e8-147">リストのコード パターンで使用されている `using` ブロックにより、作成された Activity オブジェクトはブロックの実行後に自動的に破棄されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-147">The listed code pattern is using the `using` block which automatically disposes the created Activity object after executing the block.</span></span> <span data-ttu-id="7e9e8-148">アクティビティ オブジェクトを破棄すると停止し、コードで明示的に <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType> を呼び出す必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-148">Disposing the Activity object will stop it so the code doesn't need to explicitly call <xref:System.Diagnostics.Activity.Stop?displayProperty=nameWithType>.</span></span>
<span data-ttu-id="7e9e8-149">それにより、コーディング パターンが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-149">That simplifies the coding pattern.</span></span>

- <span data-ttu-id="7e9e8-150"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> では、アクティビティを記録しているリスナーが存在するかどうかを内部で判断します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-150"><xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> internally determines if there are any listeners recording the Activity.</span></span> <span data-ttu-id="7e9e8-151">登録済みのリスナーが存在しない場合、または対象ではないリスナーが存在する場合、StartActivity() によって `null` が返され、アクティビティ オブジェクトは作成されません。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-151">If there are no registered listeners or there are listeners which are not interested, StartActivity() will return `null` and avoid creating the Activity object.</span></span> <span data-ttu-id="7e9e8-152">これでパフォーマンスが最適化されるため、非常に頻繁に呼び出される関数でもコード パターンを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-152">This is a performance optimization so that the code pattern can still be used in functions that are called very frequently.</span></span>

## <a name="optional-populate-tags"></a><span data-ttu-id="7e9e8-153">省略可能: タグを設定する</span><span class="sxs-lookup"><span data-stu-id="7e9e8-153">Optional: Populate tags</span></span>

<span data-ttu-id="7e9e8-154">アクティビティではタグと呼ばれるキー値データがサポートされます。これらは一般的に、診断に役立つ可能性のある作業のパラメーターを格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-154">Activities support key-value data called Tags, commonly used to store any parameters of the work that may be useful for diagnostics.</span></span> <span data-ttu-id="7e9e8-155">DoSomeWork() を更新してそれらが含まれるようにします。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-155">Update DoSomeWork() to include them:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                await StepTwo();
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-2b56072db8cb5a4496a4bfb69f46aa06-7bc4acda3b9cce4d-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:37:31.4949570Z
Activity.Duration:    00:00:01.5417719
Activity.TagObjects:
    foo: banana
    bar: 8
Resource associated with Activity:
    service.name: MySample
    service.instance.id: 25bbc1c3-2de5-48d9-9333-062377fea49c

Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="7e9e8-156">推奨する運用方法</span><span class="sxs-lookup"><span data-stu-id="7e9e8-156">Best Practices</span></span>

- <span data-ttu-id="7e9e8-157">前述のように、`activity` によって返される <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> は null である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-157">As mentioned above, `activity` returned by <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> may be null.</span></span> <span data-ttu-id="7e9e8-158">null 合体演算子 ?</span><span class="sxs-lookup"><span data-stu-id="7e9e8-158">The null-coallescing operator ?.</span></span> <span data-ttu-id="7e9e8-159">(C#) は、アクティビティが null でない場合に <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> のみを呼び出すのに短くて便利なものです。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-159">in C# is a convenient short-hand to only invoke <xref:System.Diagnostics.Activity.SetTag%2A?displayProperty=nameWithType> if activity is not null.</span></span> <span data-ttu-id="7e9e8-160">この動作は書き込みと同じです。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-160">The behavior is identical to writing:</span></span>

```csharp
if(activity != null)
{
    activity.SetTag("foo", foo);
}
```

- <span data-ttu-id="7e9e8-161">OpenTelemetry では、一般的な種類のアプリケーション作業を表すアクティビティにタグを設定するために推奨される一連の[規約](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions)が提供されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-161">OpenTelemetry provides a set of recommended [conventions](https://github.com/open-telemetry/opentelemetry-specification/tree/main/specification/trace/semantic_conventions) for setting Tags on Activities that represent common types of application work.</span></span>

- <span data-ttu-id="7e9e8-162">ハイ パフォーマンスが求められる関数をインストルメント化する場合、<xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> は、アクティビティをリッスンしているいずれかのコードでタグなどの補助情報を読み取ることを目的としているかどうかを示すヒントとなります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-162">If you are instrumenting functions with high performance requirements, <xref:System.Diagnostics.Activity.IsAllDataRequested?displayProperty=nameWithType> is a hint that indicates whether any of the code listening to Activities intends to read auxilliary information such as Tags.</span></span> <span data-ttu-id="7e9e8-163">リスナーがそれを読み取らない場合、インストルメント化されたコードでそれを設定する CPU サイクルを消費する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-163">If no listener will read it then there is no need for the instrumented code to spend CPU cycles populating it.</span></span> <span data-ttu-id="7e9e8-164">わかりやすくするために、このサンプルではその最適化を適用しません。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-164">For simplicity this sample doesn't apply that optimization.</span></span>

## <a name="optional-adding-events"></a><span data-ttu-id="7e9e8-165">省略可能: イベントの追加</span><span class="sxs-lookup"><span data-stu-id="7e9e8-165">Optional: Adding Events</span></span>

<span data-ttu-id="7e9e8-166">イベントは、追加の診断データの任意のストリームをアクティビティにアタッチできるタイムスタンプが付いたメッセージです。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-166">Events are timestamped messages that can attach an arbitrary stream of additional diagnostic data to Activities.</span></span> <span data-ttu-id="7e9e8-167">アクティビティにいくつかのイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-167">Add some events to the Activity:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-82cf6ea92661b84d9fd881731741d04e-33fff2835a03c041-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:39:10.6902609Z
Activity.Duration:    00:00:01.5147582
Activity.TagObjects:
    foo: banana
    bar: 8
Activity.Events:
    Part way there [3/18/2021 10:39:11 AM +00:00]
    Done now [3/18/2021 10:39:12 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: ea7f0fcb-3673-48e0-b6ce-e4af5a86ce4f

Example work done
```

#### <a name="best-practices"></a><span data-ttu-id="7e9e8-168">推奨する運用方法</span><span class="sxs-lookup"><span data-stu-id="7e9e8-168">Best Practices</span></span>

- <span data-ttu-id="7e9e8-169">イベントは、転送できるようになるまでメモリ内の一覧に格納されます。これにより、このメカニズムが、適度な数のイベントの記録にのみ適したものとなります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-169">Events are stored in an in-memory list until they can be transmitted which makes this mechanism only suitable for recording a modest number of events.</span></span> <span data-ttu-id="7e9e8-170">大容量または無制限の量のイベントの場合、[ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/) など、このタスクに重点を置いたログ API を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-170">For a large or unbounded volume of events using a logging API focused on this task such as [ILogger](https://docs.microsoft.com/aspnet/core/fundamentals/logging/) is a better choice.</span></span> <span data-ttu-id="7e9e8-171">また、ILogger を使えば、アプリ開発者が分散トレースを使用することを選択したかどうかに関係なく、ログ情報を確実に利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-171">ILogger also ensures that the logging information will be available regardless whether the app developer opts to use distributed tracing.</span></span>
<span data-ttu-id="7e9e8-172">ILogger ではアクティブなアクティビティ ID の自動取り込みがサポートされるため、その API を介してログに記録されたメッセージは、引き続き分散トレースに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-172">ILogger supports automatically capturing the active Activity IDs so messages logged via that API can still be correlated with the distributed trace.</span></span>

## <a name="optional-adding-status"></a><span data-ttu-id="7e9e8-173">省略可能: 状態の追加</span><span class="sxs-lookup"><span data-stu-id="7e9e8-173">Optional: Adding Status</span></span>

<span data-ttu-id="7e9e8-174">OpenTelemetry を使用すると、各アクティビティで、作業の成功/失敗の結果を表す[状態](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status)を報告することができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-174">OpenTelemetry allows each Activity to report a [Status](https://github.com/open-telemetry/opentelemetry-specification/blob/main/specification/trace/api.md#set-status) that represents the pass/fail result of the work.</span></span> <span data-ttu-id="7e9e8-175">そのため、現在、.NET には厳密に型指定された API がありませんが、タグを使用して確立された規約があります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-175">.NET does not currently have a strongly typed API for this purpose but there is an established convention using Tags:</span></span>

- <span data-ttu-id="7e9e8-176">`otel.status_code` は、`StatusCode` を格納するために使用されるタグ名です。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-176">`otel.status_code` is the Tag name used to store `StatusCode`.</span></span> <span data-ttu-id="7e9e8-177">StatusCode タグの値は、文字列 "UNSET"、"OK"、"ERROR" のいずれかである必要があります。これらはそれぞれ StatusCode からの列挙型 `Unset`、`Ok`、`Error` に対応しています。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-177">Values for the StatusCode tag must be one of the strings "UNSET", "OK", or "ERROR", which correspond respectively to the enums `Unset`, `Ok`, and `Error` from StatusCode.</span></span>
- <span data-ttu-id="7e9e8-178">`otel.status_description` は、省略可能な `Description` を格納するために使用されるタグ名です</span><span class="sxs-lookup"><span data-stu-id="7e9e8-178">`otel.status_description` is the Tag name used to store the optional `Description`</span></span>

<span data-ttu-id="7e9e8-179">DoSomeWork() を更新して状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-179">Update DoSomeWork() to set status:</span></span>

```csharp
        static async Task DoSomeWork(string foo, int bar)
        {
            using (Activity activity = source.StartActivity("SomeWork"))
            {
                activity?.SetTag("foo", foo);
                activity?.SetTag("bar", bar);
                await StepOne();
                activity?.AddEvent(new ActivityEvent("Part way there"));
                await StepTwo();
                activity?.AddEvent(new ActivityEvent("Done now"));

                // Pretend something went wrong
                activity?.SetTag("otel.status_code", "ERROR");
                activity?.SetTag("otel.status_description", "Use this text give more information about the error");
            }
        }
```

## <a name="optional-add-additional-activities"></a><span data-ttu-id="7e9e8-180">省略可能: アクティビティをさらに追加する</span><span class="sxs-lookup"><span data-stu-id="7e9e8-180">Optional: Add Additional Activities</span></span>

<span data-ttu-id="7e9e8-181">アクティビティを入れ子にして、より大きな作業単位の部分を記述できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-181">Activities can be nested to describe portions of a larger unit of work.</span></span> <span data-ttu-id="7e9e8-182">これは、短時間で実行されないおそれがあるコードの部分に関して、あるいは特定の外部依存関係からのエラーをより適切にローカライズするために特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-182">This can be particularly valuable around portions of code that might not execute quickly or to better localize failures that come from specific external dependencies.</span></span> <span data-ttu-id="7e9e8-183">このサンプルでは、すべての方法でアクティビティを使用していますが、それは追加のコードが最小化されているだけの理由によるものです。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-183">Although this sample uses an Activity in every method, that is solely because extra code has been minimized.</span></span> <span data-ttu-id="7e9e8-184">すべての方法でアクティビティを使用するより大規模で現実的なプロジェクトでは、非常に詳細なトレースが生成されるため、推奨されません。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-184">In a larger and more realistic project using an Activity in every method would produce extremely verbose traces so it is not recommended.</span></span>

<span data-ttu-id="7e9e8-185">StepOne と StepTwo を更新して、これらの個々のステップに関するトレースをさらに追加します。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-185">Update StepOne and StepTwo to add more tracing around these separate steps:</span></span>

```csharp
        static async Task StepOne()
        {
            using (Activity activity = source.StartActivity("StepOne"))
            {
                await Task.Delay(500);
            }
        }

        static async Task StepTwo()
        {
            using (Activity activity = source.StartActivity("StepTwo"))
            {
                await Task.Delay(1000);
            }
        }
```

```dotnetcli
> dotnet run
Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-39cac574e8fda44b-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepOne
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4278822Z
Activity.Duration:    00:00:00.5051364
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-4ccccb6efdc59546-01
Activity.ParentId:    00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: StepTwo
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.9441095Z
Activity.Duration:    00:00:01.0052729
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Activity.Id:          00-9d5aa439e0df7e49b4abff8d2d5329a9-f16529d0b7c49e44-01
Activity.DisplayName: SomeWork
Activity.Kind:        Internal
Activity.StartTime:   2021-03-18T10:40:51.4256627Z
Activity.Duration:    00:00:01.5286408
Activity.TagObjects:
    foo: banana
    bar: 8
    otel.status_code: ERROR
    otel.status_description: Use this text give more information about the error
Activity.Events:
    Part way there [3/18/2021 10:40:51 AM +00:00]
    Done now [3/18/2021 10:40:52 AM +00:00]
Resource associated with Activity:
    service.name: MySample
    service.instance.id: e0a8c12c-249d-4bdd-8180-8931b9b6e8d0

Example work done
```

<span data-ttu-id="7e9e8-186">StepOne と StepTwo の両方に、SomeWork を参照する ParentId が含まれていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-186">Notice that both StepOne and StepTwo include a ParentId that refers to SomeWork.</span></span> <span data-ttu-id="7e9e8-187">コンソールは、入れ子になった作業ツリーを視覚化するのに最適ではありませんが、[Zipkin](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md) などの多くの GUI ビューアーでは、これをガント チャートとして表示できます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-187">The console is not a great visualization of nested trees of work, but many GUI viewers such as [Zipkin](https://github.com/open-telemetry/opentelemetry-dotnet/blob/main/src/OpenTelemetry.Exporter.Zipkin/README.md) can show this as a Gantt chart:</span></span>

<span data-ttu-id="7e9e8-188">[![Zipkin ガント チャート](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)</span><span class="sxs-lookup"><span data-stu-id="7e9e8-188">[![Zipkin Gantt chart](media/zipkin-nested-activities.jpg)](media/zipkin-nested-activities.jpg)</span></span>

### <a name="optional-activitykind"></a><span data-ttu-id="7e9e8-189">省略可能: ActivityKind</span><span class="sxs-lookup"><span data-stu-id="7e9e8-189">Optional: ActivityKind</span></span>

<span data-ttu-id="7e9e8-190">アクティビティには、アクティビティ、その親およびその子の間の関係を記述する <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-190">Activities have an <xref:System.Diagnostics.Activity.Kind%2A?displayProperty=nameWithType> property which describes the relationship between the Activity, its parent and its children.</span></span> <span data-ttu-id="7e9e8-191">既定では、すべての新しいアクティビティが <xref:System.Diagnostics.ActivityKind.Internal> に設定されます。これは、リモートの親や子がないアプリケーション内の内部操作であるアクティビティに適しています。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-191">By default all new Activities are set to <xref:System.Diagnostics.ActivityKind.Internal> which is appropriate for Activities that are an internal operation within an application with no remote parent or children.</span></span> <span data-ttu-id="7e9e8-192">その他の種類は、<xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType> で kind パラメーターを使用して設定することができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-192">Other kinds can be set using the kind parameter on <xref:System.Diagnostics.ActivitySource.StartActivity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7e9e8-193">その他のオプションについては、<xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-193">See <xref:System.Diagnostics.ActivityKind?displayProperty=nameWithType> for other options.</span></span>

### <a name="optional-links"></a><span data-ttu-id="7e9e8-194">省略可能: リンク</span><span class="sxs-lookup"><span data-stu-id="7e9e8-194">Optional: Links</span></span>

<span data-ttu-id="7e9e8-195">バッチ処理システムで作業が行われると、1 つのアクティビティにより、多くの異なる要求に代わって同時に作業が表される可能性があり、それぞれに独自のトレース ID があります。アクティビティは 1 つの親を持つように制限されていますが、<xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType> を使用して追加のトレース ID にリンクすることができます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-195">When work occurs in batch processing systems a single Activity might represent work on behalf of many different requests simultaneously, each of which has its own trace-id. Although Activity is restricted to have a single parent, it can link to additional trace-ids using <xref:System.Diagnostics.ActivityLink?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7e9e8-196">各 ActivityLink には、リンクされているアクティビティに関する ID 情報を格納する <xref:System.Diagnostics.ActivityContext> が設定されます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-196">Each ActivityLink is populated with an <xref:System.Diagnostics.ActivityContext> that stores ID information about the Activity being linked to.</span></span> <span data-ttu-id="7e9e8-197">ActivityContext は、<xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> を使用してインプロセス アクティビティ オブジェクトから取得することも、<xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType> を使用してシリアル化された ID 情報から解析することもできます。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-197">ActivityContext can be retrieved from in-process Activity objects using <xref:System.Diagnostics.Activity.Context%2A?displayProperty=nameWithType> or it can be parsed from serialized id information using <xref:System.Diagnostics.ActivityContext.Parse(System.String,System.String)?displayProperty=nameWithType>.</span></span>

```csharp
void DoBatchWork(ActivityContext[] requestContexts)
{
    // Assume each context in requestContexts encodes the trace-id that was sent with a request
    using(Activity activity = s_source.StartActivity(name: "BigBatchOfWork",
                                                     kind: ActivityKind.Internal,
                                                     parentContext: null,
                                                     links: requestContexts.Select(ctx => new ActivityLink(ctx))
    {
        // do the batch of work here
    }
}
```

<span data-ttu-id="7e9e8-198">オンデマンドで追加できるイベントやタグとは異なり、リンクは StartActivity() 中に追加する必要があり、その後は変更できません。</span><span class="sxs-lookup"><span data-stu-id="7e9e8-198">Unlike events and Tags that can be added on-demand, links must be added during StartActivity() and are immutable afterwards.</span></span>
