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
# <a name="routing-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="aa5df-104">ASP.NET MVC と ASP.NET Core でのルーティングの相違点</span><span class="sxs-lookup"><span data-stu-id="aa5df-104">Routing differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="aa5df-105">ルーティングは、受信したブラウザー要求を特定のコントローラー アクション (または Razor Pages ハンドラー) にマップする役割を担います。</span><span class="sxs-lookup"><span data-stu-id="aa5df-105">Routing is responsible for mapping incoming browser requests to particular controller actions (or Razor Pages handlers).</span></span> <span data-ttu-id="aa5df-106">このセクションでは、ASP.NET MVC (および Web API) と ASP.NET Core (MVC、Razor Pages など) とでルーティングがどのように異なるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-106">This section covers how routing differs between ASP.NET MVC (and Web API) and ASP.NET Core (MVC, Razor Pages, and otherwise).</span></span>

## <a name="routing-in-aspnet-mvc-and-web-api"></a><span data-ttu-id="aa5df-107">ASP.NET MVC および Web API でのルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-107">Routing in ASP.NET MVC and Web API</span></span>

<span data-ttu-id="aa5df-108">ASP.NET MVC では、ルーティングに対する 2 つのアプローチが提供されています。</span><span class="sxs-lookup"><span data-stu-id="aa5df-108">ASP.NET MVC offers two approaches to routing:</span></span>

1. <span data-ttu-id="aa5df-109">ルート テーブル。これは、受信した要求をコントローラー アクションと照合するために使用できるルートのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="aa5df-109">The route table, which is a collection of routes that can be used to match incoming requests to controller actions.</span></span>
1. <span data-ttu-id="aa5df-110">属性ルーティング。これは同じ機能を実行しますが、グローバル ルート テーブルを編集するのではなく、アクション自体を修飾することによって実現します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-110">Attribute routing, which performs the same function but is achieved by decorating the actions themselves, rather than editing a global route table.</span></span>

## <a name="route-table"></a><span data-ttu-id="aa5df-111">ルート テーブル</span><span class="sxs-lookup"><span data-stu-id="aa5df-111">Route table</span></span>

<span data-ttu-id="aa5df-112">ルート テーブルは、アプリの起動時に構成されます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-112">The route table is configured when the app starts up.</span></span> <span data-ttu-id="aa5df-113">通常は、次のように、静的メソッド呼び出しを使用してグローバル ルート コレクションが構成されます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-113">Typically, a static method call is used to configure the global route collection, like so:</span></span>

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

<span data-ttu-id="aa5df-114">上のコードでは、ルート テーブルは `RouteCollection` 型によって管理されます。これは `MapRoute` で新しいルートを追加するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-114">In the preceding code, the route table is managed by the `RouteCollection` type, which is used to add new routes with `MapRoute`.</span></span> <span data-ttu-id="aa5df-115">ルートには名前が付けられ、ルート文字列が含まれます。これにはコントローラー、アクション、区分、その他のプレースホルダーのパラメーターを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-115">Routes are named and include a route string, which can include parameters for controllers, actions, areas, and other placeholders.</span></span> <span data-ttu-id="aa5df-116">アプリが標準規則に従っている場合、そのアクションの大部分をこの 1 つの既定のルートで処理できますが、この規則に対する例外がある場合は追加のルートを使用して構成します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-116">If an app follows a standard convention, most of its actions can be handled by this single default route, with any exceptions to this convention configured using additional routes.</span></span>

### <a name="attribute-routing-in-aspnet-mvc"></a><span data-ttu-id="aa5df-117">ASP.NET MVC での属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-117">Attribute routing in ASP.NET MVC</span></span>

<span data-ttu-id="aa5df-118">アクションに対して定義されたルートは、外部の場所で定義されたルートよりも簡単に検出および判断できます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-118">Routes that are defined with their actions may be easier to discover and reason about than routes defined in an external location.</span></span> <span data-ttu-id="aa5df-119">属性ルーティングを使用すると、`[Route]` 属性を使用して個々のアクション メソッドにルートを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-119">Using attribute routing, an individual action method can have its route defined with a `[Route]` attribute:</span></span>

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

<span data-ttu-id="aa5df-120">[ASP.NET MVC 5 の属性ルーティング](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)では、コントローラー レベルで追加できる (そして、そのコントローラー内のすべてのアクションに適用される) 既定値とプレフィックスもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="aa5df-120">[Attribute routing in ASP.NET MVC 5](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/) also supports defaults and prefixes, which can be added at the controller level (and which are applied to all actions within that controller).</span></span> <span data-ttu-id="aa5df-121">詳細については、ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa5df-121">Refer to the documentation for details.</span></span>

<span data-ttu-id="aa5df-122">属性ルーティングを設定するには、既定のルート テーブルの構成に 1 行追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa5df-122">Setting up attribute routing requires adding one line to the default route table configuration:</span></span>

```csharp
routes.MapMvcAttributeRoutes();
```

<span data-ttu-id="aa5df-123">属性ルーティングでは、組み込みとカスタムの両方のルート制約を利用でき、名前付きルートと、`[RouteArea]` 属性を使用した区分がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-123">Attribute routing can take advantage of route constraints, both built-in and custom, and supports named routes and areas using the `[RouteArea]` attribute.</span></span> <span data-ttu-id="aa5df-124">アプリで区分を使用する場合は、ルート登録コード内にもう 1 行を追加して、それらのサポートを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa5df-124">If your app uses areas, you'll need to configure support for them in your route registration code by adding one more line:</span></span>

```csharp
routes.MapMvcAttributeRoutes();

AreaRegistration.RegisterAllAreas();
```

### <a name="attribute-routing-in-aspnet-web-api-2"></a><span data-ttu-id="aa5df-125">ASP.NET Web API 2 での属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-125">Attribute routing in ASP.NET Web API 2</span></span>

<span data-ttu-id="aa5df-126">[ASP.NET Web API 2 の属性ルーティング](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)は ASP.NET MVC 5 のルーティングに似ていますが、わずかな違いがあります。</span><span class="sxs-lookup"><span data-stu-id="aa5df-126">[Attribute routing in ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2) is similar to routing in ASP.NET MVC 5, with minor differences.</span></span> <span data-ttu-id="aa5df-127">Web API 2 の構成は、通常、アプリケーションの起動時に呼び出される独自のクラス内で行われます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-127">Configuring Web API 2 is typically done in its own class, which is called during app startup.</span></span> <span data-ttu-id="aa5df-128">属性ルーティングの構成は、このクラス内で処理されます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-128">Attribute routing configuration is handled in this class:</span></span>

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

<span data-ttu-id="aa5df-129">上のコードに示されているように、属性ルーティングは、Web API アプリの規則ベースのルーティングと組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-129">As shown in the preceding code, attribute routing may be combined with convention-based routing in Web API apps.</span></span>

<span data-ttu-id="aa5df-130">属性ルーティングに加えて、ASP.NET Web API では、HTTP メソッド (たとえば GET や POST など)、ルート内の `{action}` プレースホルダー (存在する場合)、アクションのパラメーターに基づいて、[呼び出すアクションを選択](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-130">In addition to attribute routing, [ASP.NET Web API chooses which action to call](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection) based on the HTTP method (for example, GET or POST), the `{action}` placeholder in a route (if any), and parameters of the action.</span></span> <span data-ttu-id="aa5df-131">多くの場合、アクションの名前は、適切な HTTP メソッドと一致させるために "Get" または "Post" というプレフィックスが付けられているので、一致しているかどうかの判断に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-131">In many cases, the name of the action will help determine whether it's matched, since prefixing the action name with "Get" or "Post" is used to match the appropriate HTTP method to it.</span></span> <span data-ttu-id="aa5df-132">または、適切な HTTP メソッド属性 (`[HttpGet]` など) でアクションを修飾することもできます。これにより、HTTP メソッドのプレフィックスが付いていないアクション名を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="aa5df-132">Alternatively, actions can be decorated with an appropriate HTTP method attribute, like `[HttpGet]`, allowing the use of action names that aren't prefixed with an HTTP method.</span></span>

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

<span data-ttu-id="aa5df-133">上のコントローラーの場合、`localhost:123/products/` への HTTP GET 要求は `GetAll` アクションと一致します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-133">Given the above controller, an HTTP GET request to `localhost:123/products/` matches the `GetAll` action.</span></span> <span data-ttu-id="aa5df-134">`localhost:123/products?name=ardalis` への HTTP GET 要求は `FindProductsByName` アクションと一致します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-134">An HTTP GET request to `localhost:123/products?name=ardalis` matches the `FindProductsByName` action.</span></span>

## <a name="routing-in-aspnet-core-31"></a><span data-ttu-id="aa5df-135">ASP.NET Core 3.1 でのルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-135">Routing in ASP.NET Core 3.1</span></span>

<span data-ttu-id="aa5df-136">ASP.NET Core では、ルーティングはルーティング ミドルウェアによって処理されます。これは、受信した要求の URL をアクションまたは他のエンドポイントと照合します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-136">In ASP.NET Core, routing is handled by routing middleware, which matches the URLs of incoming requests to actions or other endpoints.</span></span> <span data-ttu-id="aa5df-137">コントローラー アクションは、規則ルーティングまたは属性ルーティングでルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-137">Controller actions are either conventionally routed or attribute-routed.</span></span> <span data-ttu-id="aa5df-138">規則ルーティングは、ASP.NET MVC と Web API で使用されているルート テーブル アプローチに似ています。</span><span class="sxs-lookup"><span data-stu-id="aa5df-138">Conventional routing is similar to the route table approach used in ASP.NET MVC and Web API.</span></span> <span data-ttu-id="aa5df-139">規則ルーティング、属性ルーティング、またはその両方のどれを使用する場合でも、ルーティング ミドルウェアを使用するようにアプリを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa5df-139">Whether you're using conventional, attribute, or both, you need to configure your app to use the routing middleware.</span></span> <span data-ttu-id="aa5df-140">ミドルウェアを使用するには、`Startup.Configure` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-140">To use the middleware, add the following code to your `Startup.Configure` method:</span></span>

```csharp
app.UseRouting();
```

### <a name="conventional-routing"></a><span data-ttu-id="aa5df-141">規則ルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-141">Conventional routing</span></span>

<span data-ttu-id="aa5df-142">規則ルーティングでは、受信した URL をアプリ内の "*エンドポイント*" と照合するために使用される 1 つ以上の規則を設定します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-142">With conventional routing, you set up one or more conventions that will be used to match incoming URLs to *endpoints* in the app.</span></span> <span data-ttu-id="aa5df-143">ASP.NET MVC や Web API の場合と同様に、ASP.NET Core でも、コントローラー アクションをエンドポイントにすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-143">In ASP.NET Core, these endpoints may be controller actions, like in ASP.NET MVC or Web API.</span></span> <span data-ttu-id="aa5df-144">また、Razor Pages、正常性チェック、または SignalR ハブをエンドポイントにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-144">The endpoints could also be Razor Pages, Health Checks, or SignalR hubs.</span></span> <span data-ttu-id="aa5df-145">これらのルーティング可能な機能はすべて、エンドポイントを使用する同様の方法で構成されます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-145">All of these routable features are configured in a similar fashion using endpoints:</span></span>

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

<span data-ttu-id="aa5df-146">上のコードは、正常性チェック、コントローラー、Razor Pages などのさまざまなエンドポイントを構成するために (`UseRouting` に加えて) 使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-146">The preceding code is used (in addition to `UseRouting`) to configure various endpoints, including Health Checks, controllers, and Razor Pages.</span></span> <span data-ttu-id="aa5df-147">コントローラーでは、上の構成によって既定のルーティング規則が指定されます。これは、ASP.NET MVC の初期のバージョンから推奨されてきたごく標準的な `{controller}/{action}/{id?}` パターンです。</span><span class="sxs-lookup"><span data-stu-id="aa5df-147">For controllers, the above configuration specifies a default routing convention, which is the fairly standard `{controller}/{action}/{id?}` pattern that's been recommended since the first versions of ASP.NET MVC.</span></span>

### <a name="attribute-routing"></a><span data-ttu-id="aa5df-148">属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-148">Attribute routing</span></span>

<span data-ttu-id="aa5df-149">ASP.NET Core での属性ルーティングは、コントローラーでルーティングを構成する際に推奨されるアプローチです。</span><span class="sxs-lookup"><span data-stu-id="aa5df-149">Attribute routing in ASP.NET Core is the preferred approach for configuring routing in controllers.</span></span> <span data-ttu-id="aa5df-150">API を構築する場合、コントローラーに `[ApiController]` 属性を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa5df-150">If you're building APIs, the `[ApiController]` attribute should be applied to your controllers.</span></span> <span data-ttu-id="aa5df-151">特に、この属性では、そのようなコントローラー クラス内のアクションに対して属性ルーティングを使用することが必要になります。</span><span class="sxs-lookup"><span data-stu-id="aa5df-151">Among other things, this attribute requires the use of attribute routing for actions in such controller classes.</span></span>

<span data-ttu-id="aa5df-152">ASP.NET Core での属性ルーティングは、ASP.NET MVC や Web API の場合と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-152">Attribute routing in ASP.NET Core behaves similarly in ASP.NET MVC and Web API.</span></span> <span data-ttu-id="aa5df-153">ただし、`[Route]` 属性のサポートに加えて、ルート情報を HTTP メソッド属性の一部として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-153">In addition to supporting the `[Route]` attribute, however, route information can also be specified as part of the HTTP method attribute:</span></span>

```csharp
[HttpGet("api/products/{id}")]
public async ActionResult<Product> Details(int id)
{
    // ...
}
```

<span data-ttu-id="aa5df-154">以前のバージョンと同様に、プレースホルダーを使用して既定のルートを指定し、これをコントローラー クラス レベルまたは基本クラスで追加することができます。</span><span class="sxs-lookup"><span data-stu-id="aa5df-154">As with previous versions, you can specify a default route with placeholders, and add this at the controller class level or even on a base class.</span></span> <span data-ttu-id="aa5df-155">これらのすべてのケースに、同じ `[Route]` 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa5df-155">You use the same `[Route]` attribute for all of these cases.</span></span> <span data-ttu-id="aa5df-156">たとえば、基本 API コントローラー クラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="aa5df-156">For example, a base API controller class might look like this:</span></span>

```csharp
[Route("api/{controller}/{action}/{id?:int}")]
public abstract class BaseApiController : ControllerBase, IApiController
{
    // ...
}
```

<span data-ttu-id="aa5df-157">この属性を使用すると、この型を継承するクラスは、コントローラー名、アクション名、およびオプションの整数 `id` パラメーターに基づいて URL をルーティングします。</span><span class="sxs-lookup"><span data-stu-id="aa5df-157">Using this attribute, classes inheriting from this type would route URLs to actions based on the controller name, action name, and an optional integer `id` parameter.</span></span>

## <a name="references"></a><span data-ttu-id="aa5df-158">リファレンス</span><span class="sxs-lookup"><span data-stu-id="aa5df-158">References</span></span>

- [<span data-ttu-id="aa5df-159">ASP.NET MVC ルーティングの概要</span><span class="sxs-lookup"><span data-stu-id="aa5df-159">ASP.NET MVC Routing Overview</span></span>](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/asp-net-mvc-routing-overview-cs)
- [<span data-ttu-id="aa5df-160">ASP.NET MVC 5 での属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-160">Attribute Routing in ASP.NET MVC 5</span></span>](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/)
- [<span data-ttu-id="aa5df-161">ASP.NET Web API 2 での属性ルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-161">Attribute routing in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2)
- [<span data-ttu-id="aa5df-162">ASP.NET Web API でのルーティングとアクションの選択</span><span class="sxs-lookup"><span data-stu-id="aa5df-162">Routing and Action Selection in ASP.NET Web API</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/routing-and-action-selection)
- [<span data-ttu-id="aa5df-163">ASP.NET Core のルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-163">Routing in ASP.NET Core</span></span>](/aspnet/core/fundamentals/routing)
- [<span data-ttu-id="aa5df-164">ASP.NET Core MVC でのコントローラー アクションへのルーティング</span><span class="sxs-lookup"><span data-stu-id="aa5df-164">Routing to controller actions in ASP.NET Core MVC</span></span>](/aspnet/core/mvc/controllers/routing)

>[!div class="step-by-step"]
><span data-ttu-id="aa5df-165">[前へ](configuration-differences.md)
>[次へ](comparing-razor-pages-aspnet-mvc.md)</span><span class="sxs-lookup"><span data-stu-id="aa5df-165">[Previous](configuration-differences.md)
[Next](comparing-razor-pages-aspnet-mvc.md)</span></span>
