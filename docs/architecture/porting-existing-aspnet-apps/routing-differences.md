---
title: ASP.NET MVC と ASP.NET Core でのルーティングの相違点
description: ASP.NET MVC ではルーティングがどのように定義され、実行時にどのように動作するのでしょうか? ASP.NET Core アプリではルーティングはどのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d5c18948248f03a19c97461efe3df38a5be9360b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401355"
---
# <a name="routing-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core でのルーティングの相違点

ルーティングは、受信したブラウザー要求を特定のコントローラー アクション (または Razor Pages ハンドラー) にマップする役割を担います。 このセクションでは、ASP.NET MVC (および Web API) と ASP.NET Core (MVC、Razor Pages など) とでルーティングがどのように異なるかについて説明します。

## <a name="routing-in-aspnet-mvc-and-web-api"></a>ASP.NET MVC および Web API でのルーティング

ASP.NET MVC では、ルーティングに対する 2 つのアプローチが提供されています。

1. ルート テーブル。これは、受信した要求をコントローラー アクションと照合するために使用できるルートのコレクションです。
1. 属性ルーティング。これは同じ機能を実行しますが、グローバル ルート テーブルを編集するのではなく、アクション自体を修飾することによって実現します。

## <a name="route-table"></a>ルート テーブル

ルート テーブルは、アプリの起動時に構成されます。 通常は、次のように、静的メソッド呼び出しを使用してグローバル ルート コレクションが構成されます。

```csharp
public class MvcApplication : System.Web.HttpApplication
{
    public static void RegisterRoutes(RouteCollection routes)
    {
        routes.IgnoreRoute("{resource}.axd/{*pathInfo}");
        routes.MapRoute(
            name: "Default",
            url: "{controller}/{action}/{id}",
            defaults: new { controller = "Home", action = "Index", id = "" },
            constraints: new { id = "\\d+" }
        );
    }

    protected void Application_Start()
    {
        RegisterRoutes(RouteTable.Routes);
    }
}
```

上のコードでは、ルート テーブルは `RouteCollection` 型によって管理されます。これは `MapRoute` で新しいルートを追加するために使用されます。 ルートには名前が付けられ、ルート文字列が含まれます。これにはコントローラー、アクション、区分、その他のプレースホルダーのパラメーターを含めることができます。 アプリが標準規則に従っている場合、そのアクションの大部分をこの 1 つの既定のルートで処理できますが、この規則に対する例外がある場合は追加のルートを使用して構成します。

### <a name="attribute-routing-in-aspnet-mvc"></a>ASP.NET MVC での属性ルーティング

アクションに対して定義されたルートは、外部の場所で定義されたルートよりも簡単に検出および判断できます。 属性ルーティングを使用すると、`[Route]` 属性を使用して個々のアクション メソッドにルートを定義することができます。

```csharp
public class ProductsController
{
    [Route("products")]
    public ActionResult Index()
    {
        return View();
    }

    [Route("products/{id}")]
    public ActionResult Details(int id)
    {
        return View();
    }
}
```

[ASP.NET MVC 5 の属性ルーティング](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)では、コントローラー レベルで追加できる (そして、そのコントローラー内のすべてのアクションに適用される) 既定値とプレフィックスもサポートされています。 詳細については、ドキュメントを参照してください。

属性ルーティングを設定するには、既定のルート テーブルの構成に 1 行追加する必要があります。

```csharp
routes.MapMvcAttributeRoutes();
```

属性ルーティングでは、組み込みとカスタムの両方のルート制約を利用でき、名前付きルートと、`[RouteArea]` 属性を使用した区分がサポートされます。 アプリで区分を使用する場合は、ルート登録コード内にもう 1 行を追加して、それらのサポートを構成する必要があります。

```csharp
routes.MapMvcAttributeRoutes();

AreaRegistration.RegisterAllAreas();
```

### <a name="attribute-routing-in-aspnet-web-api-2"></a>ASP.NET Web API 2 での属性ルーティング

[ASP.NET Web API 2 の属性ルーティング](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)は ASP.NET MVC 5 のルーティングに似ていますが、わずかな違いがあります。 Web API 2 の構成は、通常、アプリケーションの起動時に呼び出される独自のクラス内で行われます。 属性ルーティングの構成は、このクラス内で処理されます。

```csharp
public static class WebApiConfig
{
    public static void Register(HttpConfiguration config)
    {
        // Attribute routing.
        config.MapHttpAttributeRoutes();

        // Convention-based routing.
        config.Routes.MapHttpRoute(
            name: "DefaultApi",
            routeTemplate: "api/{controller}/{id}",
            defaults: new { id = RouteParameter.Optional }
        );
    }
}
```

上のコードに示されているように、属性ルーティングは、Web API アプリの規則ベースのルーティングと組み合わせることができます。

属性ルーティングに加えて、ASP.NET Web API では、HTTP メソッド (たとえば GET や POST など)、ルート内の `{action}` プレースホルダー (存在する場合)、アクションのパラメーターに基づいて、[呼び出すアクションを選択](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)します。 多くの場合、アクションの名前は、適切な HTTP メソッドと一致させるために "Get" または "Post" というプレフィックスが付けられているので、一致しているかどうかの判断に役立ちます。 または、適切な HTTP メソッド属性 (`[HttpGet]` など) でアクションを修飾することもできます。これにより、HTTP メソッドのプレフィックスが付いていないアクション名を使用できるようになります。

```csharp
public class ProductsController : ApiController
{
    // matched by name and (lack of) parameters
    public IEnumerable<Product> GetAll() { }

    // matched by GET and string parameter
    [HttpGet]
    public IEnumerable<Product> FindProductsByName(string name) { }
}
```

上のコントローラーの場合、`localhost:123/products/` への HTTP GET 要求は `GetAll` アクションと一致します。 `localhost:123/products?name=ardalis` への HTTP GET 要求は `FindProductsByName` アクションと一致します。

## <a name="routing-in-aspnet-core-31"></a>ASP.NET Core 3.1 でのルーティング

ASP.NET Core では、ルーティングはルーティング ミドルウェアによって処理されます。これは、受信した要求の URL をアクションまたは他のエンドポイントと照合します。 コントローラー アクションは、規則ルーティングまたは属性ルーティングでルーティングされます。 規則ルーティングは、ASP.NET MVC と Web API で使用されているルート テーブル アプローチに似ています。 規則ルーティング、属性ルーティング、またはその両方のどれを使用する場合でも、ルーティング ミドルウェアを使用するようにアプリを構成する必要があります。 ミドルウェアを使用するには、`Startup.Configure` メソッドに次のコードを追加します。

```csharp
app.UseRouting();
```

### <a name="conventional-routing"></a>規則ルーティング

規則ルーティングでは、受信した URL をアプリ内の "*エンドポイント*" と照合するために使用される 1 つ以上の規則を設定します。 ASP.NET MVC や Web API の場合と同様に、ASP.NET Core でも、コントローラー アクションをエンドポイントにすることができます。 また、Razor Pages、正常性チェック、または SignalR ハブをエンドポイントにすることもできます。 これらのルーティング可能な機能はすべて、エンドポイントを使用する同様の方法で構成されます。

```csharp
// in Startup.Configure()
app.UseEndpoints(endpoints =>
{
    endpoints.MapHealthChecks("/healthz").RequireAuthorization();
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapRazorPages();
});
```

上のコードは、正常性チェック、コントローラー、Razor Pages などのさまざまなエンドポイントを構成するために (`UseRouting` に加えて) 使用されます。 コントローラーでは、上の構成によって既定のルーティング規則が指定されます。これは、ASP.NET MVC の初期のバージョンから推奨されてきたごく標準的な `{controller}/{action}/{id?}` パターンです。

### <a name="attribute-routing"></a>属性ルーティング

ASP.NET Core での属性ルーティングは、コントローラーでルーティングを構成する際に推奨されるアプローチです。 API を構築する場合、コントローラーに `[ApiController]` 属性を適用する必要があります。 特に、この属性では、そのようなコントローラー クラス内のアクションに対して属性ルーティングを使用することが必要になります。

ASP.NET Core での属性ルーティングは、ASP.NET MVC や Web API の場合と同様に動作します。 ただし、`[Route]` 属性のサポートに加えて、ルート情報を HTTP メソッド属性の一部として指定することもできます。

```csharp
[HttpGet("api/products/{id}")]
public async ActionResult<Product> Details(int id)
{
    // ...
}
```

以前のバージョンと同様に、プレースホルダーを使用して既定のルートを指定し、これをコントローラー クラス レベルまたは基本クラスで追加することができます。 これらのすべてのケースに、同じ `[Route]` 属性を使用します。 たとえば、基本 API コントローラー クラスは次のようになります。

```csharp
[Route("api/{controller}/{action}/{id?:int}")]
public abstract class BaseApiController : ControllerBase, IApiController
{
    // ...
}
```

この属性を使用すると、この型を継承するクラスは、コントローラー名、アクション名、およびオプションの整数 `id` パラメーターに基づいて URL をルーティングします。

## <a name="references"></a>リファレンス

- [ASP.NET MVC ルーティングの概要](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/asp-net-mvc-routing-overview-cs)
- [ASP.NET MVC 5 での属性ルーティング](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)
- [ASP.NET Web API 2 での属性ルーティング](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)
- [ASP.NET Web API でのルーティングとアクションの選択](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
- [ASP.NET Core のルーティング](/aspnet/core/fundamentals/routing)
- [ASP.NET Core MVC でのコントローラー アクションへのルーティング](/aspnet/core/mvc/controllers/routing)

>[!div class="step-by-step"]
>[前へ](configuration-differences.md)
>[次へ](comparing-razor-pages-aspnet-mvc.md)
