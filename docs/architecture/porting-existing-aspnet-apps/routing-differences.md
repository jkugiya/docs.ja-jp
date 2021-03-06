---
title: ASP.NET MVC と ASP.NET Core 間のルーティングの違い
description: ルーティングはどのように定義され、ASP.NET MVC で実行時にどのように動作しますか。 ASP.NET Core アプリでのルーティングの違い
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: d5c18948248f03a19c97461efe3df38a5be9360b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401355"
---
# <a name="routing-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core 間のルーティングの違い

ルーティングは、受信ブラウザー要求を特定のコントローラーアクション (または Razor Pages ハンドラー) にマップする役割を担います。 このセクションでは、ASP.NET MVC (および Web API) と ASP.NET Core (MVC、Razor Pages など) の間でルーティングがどのように異なるかについて説明します。

## <a name="routing-in-aspnet-mvc-and-web-api"></a>ASP.NET MVC と Web API でのルーティング

ASP.NET MVC では、2つのルーティング方法を提供しています。

1. ルートテーブル。これは、着信要求をコントローラーアクションと照合するために使用できるルートのコレクションです。
1. 属性ルーティング。これは、同じ機能を実行しますが、グローバルルートテーブルを編集するのではなく、アクション自体を修飾することで実現されます。

## <a name="route-table"></a>ルート テーブル

ルートテーブルは、アプリの起動時に構成されます。 通常、次のように、静的なメソッド呼び出しを使用してグローバルルートコレクションを構成します。

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

前のコードでは、ルートテーブルは型によって管理されてい `RouteCollection` ます。これは、で新しいルートを追加するために使用され `MapRoute` ます。 ルートにはという名前が付けられ、ルート文字列が含まれます。これには、コントローラー、アクション、領域、およびその他のプレースホルダーのパラメーターを含めることができます。 アプリが標準規則に準拠している場合、その操作のほとんどは、この単一の既定ルートで処理できます。この規則に対する例外は、追加のルートを使用して構成します。

### <a name="attribute-routing-in-aspnet-mvc"></a>ASP.NET MVC での属性ルーティング

アクションを使用して定義されたルートは、外部の場所で定義されているルートよりも検出が容易であることがわかります。 属性ルーティングを使用すると、個々のアクションメソッドは、属性を使用して定義されたルートを持つことができ `[Route]` ます。

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

[ASP.NET MVC 5 の属性ルーティングで](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) は、既定とプレフィックスもサポートされています。これはコントローラーレベルで追加できます (そのコントローラー内のすべてのアクションに適用されます)。 詳細については、ドキュメントを参照してください。

属性ルーティングを設定するには、既定のルートテーブル構成に1行追加する必要があります。

```csharp
routes.MapMvcAttributeRoutes();
```

属性ルーティングでは、組み込みとカスタムの両方のルート制約を利用し、属性を使用して名前付きのルートと区分をサポートでき `[RouteArea]` ます。 アプリで区分を使用する場合は、もう1行を追加することで、ルート登録コードでそれらのサポートを構成する必要があります。

```csharp
routes.MapMvcAttributeRoutes();

AreaRegistration.RegisterAllAreas();
```

### <a name="attribute-routing-in-aspnet-web-api-2"></a>ASP.NET Web API 2 での属性ルーティング

[ASP.NET Web API 2 の属性ルーティング](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) は ASP.NET MVC 5 でのルーティングに似ていますが、わずかな違いがあります。 Web API 2 の構成は、通常、アプリケーションの起動時に呼び出される独自のクラスで行われます。 属性ルーティングの構成は、次のクラスで処理されます。

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

前のコードに示されているように、属性ルーティングは、Web API apps の規則ベースのルーティングと組み合わせることができます。

ASP.NET Web API は、属性ルーティングに加えて、HTTP メソッド (GET または POST)、ルート内のプレースホルダー (存在する場合)、アクションのパラメーターに基づいて、 [どのアクションを呼び出す](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) かを選択し `{action}` ます。 多くの場合、アクション名は "Get" または "Post" にプレフィックスを付けることによって、適切な HTTP メソッドを一致させるために、一致するかどうかを判断するのに役立ちます。 または、のように適切な HTTP メソッド属性を使用してアクションを装飾することもでき `[HttpGet]` ます。これにより、プレフィックスのないアクション名を http メソッドで使用できるようになります。

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

上記のコントローラーの場合、アクションと一致する HTTP GET 要求 `localhost:123/products/` `GetAll` 。 `localhost:123/products?name=ardalis`アクションと一致する HTTP GET 要求 `FindProductsByName` 。

## <a name="routing-in-aspnet-core-31"></a>ASP.NET Core 3.1 でのルーティング

ASP.NET Core では、ルーティングはルーティングミドルウェアによって処理されます。これは、アクションまたは他のエンドポイントへの受信要求の Url と一致します。 コントローラーアクションは、通常はルーティングまたは属性ルーティングです。 従来のルーティングは、ASP.NET MVC および Web API で使用されるルートテーブルアプローチに似ています。 従来の、属性、またはその両方を使用しているかどうかにかかわらず、ルーティングミドルウェアを使用するようにアプリを構成する必要があります。 ミドルウェアを使用するには、メソッドに次のコードを追加し `Startup.Configure` ます。

```csharp
app.UseRouting();
```

### <a name="conventional-routing"></a>規則ルーティング

従来のルーティングでは、受信 Url をアプリ内の *エンドポイント* に一致させるために使用される1つ以上の規則を設定します。 ASP.NET Core では、これらのエンドポイントは、ASP.NET MVC や Web API などのコントローラーアクションである場合があります。 エンドポイントは、Razor Pages、正常性チェック、または SignalR ハブにすることもできます。 これらのルーティング可能な機能はすべて、エンドポイントを使用して同様の方法で構成されます。

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

上のコード (に加えて) を使用して、 `UseRouting` 正常性チェック、コントローラー、Razor Pages などのさまざまなエンドポイントを構成します。 コントローラーでは、上記の構成で既定のルーティング規則が指定されています。これは、 `{controller}/{action}/{id?}` ASP.NET MVC の最初のバージョン以降に推奨されるかなり標準的なパターンです。

### <a name="attribute-routing"></a>属性ルーティング

ASP.NET Core の属性ルーティングは、コントローラーでルーティングを構成するために推奨される方法です。 Api を作成している場合は、 `[ApiController]` 属性をコントローラーに適用する必要があります。 特に、この属性では、このようなコントローラークラスのアクションに対して属性ルーティングを使用する必要があります。

ASP.NET Core の属性ルーティングは、ASP.NET MVC と Web API でも同様に動作します。 ただし、属性をサポートするだけで `[Route]` なく、ルート情報を HTTP メソッド属性の一部として指定することもできます。

```csharp
[HttpGet("api/products/{id}")]
public async ActionResult<Product> Details(int id)
{
    // ...
}
```

以前のバージョンと同様に、プレースホルダーを使用して既定のルートを指定し、これをコントローラークラスレベルまたは基本クラスでも追加できます。 `[Route]`これらのすべてのケースで同じ属性を使用します。 たとえば、基本 API コントローラークラスは次のようになります。

```csharp
[Route("api/{controller}/{action}/{id?:int}")]
public abstract class BaseApiController : ControllerBase, IApiController
{
    // ...
}
```

この属性を使用すると、この型を継承するクラスは、コントローラー名、アクション名、および省略可能な整数パラメーターに基づいて、アクションに Url をルーティングし `id` ます。

## <a name="references"></a>関連項目

- [ASP.NET MVC ルーティングの概要](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/asp-net-mvc-routing-overview-cs)
- [ASP.NET MVC 5 での属性ルーティング](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)
- [ASP.NET Web API 2 での属性ルーティング](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)
- [ASP.NET Web API でのルーティングとアクションの選択](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
- [ASP.NET Core のルーティング](/aspnet/core/fundamentals/routing)
- [ASP.NET Core MVC でのコントローラーアクションへのルーティング](/aspnet/core/mvc/controllers/routing)

>[!div class="step-by-step"]
>[前へ](configuration-differences.md)
>[次へ](comparing-razor-pages-aspnet-mvc.md)
