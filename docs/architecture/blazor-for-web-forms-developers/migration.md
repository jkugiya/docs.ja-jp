---
title: ASP.NET Web Forms から Blazor への移行
description: 既存の ASP.NET Web Forms アプリを Blazor に移行する方法について説明します。
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: 893b6f851681ec540629fe160749b2622b6d5440
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509833"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>ASP.NET Web Forms から Blazor への移行

ASP.NET Web Forms から Blazor へのコード ベースの移行は、計画を必要とする時間のかかる作業です。 この章では、プロセスの概要について説明します。 移行を容易にするには、アプリが "*N 層*" アーキテクチャに準拠していることを確認し、アプリ モデル (この場合は Web Forms) をビジネス ロジックから分離するようにします。 このレイヤーを論理的に分離することにより、.NET Core と Blazor に移動する必要があるものが明確になります。

この例では、[GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) で入手できる eShop アプリが使用されています。 eShop は、フォームの入力と検証によって CRUD 機能を提供するカタログ サービスです。

なぜ、動作しているアプリを Blazor に移行する必要があるのでしょうか。 繰り返しますが、必要はありません。 ASP.NET Web Forms は、今後何年にもわたってサポートされる予定です。 ただし、Blazor で提供される機能の多くは、移行されたアプリでのみサポートされます。 そのような機能には、次のものが含まれます。

- フレームワークにおけるパフォーマンスの向上 (`Span<T>` など)
- WebAssembly として実行する機能
- Linux と macOS のクロスプラットフォーム サポート
- 他のアプリに影響を与えない、アプリ ローカルでのデプロイまたは共有フレームワークのデプロイ

これらまたは他の新機能が十分に説得力を持っている場合は、アプリの移行に価値があるかもしれません。 移行にはさまざまな形があります。アプリ全体の場合もあれば、変更を必要とする特定のエンドポイントのみの場合もあります。 移行の決定は、最終的には、開発者が解決すべきビジネス上の問題に基づいて行われます。

## <a name="server-side-versus-client-side-hosting"></a>サーバー側ホスティングとクライアント側ホスティングの比較

[ホスティング モデル](hosting-models.md)の章で説明されているように、Blazor アプリはサーバー側とクライアント側の 2 つの異なる方法でホストできます。 サーバー側モデルでは、実際のコードをサーバー上で実行しながら、ASP.NET Core SignalR 接続を使用して DOM の更新を管理します。 クライアント側モデルは、WebAssembly としてブラウザー内で実行され、サーバー接続を必要としません。 特定のアプリにどちらが最適かは、次のようないくつかの違いによって変わる可能性があります。

- WebAssembly としての実行では、現時点ですべての機能 (スレッド処理など) がサポートされているわけではありません
- クライアントとサーバーの間の頻繁な通信によって、サーバー側モードでは待機時間の問題が発生する可能性があります
- データベースおよび内部または保護されたサービスへのアクセスには、クライアント側ホスティングでは別個のサービスが必要です

このドキュメントの執筆時点では、サーバー側モデルの方が Web Forms によく似ています。 サーバー側ホスティング モデルは実稼働可能なので、この章ではそれに焦点を当てています。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する

この最初の移行手順では、新しいプロジェクトを作成します。 このプロジェクト タイプは、.NET の SDK スタイルのプロジェクトに基づいており、以前のプロジェクト形式で使用されていた定型句の多くが簡略化されます。 詳細については、[プロジェクトの構造](project-structure.md)に関する章を参照してください。

プロジェクトが作成されたら、前のプロジェクトで使用していたライブラリをインストールします。 古い Web Forms プロジェクトでは、*packages.config* ファイルを使用して、必要な NuGet パッケージを指定する場合がありました。 新しい SDK スタイルのプロジェクトでは、*packages.config* はプロジェクト ファイルの `<PackageReference>` 要素に置き換えられています。 この方法の利点は、すべての依存関係が推移的にインストールされることです。 必要な最上位の依存関係のみを指定します。

Entity Framework 6 や log4nett など、使用している依存関係の多くは .NET で利用できます。 使用可能な .NET または .NET Standard バージョンがない場合は、.NET Framework バージョンを使用できることがよくあります。 実際のメリットはケースによって異なります。 .NET では使用できない API が使用されていると、ランタイム エラーが発生します。 Visual Studio では、そのようなパッケージが通知されます。 **ソリューション エクスプローラー** で、プロジェクトの **[参照設定]** ノードに黄色いアイコンが表示されます。

Blazor ベースの eShop プロジェクトでは、インストールされているパッケージを確認できます。 以前は、プロジェクトで使用するすべてのパッケージを *packages.config* ファイルに指定していたため、ファイルはほぼ 50 行の長さになっていました。 *packages.config* のスニペットを次に示します。

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

`<packages>` 要素には、必要なすべての依存関係が含まれています。 これらのパッケージのどれが自分の必要とするものかを特定するのは困難です。 いくつかの `<package>` 要素は、必要な依存関係のニーズを満たすためだけに一覧に含まれています。

Blazor プロジェクトでは、自分の必要とする依存関係がプロジェクト ファイルの `<ItemGroup>` 要素内に一覧表示されます。

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.4.4" />
    <PackageReference Include="log4net" Version="2.0.12" />
    <PackageReference Include="Microsoft.Extensions.Logging.Log4Net.AspNetCore" Version="2.2.12" />
</ItemGroup>
```

Web Forms 開発者に役立つ NuGet パッケージの 1 つは、[Windows 互換機能パック](../../core/porting/windows-compat-pack.md)です。 .NET はクロスプラットフォームですが、一部の機能は Windows でのみ使用できます。 Windows 固有の機能は、互換機能パックをインストールすることによって利用可能になります。 このような機能の例としては、レジストリ、WMI、ディレクトリ サービスなどがあります。 このパッケージによって約 2 万の API が追加され、既に使い慣れている多くのサービスがアクティブ化されます。 eShop プロジェクトは互換性パックを必要としません。ただし、プロジェクトで Windows 固有の機能が使用されている場合は、このパッケージによって移行作業が容易になります。

## <a name="enable-startup-process"></a>スタートアップ プロセスを有効にする

Blazor のスタートアップ プロセスは、Web Forms から変更され、他の ASP.NET Core サービスの場合と同様のセットアップに従います。 サーバー側でホストされている場合、Blazor コンポーネントは通常の ASP.NET Core アプリの一部として実行されます。 WebAssembly でブラウザーにホストされている場合、Blazor コンポーネントでは類似のホスティング モデルを使用します。 違いは、コンポーネントがどのバックエンド プロセスからも独立したサービスとして実行されることです。 どちらの方法でも、スタートアップは似ています。

*Global.asax.cs* ファイルは、Web Forms プロジェクトの既定のスタートアップ ページです。 eShop プロジェクトでは、このファイルによって制御の反転 (IOC) コンテナーが構成され、アプリまたは要求のさまざまなライフサイクル イベントが処理されます。 これらのイベントの一部は、ミドルウェア (`Application_BeginRequest` など) で処理されます。 他のイベントでは、依存関係の挿入 (DI) によって特定のサービスをオーバーライドする必要があります。

たとえば、eShop の *Global.asax.cs* ファイルには、次のようなコードが含まれています。

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

上記のファイルは、サーバー側 Blazor の `Startup` クラスになります。

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

Web Forms から大きく変わった点の 1 つに、DI の突出があります。 DI は、ASP.NET Core 設計の基本原則となってきました。 ASP.NET Core フレームワークのほぼすべての側面のカスタマイズをサポートしています。 多くのシナリオで使用できる組み込みのサービス プロバイダーもあります。 さらにカスタマイズが必要な場合は、多くのコミュニティ プロジェクトによるサポートを受けることができます。 たとえば、サード パーティの DI ライブラリへの投資を進めることができます。

元の eShop アプリには、セッション管理のための構成がいくつかあります。 サーバー側 Blazor では通信に ASP.NET Core SignalR が使用され、接続が HTTP コンテキストとは関係なく発生する可能性があるため、セッション状態はサポートされません。 セッション状態を使用するアプリでは、Blazor アプリとして実行する前に再設計が必要です。

アプリの起動の詳細については、「[アプリの起動](app-startup.md)」を参照してください。

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>HTTP モジュールとハンドラーをミドルウェアに移行する

HTTP モジュールとハンドラーは、HTTP 要求パイプラインを制御するための Web Forms の一般的なパターンです。 `IHttpModule` または `IHttpHandler` を実装するクラスを登録して、受信要求を処理することができます。 Web Forms では、*web.config* ファイルでモジュールとハンドラーを構成します。 Web Forms では、アプリのライフサイクル イベント処理にも重要な基盤が置かれています。 ASP.NET Core では、代わりにミドルウェアが使用されます。 ミドルウェアは `Startup` クラスの `Configure` メソッドで登録されます。 ミドルウェアの実行順序は、登録順序によって決まります。

「[スタートアップ プロセスを有効にする](#enable-startup-process)」 セクションでは、Web Forms によってライフサイクル イベントが `Application_BeginRequest` メソッドとして生成されました。 このイベントは ASP.NET Core では使用できません。 この動作を実現する 1 つの方法は、*Startup.cs* ファイルの例のようにミドルウェアを実装することです。 このミドルウェアは同じロジックを実行し、ミドルウェア パイプライン内の次のハンドラーに制御を移します。

モジュールとハンドラーの移行の詳細については、「[HTTP ハンドラーとモジュールを ASP.NET Core ミドルウェアに移行する](/aspnet/core/migration/http-modules)」を参照してください。

## <a name="migrate-static-files"></a>静的ファイルを移行する

静的ファイル (HTML、CSS、画像、JavaScript など) を提供するには、ミドルウェアによってファイルが公開される必要があります。 `UseStaticFiles` メソッドを呼び出すと、Web ルート パスから静的ファイルを提供できるようになります。 既定の Web ルート ディレクトリは *wwwroot* ですが、カスタマイズすることができます。 eShop の `Startup` クラスの `Configure` メソッドには次のように含まれています。

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

eShop プロジェクトでは、静的ファイルの基本アクセスが有効になります。 静的ファイルのアクセスには多くのカスタマイズが用意されています。 既定のファイルまたはファイル ブラウザーを有効にする方法については、「[ASP.NET Core の静的ファイル](/aspnet/core/fundamentals/static-files)」を参照してください。

## <a name="migrate-runtime-bundling-and-minification-setup"></a>実行時のバンドルと縮小の設定を移行する

バンドルと縮小は、特定のファイル タイプを取得するサーバー要求の数とサイズを減らすためのパフォーマンス最適化手法です。 多くの場合、JavaScript と CSS では、クライアントに送信される前に何らかの形式のバンドルまたは縮小が行われます。 ASP.NET Web Forms では、これらの最適化は実行時に処理されます。 最適化規則は *App_Start/BundleConfig.cs* ファイルに定義されています。 ASP.NET Core では、より宣言的な方法が採用されています。 縮小するファイルの一覧と具体的な縮小設定が 1 つのファイルで指定されます。

バンドルと縮小の詳細については、「[ASP.NET Core での静的資産のバンドルと縮小](/aspnet/core/client-side/bundling-and-minification)」を参照してください。

## <a name="migrate-aspx-pages"></a>ASPX ページを移行する

Web Forms アプリのページは、 *.aspx* 拡張子を持つファイルです。 Web Forms ページは、多くの場合、Blazor のコンポーネントにマップできます。 Blazor コンポーネントは、 *.razor* 拡張子を持つファイルで作成されます。 eShop プロジェクトの場合、5 つのページが 1 つの Razor ページに変換されます。

たとえば、詳細ビューは、Web Forms プロジェクトの 3 つのファイル *Details.aspx*、*Details.aspx.cs*、および *Details.aspx.designer.cs* で構成されています。 Blazor への変換時に、分離コードとマークアップは *Details.razor* に結合されます。 Razor コンパイル ( *.designer.cs* ファイルの内容と同じ) は *obj* ディレクトリに格納されますが、既定では **ソリューション エクスプローラー** に表示されません。 Web Forms ページは、次のマークアップで構成されています。

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

上記のマークアップの分離コードには、次のコードが含まれています。

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

Blazor への変換時に、Web Forms ページは次のコードに変換されます。

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

コードとマークアップが同じファイル内にあることに注意してください。 必要なサービスには、`@inject` 属性を使用してアクセスできるようになります。 `@page` ディレクティブに従って、このページには `Catalog/Details/{id}` ルートでアクセスできます。 ルートの `{id}` プレースホルダーの値は、整数に制約されています。 [ルーティング](pages-routing-layouts.md)に関するセクションで説明されているように、Web Forms とは異なり、Razor コンポーネントでは、そのルートおよび含まれるすべてのパラメーターが明示的に指定されます。 多くの Web Forms コントロールには、完全に相当するものが Blazor に存在しない場合があります。 多くの場合、同等の HTML スニペットを同じ目的で使用できます。 たとえば、`<asp:Label />` コントロールは HTML の `<label>` 要素に置き換えることができます。

### <a name="model-validation-in-blazor"></a>Blazor でのモデル検証

Web Forms のコードに検証処理が含まれている場合、その多くは、ほとんど変更せずに移すことができます。 Blazor で実行する利点は、カスタム JavaScript がなくても同じ検証ロジックを実行できることです。 データ注釈を使用すると、モデル検証が容易になります。

たとえば、*Create.aspx* ページには、検証処理を含むデータ入力フォームがあります。 スニペットの例は次のようになります。

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

Blazor では、同等のマークアップが *Create.razor* ファイルで提供されます。

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

`EditForm` コンテキストには検証のサポートが含まれており、入力をラップすることができます。 データ注釈は、検証処理を追加する一般的な方法です。 このような検証のサポートは、`DataAnnotationsValidator` コンポーネントを介して追加できます。 このメカニズムの詳細については、「[ASP.NET Core Blazor のフォームと検証](/aspnet/core/blazor/forms-validation)」を参照してください。

## <a name="migrate-configuration"></a>構成の移行

Web Forms プロジェクトでは、通常、構成データは *web.config* ファイルに格納されます。 構成データには、`ConfigurationManager` を使用してアクセスします。 多くの場合、オブジェクトの解析にはサービスが必要でした。 .NET Framework 4.7.2 では、`ConfigurationBuilders` によって構成に組み立て可能性が追加されました。 これらのビルダーを使用すると、開発者はさまざまな構成ソースを追加でき、後で実行時にそれらが組み立てられて必要な値が取得されていました。

ASP.NET Core では、アプリとデプロイで使用される構成ソースを定義できる柔軟な構成システムが導入されました。 Web Forms アプリで使用されている可能性のある `ConfigurationBuilder` インフラストラクチャは、ASP.NET Core 構成システムで使用されている概念をモデルとしています。

次のスニペットは、Web Forms の eShop プロジェクトで *web.config* を使用して構成値を格納する方法を示しています。

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

データベース接続文字列などのシークレットは、*web.config* 内に格納されるのが一般的です。シークレットは必然的に、ソース管理などの安全でない場所に保持されます。 ASP.NET Core の Blazor では、上記の XML ベースの構成が次の JSON に置き換えられます。

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON は既定の構成形式ですが、ASP.NET Core では XML などの他の多くの形式がサポートされています。 コミュニティでサポートされている形式もいくつかあります。

Blazor プロジェクトの `Startup` クラスのコンストラクターは、コンストラクターの挿入と呼ばれる DI の手法を使用して、`IConfiguration` インスタンスを受け入れます。

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

既定では、環境変数、JSON ファイル (*appsettings.json* と *appsettings.{Environment}.json*)、およびコマンド ライン オプションが、有効な構成ソースとして構成オブジェクトに登録されます。 構成ソースには、`Configuration[key]` を介してアクセスできます。 より高度な手法は、オプション パターンを使用して、構成データをオブジェクトにバインドすることです。 構成とオプション パターンの詳細については、「[ASP.NET Core の構成](/aspnet/core/fundamentals/configuration/)」と「[ASP.NET Core のオプション パターン](/aspnet/core/fundamentals/configuration/options)」をそれぞれ参照してください。

## <a name="migrate-data-access"></a>データ アクセスを移行する

データ アクセスは、あらゆるアプリの重要な側面です。 eShop プロジェクトでは、カタログ情報をデータベースに格納し、Entity Framework (EF) 6 でデータを取得します。 EF 6 は .NET 5.0 でサポートされているため、プロジェクトで引き続き使用できます。

eShop には、次の EF 関連の変更が必要でした。

- .NET Framework では、`DbContext` オブジェクトは *name=ConnectionString* という形式の文字列を受け取り、`ConfigurationManager.AppSettings[ConnectionString]` からの接続文字列を使用して接続します。 .NET Core では、これはサポートされていません。 接続文字列を指定する必要があります。
- データベースは同期的にアクセスされていました。 これは機能しますが、スケーラビリティが低下する可能性があります。 このロジックを非同期パターンに移行する必要があります。

データセット バインディング用の同じネイティブ サポートは存在しませんが、Blazor では、Razor ページでの C# のサポートにより柔軟性と能力が提供されます。 たとえば、計算を実行して結果を表示できます。 Blazor のデータ パターンの詳細については、[データ アクセス](data.md)に関する章を参照してください。

## <a name="architectural-changes"></a>アーキテクチャの変更

最後に、Blazor への移行時に考慮すべき重要なアーキテクチャの違いがいくつかあります。 これらの変更の多くは、.NET Core または ASP.NET Core に基づくすべてのものに適用されます。

Blazor は .NET Core 上に構築されているため、.NET Core でのサポートを確実にする際の考慮事項があります。 主な変更点には、次の機能の削除が含まれます。

- 複数のアプリケーション ドメイン
- リモート処理
- コード アクセス セキュリティ (CAS)
- セキュリティ透過性

.NET Core での実行をサポートするために必要な変更を特定する方法の詳細については、[.NET Framework から .NET Core へのコードの移植](../../core/porting/index.md)に関するページを参照してください。

ASP.NET Core は ASP.NET を再考したバージョンであり、いくつかの変更は最初は明白でないかもしれません。 主な変更点は次のとおりです。

- 同期コンテキストがありません。つまり、`HttpContext.Current`、`Thread.CurrentPrincipal`、またはその他の静的アクセサーは存在しません
- シャドウ コピーがありません
- 要求キューがありません

ASP.NET Core の多くの操作は非同期であるため、I/O 主体のタスクを簡単にオフロードできます。 `Task.Wait()` または `Task.GetResult()` を使用してブロックしないことが重要です。使用すると、スレッド プールのリソースが急速に枯渇する可能性があります。

## <a name="migration-conclusion"></a>移行の結論

ここまで、Web Forms プロジェクトを Blazor に移行するために必要なことの例を多数見てきました。 完全な例については、[eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) プロジェクトを参照してください。

>[!div class="step-by-step"]
>[[戻る]](security-authentication-authorization.md)
