---
title: Blazor アプリのプロジェクト構造
description: ASP.NET Web Forms のプロジェクト構造と Blazor プロジェクトを比較する方法について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: ba7113c88db728f30812821deaf7c06a80663d1f
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "98189090"
---
# <a name="project-structure-for-blazor-apps"></a>Blazor アプリのプロジェクト構造

プロジェクト構造が大きく異なるにもかかわらず、ASP.NET Web Forms と Blazor には共通するさまざまな概念があります。 ここでは、Blazor プロジェクトの構造を観察し、それを ASP.NET Web Forms プロジェクトと比較します。

最初の Blazor アプリを作成するには、[Blazor の開始手順](/aspnet/core/blazor/get-started)に従ってください。 指示に従って、ASP.NET Core でホストされている Blazor サーバー アプリまたは Blazor WebAssembly アプリを作成できます。 ホスティングモデル固有のロジックを除き、両方のプロジェクトのコードはほぼ同じです。

## <a name="project-file"></a>プロジェクト ファイル

Blazor サーバー アプリは .NET プロジェクトです。 Blazor サーバー アプリのプロジェクト ファイルは、概ね次のような簡単なものです。

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Blazor WebAssembly アプリのプロジェクト ファイルは少し複雑になります (正確なバージョン番号は異なる場合があります)。

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

Blazor WebAssembly プロジェクトは、WebAssembly ベースの .NET ランタイム上のブラウザーで実行されるため、`Microsoft.NET.Sdk.Web` sdk ではなく `Microsoft.NET.Sdk.BlazorWebAssembly` をターゲットとします。 サーバーや開発者コンピューター上で行うように、.NET を Web ブラウザーにインストールすることはできません。 その結果、プロジェクトでは個別のパッケージ参照を使用して、Blazor フレームワークが参照されます。

これに対し、既定の ASP.NET Web Forms プロジェクトでは、 *.csproj* ファイルに約 300 行の XML が含まれており、そのほとんどはプロジェクト内のさまざまなコードおよびコンテンツ ファイルを明示的に示すものです。 `.NET 5` のリリースにより、`Blazor Server` および `Blazor WebAssembly` のアプリは統合された 1 つのランタイムを簡単に共有できます。

これらはサポートされていますが、個々のアセンブリ参照は .NET プロジェクトではあまり一般的ではありません。 ほとんどのプロジェクトの依存関係は、NuGet パッケージ参照として処理されます。 .NET プロジェクトの最上位レベルのパッケージの依存関係のみ参照する必要があります。 推移的な依存関係は自動的に追加されます。 ASP.NET Web Forms プロジェクトでよく見られる *packages.config* ファイルを使用してパッケージを参照するのではなく、`<PackageReference>` 要素を使用してパッケージ参照をプロジェクトファイルに追加します。

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a>エントリ ポイント

Blazor サーバー アプリのエントリ ポイントは、コンソール アプリで見られるように *Program.cs* ファイルで定義されます。 アプリを実行すると、Web アプリに固有の既定値を使用して Web ホスト インスタンスが作成されて実行されます。 Web ホストは Blazor サーバー アプリのライフサイクルを管理し、ホストレベルのサービスを設定します。 このようなサービスの例としては、構成、ログ記録、依存関係の注入、HTTP サーバーなどがあります。 このコードはほとんどが定型であり、変更されることはほとんどありません。

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

Blazor WebAssembly アプリでは、*Program.cs* でエントリ ポイントが定義されます。 コードは少し異なります。 コードは、同じホストレベルのサービスをアプリに提供するようにアプリ ホストを設定するという点で似ています。 ただし、WebAssembly アプリ ホストはブラウザーで直接実行されるため、HTTP サーバーを設定しません。

Blazor アプリには、アプリのスタートアップ ロジックを定義するための *global.asax* ファイルではなく `Startup` クラスがあります。 `Startup` クラスはアプリとアプリ固有のサービスを構成するために使用されます。 Blazor サーバーアプリでは、`Startup` クラスを使用して、クライアント ブラウザーとサーバーの間で Blazor によって使用されるリアルタイム接続のエンドポイントを設定します。 Blazor WebAssembly アプリでは、`Startup` クラスによって、アプリのルート コンポーネントと、それらをレンダリングする場所が定義されます。 `Startup` クラスについては、「[アプリの起動](./app-startup.md)」セクションで詳しく説明します。

## <a name="static-files"></a>静的ファイル

ASP.NET Web Forms プロジェクトとは異なり、Blazor プロジェクト内のすべてのファイルを静的ファイルとして要求できるわけではありません。 *wwwroot* フォルダー内のファイルのみが Web アドレスを指定できます。 このフォルダーは、アプリの "Web ルート" と呼ばれます。 アプリの Web ルート以外のものは、web アドレスを指定 "*できません*"。 このセットアップでは、プロジェクト ファイルが Web 経由で誤って公開されないようにするための追加のセキュリティレベルが提供されます。

## <a name="configuration"></a>構成

ASP.NET Web Forms アプリの構成は、通常 1 つ以上の *web.config* ファイルを使用して処理されます。 Blazor アプリには通常、*web.config* ファイルがありません。 ファイルがある場合、ファイルは IIS でホストされている場合に IIS 固有の設定を構成するためにのみ使用されます。 その代わりに、Blazor サーバー アプリは ASP.NET Core 構成の抽象化を使用します (Blazor WebAssembly アプリでは現在同じ構成の抽象化はサポートされていませんが、将来追加される機能である可能性があります)。 たとえば、既定の Blazor サーバー アプリでは、一部の設定が *appsettings.json* に格納されます。

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

ASP.NET Core プロジェクトの構成の詳細については、[構成](./config.md)セクションを参照してください。

## <a name="razor-components"></a>Razor のコンポーネント

Blazor プロジェクト内のほとんどのファイルは *.razor* ファイルです。 Razor は、Web UI を動的に生成するために使用される HTML および C# に基づくテンプレート言語です。 この *.razor* ファイルは、アプリの UI を構成するコンポーネントを定義します。 コンポーネントの大半は、Blazor サーバーと Blazor WebAssembly アプリの両方で同一です。 Blazor のコンポーネントは、ASP.NET Web Forms のユーザー コントロールに似ています。

各 Razor コンポーネント ファイルは、プロジェクトのビルド時に .NET クラスにコンパイルされます。 生成されたクラスは、コンポーネントの状態、レンダリング ロジック、ライフサイクル メソッド、イベント ハンドラー、およびその他のロジックをキャプチャします。 「[Blazor を使用して再利用可能な UI コンポーネントを構築する](./components.md)」セクションで、コンポーネントの作成について見ていきます。

*_Imports.razor* ファイルは Razor コンポーネント ファイルではありません。 代わりに、これらは同じフォルダーおよびそのサブフォルダー内の他の *.razor* ファイルにインポートする Razor ディレクティブのセットを定義します。 たとえば、 *_Imports.razor* ファイルは、一般的に使用される名前空間の `using` ディレクティブを追加する従来の方法です。

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a>ページ

Blazor アプリ内のページはどこにあるでしょうか。 Blazor では、ASP.NET Web Forms アプリの *.aspx* ファイルのように、アドレス指定可能なページに対して個別のファイル拡張子は定義されません。 代わりに、ページはコンポーネントにルートを割り当てることによって定義されます。 ルートは通常、`@page` Razor ディレクティブを使用して割り当てられます。 たとえば、*Pages/Counter.razor* ファイルで作成された `Counter` コンポーネントは、次のルートを定義します。

```razor
@page "/counter"
```

Blazor でのルーティングは、サーバー側ではなくクライアント側で処理されます。 ユーザーがブラウザーで移動すると、Blazor はナビゲーションをインターセプトし、一致するルートを使用してコンポーネントをレンダリングします。

コンポーネントのルートは、 *.aspx* ページのように、コンポーネントのファイルの場所によって現在推測されていません。 この機能は、今後追加される可能性があります。 各ルートはコンポーネント上で明示的に指定する必要があります。 ルーティング可能なコンポーネントを *Pages* フォルダーに格納することは、特別な意味を持たず、単なる慣例です。

Blazor でのルーティングの詳細については、「[ページ、ルーティング、レイアウト](./pages-routing-layouts.md)」セクションを参照してください。

## <a name="layout"></a>レイアウト

ASP.NET Web Forms アプリでは、共通ページ レイアウトはマスター ページ (*Site.Master*) を使用して処理されます。 Blazor アプリでは、ページ レイアウトはレイアウト コンポーネント (*Shared/MainLayout.razor*) を使用して処理されます。 レイアウト コンポーネントの詳細については、「[ページ、ルーティング、レイアウト](./pages-routing-layouts.md)」セクションを参照してください。

## <a name="bootstrap-blazor"></a>Blazor をブートストラップする

Blazor をブートストラップするには、アプリは次のことを行う必要があります。

- ページ上でルート コンポーネント (*App.Razor*) がレンダリングされる場所を指定します。
- 対応する Blazor フレームワーク スクリプトを追加します。

Blazor サーバー アプリでは、ルート コンポーネントのホスト ページは *_Host.cshtml* ファイルに定義されています。 このファイルはコンポーネントではなく Razor ページを定義します。 Razor ページでは Razor 構文を使用して、サーバーアドレス指定可能なページを定義します。これは *.aspx* ページと非常によく似ています。 `Html.RenderComponentAsync<TComponent>(RenderMode)` メソッドは、ルートレベルのコンポーネントをレンダリングする場所を定義するために使用されます。 `RenderMode` オプションは、コンポーネントをレンダリングする方法を示します。 次の表に、サポートされる `RenderMode` オプションについて説明します。

|オプション                        |説明       |
|------------------------------|------------------|
|`RenderMode.Server`           |ブラウザーとの接続が確立されると、対話形式でレンダリングされます|
|`RenderMode.ServerPrerendered`|最初に事前レンダリングされ、次に対話形式でレンダリングされます|
|`RenderMode.Static`           |静的コンテンツとしてレンダリングされます|

*_framework/blazor.server.js* へのスクリプト参照は、サーバーとのリアルタイム接続を確立し、次にすべてのユーザー操作と UI 更新を処理します。

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

Blazor WebAssembly アプリでは、ホスト ページは *wwwroot/index.html* の下の単純な静的 HTML ファイルです。 `<div>` という id を持つ要素 `app` は、ルート コンポーネントのレンダリング先を示すために使用されます。

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

レンダリングするルート コンポーネントは、アプリの `Program.Main` メソッドで指定され、依存関係の挿入によってサービスを登録する柔軟性があります。 詳細については、「[ASP.NET Core Blazor の依存関係の挿入](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly)」を参照してください。

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a>ビルド出力

Blazor プロジェクトをビルドされたら、すべての Razor コンポーネントとコード ファイルが 1 つのアセンブリにコンパイルされます。 ASP.NET Web Forms プロジェクトとは異なり、Blazor は UI ロジックのランタイム コンパイルをサポートしていません。

## <a name="run-the-app"></a>アプリを実行する

Blazor サーバー アプリを実行するには、Visual Studio で `F5` を押します。 Blazor アプリはランタイム コンパイルをサポートしていません。 コードとコンポーネントのマークアップの変更結果を表示するには、デバッガーがアタッチされた状態でアプリをリビルドして再起動します。 デバッガーがアタッチされていない状態で実行した場合 (`Ctrl+F5`)、Visual Studio はファイルの変更を監視し、変更が行われたときにアプリを再起動します。 変更が行われると、ブラウザーが手動で更新されます。

Blazor WebAssembly アプリを実行するには、次のいずれかの方法を選択します。

- 開発サーバーを使用して、クライアント プロジェクトを直接実行する。
- ASP.NET Core を使用してアプリをホストするときに、サーバー プロジェクトを実行する。

Blazor WebAssemblyアプリは、ブラウザーと Visual Studio の両方でデバッグできます。詳細については、「[ASP.NET Core Blazor WebAssembly をデバッグする](/aspnet/core/blazor/debug)」を参照してください。

>[!div class="step-by-step"]
>[前へ](hosting-models.md)
>[次へ](app-startup.md)
