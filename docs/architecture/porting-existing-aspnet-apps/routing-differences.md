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
# <a name="routing-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="0815e-104">ASP.NET MVC と ASP.NET Core 間のルーティングの違い</span><span class="sxs-lookup"><span data-stu-id="0815e-104">Routing differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="0815e-105">ルーティングは、受信ブラウザー要求を特定のコントローラーアクション (または Razor Pages ハンドラー) にマップする役割を担います。</span><span class="sxs-lookup"><span data-stu-id="0815e-105">Routing is responsible for mapping incoming browser requests to particular controller actions (or Razor Pages handlers).</span></span> <span data-ttu-id="0815e-106">このセクションでは、ASP.NET MVC (および Web API) と ASP.NET Core (MVC、Razor Pages など) の間でルーティングがどのように異なるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0815e-106">This section covers how routing differs between ASP.NET MVC (and Web API) and ASP.NET Core (MVC, Razor Pages, and otherwise).</span></span>

## <a name="routing-in-aspnet-mvc-and-web-api"></a><span data-ttu-id="0815e-107">ASP.NET MVC と Web API でのルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-107">Routing in ASP.NET MVC and Web API</span></span>

<span data-ttu-id="0815e-108">ASP.NET MVC では、2つのルーティング方法を提供しています。</span><span class="sxs-lookup"><span data-stu-id="0815e-108">ASP.NET MVC offers two approaches to routing:</span></span>

1. <span data-ttu-id="0815e-109">ルートテーブル。これは、着信要求をコントローラーアクションと照合するために使用できるルートのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="0815e-109">The route table, which is a collection of routes that can be used to match incoming requests to controller actions.</span></span>
1. <span data-ttu-id="0815e-110">属性ルーティング。これは、同じ機能を実行しますが、グローバルルートテーブルを編集するのではなく、アクション自体を修飾することで実現されます。</span><span class="sxs-lookup"><span data-stu-id="0815e-110">Attribute routing, which performs the same function but is achieved by decorating the actions themselves, rather than editing a global route table.</span></span>

## <a name="route-table"></a><span data-ttu-id="0815e-111">ルート テーブル</span><span class="sxs-lookup"><span data-stu-id="0815e-111">Route table</span></span>

<span data-ttu-id="0815e-112">ルートテーブルは、アプリの起動時に構成されます。</span><span class="sxs-lookup"><span data-stu-id="0815e-112">The route table is configured when the app starts up.</span></span> <span data-ttu-id="0815e-113">通常、次のように、静的なメソッド呼び出しを使用してグローバルルートコレクションを構成します。</span><span class="sxs-lookup"><span data-stu-id="0815e-113">Typically, a static method call is used to configure the global route collection, like so:</span></span>

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

<span data-ttu-id="0815e-114">前のコードでは、ルートテーブルは型によって管理されてい `RouteCollection` ます。これは、で新しいルートを追加するために使用され `MapRoute` ます。</span><span class="sxs-lookup"><span data-stu-id="0815e-114">In the preceding code, the route table is managed by the `RouteCollection` type, which is used to add new routes with `MapRoute`.</span></span> <span data-ttu-id="0815e-115">ルートにはという名前が付けられ、ルート文字列が含まれます。これには、コントローラー、アクション、領域、およびその他のプレースホルダーのパラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0815e-115">Routes are named and include a route string, which can include parameters for controllers, actions, areas, and other placeholders.</span></span> <span data-ttu-id="0815e-116">アプリが標準規則に準拠している場合、その操作のほとんどは、この単一の既定ルートで処理できます。この規則に対する例外は、追加のルートを使用して構成します。</span><span class="sxs-lookup"><span data-stu-id="0815e-116">If an app follows a standard convention, most of its actions can be handled by this single default route, with any exceptions to this convention configured using additional routes.</span></span>

### <a name="attribute-routing-in-aspnet-mvc"></a><span data-ttu-id="0815e-117">ASP.NET MVC での属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-117">Attribute routing in ASP.NET MVC</span></span>

<span data-ttu-id="0815e-118">アクションを使用して定義されたルートは、外部の場所で定義されているルートよりも検出が容易であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="0815e-118">Routes that are defined with their actions may be easier to discover and reason about than routes defined in an external location.</span></span> <span data-ttu-id="0815e-119">属性ルーティングを使用すると、個々のアクションメソッドは、属性を使用して定義されたルートを持つことができ `[Route]` ます。</span><span class="sxs-lookup"><span data-stu-id="0815e-119">Using attribute routing, an individual action method can have its route defined with a `[Route]` attribute:</span></span>

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

<span data-ttu-id="0815e-120">[ASP.NET MVC 5 の属性ルーティングで](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) は、既定とプレフィックスもサポートされています。これはコントローラーレベルで追加できます (そのコントローラー内のすべてのアクションに適用されます)。</span><span class="sxs-lookup"><span data-stu-id="0815e-120">[Attribute routing in ASP.NET MVC 5](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) also supports defaults and prefixes, which can be added at the controller level (and which are applied to all actions within that controller).</span></span> <span data-ttu-id="0815e-121">詳細については、ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0815e-121">Refer to the documentation for details.</span></span>

<span data-ttu-id="0815e-122">属性ルーティングを設定するには、既定のルートテーブル構成に1行追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0815e-122">Setting up attribute routing requires adding one line to the default route table configuration:</span></span>

```csharp
routes.MapMvcAttributeRoutes();
```

<span data-ttu-id="0815e-123">属性ルーティングでは、組み込みとカスタムの両方のルート制約を利用し、属性を使用して名前付きのルートと区分をサポートでき `[RouteArea]` ます。</span><span class="sxs-lookup"><span data-stu-id="0815e-123">Attribute routing can take advantage of route constraints, both built-in and custom, and supports named routes and areas using the `[RouteArea]` attribute.</span></span> <span data-ttu-id="0815e-124">アプリで区分を使用する場合は、もう1行を追加することで、ルート登録コードでそれらのサポートを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0815e-124">If your app uses areas, you'll need to configure support for them in your route registration code by adding one more line:</span></span>

```csharp
routes.MapMvcAttributeRoutes();

AreaRegistration.RegisterAllAreas();
```

### <a name="attribute-routing-in-aspnet-web-api-2"></a><span data-ttu-id="0815e-125">ASP.NET Web API 2 での属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-125">Attribute routing in ASP.NET Web API 2</span></span>

<span data-ttu-id="0815e-126">[ASP.NET Web API 2 の属性ルーティング](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) は ASP.NET MVC 5 でのルーティングに似ていますが、わずかな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="0815e-126">[Attribute routing in ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) is similar to routing in ASP.NET MVC 5, with minor differences.</span></span> <span data-ttu-id="0815e-127">Web API 2 の構成は、通常、アプリケーションの起動時に呼び出される独自のクラスで行われます。</span><span class="sxs-lookup"><span data-stu-id="0815e-127">Configuring Web API 2 is typically done in its own class, which is called during app startup.</span></span> <span data-ttu-id="0815e-128">属性ルーティングの構成は、次のクラスで処理されます。</span><span class="sxs-lookup"><span data-stu-id="0815e-128">Attribute routing configuration is handled in this class:</span></span>

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

<span data-ttu-id="0815e-129">前のコードに示されているように、属性ルーティングは、Web API apps の規則ベースのルーティングと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="0815e-129">As shown in the preceding code, attribute routing may be combined with convention-based routing in Web API apps.</span></span>

<span data-ttu-id="0815e-130">ASP.NET Web API は、属性ルーティングに加えて、HTTP メソッド (GET または POST)、ルート内のプレースホルダー (存在する場合)、アクションのパラメーターに基づいて、 [どのアクションを呼び出す](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) かを選択し `{action}` ます。</span><span class="sxs-lookup"><span data-stu-id="0815e-130">In addition to attribute routing, [ASP.NET Web API chooses which action to call](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) based on the HTTP method (for example, GET or POST), the `{action}` placeholder in a route (if any), and parameters of the action.</span></span> <span data-ttu-id="0815e-131">多くの場合、アクション名は "Get" または "Post" にプレフィックスを付けることによって、適切な HTTP メソッドを一致させるために、一致するかどうかを判断するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0815e-131">In many cases, the name of the action will help determine whether it's matched, since prefixing the action name with "Get" or "Post" is used to match the appropriate HTTP method to it.</span></span> <span data-ttu-id="0815e-132">または、のように適切な HTTP メソッド属性を使用してアクションを装飾することもでき `[HttpGet]` ます。これにより、プレフィックスのないアクション名を http メソッドで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0815e-132">Alternatively, actions can be decorated with an appropriate HTTP method attribute, like `[HttpGet]`, allowing the use of action names that aren't prefixed with an HTTP method.</span></span>

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

<span data-ttu-id="0815e-133">上記のコントローラーの場合、アクションと一致する HTTP GET 要求 `localhost:123/products/` `GetAll` 。</span><span class="sxs-lookup"><span data-stu-id="0815e-133">Given the above controller, an HTTP GET request to `localhost:123/products/` matches the `GetAll` action.</span></span> <span data-ttu-id="0815e-134">`localhost:123/products?name=ardalis`アクションと一致する HTTP GET 要求 `FindProductsByName` 。</span><span class="sxs-lookup"><span data-stu-id="0815e-134">An HTTP GET request to `localhost:123/products?name=ardalis` matches the `FindProductsByName` action.</span></span>

## <a name="routing-in-aspnet-core-31"></a><span data-ttu-id="0815e-135">ASP.NET Core 3.1 でのルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-135">Routing in ASP.NET Core 3.1</span></span>

<span data-ttu-id="0815e-136">ASP.NET Core では、ルーティングはルーティングミドルウェアによって処理されます。これは、アクションまたは他のエンドポイントへの受信要求の Url と一致します。</span><span class="sxs-lookup"><span data-stu-id="0815e-136">In ASP.NET Core, routing is handled by routing middleware, which matches the URLs of incoming requests to actions or other endpoints.</span></span> <span data-ttu-id="0815e-137">コントローラーアクションは、通常はルーティングまたは属性ルーティングです。</span><span class="sxs-lookup"><span data-stu-id="0815e-137">Controller actions are either conventionally routed or attribute-routed.</span></span> <span data-ttu-id="0815e-138">従来のルーティングは、ASP.NET MVC および Web API で使用されるルートテーブルアプローチに似ています。</span><span class="sxs-lookup"><span data-stu-id="0815e-138">Conventional routing is similar to the route table approach used in ASP.NET MVC and Web API.</span></span> <span data-ttu-id="0815e-139">従来の、属性、またはその両方を使用しているかどうかにかかわらず、ルーティングミドルウェアを使用するようにアプリを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0815e-139">Whether you're using conventional, attribute, or both, you need to configure your app to use the routing middleware.</span></span> <span data-ttu-id="0815e-140">ミドルウェアを使用するには、メソッドに次のコードを追加し `Startup.Configure` ます。</span><span class="sxs-lookup"><span data-stu-id="0815e-140">To use the middleware, add the following code to your `Startup.Configure` method:</span></span>

```csharp
app.UseRouting();
```

### <a name="conventional-routing"></a><span data-ttu-id="0815e-141">規則ルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-141">Conventional routing</span></span>

<span data-ttu-id="0815e-142">従来のルーティングでは、受信 Url をアプリ内の *エンドポイント* に一致させるために使用される1つ以上の規則を設定します。</span><span class="sxs-lookup"><span data-stu-id="0815e-142">With conventional routing, you set up one or more conventions that will be used to match incoming URLs to *endpoints* in the app.</span></span> <span data-ttu-id="0815e-143">ASP.NET Core では、これらのエンドポイントは、ASP.NET MVC や Web API などのコントローラーアクションである場合があります。</span><span class="sxs-lookup"><span data-stu-id="0815e-143">In ASP.NET Core, these endpoints may be controller actions, like in ASP.NET MVC or Web API.</span></span> <span data-ttu-id="0815e-144">エンドポイントは、Razor Pages、正常性チェック、または SignalR ハブにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0815e-144">The endpoints could also be Razor Pages, Health Checks, or SignalR hubs.</span></span> <span data-ttu-id="0815e-145">これらのルーティング可能な機能はすべて、エンドポイントを使用して同様の方法で構成されます。</span><span class="sxs-lookup"><span data-stu-id="0815e-145">All of these routable features are configured in a similar fashion using endpoints:</span></span>

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

<span data-ttu-id="0815e-146">上のコード (に加えて) を使用して、 `UseRouting` 正常性チェック、コントローラー、Razor Pages などのさまざまなエンドポイントを構成します。</span><span class="sxs-lookup"><span data-stu-id="0815e-146">The preceding code is used (in addition to `UseRouting`) to configure various endpoints, including Health Checks, controllers, and Razor Pages.</span></span> <span data-ttu-id="0815e-147">コントローラーでは、上記の構成で既定のルーティング規則が指定されています。これは、 `{controller}/{action}/{id?}` ASP.NET MVC の最初のバージョン以降に推奨されるかなり標準的なパターンです。</span><span class="sxs-lookup"><span data-stu-id="0815e-147">For controllers, the above configuration specifies a default routing convention, which is the fairly standard `{controller}/{action}/{id?}` pattern that's been recommended since the first versions of ASP.NET MVC.</span></span>

### <a name="attribute-routing"></a><span data-ttu-id="0815e-148">属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-148">Attribute routing</span></span>

<span data-ttu-id="0815e-149">ASP.NET Core の属性ルーティングは、コントローラーでルーティングを構成するために推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="0815e-149">Attribute routing in ASP.NET Core is the preferred approach for configuring routing in controllers.</span></span> <span data-ttu-id="0815e-150">Api を作成している場合は、 `[ApiController]` 属性をコントローラーに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0815e-150">If you're building APIs, the `[ApiController]` attribute should be applied to your controllers.</span></span> <span data-ttu-id="0815e-151">特に、この属性では、このようなコントローラークラスのアクションに対して属性ルーティングを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0815e-151">Among other things, this attribute requires the use of attribute routing for actions in such controller classes.</span></span>

<span data-ttu-id="0815e-152">ASP.NET Core の属性ルーティングは、ASP.NET MVC と Web API でも同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="0815e-152">Attribute routing in ASP.NET Core behaves similarly in ASP.NET MVC and Web API.</span></span> <span data-ttu-id="0815e-153">ただし、属性をサポートするだけで `[Route]` なく、ルート情報を HTTP メソッド属性の一部として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="0815e-153">In addition to supporting the `[Route]` attribute, however, route information can also be specified as part of the HTTP method attribute:</span></span>

```csharp
[HttpGet("api/products/{id}")]
public async ActionResult<Product> Details(int id)
{
    // ...
}
```

<span data-ttu-id="0815e-154">以前のバージョンと同様に、プレースホルダーを使用して既定のルートを指定し、これをコントローラークラスレベルまたは基本クラスでも追加できます。</span><span class="sxs-lookup"><span data-stu-id="0815e-154">As with previous versions, you can specify a default route with placeholders, and add this at the controller class level or even on a base class.</span></span> <span data-ttu-id="0815e-155">`[Route]`これらのすべてのケースで同じ属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="0815e-155">You use the same `[Route]` attribute for all of these cases.</span></span> <span data-ttu-id="0815e-156">たとえば、基本 API コントローラークラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0815e-156">For example, a base API controller class might look like this:</span></span>

```csharp
[Route("api/{controller}/{action}/{id?:int}")]
public abstract class BaseApiController : ControllerBase, IApiController
{
    // ...
}
```

<span data-ttu-id="0815e-157">この属性を使用すると、この型を継承するクラスは、コントローラー名、アクション名、および省略可能な整数パラメーターに基づいて、アクションに Url をルーティングし `id` ます。</span><span class="sxs-lookup"><span data-stu-id="0815e-157">Using this attribute, classes inheriting from this type would route URLs to actions based on the controller name, action name, and an optional integer `id` parameter.</span></span>

## <a name="references"></a><span data-ttu-id="0815e-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="0815e-158">References</span></span>

- [<span data-ttu-id="0815e-159">ASP.NET MVC ルーティングの概要</span><span class="sxs-lookup"><span data-stu-id="0815e-159">ASP.NET MVC Routing Overview</span></span>](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/asp-net-mvc-routing-overview-cs)
- [<span data-ttu-id="0815e-160">ASP.NET MVC 5 での属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-160">Attribute Routing in ASP.NET MVC 5</span></span>](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)
- [<span data-ttu-id="0815e-161">ASP.NET Web API 2 での属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-161">Attribute routing in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)
- [<span data-ttu-id="0815e-162">ASP.NET Web API でのルーティングとアクションの選択</span><span class="sxs-lookup"><span data-stu-id="0815e-162">Routing and Action Selection in ASP.NET Web API</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
- [<span data-ttu-id="0815e-163">ASP.NET Core のルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-163">Routing in ASP.NET Core</span></span>](/aspnet/core/fundamentals/routing)
- [<span data-ttu-id="0815e-164">ASP.NET Core MVC でのコントローラーアクションへのルーティング</span><span class="sxs-lookup"><span data-stu-id="0815e-164">Routing to controller actions in ASP.NET Core MVC</span></span>](/aspnet/core/mvc/controllers/routing)

>[!div class="step-by-step"]
><span data-ttu-id="0815e-165">[前へ](configuration-differences.md)
>[次へ](comparing-razor-pages-aspnet-mvc.md)</span><span class="sxs-lookup"><span data-stu-id="0815e-165">[Previous](configuration-differences.md)
[Next](comparing-razor-pages-aspnet-mvc.md)</span></span>
