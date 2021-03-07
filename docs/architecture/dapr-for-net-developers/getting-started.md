---
title: Dapr を使ってみる
description: ローカル開発環境を準備し、Dapr で初めての .NET アプリケーションを構築するためのガイドです。
author: amolenk
ms.date: 02/25/2021
ms.openlocfilehash: 68b1982c7283e0717ff7e1e254e5f313cd480d7b
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102401474"
---
# <a name="get-started-with-dapr"></a>Dapr を使ってみる

最初の2つの章では、Dapr に関する基本的な概念を学習しました。 それ *を体験してください。* この章では、ローカル開発環境を準備し、2つの Dapr .NET アプリケーションを構築する手順について説明します。

## <a name="install-dapr-into-your-local-environment"></a>ローカル環境に Dapr をインストールする

まず、開発用コンピューターに Dapr をインストールします。 完了すると、Dapr アプリケーションを [自己ホスト型モード](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-overview/)でビルドして実行できます。

1. [Dapr CLI をインストール](https://docs.dapr.io/getting-started/install-dapr-cli/)します。 これにより、Dapr インスタンスの起動、実行、および管理を行うことができます。 また、デバッグサポートも提供します。

1. [Docker Desktop](https://docs.docker.com/get-docker/)をインストールします。 Windows で実行している場合は、Linux コンテナーを使用するように **Docker Desktop For windows** が構成されていることを確認してください。

> [!NOTE]
> 既定では、Dapr は Docker コンテナーを使用して、すぐに使用できる最適なエクスペリエンスを提供します。 Docker の外部で Dapr を実行するには、この手順をスキップして、 [*スリム* な初期化を実行](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/)します。 この章の例では、Docker コンテナーを使用する必要があります。

1. [Dapr を初期化](https://docs.dapr.io/getting-started/install-dapr/)します。 この手順では、最新の Dapr バイナリとコンテナーイメージをインストールして、開発環境を設定します。

1. [.NET Core 3.1 SDK をインストールします](https://dotnet.microsoft.com/download/dotnet/3.1)。

Dapr がインストールされたので、次は、最初の Dapr アプリケーションを構築します。

## <a name="build-your-first-dapr-application"></a>最初の Dapr アプリケーションを構築する

まず、 [Dapr state management](state-management.md) ビルディングブロックを使用する単純な .net コンソールアプリケーションを作成します。

### <a name="create-the-application"></a>アプリケーションを作成する

1. 任意のコマンドシェルまたはターミナルを開きます。 [Visual Studio Code](https://code.visualstudio.com/)のターミナル機能について考えてみましょう。 アプリケーションをビルドするルートフォルダーに移動します。 次のコマンドを入力して、新しい .NET コンソールアプリケーションを作成します。

    ```dotnetcli
    dotnet new console -o DaprCounter
    ```

    このコマンドは、単純な "Hello World" .NET Core アプリケーションをスキャフォールディングします。

1. 次に、前のコマンドで作成した新しいディレクトリに移動します。

    ```console
    cd DaprCounter
    ```

1. コマンドを使用して、新しく作成したアプリケーションを実行し `dotnet run` ます。 これにより、"Hello World!" が書き込まれる コンソール画面を表示するには、次のようにします。

    ```dotnetcli
    dotnet run
    ```

### <a name="add-dapr-state-management"></a>Dapr 状態管理の追加

次に、Dapr [state management ビルディングブロック](https://docs.dapr.io/developing-applications/building-blocks/state-management/state-management-overview/) を使用して、プログラムにステートフルカウンターを実装します。

Dapr の HTTP および gRPC のネイティブサポートを使用して、任意の開発プラットフォームで Dapr Api を呼び出すことができます。 ただし、.NET 開発者は、Dapr .NET SDK をより自然で直感的に見つけることができます。 このメソッドは、厳密に型指定された .NET クライアントを使用して Dapr Api を呼び出します。 .NET SDK も ASP.NET Core と緊密に統合されています。

1. ターミナルウィンドウで、 `Dapr.Client` NuGet パッケージをアプリケーションに追加します。

    ```dotnetcli
    dotnet add package Dapr.Client
    ```

    > [!NOTE]
    > Dapr のプレリリース版を使用している場合は、必ずフラグをコマンドに追加してください `--prerelease` 。

1. お気に入りの `Program.cs` エディターでファイルを開き、その内容を次のコードに更新します。

    ```csharp
    using System;
    using System.Threading.Tasks;
    using Dapr.Client;

    namespace DaprCounter
    {
        class Program
        {
            static async Task Main(string[] args)
            {
                const string storeName = "statestore";
                const string key = "counter";

                var daprClient = new DaprClientBuilder().Build();
                var counter = await daprClient.GetStateAsync<int>(storeName, key);

                while (true)
                {
                    Console.WriteLine($"Counter = {counter++}");

                    await daprClient.SaveStateAsync(storeName, key, counter);
                    await Task.Delay(1000);
                }
            }
        }
    }
    ```

    更新されたコードは、次の手順を実装します。

    - 最初に、新しい `DaprClient` インスタンスがインスタンス化されます。 このクラスを使用すると、Dapr サイドカーを操作できます。
    - 状態ストアから、 `DaprClient.GetStateAsync` キーの値をフェッチし `counter` ます。 キーが存在しない場合は、既定 `int` 値 ( `0` ) が返されます。
    - 次に、コードは反復処理を行い、値をコンソールに書き込んで、 `counter` 増分値を状態ストアに保存します。

1. Dapr CLI コマンドを実行すると、 `run` アプリケーションが開始されます。 このメソッドは、基になる dapr ランタイムを呼び出し、アプリケーションと dapr サイドカーの両方を同時に実行できるようにします。 を省略した場合 `app-id` 、dapr はアプリケーションの一意の名前を生成します。 コマンドの最後のセグメントは、 `dotnet run` .net core アプリケーションを実行するように Dapr ランタイムに指示します。

    > [!IMPORTANT]
    > 状態管理のビルディングブロックを使用する場合は、常に明示的なパラメーターを渡す必要があり `app-id` ます。 ブロックでは、キーと値のペアごとに、その状態キーの *プレフィックス* としてアプリケーション id の値を使用します。 アプリケーション id が変更されると、以前に保存された状態にアクセスできなくなります。

    ここで、次のコマンドを使用してアプリケーションを実行します。

    ```console
    dapr run --app-id DaprCounter dotnet run
    ```

    アプリケーションを停止して再起動してみてください。 カウンターがリセットされていないことがわかります。 代わりに、以前に保存した状態から続行します。 Dapr 構成ブロックは、アプリケーションをステートフルにします。

> [!IMPORTANT]
> サンプルアプリケーションは、事前に構成された状態コンポーネントと通信しますが、直接依存関係がないことを理解しておくことが重要です。 Dapr は依存関係を抽象化します。 すぐにわかるように、基になる状態ストアコンポーネントは、単純な構成の更新を使用して変更できます。

実際には状態が保存されていることに疑問があるかもしれません。

## <a name="component-configuration-files"></a>コンポーネント構成ファイル

ローカル環境に対して Dapr を最初に初期化したときに、Redis コンテナーが自動的にプロビジョニングされます。 Dapr は、コンポーネント構成ファイル (権利あり) を使用して、Redis コンテナーを既定の状態ストアコンポーネントとして構成しました `statestore.yaml` 。 その内容を見てみましょう。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!NOTE]
> 既定のコンポーネント構成ファイルは、 `$HOME/.dapr/components` Linux/macOS のフォルダーと Windows 上のフォルダーに格納され `%USERPROFILE%\.dapr\components` ます。

前のコンポーネント構成ファイルの形式に注意してください。

- 各コンポーネントには名前があります。 上記のサンプルでは、という名前のコンポーネントが `statestore` あります。 最初のコード例では、この名前を使用して、使用するコンポーネントを Dapr に指示しています。
- 各コンポーネント構成ファイルには `spec` セクションがあります。 `type`コンポーネントの種類を指定するフィールドが含まれています。 フィールドは、 `version` コンポーネントのバージョンを指定します。 フィールドには、 `metadata` 接続の詳細やその他の設定など、コンポーネントに必要な情報が含まれています。 メタデータ値は、コンポーネントの種類によって異なります。

Dapr サイドカーは、アプリケーションで構成されているすべての dapr コンポーネントを使用できます。 しかし、コンポーネントのアクセシビリティを制限するアーキテクチャ上の理由がある場合はどうでしょうか。 Redis コンポーネントを、運用環境でのみ実行される Dapr サイドカーに制限するにはどうすればよいでしょうか。

これを行うには、 `namespace` 運用環境のを定義します。 名前を指定することもでき `production` ます。 自己ホスト型モードでは、環境変数を設定することによって dapr サイドカーの名前空間を指定し `NAMESPACE` ます。 構成した場合、Dapr サイドカーは、名前空間に一致するコンポーネントのみを読み込みます。 Kubernetes のデプロイでは、Kubernetes 名前空間によって、読み込まれるコンポーネントが決まります。 次の例は、名前空間に配置された Redis コンポーネントを示して `production` います。 要素内の宣言を確認し `namespace` `metadata` ます。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

> [!IMPORTANT]
> 名前空間のコンポーネントは、同じ名前空間で実行されているアプリケーションにのみアクセスできます。 Dapr アプリケーションがコンポーネントの読み込みに失敗した場合は、アプリケーションの名前空間が component 名前空間と一致していることを確認してください。 これは、アプリケーションの名前空間が環境変数に格納される自己ホスト型のモードでは特に注意が必要です `NAMESPACE` 。

必要に応じて、コンポーネントを特定のアプリケーションに限定することもできます。 名前空間内で、 `production` Redis cache へのアクセスをアプリケーションのみに制限することができ `DaprCounter` ます。 これを行うには `scopes` 、コンポーネントの構成でを指定します。 次の例は、Redis コンポーネントへのアクセスを `statestore` 名前空間内のアプリケーションに制限する方法を示してい `DaprCounter` `production` ます。

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
  namespace: production
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
  scopes:
  - DaprCounter
```

## <a name="build-a-multi-container-dapr-application"></a>複数コンテナーの Dapr アプリケーションを構築する

最初の例では、Dapr サイドカーとサイドバイサイドで実行された単純な .NET コンソールアプリケーションを作成しました。 しかし、多くの場合、最新の分散アプリケーションは多くの移動パーツで構成されています。 これらのユーザーは、独立したマイクロサービスを同時に実行できます。 これらのモダンアプリケーションは通常、コンテナー化され、Docker Compose や Kubernetes などのコンテナーオーケストレーションツールを必要とします。

次の例では、複数コンテナーアプリケーションを作成します。 また、 [Dapr サービスの呼び出し](service-invocation.md) の構成要素を使用して、サービス間の通信を行います。 このソリューションは、web API から天気予報を取得する web アプリケーションで構成されます。 これらはそれぞれ、Docker コンテナーで実行されます。 Docker Compose を使用して、コンテナーをローカルで実行し、デバッグ機能を有効にします。

Dapr 用のローカル環境を構成し、 [.Net Core 3.1 開発ツール](https://dotnet.microsoft.com/download/dotnet-core/3.1) をインストールしたことを確認します (手順については、この章の最初で説明しています)。

また、 **.Net Core クロスプラットフォーム開発** ワークロードがインストールされた [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)を使用して、このサンプルを完了する必要があります。

### <a name="create-the-application"></a>アプリケーションを作成する

1. Visual Studio 2019 で **ASP.NET Core Web アプリ** プロジェクトを作成します。

    :::image type="content" source="./media/getting-started/multicontainer-createproject.png" alt-text="新しいプロジェクトの作成のスクリーンショット":::

1. プロジェクト `DaprFrontEnd` とソリューションの名前を指定し `DaprMultiContainer` ます。

    :::image type="content" source="./media/getting-started/multicontainer-configureproject.png" alt-text="新しいプロジェクトの構成のスクリーンショット":::

1. **[Web アプリケーション]** を選択し、Razor Pages を使用して Web アプリケーションを作成します。 [Enable Docker Support]\(Docker サポートを有効にする\) は **選択しないで** ください。 Docker サポートは、後で追加します。

    :::image type="content" source="./media/getting-started/multicontainer-createwebapp.png" alt-text="新しい ASP.NET Core web アプリケーションの作成のスクリーンショット":::

1. ASP.NET Core Web API プロジェクトを同じソリューションに追加し、 _DaprBackEnd_ という呼び出しを行います。 プロジェクトの種類として [ **API** ] を選択します。 既定では、dapr サイドカーは、パブリック API へのアクセスを制限するためにネットワーク境界に依存しています。 そのため、[ **HTTPS 用に構成**] のチェックボックスをオフにします。

    :::image type="content" source="./media/getting-started/multicontainer-createwebapi.png" alt-text="Web API の作成のスクリーンショット":::

### <a name="add-dapr-service-invocation"></a>Dapr サービスの呼び出しの追加

ここでは、Dapr [サービス呼び出し構成ブロック](https://docs.dapr.io/developing-applications/building-blocks/service-invocation/service-invocation-overview/)を使用して、サービス間の通信を構成します。 Web アプリで web API から天気予報を取得できるようにします。 サービス呼び出しの構成ブロックには、多くの利点があります。 これには、サービスの検出、自動再試行、メッセージの暗号化 (mTLS を使用)、改善された可観測性が含まれます。 Dapr sidecar でサービス呼び出し API を呼び出すには、Dapr .NET SDK を使用します。

1. Visual Studio で、パッケージマネージャーコンソール ([**ツール > NuGet パッケージマネージャー > パッケージマネージャーコンソール**) を開き、 `DaprFrontEnd` が既定のプロジェクトであることを確認します。 コンソールで、 `Dapr.AspNetCore` NuGet パッケージをプロジェクトに追加します。

    ```powershell
    Install-Package Dapr.AspNetCore
    ```

    > [!NOTE]
    > プレリリースされているのバージョンを対象としている場合は、 `Dapr.AspNetCore` フラグを指定する必要があり `-Prerelease` ます。

1. プロジェクトで `DaprFrontEnd` *Startup.cs* ファイルを開き、 `ConfigureServices` メソッドを次のコードに置き換えます。

    ```csharp
    // This method gets called by the runtime. Use this method to add services to the container.
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddControllers().AddDapr();
        services.AddRazorPages();
    }
    ```

    を呼び出すと、 `AddDapr` `DaprClient` ASP.NET Core 依存関係の挿入システムにクラスが登録されます。 後で、クラスを使用して `DaprClient` Dapr sidecar と通信します。

1. *WeatherForecast* という名前の新しい C# クラスファイルをプロジェクトに追加し `DaprFrontEnd` ます。

    ```csharp
    using System;

    namespace DaprFrontEnd
    {
        public class WeatherForecast
        {
            public DateTime Date { get; set; }

            public int TemperatureC { get; set; }

            public int TemperatureF { get; set; }

            public string Summary { get; set; }
        }
    }
    ```

1. *Pages* フォルダーの *Index.cshtml.cs* ファイルを開き、その内容を次のコードに置き換えます。

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Net.Http;
    using System.Threading.Tasks;
    using Dapr.Client;
    using Microsoft.AspNetCore.Mvc.RazorPages;

    namespace DaprFrontEnd.Pages
    {
        public class IndexModel : PageModel
        {
            private readonly DaprClient _daprClient;

            public IndexModel(DaprClient daprClient)
            {
                _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));
            }

            public async Task OnGet()
            {
                var forecasts = await _daprClient.InvokeMethodAsync<IEnumerable<WeatherForecast>>(
                    HttpMethod.Get,
                    "daprbackend",
                    "weatherforecast");

                ViewData["WeatherForecastData"] = forecasts;
            }
        }
    }
    ```

    クラスをコンストラクターに挿入することによって、Dapr 機能を web アプリに追加し `DaprClient` `IndexModel` ます。 メソッドでは、 `OnGet` Dapr サービスの呼び出し構成ブロックを使用して、API サービスを呼び出します。 メソッドは、 `OnGet` ユーザーがホームページにアクセスするたびに呼び出されます。 `DaprClient.InvokeMethodAsync`サービスのメソッドを呼び出すには、メソッドを使用し `weatherforecast` `daprbackend` ます。 `daprbackend`後で Dapr で実行するように構成するときに、アプリケーション ID として使用するように WEB API を構成します。 最後に、サービス応答がビューデータに保存されます。

1. *Pages* フォルダー内の *Index. cshtml* ファイルの内容を次のコードに置き換えます。 ビューデータに格納されている天気予報がユーザーに表示されます。

    ```razor
    @page
    @model IndexModel
    @{
        ViewData["Title"] = "Home page";
    }

    <div class="text-center">
        <h1 class="display-4">Welcome</h1>
        <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
        @foreach (var forecast in (IEnumerable<WeatherForecast>)ViewData["WeatherForecastData"])
        {
            <p>The forecast for @forecast.Date is @forecast.Summary!</p>
        }
    </div>
    ```

### <a name="add-container-support"></a>コンテナー サポートを追加する

この例の最後の部分では、コンテナーのサポートを追加し、Docker Compose を使用してソリューションを実行します。

1. プロジェクトを右クリック `DaprFrontEnd` し、[   >  **コンテナー Orchestrator サポート** の追加] を選択します。 [ **コンテナー Orchestrator サポートの追加** ] ダイアログが表示されます。

    :::image type="content" source="./media/getting-started/multicontainer-addorchestrator.png" alt-text="コンテナー orchestrator サポートの追加のスクリーンショット":::

    **[Docker Compose]** を選択します。

1. 次のダイアログボックスで、ターゲット OS として [ **Linux** ] を選択します。

    :::image type="content" source="./media/getting-started/multicontainer-targetos.png" alt-text="Docker ターゲット OS の選択のスクリーンショット":::

    Visual Studio によって、ソリューションの **docker-作成** フォルダーに *docker-compose.yml* ファイルと *dockerignore* ファイルが作成されます。

    :::image type="content" source="./media/getting-started/multicontainer-dockersolution.png" alt-text="Docker 作成プロジェクトのスクリーンショット":::

    *Docker-compose.yml* ファイルには、次の内容が含まれています。

    ```yaml
    version: "3.4"

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
    ```

    *.dockerignore* ファイルには、Docker によってコンテナーに含める必要のないファイルの種類と拡張機能が含まれます。 これらのファイルは開発環境とソース管理に関連付けられており、デプロイするアプリやサービスには関連付けられていません。

    *DaprFrontEnd* プロジェクトディレクトリのルートに、新しい *dockerfile* が作成されました。 *Dockerfile* は、イメージをビルドするために使用される一連のコマンドです。 詳細については、「 [Dockerfile リファレンス](https://docs.docker.com/engine/reference/builder)」を参照してください。

    *Dockerfile* には、yaml が含まれています。

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80
    EXPOSE 443

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprFrontEnd/DaprFrontEnd.csproj", "DaprFrontEnd/"]
    RUN dotnet restore "DaprFrontEnd/DaprFrontEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprFrontEnd"
    RUN dotnet build "DaprFrontEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprFrontEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprFrontEnd.dll"]
    ```

    前の *Dockerfile* は、呼び出されると、次の手順を順番に実行します。

    1. イメージを取得し、 `mcr.microsoft.com/dotnet/aspnet:3.1` 名前をに `base` します。
    1. 作業ディレクトリを */アプリ* に設定します。
    1. ポート `80` とを公開 `443` します。
    1. イメージを取得し、 `mcr.microsoft.com/dotnet/sdk:3.1` 名前をに `build` します。
    1. 作業ディレクトリを */src* に設定します。
    1. _DaprFrontEnd/DaprFrontEnd_ を *DaprFrontEnd/* という名前の新しいディレクトリにコピーします。
    1. [`dotnet restore`](../../core/tools/dotnet-restore.md)プロジェクトでを呼び出します。
    1. ルートディレクトリからイメージのルートにすべてをコピーします。
    1. 作業ディレクトリを _/src/DaprFrontEnd_ に設定します。
    1. [`dotnet build`](../../core/tools/dotnet-build.md)プロジェクトでを呼び出します。
        - **リリース** 構成をターゲットにして、 */app/build* に出力します。
    1. 既存の基本イメージから新しいビルドステージを初期化し、名前をに `build` `publish` します。
    1. `dotnet publish`プロジェクトでを呼び出します。
        - **リリース** 構成をターゲットにして、 */app/publish* に出力します。
    1. 既存の基本イメージから新しいビルドステージを初期化し、名前をに `publish` `final` します。
    1. 作業ディレクトリを */アプリ* に設定します。
    1. イメージ `/app/publish` のディレクトリを `publish` イメージのルートにコピーし `final` ます。
    1. エントリポイントをイメージとしてに設定 `dotnet` し、を `DaprFrontEnd.dll` arg として渡します。

1. `DaprBackEnd`Web API プロジェクトで、プロジェクトノードを右クリックし、[   >  **コンテナー Orchestrator サポート** の追加] を選択します。 [ **Docker Compose**] を選択し、ターゲット OS として [ **Linux** ] をもう一度選択します。

    _DaprBackEnd_ プロジェクトディレクトリのルートに、新しい *dockerfile* が作成されました。 *Dockerfile* には、次の yaml が含まれています。

    ```yml
    FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
    WORKDIR /app
    EXPOSE 80

    FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
    WORKDIR /src
    COPY ["DaprBackEnd/DaprBackEnd.csproj", "DaprBackEnd/"]
    RUN dotnet restore "DaprBackEnd/DaprBackEnd.csproj"
    COPY . .
    WORKDIR "/src/DaprBackEnd"
    RUN dotnet build "DaprBackEnd.csproj" -c Release -o /app/build

    FROM build AS publish
    RUN dotnet publish "DaprBackEnd.csproj" -c Release -o /app/publish

    FROM base AS final
    WORKDIR /app
    COPY --from=publish /app/publish .
    ENTRYPOINT ["dotnet", "DaprBackEnd.dll"]
    ```

    *Docker-compose.yml* ファイルをもう一度開き、内容を確認します。 Visual Studio によって **Docker Compose** ファイルが更新されました。 2つのサービスが含まれるようになりました。

    ```yaml
    version: '3.4'

    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
    ```

1. コンテナー化されたアプリケーション内から Dapr 構成ブロックを使用するには、作成ファイルに Dapr サイドカーコンテナーを追加する必要があります。 次の例に一致するように、 *docker-compose.yml* ファイルの内容を慎重に更新します。 書式設定と間隔に注意してください。タブは使用しません。

    ```yaml
    version: '3.4'
    
    services:
      daprfrontend:
        image: ${DOCKER_REGISTRY-}daprfrontend
        build:
          context: .
          dockerfile: DaprFrontEnd/Dockerfile
        ports:
          - "51000:50001"

      daprfrontend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprfrontend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprfrontend"

      daprbackend:
        image: ${DOCKER_REGISTRY-}daprbackend
        build:
          context: .
          dockerfile: DaprBackEnd/Dockerfile
        ports:
          - "52000:50001"

      daprbackend-dapr:
        image: "daprio/daprd:latest"
        command: [ "./daprd", "-app-id", "daprbackend", "-app-port", "80" ]
        depends_on:
          - daprfrontend
        network_mode: "service:daprbackend"
    ```

    更新されたファイルでは、 `daprfrontend-dapr` `daprbackend-dapr` サービスとサービスにそれぞれ追加されて `daprfrontend` `daprbackend` います。 更新されたファイルで、次の変更に注意してください。

    - サイドカーは、コンテナーイメージを使用し `daprio/daprd:latest` ます。 `latest`運用環境のシナリオでは、タグを使用しないことをお勧めします。 運用環境では、特定のバージョン番号を使用することをお勧めします。
    - 作成ファイルで定義されている各サービスには、ネットワークの分離を目的とした独自のネットワーク名前空間があります。 サイドカーは、 `network_mode: "service:..."` アプリケーションと同じネットワーク名前空間で実行されることを保証するために使用されます。 これにより、を使用して、サイドカーとアプリケーションが通信できるように `localhost` なります。
    - Dapr サイドカーが gRPC 通信をリッスンしているポート (既定では 50001) を公開して、sidecars が相互に通信できるようにする必要があります。

1. ソリューション (<kbd>F5</kbd> キーまたは <kbd>Ctrl + F5</kbd>キー) を実行して、予期したとおりに動作することを確認します。 すべてが正しく構成されている場合は、天気予報データが表示されます。

    :::image type="content" source="./media/getting-started/multicontainer-result.png" alt-text="気象予測データを示す最後のソリューションのスクリーンショット":::

    Docker Compose と Visual Studio 2019 を使用してローカルで実行すると、ブレークポイントを設定し、アプリケーションにデバッグできます。 運用環境のシナリオでは、Kubernetes でアプリケーションをホストすることをお勧めします。 この本には、Kubernetes にデプロイするためのスクリプトを含む、付属の参照アプリケーション [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr)が含まれています。

    このチュートリアルで使用する Dapr サービス呼び出しの構成ブロックの詳細については、 [6 章](service-invocation.md)を参照してください。

## <a name="summary"></a>まとめ

この章では、dapr ドライブを *テスト* する機会がありました。 Dapr .NET SDK を使用して、Dapr が .NET アプリケーションプラットフォームと統合されていることを確認しました。

最初の例は、Dapr state management ビルディングブロックを使用した、単純なステートフルな .NET コンソールアプリケーションです。

2番目の例では、Docker で実行されている複数コンテナーアプリケーションを使用しています。 Docker Compose で Visual Studio を使用することにより、すべての .NET アプリで使い慣れた *F5 デバッグエクスペリエンス* を利用できました。

また、Dapr コンポーネント構成ファイルについても詳しく見ていきます。 これらは、Dapr 構成要素によって使用される実際のインフラストラクチャ実装を構成します。 名前空間とスコープを使用すると、特定の環境やアプリケーションへのコンポーネントアクセスを制限できます。

今後の章では、Dapr によって提供される構成要素について詳しく説明します。

### <a name="references"></a>関連項目

- [Dapr のドキュメント-概要](https://docs.dapr.io/getting-started)
- [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr)

> [!div class="step-by-step"]
> [前へ](dapr-at-20000-feet.md)
> [次へ](reference-application.md)
