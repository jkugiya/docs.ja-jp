---
title: .NET での汎用ホスト
author: IEvangelist
description: アプリの起動と有効期間の管理を行う .NET 汎用ホストについて説明します。
ms.author: dapine
ms.date: 12/18/2020
ms.openlocfilehash: bf6d5ad624bbed46994633abace0af64712757f3
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "102402119"
---
# <a name="net-generic-host"></a>.NET での汎用ホスト

Worker サービス テンプレートを使用すると、.NET 汎用ホスト <xref:Microsoft.Extensions.Hosting.HostBuilder> が作成されます。 汎用ホストは、コンソール アプリなど、他の種類の .NET アプリケーションで使用できます。

"*ホスト*" とは、以下のようなアプリのリソースをカプセル化するオブジェクトです:

- 依存関係の挿入 (DI)
- ログの記録
- 構成
- `IHostedService` の実装

ホストが起動すると、サービス コンテナーのホステッド サービスのコレクションに登録されている <xref:Microsoft.Extensions.Hosting.IHostedService> の各実装で <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> が呼び出されます。 Worker サービス アプリでは、<xref:Microsoft.Extensions.Hosting.BackgroundService> インスタンスを含むすべての `IHostedService` 実装で、<xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> メソッドが呼び出されます。

アプリの相互依存するすべてのリソースを 1 つのオブジェクトに含める主な理由は、アプリの起動と正常なシャットダウンの制御の有効期間の管理のためです。 これを実行するには、[Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet パッケージを使用します。

## <a name="set-up-a-host"></a>ホストを設定する

ホストは通常、`Program` クラス内のコードによって構成、ビルド、および実行されます。 `Main` メソッド:

- <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> メソッドを呼び出して、builder オブジェクトを作成および構成します。
- <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> を呼び出して <xref:Microsoft.Extensions.Hosting.IHost> インスタンスを作成します。
- ホスト オブジェクトに対して <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> または <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> メソッドを呼び出します。

.NET Worker サービス テンプレートを使用すると、汎用ホストを作成する次のコードが生成されます。

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureServices((hostContext, services) =>
            {
                services.AddHostedService<Worker>();
            });
}
```

## <a name="default-builder-settings"></a>既定の builder 設定

<xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> メソッド:

- <xref:System.IO.Directory.GetCurrentDirectory> によって返されるパスにコンテンツ ルートを設定します。
- 次から[ ホスト構成](#host-configuration)を読み込みます。
  - プレフィックス `DOTNET_` が付いた環境変数。
  - コマンド ライン引数。
- 次からアプリの構成を読み込みます。
  - *appsettings.json*。
  - *appsettings.{Environment}.json*。
  - `Development` 環境でアプリが実行される場合に使用されるシークレット マネージャー。
  - 環境変数。
  - コマンド ライン引数。
- 次のログ プロバイダーを追加します。
  - コンソール
  - デバッグ
  - EventSource
  - イベント ログ (Windows で実行されている場合のみ)
- 環境が `Development` である場合は、スコープの検証と[依存関係の検証](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild)を有効にします。

`ConfigureServices` メソッドには、サービスを <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> インスタンスに追加する機能があります。 これらのサービスは、後で、依存関係の挿入から使用できるようになります。

## <a name="framework-provided-services"></a>フレームワークが提供するサービス

以下のサービスは、自動的に登録されます。

- [IHostApplicationLifetime](#ihostapplicationlifetime)
- [IHostLifetime](#ihostlifetime)
- [IHostEnvironment](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a>IHostApplicationLifetime

起動後タスクとグレースフル シャットダウン タスクを処理するために <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> サービスを任意のクラスに注入します。 インターフェイス上の 3 つのプロパティは、アプリの起動およびアプリの停止のイベント ハンドラー メソッドを登録するために使用されるキャンセル トークンです。 インターフェイスには <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> メソッドも含まれています。

次の例は、`IHostApplicationLifetime` イベントを登録する `IHostedService` の実装です。

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

`ExampleHostedService` 実装を追加するように Worker サービス テンプレートを変更することができます。

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

アプリケーションにより、次のサンプル出力が書き込まれます。

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a>IHostLifetime

<xref:Microsoft.Extensions.Hosting.IHostLifetime> 実装では、ホストを開始および停止するタイミングが制御されます。 登録されている最後の実装が使用されます。

`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` は、既定の `IHostLifetime` 実装です。 `ConsoleLifetime`:

- <kbd>Ctrl</kbd>+<kbd>C</kbd>、[SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)、または [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) をリッスンし、<xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> を呼び出して、シャットダウン プロセスを開始します。
- `RunAsync` や `WaitForShutdownAsync` などの拡張機能のブロックを解除します。

## <a name="ihostenvironment"></a>IHostEnvironment

次の設定に関する情報を取得するため、クラスに <xref:Microsoft.Extensions.Hosting.IHostEnvironment> サービスを注入します。

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a>ホストの構成

ホスト構成は、[IHostEnvironment](#ihostenvironment) 実装のプロパティを構成するために使用されます。

ホスト構成は、<xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> メソッド内の [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) で使用できます。 `ConfigureAppConfiguration` メソッドを呼び出すと、`HostBuilderContext` と `IConfigurationBuilder` が `configureDelegate` に渡されます。 `configureDelegate` は `Action<HostBuilderContext, IConfigurationBuilder>` として定義されています。 このホスト ビルダー コンテキストには、`IConfiguration` のインスタンスである `.Configuration` プロパティがあります。 これはホストから構築された構成を表します。一方、`IConfigurationBuilder` はアプリの構成に使用されるビルダー オブジェクトです。

> [!TIP]
> `ConfigureAppConfiguration` が呼び出された後、`HostBuilderContext.Configuration` は[アプリの構成](#app-configuration)に置き換えられます。

ホストの構成を追加するには、`IHostBuilder` 上で <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> を呼び出します。 `ConfigureHostConfiguration` を複数回呼び出して結果を追加できます。 ホストは、指定されたキーで最後に値を設定したオプションを使用します。

次の例では、ホストの構成を作成します。

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="19-25":::

## <a name="app-configuration"></a>アプリの構成

アプリの構成は、`IHostBuilder` 上で <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> を呼び出すことで作成されます。 `ConfigureAppConfiguration` を複数回呼び出して結果を追加できます。 アプリは、指定されたキーで最後に値を設定したオプションを使用します。

`ConfigureAppConfiguration` によって作成された構成は、[ HostBuilderContext.Configuration ](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) で、以降の操作のために、かつ DI からのサービスとして利用できます。 ホストの構成はアプリの構成にも追加されます。

詳細については、「[.NET での構成](configuration.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [.NET での構成](configuration.md)
- [ASP.NET Core の Web ホスト](/aspnet/core/fundamentals/host/web-host)
- 汎用ホストのバグは、[github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) リポジトリに作成する必要があります
