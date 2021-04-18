---
title: .NET での依存関係の挿入
description: .NET で依存関係の挿入を実装する方法とそれを使う方法について説明します。
author: IEvangelist
ms.author: dapine
ms.date: 04/12/2021
ms.topic: overview
ms.openlocfilehash: 2feb8b44d7701839bd889138c1f7c8f1fb2be71a
ms.sourcegitcommit: aab60b21144bf04b3057b5d59aa7c58edaef32d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2021
ms.locfileid: "107494286"
---
# <a name="dependency-injection-in-net"></a>.NET での依存関係の挿入

.NET では依存関係の挿入 (DI) ソフトウェア設計パターンがサポートされています。これは、クラスとその依存関係の間で[制御の反転 (IoC)](../../architecture/modern-web-apps-azure/architectural-principles.md#dependency-inversion) を実現するための手法です。 .NET での依存関係の挿入は、構成、ログ、オプション パターンと並び、[第一級オブジェクト](https://en.wikipedia.org/wiki/First-class_citizen)です。

"*依存関係*" とは、他のオブジェクトが依存するオブジェクトのことです。 他のクラスが依存している、次の `Write` メソッドを備えた `MessageWriter` クラスを調べます。

```csharp
public class MessageWriter
{
    public void Write(string message)
    {
        Console.WriteLine($"MessageWriter.Write(message: \"{message}\")");
    }
}
```

クラスは、`MessageWriter` クラスのインスタンスを作成して、その `Write` メソッドを使用することができます。 次の例で、`MessageWriter` クラスは `Worker` クラスの依存関係です。

```csharp
public class Worker : BackgroundService
{
    private readonly MessageWriter _messageWriter = new MessageWriter();

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _messageWriter.Write($"Worker running at: {DateTimeOffset.Now}");
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

このクラスは `MessageWriter` クラスを作成し、これに直接依存しています。 ハードコーディングされた依存関係には、前の例のような問題があり、次の理由から回避する必要があります。

- `MessageWriter` を別の実装で置き換えるには、`Worker` クラスを変更する必要があります。
- `MessageWriter` が依存関係を含んでいる場合、これらは `Worker` クラスによって構成する必要があります。 複数のクラスが `MessageWriter` に依存している大規模なプロジェクトでは、構成コードがアプリ全体に分散するようになります。
- このような実装では、単体テストを行うことが困難です。 アプリはモックまたはスタブの `MessageWriter` クラスを使用する必要がありますが、この方法では不可能です。

依存関係の挿入は、次の方法によってこれらの問題に対応します。

- 依存関係の実装を抽象化するための、インターフェイスまたは基底クラスの使用。
- サービス コンテナー内の依存関係の登録。 .NET には、組み込みのサービス コンテナー <xref:System.IServiceProvider> が用意されています。 通常、サービスは、アプリの起動時に登録され、<xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> に追加されます。 すべてのサービスが追加されたら、<xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> を使用してサービス コンテナーを作成します。
- サービスを使用するクラスのコンストラクターへの、サービスの "*挿入*"。 依存関係のインスタンスの作成、およびインスタンスが不要になったときの廃棄の役割を、フレームワークが担当します。

たとえば、`IMessageWriter` インターフェイスに `Write` メソッドを定義します。

:::code language="csharp" source="snippets/configuration/dependency-injection/IMessageWriter.cs":::

このインターフェイスは、具象型 `MessageWriter` によって実装されます。

:::code language="csharp" source="snippets/configuration/dependency-injection/MessageWriter.cs":::

このサンプル コードの場合、具象型 `MessageWriter` を使用して `IMessageWriter` サービスが登録されます。 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> メソッドによって、サービスは、1 つの要求の有効期間であるスコープ付き有効期間で登録されます。 [サービスの有効期間](#service-lifetimes)については、この記事の後半で説明します。

:::code language="csharp" source="snippets/configuration/dependency-injection/Program.cs" highlight="16":::

サンプル アプリでは、`IMessageWriter` サービスが要求され、`Write` メソッドを呼び出すために使用されます。

:::code language="csharp" source="snippets/configuration/dependency-injection/Worker.cs":::

DI パターンを使用することにより、Worker サービスは次のようになります。

- 具象型 `MessageWriter` は使用されず、実装される `IMessageWriter` インターフェイスのみが使用されます。 これにより、コントローラーが使用する実装は、コントローラーを変更することなく、簡単に変更できるようになります。
- `MessageWriter` のインスタンスは作成されず、DI コンテナーによって作成されます。

組み込みのログ API を使用すると、`IMessageWriter` インターフェイスの実装を向上させることができます。

:::code language="csharp" source="snippets/configuration/dependency-injection/LoggingMessageWriter.cs":::

更新された `ConfigureServices` メソッドでは、新しい `IMessageWriter` の実装が登録されます。

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureServices((_, services) =>
            services.AddHostedService<Worker>()
                    .AddScoped<IMessageWriter, LoggingMessageWriter>());
```

`LoggingMessageWriter` は、コンストラクターで要求される <xref:Microsoft.Extensions.Logging.ILogger%601> によって異なります。 `ILogger<TCategoryName>` は、[フレームワークで提供されるサービス](#framework-provided-services)です。

依存関係の挿入をチェーン形式で使用することはよくあります。 次に、要求されたそれぞれの依存関係が、それ自身の依存関係を要求します。 コンテナーによってグラフ内の依存関係が解決され、完全に解決されたサービスが返されます。 解決する必要がある依存関係の集合的なセットは、通常、"*依存関係ツリー*"、"*依存関係グラフ*"、または "*オブジェクト グラフ*" と呼ばれます。

コンテナーでは、[(ジェネリック) オープン型](/dotnet/csharp/language-reference/language-specification/types#open-and-closed-types)を活用し、すべての [(ジェネリック) 構築型](/dotnet/csharp/language-reference/language-specification/types#constructed-types)を登録する必要をなくすことで、`ILogger<TCategoryName>` を解決します。

依存関係の挿入に関する用語では、サービスは次のようになります。

- 通常、他のオブジェクト (`IMessageWriter` サービスなど) にサービスを提供するオブジェクトです。
- Web サービスを使用する場合はありますが、サービスは Web サービスに関連付けられていません。

フレームワークは、堅牢な ログ システムを備えています。 前の例に示されている `IMessageWriter` の実装は、ログを実装するのではなく、基本的な DI を実演するために記述されています。 ほとんどのアプリでは、ロガーを記述する必要はありません。 次のコードは、既定のログを使用する方法を示しています。この場合、`Worker` をホステッド サービス <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> として `ConfigureServices` に登録するだけで済みます。

```csharp
public class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```

前のコードを使用すると、ログ がフレームワークによって提供されるため、`ConfigureServices` を更新する必要はありません。

## <a name="register-groups-of-services-with-extension-methods"></a>拡張メソッドを使用したサービスのグループを登録する

Microsoft 拡張機能には、関連するサービスのグループを登録するための規則が使用されます。 規則は、単一の `Add{GROUP_NAME}` 拡張メソッドを使用して、フレームワーク機能に必要なすべてのサービスを登録するというものです。 たとえば、<xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> 拡張メソッドにより、オプションの使用に必要なすべてのサービスが登録されます。

## <a name="framework-provided-services"></a>フレームワークが提供するサービス

`ConfigureServices` メソッドにより、プラットフォーム機能など、アプリに使用されるサービスが登録されます。 最初に、`ConfigureServices` に提供される `IServiceCollection` には、フレームワークによって定義されたサービスがあります ([ホストの構成方法](generic-host.md#host-configuration)によって異なります)。 .NET テンプレートに基づくアプリの場合、フレームワークにより、数百単位のサービスが登録されます。

次の表に、フレームワークによって登録されるサービスのごく一部を示します。

| サービスの種類                                                                                  | 有効期間  |
|-----------------------------------------------------------------------------------------------|-----------|
| <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory?displayProperty=fullName> | シングルトン |
| <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime>                                  | シングルトン |
| <xref:Microsoft.Extensions.Logging.ILogger%601?displayProperty=fullName>                      | シングルトン |
| <xref:Microsoft.Extensions.Logging.ILoggerFactory?displayProperty=fullName>                   | シングルトン |
| <xref:Microsoft.Extensions.ObjectPool.ObjectPoolProvider?displayProperty=fullName>            | シングルトン |
| <xref:Microsoft.Extensions.Options.IConfigureOptions%601?displayProperty=fullName>            | 一時的 |
| <xref:Microsoft.Extensions.Options.IOptions%601?displayProperty=fullName>                     | シングルトン |
| <xref:System.Diagnostics.DiagnosticListener?displayProperty=fullName>                         | シングルトン |
| <xref:System.Diagnostics.DiagnosticSource?displayProperty=fullName>                           | シングルトン |

## <a name="service-lifetimes"></a>サービスの有効期間

サービスは、次のいずれかの有効期間で構成できます。

- 一時的
- スコープ
- シングルトン

次のセクションでは、前の有効期間について個別に説明します。 登録される各サービスの適切な有効期間を選択します。

### <a name="transient"></a>一時的

有効期間が一時的なサービスは、サービス コンテナーから要求されるたびに作成されます。 この有効期間は、軽量でステートレスのサービスに最適です。 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddTransient%2A> で一時的なサービスを登録します。

要求を処理するアプリでは、一時的なサービスが要求の最後に破棄されます。

### <a name="scoped"></a>スコープ

Web アプリケーションの場合、スコープ付き有効期間は、クライアント要求 (接続) ごとにサービスが 1 回作成されることを示します。 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddScoped%2A> でスコープ付きサービスを登録します。

要求を処理するアプリでは、スコープ付きサービスは要求の最後で破棄されます。

Entity Framework Core を使用する場合、既定では <xref:Microsoft.Extensions.DependencyInjection.EntityFrameworkServiceCollectionExtensions.AddDbContext%2A> 拡張メソッドによって、スコープ付き有効期間を持つ `DbContext` 型が登録されます。

> [!NOTE]
> シングルトンからスコープ付きサービスを解決 ***しない*** でください。また、たとえば一時的なサービスにより、間接的に解決しないようにご注意ください。 後続の要求を処理する際に、サービスが正しくない状態になる可能性があります。 次の場合は問題ありません。
>
> - スコープ付きまたは一時的なサービスからシングルトン サービスを解決する。
> - スコープ付きサービスを、別のスコープ付きまたは一時的なサービスから解決する。

既定では、開発環境で、より長い有効期間を持つ別のサービスからサービスを解決すると、例外がスローされます。 詳しくは、「[スコープの検証](#scope-validation)」をご覧ください。

### <a name="singleton"></a>シングルトン

シングルトン有効期間サービスが作成されるのは、次のいずれかの場合です。

- それらが初めて要求された場合。
- 開発者によって、実装インスタンスがコンテナーに直接提供される場合。 このアプローチはほとんど必要ありません。

依存関係の挿入コンテナーから送信されるサービス実装の後続の要求すべてには、同じインスタンスが使用されます。 アプリをシングルトンで動作させる必要がある場合は、サービス コンテナーによるサービスの有効期間の管理を許可してください。 シングルトン デザイン パターンを実装したり、シングルトンを破棄するコードを提供したりしないでください。 コンテナーからサービスを解決したコードによって、サービスが破棄されることはありません。 型またはファクトリがシングルトンとして登録されている場合、コンテナーによってシングルトンが自動的に破棄されます。

シングルトン サービスを <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A> で登録します。 シングルトン サービスはスレッド セーフである必要があり、ほとんどの場合、ステートレス サービスで使用されます。

要求を処理するアプリでは、アプリのシャットダウン時に <xref:Microsoft.Extensions.DependencyInjection.ServiceProvider> が破棄されるとき、シングルトン サービスが破棄されます。 アプリがシャットダウンされるまでメモリは解放されないため、シングルトン サービスでのメモリ使用を考慮してください。

## <a name="service-registration-methods"></a>サービス登録メソッド

このフレームワークでは、特定のシナリオで役立つサービス登録拡張メソッドが提供されます。

| メソッド | 自動<br>object<br>破棄 | 複数<br>実装 | 引数を渡す |
|--|:-:|:-:|:-:|
| `Add{LIFETIME}<{SERVICE}, {IMPLEMENTATION}>()`<br><br>例:<br><br>`services.AddSingleton<IMyDep, MyDep>();` | はい | はい | いいえ |
| `Add{LIFETIME}<{SERVICE}>(sp => new {IMPLEMENTATION})`<br><br>次に例を示します。<br><br>`services.AddSingleton<IMyDep>(sp => new MyDep());`<br>`services.AddSingleton<IMyDep>(sp => new MyDep(99));` | はい | はい | はい |
| `Add{LIFETIME}<{IMPLEMENTATION}>()`<br><br>例:<br><br>`services.AddSingleton<MyDep>();` | はい | いいえ | いいえ |
| `AddSingleton<{SERVICE}>(new {IMPLEMENTATION})`<br><br>次に例を示します。<br><br>`services.AddSingleton<IMyDep>(new MyDep());`<br>`services.AddSingleton<IMyDep>(new MyDep(99));` | いいえ | はい | はい |
| `AddSingleton(new {IMPLEMENTATION})`<br><br>次に例を示します。<br><br>`services.AddSingleton(new MyDep());`<br>`services.AddSingleton(new MyDep(99));` | いいえ | いいえ | はい |

型の廃棄の詳細については、「[サービスの破棄](dependency-injection-guidelines.md#disposal-of-services)」を参照してください。

実装型のみでサービスを登録することは、同じ実装とサービスの型でそのサービスを登録することと同じです。 明示的なサービス型を使用しないメソッドを使用してサービスの複数の実装を登録できないのは、このためです。 これらのメソッドでは、サービスの複数の "*インスタンス*" を登録できますが、すべて同じ "*実装*" 型になります。

上記のサービス登録メソッドのずれかを使用して、同じサービス型の複数のサービス インスタンスを登録できます。 次の例では、`IMessageWriter` をサービス型として使用して、`AddSingleton` を 2 回呼び出します。 2 回目の `AddSingleton` の呼び出しにより、`IMessageWriter` として解決された場合は前のものがオーバーライドされ、`IEnumerable<IMessageWriter>` を介して複数のサービスが解決された場合は前のものに追加されます。 `IEnumerable<{SERVICE}>` を介して解決された場合、サービスは登録された順に表示されます。

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/Program.cs" highlight="19-24":::

上記のサンプル ソース コードを使用すると、`IMessageWriter` の 2 つの実装が登録されます。

:::code language="csharp" source="snippets/configuration/console-di-ienumerable/ExampleService.cs" highlight="9-18":::

`ExampleService` により、2 つのコンストラクター パラメーター (1 つの `IMessageWriter` と `IEnumerable<IMessageWriter>`) が定義されます。 1 つの `IMessageWriter` は登録された最後の実装です。一方、`IEnumerable<IMessageWriter>` は登録されたすべての実装を表します。

フレームワークには `TryAdd{LIFETIME}` 拡張メソッドも用意されており、実装がまだ登録されていない場合にのみ、サービスが登録されます。

次の例では、`AddSingleton` の呼び出しによって、`IMessageWriter` の実装として `ConsoleMessageWriter` が登録されます。 `TryAddSingleton` の呼び出しでは何も行われません。`IMessageWriter` には登録された実装が既に含まれているからです。

```csharp
services.AddSingleton<IMessageWriter, ConsoleMessageWriter>();
services.TryAddSingleton<IMessageWriter, LoggingMessageWriter>();
```

`TryAddSingleton` は、既に追加されており、"試行" は失敗するため、効果はありません。 `ExampleService` により、以下がアサートされます。

```csharp
public class ExampleService
{
    public ExampleService(
        IMessageWriter messageWriter,
        IEnumerable<IMessageWriter> messageWriters)
    {
        Trace.Assert(messageWriter is ConsoleMessageWriter);
        Trace.Assert(messageWriters.Single() is ConsoleMessageWriter);
    }
}
```

詳細については、次を参照してください。

- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAdd%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddTransient%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddScoped%2A>
- <xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddSingleton%2A>

[TryAddEnumerable(ServiceDescriptor)](xref:Microsoft.Extensions.DependencyInjection.Extensions.ServiceCollectionDescriptorExtensions.TryAddEnumerable%2A) メソッドでは、"*同じ型*" の実装がまだ存在しない場合にのみサービスが登録されます。 複数のサービスは、`IEnumerable<{SERVICE}>` によって解決されます。 サービスを登録するときに、同じ型のいずれかがまだ追加されていない場合は、インスタンスを追加します。 ライブラリの作成者は、コンテナー内の実装の複数のコピーを登録しないようにするため `TryAddEnumerable` を使用します。

次の例では、`TryAddEnumerable` の最初の呼び出しで、`IMessageWriter1` の実装として `MessageWriter` が登録されます。 2 番目の呼び出しでは `IMessageWriter2` に `MessageWriter` が登録されます。 3 番目の呼び出しでは何も行われません。`IMessageWriter1` には `MessageWriter` の登録済みの実装が既に含まれているからです。

```csharp
public interface IMessageWriter1 { }
public interface IMessageWriter2 { }

public class MessageWriter : IMessageWriter1, IMessageWriter2
{
}

services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter2, MessageWriter>());
services.TryAddEnumerable(ServiceDescriptor.Singleton<IMessageWriter1, MessageWriter>());
```

サービスの登録は、通常、同じ種類の複数の実装を登録する場合を除き、順序に依存しません。

`IServiceCollection` は <xref:Microsoft.Extensions.DependencyInjection.ServiceDescriptor> オブジェクトのコレクションです。 次の例は、`ServiceDescriptor` の作成と追加によってサービスを登録する方法を示しています。

```csharp
string secretKey = Configuration["SecretKey"];
var descriptor = new ServiceDescriptor(
    typeof(IMessageWriter),
    _ => new DefaultMessageWriter(secretKey),
    ServiceLifetime.Transient);

services.Add(descriptor);
```

組み込みの `Add{LIFETIME}` メソッドでも同じ方法が使用されます。 たとえば、[AddScoped のソース コード](https://github.com/dotnet/extensions/blob/v3.1.8/src/DependencyInjection/DI.Abstractions/src/ServiceCollectionServiceExtensions.cs#L216-L237)をご覧ください。

### <a name="constructor-injection-behavior"></a>コンストラクターの挿入の動作

サービスは次を使用することによって解決できます。

- <xref:System.IServiceProvider>
- <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities>:
  - コンテナーに登録されていないオブジェクトが作成されます。
  - 一部のフレームワーク機能に使用されます。

コンストラクターは、依存関係の挿入によって提供されない引数を受け取ることができますが、引数は既定値を割り当てる必要があります。

`IServiceProvider` または `ActivatorUtilities` によってサービスを解決する場合、コンストラクターの挿入には、"*パブリック*" コンストラクターが必要です。

`ActivatorUtilities` によってサービスを解決する場合、コンストラクターの挿入に必要なことは、該当するコンストラクターが 1 つだけ存在することです。 コンストラクターのオーバーロードはサポートされていますが、依存関係の挿入によってすべての引数を設定できるオーバーロードは 1 つしか存在できません。

## <a name="scope-validation"></a>スコープの検証

アプリが `Development` 環境で実行されていて、ホストを構築するために [CreateDefaultBuilder](generic-host.md#default-builder-settings) が呼び出される場合、既定のサービス プロバイダーによって次を確認するためのチェックが実行されます。

- スコープ付きサービスが、ルート サービス プロバイダーによって解決されない。
- スコープ付きサービスが、シングルトンに挿入されない。

<xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> が呼び出されると、ルート サービス プロバイダーが作成されます。 ルート サービス プロバイダーの有効期間は、プロバイダーがアプリで開始されるとアプリの有効期間に対応し、アプリのシャットダウン時には破棄されます。

スコープ サービスは、それを作成したコンテナーによって破棄されます。 ルート コンテナーに作成されたスコープ付きサービスは、アプリのシャットダウン時に、ルート コンテナーによってのみ破棄されるため、サービスの有効期間は実質的にシングルトンに昇格されます。 `BuildServiceProvider` が呼び出されると、サービス スコープの検証がこれらの状況をキャッチします。

## <a name="scope-scenarios"></a>スコープのシナリオ

<xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory> は常にシングルトンとして登録されますが、<xref:System.IServiceProvider> は包含クラスの有効期間に基づいて変化する可能性があります。 たとえば、スコープからサービスを解決し、それらのサービスのいずれかが <xref:System.IServiceProvider> 受け取ると、それは、スコープ付のインスタンスになります。

<xref:Microsoft.Extensions.Hosting.BackgroundService> などの <xref:Microsoft.Extensions.Hosting.IHostedService> の実装内でスコープ サービスを実現するには、コンストラクター インジェクションを介してサービスの依存関係を挿入 "*しないでください*"。 代わりに、<xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory> を挿入し、スコープを作成し、そしてそのスコープから依存関係を解決して適切なサービス有効期間を使用します。

:::code language="csharp" source="snippets/configuration/worker-scope/Worker.cs" highlight="13,15-16,22":::

前のコードでは、アプリが実行されている間、バックグラウンド サービスは次のようになります。

- <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory> に依存する。
- 追加のサービスを解決するために <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> を作成する。
- 利用に向けてスコープ付のサービスを解決する。
- オブジェクトを処理してから、それらを中継し、最後に処理済みとしてマークする。

サンプル ソース コードから、スコープ付きサービスの有効期間が <xref:Microsoft.Extensions.Hosting.IHostedService> の実装にどのような恩恵をもたらすかを確認できます。

## <a name="see-also"></a>関連項目

- [.NET で依存関係の挿入を使用する](dependency-injection-usage.md)
- [依存関係の挿入のガイドライン](dependency-injection-guidelines.md)
- [ASP.NET Core での依存関係の挿入](/aspnet/core/fundamentals/dependency-injection)
- [NDC カンファレンス DI アプリ開発のパターン](https://www.youtube.com/watch?v=x-C-CNBVTaY)
- [明示的な依存関係の原則](../../architecture/modern-web-apps-azure/architectural-principles.md#explicit-dependencies)
- [制御の反転コンテナーと依存関係の挿入パターン (Martin Fowler)](https://www.martinfowler.com/articles/injection.html)
- DI のバグは、[github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) リポジトリに作成する必要があります。
