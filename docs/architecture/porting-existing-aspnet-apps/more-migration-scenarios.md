---
title: その他の移行シナリオ
description: このセクションでは、.NET Framework アプリを .NET Core / .NET 5 にアップグレードするためのその他の移行シナリオおよび手法について説明します。
author: ardalis
ms.date: 02/11/2021
ms.openlocfilehash: c819fd42cd02da9b643873cda5f2ecf8bc21e559
ms.sourcegitcommit: 44af69720863bd09bd7a4509bf1ec119466ba6e8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2021
ms.locfileid: "106231168"
---
# <a name="more-migration-scenarios"></a>その他の移行シナリオ

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

このセクションでは、ASP.NET アプリのさまざまなシナリオについて説明し、そのそれぞれを解決するための固有の手法を示します。 このセクションを使用して、ご自分のアプリに当てはまるシナリオを特定し、ご自分のアプリとそのホスト環境にどの手法が適しているかを評価することができます。

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a>ASP.NET MVC 5 と WebApi 2 を ASP.NET Core MVC に移行する

ASP.NET MVC 5 アプリと Web API 2 アプリでの一般的なシナリオは、両方の製品を同じアプリケーションにインストールするためのものでした。 これはサポートされている比較的一般的なアプローチで、多くのチームで使用されていますが、2 つの製品で異なる抽象化が使用されるため、いくつかの余分な作業が必要になります。 たとえば、ASP.NET MVC 用のルートの設定は、`RouteCollection` に対して `MapMvcAttributeRoutes()` や `MapRoute()` などのメソッドを使用することで行います。 しかし、ASP.NET Web API 2 のルーティングは、`HttpConfiguration` と `MapHttpAttributeRoutes()` や `MapHttpRoute()` などのメソッドを使用して管理されます。

`eShopLegacyMVC` アプリには ASP.NET MVC と Web API の両方が含まれており、その `App_Start` フォルダー内には両方のルートを設定するためのメソッドが含まれています。 Autofac を使用した依存関係の挿入もサポートされており、この場合もまた、構成のために 2 組の類似した作業が必要になります。

```csharp
protected IContainer RegisterContainer()
{
    var builder = new ContainerBuilder();

    var thisAssembly = Assembly.GetExecutingAssembly();
    builder.RegisterControllers(thisAssembly);      // MVC controllers
    builder.RegisterApiControllers(thisAssembly);   // Web API controllers

    var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
    builder.RegisterModule(new ApplicationModule(mockData));

    var container = builder.Build();

    // set mvc resolver
    DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

    // set webapi resolver
    var resolver = new AutofacWebApiDependencyResolver(container);
    GlobalConfiguration.Configuration.DependencyResolver = resolver;

    return container;
}
```

これらのアプリを ASP.NET Core を使用するようにアップグレードすると、この重複した作業とそれに伴うことがある混乱を排除できます。 ASP.NET Core MVC は、ルーティング、フィルターなどに関する 1 組の規則を備えた統合フレームワークです。 依存関係の挿入は、.NET Core 自体に組み込まれています。 サンプル内の `eShopPorted` アプリで示されているように、これらすべてを `Startup.cs` 内で構成できます。

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a>HttpResponseMessage を ASP.NET Core に移行する

ASP.NET Web API アプリの中には、`HttpResponseMessage` を返すアクション メソッドが含まれているものもあります。 この型は ASP.NET Core には存在しません。 これを `Delete` アクション メソッドで使用する例を以下に示します。基本 `ApiController` に対して `ResponseMessage` ヘルパー メソッドを使用しています。

```csharp
// DELETE api/<controller>/5
[HttpDelete]
public IHttpActionResult Delete(int id)
{
    var brandToDelete = _service.GetCatalogBrands().FirstOrDefault(x => x.Id == id);
    if (brandToDelete == null)
    {
        return ResponseMessage(new HttpResponseMessage(HttpStatusCode.NotFound));
    }

    // demo only - don't actually delete
    return ResponseMessage(new HttpResponseMessage(HttpStatusCode.OK));
}
```

ASP.NET Core MVC では、すべての一般的な HTTP 応答状態コードに対して利用可能なヘルパー メソッドが存在するため、上のメソッドは次のコードに移植できます。

```csharp
[HttpDelete("{id}")]
public IActionResult Delete(int id)
{
    var brandToDelete = _service.GetCatalogBrands().FirstOrDefault(x => x.Id == id);
    if (brandToDelete == null)
    {
        return NotFound();
    }

    // demo only - don't actually delete
    return Ok();
}
```

ヘルパーが存在しないカスタム状態コードを返す必要がある場合は、常に `return StatusCode(int statusCode)` を使用して任意の数値コードを返すことができます。

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a>コンテンツ ネゴシエーションを ASP.NET Web API から ASP.NET Core に移行する

ASP.NET Web API 2 では、[コンテンツ ネゴシエーション](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)がネイティブでサポートされます。 サンプル アプリには、その結果を XML または JSON で一覧表示することでこのサポートを示す `BrandsController` が含まれています。 これは要求の `Accept` ヘッダーに基づいており、そこに `application/xml` が含まれるか `application/json` が含まれるかによって変わります。

ASP.NET MVC 5 アプリには、コンテンツ ネゴシエーションのサポートが組み込まれていません。

コンテンツ ネゴシエーションは、より柔軟性が高く、より多くのクライアントが API を利用できるようになるため、特定のエンコードの種類を返すよりも推奨されます。 現在、特定の形式を返すアクション メソッドを使用している場合は、コードを ASP.NET Core に移植するときに、コンテンツ ネゴシエーションでサポートされている結果の種類を返すようにそれらを変更することを検討する必要があります。

次のコードでは、クライアントの `Accept` ヘッダーのコンテンツに関係なく、データが JSON 形式で返されます。

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

ASP.NET Core MVC では、適切な[戻り値の型](/aspnet/core/web-api/action-return-types)が指定されていれば、[コンテンツ ネゴシエーションがネイティブでサポートされます](/aspnet/core/web-api/advanced/formatting)。 コンテンツ ネゴシエーションは、コントローラー ヘルパー メソッドによって返される状態コード固有のアクション結果で返される [ObjectResult] によって実装されます。 ASP.NET Core MVC に実装された、コンテンツ ネゴシエーションを使用する上記のアクション メソッドは次のようになります。

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

これにより、データが既定で JSON 形式で返されるようになります。 [該当するフォーマッタがアプリに構成されている場合は](/aspnet/core/web-api/advanced/formatting)、XML やその他の形式が使用されます。

## <a name="custom-model-binding"></a>カスタム モデル バインド

ほとんどの ASP.NET MVC および Web API アプリでは、モデル バインドを使用します。 既定のモデル バインド構文は、これらのアプリと ASP.NET Core MVC との間でシームレスに移行できます。 しかし、場合によっては、特定のモデルの型または使用シナリオをサポートするために、お客様が[カスタム モデル バインダー](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders)を作成していることがあります。 ASP.NET MVC および Web API プロジェクトのカスタム モデル バインダーでは、`System.Web.Mvc` および `System.Web.Http` 名前空間でそれぞれ定義されている個別の `IModelBinder` インターフェイスが使用されます。 どちらの場合も、カスタム バインダーでは、コントローラーまたはアクション コンテキストとモデル バインド コンテキストを引数として受け取る `Bind` メソッドが公開されます。

カスタム バインダーを作成したら、アプリに登録する必要があります。 この手順では、別の型 `ModelBinderProvider` を作成する必要があります。これはファクトリとして機能し、要求の間にモデル バインダーを作成します。 次に示すように、MVC アプリでは `ApplicationStart` の間にバインダーを追加できます。

```csharp
ModelBinderProviders.BinderProviders.Insert(0, new MyCustomBinderProvider()); // MVC
```

Web API アプリでは、属性を使用してカスタム バインダーを参照できます。 次に示すように、`ModelBinder` 属性をアクション メソッドのパラメーターまたはパラメーターの型定義に追加できます。

```csharp
// attribute on action method parameter
public HttpResponseMessage([ModelBinder(typeof(MyCustomBinder))] CustomDTO custom)
{
}

// attribute on type
[ModelBinder(typeof(MyCustomBinder))]
public class CustomDTO
{
}
```

ASP.NET Web API でモデル バインダーをグローバルに登録するには、アプリの起動時にそのプロバイダーを追加する必要があります。

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        var provider = new CustomModelBinderProvider(
            typeof(CustomDTO), new CustomModelBinder());
        config.Services.Insert(typeof(ModelBinderProvider), 0, provider);

        // ...
    }
}
```

[カスタム モデル プロバイダーを ASP.NET Core に](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)移行する場合、Web API パターンの方が ASP.NET MVC 5 よりも ASP.NET Core のアプローチに近くなります。 ASP.NET Core の `IModelBinder` インターフェイスと Web API のものとの主な違いは、ASP.NET Core のメソッドは非同期 (`BindModelAsync`) であり、Web API 版で必要な 2 つのパラメーターではなく、1 つの `BindingModelContext` パラメーターのみを必要とすることです。 ASP.NET Core では、個々のアクション メソッド パラメーターまたはそれらに関連付けられている型に対して `[ModelBinder]` 属性を使用できます。 また、必要に応じてアプリ内でグローバルに使用される `ModelBinderProvider` を作成することもできます。 このようなプロバイダーを構成するには、`Startup` の `ConfigureServices` にコードを追加します。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.ModelBinderProviders.Insert(0, new CustomModelBinderProvider());
    });
}
```

## <a name="media-formatters"></a>メディア フォーマッタ

ASP.NET Web API では複数のメディア形式がサポートされていて、カスタム メディア フォーマッタを使用して拡張できます。 このドキュメントでは、[CSV メディア フォーマッタの例](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter)について説明します。これを使うと、コンマ区切り値の形式でデータを送信できます。 Web API アプリでカスタム メディア フォーマッタを使用する場合は、それらを [ASP.NET Core カスタム フォーマッタ](/aspnet/core/web-api/advanced/custom-formatters)に変換する必要があります。

Web API 2 でカスタム フォーマッタを作成するためには、適切な基底クラスから継承した後、`HttpConfiguration` オブジェクトを使用して Web API パイプラインにフォーマッタを追加しました。

```csharp
public static void ConfigureApis(HttpConfiguration config)
{
    config.Formatters.Add(new ProductCsvFormatter());
}
```

ASP.NET Core でも、プロセスは似ています。 ASP.NET Core では、入力フォーマッタ (モデル バインドで使用される) と出力フォーマッタ (応答の書式設定に使用される) の両方がサポートされています。 特定の方法で出力応答にカスタム フォーマッタを追加するには、適切な基底クラスから継承し、`Startup` の MVC にフォーマッタを追加する必要があります。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.InputFormatters.Insert(0, new CustomInputFormatter());
        options.OutputFormatters.Insert(0, new CustomOutputFormatter());
    });
}
```

基底クラスの完全な一覧は、[Microsoft.AspNetCore.Mvc.Formatters](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) 名前空間にあります。

Web API フォーマッタから ASP.NET Core MVC フォーマッタに移行する手順は次のとおりです。

1. 新しいフォーマッタに適した基底クラスを特定する。
1. 基底クラスの新しいインスタンスを作成し、その必須メソッドを実装する。
1. Web API フォーマッタから新しい実装に機能をコピーする。
1. 新しいフォーマッタを使用するように、ASP.NET Core アプリの `ConfigureServices` メソッドで MVC を構成する。

## <a name="custom-filters"></a>カスタム フィルター

ASP.NET Core アプリでは、要求処理パイプラインの特定のステージの前または後にコードを実行するために、フィルターが使用されます。 ASP.NET MVC と Web API でもほぼ同じ方法でフィルターが使用されますが、細部は異なります。 たとえば、[ASP.NET MVC では 4 種類のフィルターがサポートされています](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters)。 ASP.NET Web API 2 でも同様のフィルターがサポートされており、MVC と Web API の両方に[フィルターをオーバーライドする](/dotnet/api/system.web.mvc.filters.ioverridefilter)属性が含まれています。

ASP.NET MVC と Web API アプリで使用される最も一般的なフィルターは、アクション フィルターです。これは [IActionFilter インターフェイス](/dotnet/api/system.web.mvc.iactionfilter)によって定義されます。 このインターフェイスには、前 (`OnActionExecuting`) と後 (`OnActionExecuted`) 用のメソッドが用意されています。各メソッドに示されているように、アクションの実行の前後にコードを実行するために使用できます。

ASP.NET Core でも引き続きフィルターがサポートされ、その MVC と Web API の統合は、それらの実装に対するアプローチが 1 つだけであることを意味します。 こちらの[ドキュメントには、ASP.NET Core MVC に組み込まれている 5 種類のフィルターの詳細な説明が記載されています](/aspnet/core/mvc/controllers/filters#filter-types)。 ASP.NET MVC と ASP.NET Web API でサポートされているすべてのフィルターのバリアントには、ASP.NET Core の関連バージョンがあるため、移行は通常、適切なインターフェイスや基底クラスを特定してコードを移行するだけで済みます。

同期インターフェイスに加えて、ASP.NET Core には `IAsyncActionFilter` などの非同期インターフェイスも用意されており、次に示すように、アクションの前と後両方に実行するコードを組み込むために使用できる、単一の非同期メソッドが提供されます。

```csharp
public class SampleAsyncActionFilter : IAsyncActionFilter
{
    public async Task OnActionExecutionAsync(
        ActionExecutingContext context,
        ActionExecutionDelegate next)
    {
        // Do something before the action executes.

        // next() calls the action method.
        var resultContext = await next();
        // resultContext.Result is set.
        // Do something after the action executes.
    }
}
```

非同期コード (または非同期にする必要のあるコード) を移行する場合、チームでは、この目的のために用意されている組み込みの非同期型の利用を検討する必要があります。

ほとんどの ASP.NET MVC および Web API アプリでは、多数のカスタム フィルターが使用されることはありません。 ASP.NET Core MVC でのフィルターに対するアプローチは ASP.NET MVC および Web API でのフィルターと密接に適合するため、カスタム フィルターの移行は通常、非常に簡単です。 ASP.NET Core のドキュメントに記載されているフィルターに関する詳細なドキュメントを必ずお読みください。確実に十分に理解できたら、古いシステムから新しいシステムのフィルターにロジックを移植します。

## <a name="route-constraints"></a>ルート制約

ASP.NET Core では、要求をルーティングするために、ルート制約を使用して要求が適切にルーティングされるようにします。 [ASP.NET Core では、この目的のためにさまざまなルート制約が多数サポートされています]/aspnet/core/fundamentals/routing#route-constraint-reference)。 ルート制約はルート テーブルで適用できますが、ASP.NET MVC 5 や [ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) を使用して構築されたほとんどのアプリでは、属性ルートに適用されたインライン ルート制約を使用します。 インライン ルート制約では、次のような形式を使用します。

```csharp
[Route("/customer/{id:int}")]
```

`id` ルート パラメーターの後の `:int` によって、値が `int` 型に一致するように制約されます。 ルート制約を使用する利点の 1 つは、パラメーターの型が異なるだけで他は等しい 2 つのルートが存在できるようになることです。 これにより、パラメーターの型のみに基づくルートの[メソッドのオーバーロード](/dotnet/standard/design-guidelines/member-overloading)に相当するものが可能になります。

ルート制約、その構文、および使用法のセットは、3 つのアプローチすべてにおいて非常によく似ています。 カスタム ルート制約は、お客様のアプリケーションでは非常にまれです。 アプリでカスタム ルート制約を使用していて ASP.NET Core に移植する必要がある場合は、こちらのドキュメントに [ASP.NET Core でカスタム ルート制約を作成する方法](/aspnet/core/fundamentals/routing#custom-route-constraints)を示す例が記載されています。 基本的に、必要なすべての操作は、`IRouteConstraint` とその `Match` メソッドを実装した後、アプリのルーティングを構成するときにカスタム制約を追加することだけです。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers();

    services.AddRouting(options =>
    {
        options.ConstraintMap.Add("customName", typeof(MyCustomConstraint));
    });
}
```

これは、ASP.NET Web API でカスタム制約を使用する方法とよく似ています。その場合 `IHttpRouteConstraint` を使用し、リゾルバーと `HttpConfiguration.MapHttpAttributeRoutes` への呼び出しを使用してそれを構成します。

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        var constraintResolver = new DefaultInlineConstraintResolver();
        constraintResolver.ConstraintMap.Add("nonzero", typeof(CustomConstraint));

        config.MapHttpAttributeRoutes(constraintResolver);
    }
}
```

ASP.NET MVC 5 でもよく似た方法に従います。インターフェイス名として `IRouteConstraint` を使用し、ルート構成の一部として制約を構成します。

```csharp
public class RouteConfig
{
    public static void RegisterRoutes(RouteCollection routes)
    {
        routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

        var constraintsResolver = new DefaultInlineConstraintResolver();
        constraintsResolver.ConstraintMap.Add("values", typeof(ValuesConstraint));
        routes.MapMvcAttributeRoutes(constraintsResolver);
    }
}
```

通常、ルート制約の使用方法およびカスタム ルート制約を ASP.NET Core に移行するのは、非常に簡単です。

## <a name="custom-route-handlers"></a>カスタム ルート ハンドラー

ASP.NET MVC 5 のもう 1 つのかなり高度な機能は、ルート ハンドラーです。 カスタム ルート ハンドラーでは `IRouteHandler` を実装します。これには、指定された要求に対して `IHttpHandler` を返す 1 つのメソッドが含まれています。 次に、`IHttpHandler` によって、`IsReusable` プロパティと 1 つの `ProcessRequest` メソッドが公開されます。 ASP.NET MVC 5 では、カスタム ハンドラーを使用するようにルート テーブルで特定のルートを構成することができます。

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.Add(new Route("custom", new CustomRouteHandler()));
}
```

カスタム ルート ハンドラーを ASP.NET MVC 5 から ASP.NET Core に移行する場合、フィルター (アクション フィルターなど) またはカスタムの [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter) のいずれかを使用できます。 フィルターの方法は比較的簡単であり、*Startup.cs* の `ConfigureServices` に MVC を追加するときにグローバル フィルターとして追加できます。

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(CustomActionFilter));
    });
}
```

`IRouter` オプションの場合は、インターフェイスの `RouteAsync` メソッドと `GetVirtualPath` メソッドを実装する必要があります。 カスタム ルーターは、*Startup.cs* の `Configure` メソッドで要求パイプラインに追加されます。

```csharp
public void Configure(IApplicationBuilder app)
{
    // ...
    app.UseMvc(routes =>
    {
        routes.Routes.Add(new CustomRouter(routes.DefaultHandler));
    });
}
```

ASP.NET Web API では、これらのハンドラーは [カスタム メッセージ ハンドラー](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)と呼ばれ、*ルート ハンドラー* とは呼ばれません。 メッセージ ハンドラーは `DelegatingHandler` から派生し、その `SendAsync` メソッドをオーバーライドする必要があります。 メッセージ ハンドラーを連結して、ASP.NET Core のミドルウェアおよびその要求パイプラインと非常によく似た方法でパイプラインを形成できます。

ASP.NET Core には、`DelegatingHandler` 型や、個別のメッセージ ハンドラー パイプラインがありません。 代わりに、グローバル フィルター、カスタム `IRouter` インスタンス (上記を参照)、またはカスタム ミドルウェアを使用して、そのようなハンドラーを移行する必要があります。 ASP.NET Core MVC フィルターと `IRouter` 型には、コントローラーやアクションなどの MVC 構成要素に対する組み込みアクセスを持つという利点があります。一方、ミドルウェアは MVC とは関係ない下位レベルのアプローチです。 これにより柔軟性が向上しますが、MVC の構成要素にアクセスする必要がある場合はより多くの労力が必要になります。

## <a name="cors-support"></a>CORS のサポート

CORS (クロスオリジン リソース共有) は、サーバーが、提供した応答からのものではない要求を受け入れることを許可する W3C 標準です。 ASP.NET MVC 5 および ASP.NET Web API 2 では、さまざまな方法で CORS がサポートされています。 ASP.NET MVC 5 で CORS サポートを有効にする最も簡単な方法は、次のようなアクション フィルターを使用することです。

```csharp
public class AllowCrossSiteAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext filterContext)
    {
        filterContext.RequestContext.HttpContext.Response.AddHeader(
            "Access-Control-Allow-Origin", "example.com");
        base.OnActionExecuting(filterContext);
    }
}
```

ASP.NET Web API でもこのようなフィルターを使用することができますが、[CORS を有効にするための組み込みサポート](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors)も用意されています。

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        config.EnableCors();
        // ...
    }
}
```

これを追加した後は、次のように、`EnableCors` 属性を使用して許可されたオリジン、ヘッダー、およびメソッドを構成できます。

```csharp
[EnableCors(origins: "https://dot.net", headers: "*", methods: "*")]
public class TestController : ApiController
{
    // Controller methods not shown...
}
```

ASP.NET MVC 5 または ASP.NET Web API 2 から CORS の実装を移行する前に、必ず [CORS のしくみ](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) を確認し、現在のシステムで CORS が期待どおりに動作していることを示す自動テストを作成してください。

ASP.NET Core には、CORS を有効にするための組み込みの方法が 3 つあります。

- `ConfigureServices` で[ポリシーを使用して構成する](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware)
- [エンドポイント ルーティング](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing)を使用して有効にする
- [`EnableCors` 属性](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes)を使用して有効にする

これらの各方法については、上記のオプションのリンク先のドキュメントで詳しく説明されています。 どれを選択するかは、既存のアプリで CORS がどのようにサポートされているかによって大きく異なります。 アプリで属性を使用している場合は、おそらく `EnableCors` 属性を使用するように移行するのが最も簡単です。 アプリでフィルターを使用している場合は、その方法を使用し続ける (ただしこれは ASP.NET Core で使用される一般的な方法ではありません) か、属性またはポリシーを使用するように移行することができます。 エンドポイント ルーティングは、ASP.NET Core 3 で導入された比較的新しい機能です。そのため、ASP.NET MVC 5 や ASP.NET Web API 2 アプリには同様の機能はありません。

## <a name="custom-areas"></a>カスタム エリア

多くの ASP.NET MVC アプリでは、エリアを使用してプロジェクトを整理します。 エリアは通常、プロジェクトのルートの *Areas* フォルダー内に配置し、アプリケーションの起動時に、通常は `Application_Start()` で登録する必要があります。

```csharp
AreaRegistration.RegisterAllAreas();
```

起動時にすべてのエリアを登録する代わりに、個々のコントローラーで `RouteArea` 属性を使用することもできます。

```csharp
[RouteArea("Admin")]
public class SomeController : Controller
```

エリアを使用する場合は、別のエリアにあるアクションへのリンクを生成するために、追加の引数が HTML ヘルパー メソッドに渡されます。

```cshtml
@Html.ActionLink("News", "Index", "News", new { area = "News" }, null)
```

通常、ASP.NET Web API アプリでは、エリアを明示的に使用しません。プロジェクト内の任意のフォルダーにコントローラーを配置できるためです。 チームでは、任意のフォルダー構造を使用して、使用する API コントローラーを整理することができます。

[エリア](/aspnet/core/mvc/controllers/areas)は ASP.NET Core MVC でサポートされています。 使用されるアプローチは、ASP.NET MVC 5 におけるエリアの使用とほぼ同じです。 エリアを使用したコードを移行する開発者は、次の相違点に注意してください。

- `AreaRegistration.RegisterAllAreas` は ASP.NET Core MVC では使用されません
- エリアは `[Area("name")]` 属性を使用して適用されます (ASP.NET MVC 5 のように `RouteArea` ではありません)
- 必要に応じて、ルート テーブル テンプレートにエリアを追加できます (または、属性ルーティングを使用できます)

ASP.NET Core MVC でルート テーブルにエリアのサポートを追加するには、以下を *Startup.cs* の `Configure` に追加します。

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "MyArea",
        pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");

    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

また、属性ルーティングでエリアを使用することもできます。その場合、ルート定義で `{area}` キーワードを使用します (ルート テンプレートで使用できるいくつかの[予約済みルーティング名](/aspnet/core/mvc/controllers/routing#reserved-routing-names)の 1 つです)。

タグ ヘルパーでは、`asp-area` 属性でエリアがサポートされています。これを使用して、Razor ビューおよびページ内でリンクを生成できます。

```razor
<ul>
    <li>
        <a asp-area="Products" asp-controller="Home" asp-action="About">
            Products/Home/About
        </a>
    </li>
    <li>
        <a asp-area="Services" asp-controller="Home" asp-action="About">
            Services About
        </a>
    </li>
    <li>
        <a asp-area="" asp-controller="Home" asp-action="About">
            /Home/About
        </a>
    </li>
</ul>
```

Razor Pages に移行する場合は、*Pages* フォルダー内の *Areas* フォルダーを使用する必要があります。 詳細については、「[Razor Pages でのエリア](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages)」を参照してください。

上記のガイダンスに加えて、チームでは移行計画プロセスの一環として、[ASP.NET Core のルーティングがエリアと連携するしくみ](/aspnet/core/mvc/controllers/routing#areas)を確認する必要があります。

## <a name="integration-tests-for-aspnet-mvc-and-aspnet-web-api"></a>ASP.NET MVC と ASP.NET Web API 用の統合テスト

統合テストは、アプリの異なるいくつかの部分が正しく連携して動作することを検証する自動テストです。 通常、ASP.NET MVC と ASP.NET Web API 用の統合テストを作成する場合は、実際の Web サーバー (IIS や IIS Express のローカル インスタンスなど) にアプリを配置した後、HTTP クライアントを使用してこのホストされたアプリケーションに要求を行う必要がありました。 このようなテストの一部では、[Selenium](https://www.selenium.dev/) などのブラウザー自動化ツールを使用して、クライアント側のユーザー インターフェイスと対話する場合があります。ただし、それらは多くの場合、統合テストではなく *UI テスト* と呼ばれます。

移行したアプリがその元のバージョンと同じ動作をする場合、統合テスト (および UI テスト) を実行するためにチームで使用している既存のテクノロジは、すべて以前と同じように機能し続けます。 通常、これらのテストは、テスト対象のアプリをホストするために使用されている基になるテクノロジには関心がなく、HTTP 要求を介してのみ対話が行われます。 より困難になる可能性があるのは、テストがアプリと対話し、各テストの前に既知の良好な状態になるようにする方法に関してです。 これにはいくつかの移行作業が必要になる場合があります。ASP.NET Core では、ASP.NET MVC や ASP.NET Web API と比較して、構成と起動が大きく異なるためです。

[ASP.NET Core の組み込み統合テスト](/aspnet/core/test/integration-tests) サポートを使用するように統合テストを移行することを強くお勧めします。 ASP.NET Core では、アプリを `TestHost` に配置することで、アプリをテストできます。これは `WebApplicationFactory` を使用して構成されます。 テスト用にアプリをホストするために必要なセットアップが少しありますが、一度設定すれば、個々の統合テストの作成が非常に簡単になります。

ASP.NET Core の統合テスト サポートの最も優れた機能の 1 つは、アプリがメモリ内でホストされることです。 アプリをホストするために実際の Web サーバーを構成する必要はありません。 ブラウザー自動化ツールを使用する必要はありません (ASP.NET Core のみをテストし、クライアント側の動作はテストしない場合)。 ファイアウォールの問題やプロセスの開始と停止に関する問題など、自動化された統合テストのために実際の Web サーバーを使用しようとしたときに発生する可能性のある問題の多くが、この方法によって排除されます。 また、要求はすべてメモリ内で、ネットワーク要件なしで作成されるため、個別の Web サーバーを設定して (同じコンピューター上で実行されていても) ネットワーク経由で通信する必要があるテストよりも、テストの実行がずっと高速になる傾向があります。

[eShopOnWeb 参照アプリケーション](https://github.com/dotnet-architecture/eShopOnWeb)からの ASP.NET Core 統合テスト (下位レベルの統合テストと区別するため "*機能テスト*" と呼ばれることもあります) の例を次に示します。

```csharp
public class GetByIdEndpoint : IClassFixture<ApiTestFixture>
{
    JsonSerializerOptions _jsonOptions = new JsonSerializerOptions { PropertyNameCaseInsensitive = true };

    public GetByIdEndpoint(ApiTestFixture factory)
    {
        Client = factory.CreateClient();
    }

    public HttpClient Client { get; }

    [Fact]
    public async Task ReturnsItemGivenValidId()
    {
        var response = await Client.GetAsync("api/catalog-items/5");
        response.EnsureSuccessStatusCode();
        var stringResponse = await response.Content.ReadAsStringAsync();
        var model = stringResponse.FromJson<GetByIdCatalogItemResponse>();

        Assert.Equal(5, model.CatalogItem.Id);
        Assert.Equal("Roslyn Red Sheet", model.CatalogItem.Name);
    }
}
```

移行しているアプリに統合テストがない場合、移行プロセスはそれらを追加する良い機会となります。 これらのテストでは、移行されたアプリがチームの想定どおりに動作することを確認できます。 このようなテストを移行の早い段階で実行すると、後の移行作業によってアプリの以前に移行された部分が破損しないようにすることができます。 ASP.NET Core で統合テストを設定して実行するのがいかに簡単であるかを考えると、通常、そのようなテストの設定に費やした投資に対する利益は、非常に高くなります。

## <a name="wcf-client-configuration"></a>WCF クライアントの構成

アプリで現在、クライアントとして WCF サービスに依存している場合、このシナリオはサポートされます。 ただし、*web.config* から新しい *appsettings.json* ファイルを使用するように[構成を移行する](/aspnet/core/migration/configuration)必要があります。 別の方法として、クライアントの作成時にプログラムによって必要な構成を追加することもできます。 次に例を示します。

```csharp
var wcfClient = new OrderServiceClient(
    new BasicHttpBinding(BasicHttpSecurityMode.None),
    new EndpointAddress("http://localhost:5050/OrderService.svc"));
```

アプリが依存している、WCF を使用して構築された広範なサービスが組織にある場合は、代わりに gRPC を使用するように移行することを検討してください。 gRPC の詳細、移行が必要な理由、および詳細な移行ガイドについては、[WCF 開発者向け gRPC](/dotnet/architecture/grpc-for-wcf-developers/) に関する電子ブックを参照してください。

## <a name="references"></a>References

- [ASP.NET Web API のコンテンツ ネゴシエーション](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [ASP.NET Core Web API の応答データの書式設定](/aspnet/core/web-api/advanced/formatting)
- [ASP.NET Web API のカスタム モデル バインダー](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders)
- [ASP.NET Core のカスタム モデル バインダー](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)
- [ASP.NET Web API 2 のメディア フォーマッタ](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)\
- [ASP.NET Core Web API のカスタム フォーマッタ](/aspnet/core/web-api/advanced/custom-formatters)
- [ASP.NET Core フィルター](/aspnet/core/mvc/controllers/filters)
- [ASP.NET Web API 2 のルート制約](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints)
- [ASP.NET MVC 5 のルート制約](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/#route-constraints)
- [ASP.NET Core ルート制約のリファレンス](/aspnet/core/fundamentals/routing#route-constraint-reference)
- [ASP.NET Web API 2 のカスタム メッセージ ハンドラー](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)
- [MVC 5 と Web API 2 のシンプルな CORS コントロール](https://stackoverflow.com/questions/6290053/setting-access-control-allow-origin-in-asp-net-mvc-simplest-possible-method)
- [Web API でクロスオリジン要求を有効にする](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors)
- [ASP.NET Core でクロスオリジン要求 (CORS) を有効にする](/aspnet/core/security/cors)
- [ASP.NET Core の区分](/aspnet/core/mvc/controllers/areas)
- [ASP.NET Core での統合テスト](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
>[前へ](example-migration-eshop.md)
>[次へ](deployment-scenarios.md)
