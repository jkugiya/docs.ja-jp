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
# <a name="app-startup"></a><span data-ttu-id="45e91-103">アプリの起動</span><span class="sxs-lookup"><span data-stu-id="45e91-103">App startup</span></span>

<span data-ttu-id="45e91-104">ASP.NET 用に記述されたアプリケーションには通常、HTML レンダリングと .NET 処理の両方で、どのサービスを構成して使用できるようにするかを制御する `Application_Start` イベントを定義する `global.asax.cs` ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="45e91-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="45e91-105">この章では、ASP.NET Core と Blazor Server との若干の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="45e91-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="45e91-106">Application_Start と Web Forms</span><span class="sxs-lookup"><span data-stu-id="45e91-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="45e91-107">既定の Web フォームである `Application_Start` メソッドは、多くの構成タスクに対応するために、長年にわたって拡張されています。</span><span class="sxs-lookup"><span data-stu-id="45e91-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="45e91-108">Visual Studio 2019 の既定のテンプレートを使用した新しい Web フォーム プロジェクトには、次の構成ロジックが含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="45e91-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="45e91-109">`RouteConfig` - アプリケーションの URL ルーティング</span><span class="sxs-lookup"><span data-stu-id="45e91-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="45e91-110">`BundleConfig` - CSS と JavaScript のバンドルと縮小</span><span class="sxs-lookup"><span data-stu-id="45e91-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="45e91-111">これらの各ファイルは `App_Start` フォルダーに格納され、アプリケーションの開始時に 1 回だけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="45e91-111">Each of these individual files resides in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="45e91-112">既定のプロジェクト テンプレートの `RouteConfig` では、アプリケーションの URL がファイル拡張子 `.ASPX` を省略できるように、Web フォーム用の `FriendlyUrlSettings` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="45e91-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="45e91-113">既定のテンプレートには、拡張子を省略したファイル名を持つフレンドリ URL に対して `.ASPX` ページの永続的な HTTP リダイレクト ステータス コード (HTTP 301) を提供するディレクティブも含まれています。</span><span class="sxs-lookup"><span data-stu-id="45e91-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="45e91-114">ASP.NET Core および Blazor では、これらのメソッドは単純化されて `Startup` クラスに統合されるか、一般的な Web テクノロジを優先して除去されます。</span><span class="sxs-lookup"><span data-stu-id="45e91-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="45e91-115">Blazor Server の Startup の構造</span><span class="sxs-lookup"><span data-stu-id="45e91-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="45e91-116">Blazor Server アプリケーションは、ASP.NET Core 3.0 以降のバージョン上に存在します。</span><span class="sxs-lookup"><span data-stu-id="45e91-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later version.</span></span>  <span data-ttu-id="45e91-117">ASP.NET Core Web アプリケーションは、アプリケーションのルートフォルダーにある `Startup.cs` クラスのメソッドのペアによって構成されます。</span><span class="sxs-lookup"><span data-stu-id="45e91-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="45e91-118">Startup クラスの既定のコンテンツを以下に示します</span><span class="sxs-lookup"><span data-stu-id="45e91-118">The Startup class's default content is listed below</span></span>

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

<span data-ttu-id="45e91-119">ASP.NET Core の他の部分と同様に、Startup クラスは依存関係の挿入の原則によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="45e91-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="45e91-120">`IConfiguration` はコンストラクターに提供され、後で構成中にアクセスできるようにパブリック プロパティに格納されます。</span><span class="sxs-lookup"><span data-stu-id="45e91-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="45e91-121">ASP.NET Core で導入された `ConfigureServices` メソッドを使用すると、さまざまな ASP.NET Core フレームワーク サービスを、フレームワークの組み込み依存関係挿入コンテナー用に構成できます。</span><span class="sxs-lookup"><span data-stu-id="45e91-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="45e91-122">さまざまな `services.Add*` メソッドにより、認証、Razor Pages ルーティング、MVC コントローラー ルーティング、SignalR、Blazor Server の対話など、多くの機能を有効にするサービスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="45e91-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="45e91-123">このメソッドは Web フォームでは必要ありませんでした。これは、ASPX、ASCX、ASHX、ASMX の各ファイルの解析と処理は、web.config 構成ファイルの ASP.NET を参照することによって定義されていたためです。</span><span class="sxs-lookup"><span data-stu-id="45e91-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files were defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="45e91-124">ASP.NET Core での依存関係の挿入の詳細については、 [オンライン ドキュメント](/aspnet/core/fundamentals/dependency-injection)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45e91-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="45e91-125">`Configure` メソッドには、ASP.NET Core への HTTP パイプラインの概念が導入されています。</span><span class="sxs-lookup"><span data-stu-id="45e91-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="45e91-126">このメソッドでは、アプリケーションに送信されたすべての要求を処理する[ミドルウェア](middleware.md)が完全に宣言されています。</span><span class="sxs-lookup"><span data-stu-id="45e91-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="45e91-127">既定の構成では、これらの機能のほとんどが Web フォーム構成ファイルに分散されており、今では参照しやすいように 1 か所にまとめられています。</span><span class="sxs-lookup"><span data-stu-id="45e91-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="45e91-128">カスタム エラー ページの構成は `web.config` ファイルに配置されなくなりましたが、アプリケーション環境に `Development` ラベルが付いていない場合に常に表示されるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="45e91-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="45e91-129">さらに ASP.NET Core アプリケーションは、既定で `UseHttpsRedirection` メソッド呼び出しによって、TLS によるセキュリティで保護されたページを提供するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="45e91-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="45e91-130">次に、予期しない構成メソッドが `UseStaticFiles` に示されています。</span><span class="sxs-lookup"><span data-stu-id="45e91-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="45e91-131">ASP.NET Core では、静的ファイル (JavaScript、CSS、イメージ ファイルなど) に対する要求のサポートを明示的に有効にする必要があり、アプリの *wwwroot* フォルダー内のファイルのみが既定でパブリック アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="45e91-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="45e91-132">次の行は、Web フォームからの構成オプションの 1 つをレプリケートする最初の行 `UseRouting` です。</span><span class="sxs-lookup"><span data-stu-id="45e91-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="45e91-133">このメソッドによって、パイプラインに ASP.NET Core ルーターが追加されます。これは、ここで構成することも、ルーティング先として検討できる個々のファイルで構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="45e91-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="45e91-134">ルーティング構成の詳細については、[ルーティングのセクション](pages-routing-layouts.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45e91-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="45e91-135">このメソッドの最後のステートメントでは、ASP.NET Core がリッスンするエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="45e91-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="45e91-136">これらのルートは Web アクセス可能な場所であり、ユーザーは Web サーバー上でアクセスし、.NET によって処理されてユーザーに返される一部のコンテンツを受信します。</span><span class="sxs-lookup"><span data-stu-id="45e91-136">These routes are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="45e91-137">最初のエントリ `MapBlazorHub` は、Blazor コンポーネントの状態とレンダリングが処理されるサーバーへのリアルタイムおよび永続的な接続を提供するために使用する SignalR ハブを構成します。</span><span class="sxs-lookup"><span data-stu-id="45e91-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="45e91-138">`MapFallbackToPage` メソッド呼び出しは、Blazor アプリケーションを開始し、クライアント側からのディープリンク設定要求を処理するようにアプリケーションを構成する、ページの Web アクセス可能な場所を示します。</span><span class="sxs-lookup"><span data-stu-id="45e91-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="45e91-139">この機能の動作は、ブラウザーを開き、既定のプロジェクト テンプレート内の `/counter` などのアプリケーション内の Blazor で処理されたルートに直接移動した場合に確認できます。</span><span class="sxs-lookup"><span data-stu-id="45e91-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="45e91-140">要求は *_Host.cshtml* フォールバック ページによって処理され、その後 Blazor ルーターが実行されてカウンター ページがレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="45e91-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="45e91-141">BundleConfig プロセスのアップグレード</span><span class="sxs-lookup"><span data-stu-id="45e91-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="45e91-142">CSS スタイルシートや JavaScript ファイルなどのバンドル アセットのためのテクノロジは大幅に進化しており、他のテクノロジを使用して、これらのリソースを管理するためのツールと手法が急速に進化しています。</span><span class="sxs-lookup"><span data-stu-id="45e91-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="45e91-143">このため、Grunt/Gulp/WebPack などの Node コマンドライン ツールを使用して、静的なアセットをパッケージ化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="45e91-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="45e91-144">Grunt、Gulp、および WebPack のコマンドライン ツールとそれらに関連する構成をアプリケーションに追加でき、ASP.NET Core は、アプリケーションのビルド プロセス中にこれらのファイルを自動的に無視します。</span><span class="sxs-lookup"><span data-stu-id="45e91-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="45e91-145">gulp スクリプトとそのスクリプト内の `min` ターゲットがトリガーされる次のような構文で、プロジェクト ファイル内に `Target` を追加することによって、これらのタスクを実行する呼び出しを追加できます</span><span class="sxs-lookup"><span data-stu-id="45e91-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="45e91-146">CSS ファイルと JavaScript ファイルを管理するための両方の方法の詳細については、「[ASP.NET Core での静的資産のバンドルと縮小](/aspnet/core/client-side/bundling-and-minification)」のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="45e91-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="45e91-147">[前へ](project-structure.md)
>[次へ](components.md)</span><span class="sxs-lookup"><span data-stu-id="45e91-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
