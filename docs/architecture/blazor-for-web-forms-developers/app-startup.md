---
title: アプリの起動
description: アプリのスタートアップ ロジックを定義する方法について説明します。
author: csharpfritz
ms.author: jefritz
ms.date: 11/20/2020
ms.openlocfilehash: d812079f84f67409334d07c4c10c5577446503be
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509703"
---
# <a name="app-startup"></a>アプリの起動

ASP.NET 用に記述されたアプリケーションには通常、HTML レンダリングと .NET 処理の両方で、どのサービスを構成して使用できるようにするかを制御する `Application_Start` イベントを定義する `global.asax.cs` ファイルがあります。 この章では、ASP.NET Core と Blazor Server との若干の違いについて説明します。

## <a name="application_start-and-web-forms"></a>Application_Start と Web Forms

既定の Web フォームである `Application_Start` メソッドは、多くの構成タスクに対応するために、長年にわたって拡張されています。  Visual Studio 2019 の既定のテンプレートを使用した新しい Web フォーム プロジェクトには、次の構成ロジックが含まれるようになりました。

- `RouteConfig` - アプリケーションの URL ルーティング
- `BundleConfig` - CSS と JavaScript のバンドルと縮小

これらの各ファイルは `App_Start` フォルダーに格納され、アプリケーションの開始時に 1 回だけ実行されます。  既定のプロジェクト テンプレートの `RouteConfig` では、アプリケーションの URL がファイル拡張子 `.ASPX` を省略できるように、Web フォーム用の `FriendlyUrlSettings` が追加されます。  既定のテンプレートには、拡張子を省略したファイル名を持つフレンドリ URL に対して `.ASPX` ページの永続的な HTTP リダイレクト ステータス コード (HTTP 301) を提供するディレクティブも含まれています。

ASP.NET Core および Blazor では、これらのメソッドは単純化されて `Startup` クラスに統合されるか、一般的な Web テクノロジを優先して除去されます。

## <a name="blazor-server-startup-structure"></a>Blazor Server の Startup の構造

Blazor Server アプリケーションは、ASP.NET Core 3.0 以降のバージョン上に存在します。  ASP.NET Core Web アプリケーションは、アプリケーションのルートフォルダーにある `Startup.cs` クラスのメソッドのペアによって構成されます。  Startup クラスの既定のコンテンツを以下に示します

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

ASP.NET Core の他の部分と同様に、Startup クラスは依存関係の挿入の原則によって作成されます。  `IConfiguration` はコンストラクターに提供され、後で構成中にアクセスできるようにパブリック プロパティに格納されます。

ASP.NET Core で導入された `ConfigureServices` メソッドを使用すると、さまざまな ASP.NET Core フレームワーク サービスを、フレームワークの組み込み依存関係挿入コンテナー用に構成できます。  さまざまな `services.Add*` メソッドにより、認証、Razor Pages ルーティング、MVC コントローラー ルーティング、SignalR、Blazor Server の対話など、多くの機能を有効にするサービスが追加されます。  このメソッドは Web フォームでは必要ありませんでした。これは、ASPX、ASCX、ASHX、ASMX の各ファイルの解析と処理は、web.config 構成ファイルの ASP.NET を参照することによって定義されていたためです。  ASP.NET Core での依存関係の挿入の詳細については、 [オンライン ドキュメント](/aspnet/core/fundamentals/dependency-injection)を参照してください。

`Configure` メソッドには、ASP.NET Core への HTTP パイプラインの概念が導入されています。  このメソッドでは、アプリケーションに送信されたすべての要求を処理する[ミドルウェア](middleware.md)が完全に宣言されています。 既定の構成では、これらの機能のほとんどが Web フォーム構成ファイルに分散されており、今では参照しやすいように 1 か所にまとめられています。

カスタム エラー ページの構成は `web.config` ファイルに配置されなくなりましたが、アプリケーション環境に `Development` ラベルが付いていない場合に常に表示されるように構成されています。  さらに ASP.NET Core アプリケーションは、既定で `UseHttpsRedirection` メソッド呼び出しによって、TLS によるセキュリティで保護されたページを提供するように構成されています。

次に、予期しない構成メソッドが `UseStaticFiles` に示されています。  ASP.NET Core では、静的ファイル (JavaScript、CSS、イメージ ファイルなど) に対する要求のサポートを明示的に有効にする必要があり、アプリの *wwwroot* フォルダー内のファイルのみが既定でパブリック アドレスを指定できます。

次の行は、Web フォームからの構成オプションの 1 つをレプリケートする最初の行 `UseRouting` です。  このメソッドによって、パイプラインに ASP.NET Core ルーターが追加されます。これは、ここで構成することも、ルーティング先として検討できる個々のファイルで構成することもできます。  ルーティング構成の詳細については、[ルーティングのセクション](pages-routing-layouts.md)を参照してください。

このメソッドの最後のステートメントでは、ASP.NET Core がリッスンするエンドポイントを定義します。  これらのルートは Web アクセス可能な場所であり、ユーザーは Web サーバー上でアクセスし、.NET によって処理されてユーザーに返される一部のコンテンツを受信します。  最初のエントリ `MapBlazorHub` は、Blazor コンポーネントの状態とレンダリングが処理されるサーバーへのリアルタイムおよび永続的な接続を提供するために使用する SignalR ハブを構成します。  `MapFallbackToPage` メソッド呼び出しは、Blazor アプリケーションを開始し、クライアント側からのディープリンク設定要求を処理するようにアプリケーションを構成する、ページの Web アクセス可能な場所を示します。  この機能の動作は、ブラウザーを開き、既定のプロジェクト テンプレート内の `/counter` などのアプリケーション内の Blazor で処理されたルートに直接移動した場合に確認できます。 要求は *_Host.cshtml* フォールバック ページによって処理され、その後 Blazor ルーターが実行されてカウンター ページがレンダリングされます。

## <a name="upgrading-the-bundleconfig-process"></a>BundleConfig プロセスのアップグレード

CSS スタイルシートや JavaScript ファイルなどのバンドル アセットのためのテクノロジは大幅に進化しており、他のテクノロジを使用して、これらのリソースを管理するためのツールと手法が急速に進化しています。  このため、Grunt/Gulp/WebPack などの Node コマンドライン ツールを使用して、静的なアセットをパッケージ化することをお勧めします。

Grunt、Gulp、および WebPack のコマンドライン ツールとそれらに関連する構成をアプリケーションに追加でき、ASP.NET Core は、アプリケーションのビルド プロセス中にこれらのファイルを自動的に無視します。  gulp スクリプトとそのスクリプト内の `min` ターゲットがトリガーされる次のような構文で、プロジェクト ファイル内に `Target` を追加することによって、これらのタスクを実行する呼び出しを追加できます

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

CSS ファイルと JavaScript ファイルを管理するための両方の方法の詳細については、「[ASP.NET Core での静的資産のバンドルと縮小](/aspnet/core/client-side/bundling-and-minification)」のドキュメントを参照してください。

>[!div class="step-by-step"]
>[前へ](project-structure.md)
>[次へ](components.md)
