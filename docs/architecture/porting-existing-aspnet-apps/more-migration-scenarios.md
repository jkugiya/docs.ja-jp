---
title: その他の移行シナリオ
description: このセクションでは、.NET Framework アプリを .NET Core / .NET 5 にアップグレードするためのその他の移行シナリオおよび手法について説明します。
author: ardalis
ms.date: 02/11/2021
ms.openlocfilehash: fa1b756d8852854e50127ae3e7443e2949cceaa8
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401358"
---
# <a name="more-migration-scenarios"></a><span data-ttu-id="6a41a-103">その他の移行シナリオ</span><span class="sxs-lookup"><span data-stu-id="6a41a-103">More migration scenarios</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6a41a-104">このセクションでは、ASP.NET アプリのさまざまなシナリオについて説明し、そのそれぞれを解決するための固有の手法を示します。</span><span class="sxs-lookup"><span data-stu-id="6a41a-104">This section describes several different ASP.NET app scenarios, and offers specific techniques for solving each of them.</span></span> <span data-ttu-id="6a41a-105">このセクションを使用して、ご自分のアプリに当てはまるシナリオを特定し、ご自分のアプリとそのホスト環境にどの手法が適しているかを評価することができます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-105">You can use this section to identify scenarios applicable to your app, and evaluate which techniques will work for your app and its hosting environment.</span></span>

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a><span data-ttu-id="6a41a-106">ASP.NET MVC 5 と WebApi 2 を ASP.NET Core MVC に移行する</span><span class="sxs-lookup"><span data-stu-id="6a41a-106">Migrate ASP.NET MVC 5 and WebApi 2 to ASP.NET Core MVC</span></span>

<span data-ttu-id="6a41a-107">ASP.NET MVC 5 アプリと Web API 2 アプリでの一般的なシナリオは、両方の製品を同じアプリケーションにインストールするためのものでした。</span><span class="sxs-lookup"><span data-stu-id="6a41a-107">A common scenario in ASP.NET MVC 5 and Web API 2 apps was for both products to be installed in the same application.</span></span> <span data-ttu-id="6a41a-108">これはサポートされている比較的一般的なアプローチで、多くのチームで使用されていますが、2 つの製品で異なる抽象化が使用されるため、いくつかの余分な作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6a41a-108">This is a supported and relatively common approach used by many teams, but because the two products use different abstractions, there is some redundant effort needed.</span></span> <span data-ttu-id="6a41a-109">たとえば、ASP.NET MVC 用のルートの設定は、`RouteCollection` に対して `MapMvcAttributeRoutes()` や `MapRoute()` などのメソッドを使用することで行います。</span><span class="sxs-lookup"><span data-stu-id="6a41a-109">For example, setting up routes for ASP.NET MVC is done using methods on `RouteCollection`, such as `MapMvcAttributeRoutes()` and `MapRoute()`.</span></span> <span data-ttu-id="6a41a-110">しかし、ASP.NET Web API 2 のルーティングは、`HttpConfiguration` と `MapHttpAttributeRoutes()` や `MapHttpRoute()` などのメソッドを使用して管理されます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-110">But ASP.NET Web API 2 routing is managed with `HttpConfiguration` and methods like `MapHttpAttributeRoutes()` and `MapHttpRoute()`.</span></span>

<span data-ttu-id="6a41a-111">`eShopLegacyMVC` アプリには ASP.NET MVC と Web API の両方が含まれており、その `App_Start` フォルダー内には両方のルートを設定するためのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a41a-111">The `eShopLegacyMVC` app includes both ASP.NET MVC and Web API, and includes methods in its `App_Start` folder for setting up routes for both.</span></span> <span data-ttu-id="6a41a-112">Autofac を使用した依存関係の挿入もサポートされており、この場合もまた、構成のために 2 組の類似した作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6a41a-112">It also supports dependency injection using Autofac, which also requires two sets of similar work to configure:</span></span>

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

<span data-ttu-id="6a41a-113">これらのアプリを ASP.NET Core を使用するようにアップグレードすると、この重複した作業とそれに伴うことがある混乱を排除できます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-113">When upgrading these apps to use ASP.NET Core, this duplicate effort and the confusion that sometimes accompanies it is eliminated.</span></span> <span data-ttu-id="6a41a-114">ASP.NET Core MVC は、ルーティング、フィルターなどに関する 1 組の規則を備えた統合フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="6a41a-114">ASP.NET Core MVC is a unified framework with one set of rules for routing, filters, and more.</span></span> <span data-ttu-id="6a41a-115">依存関係の挿入は、.NET Core 自体に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="6a41a-115">Dependency injection is built into .NET Core itself.</span></span> <span data-ttu-id="6a41a-116">サンプル内の `eShopPorted` アプリで示されているように、これらすべてを `Startup.cs` 内で構成できます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-116">All of this can can be configured in `Startup.cs`, as is shown in the `eShopPorted` app in the sample.</span></span>

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a><span data-ttu-id="6a41a-117">HttpResponseMessage を ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="6a41a-117">Migrate HttpResponseMessage to ASP.NET Core</span></span>

<span data-ttu-id="6a41a-118">ASP.NET Web API アプリの中には、`HttpResponseMessage` を返すアクション メソッドが含まれているものもあります。</span><span class="sxs-lookup"><span data-stu-id="6a41a-118">Some ASP.NET Web API apps may have action methods that return `HttpResponseMessage`.</span></span> <span data-ttu-id="6a41a-119">この型は ASP.NET Core には存在しません。</span><span class="sxs-lookup"><span data-stu-id="6a41a-119">This type does not exist in ASP.NET Core.</span></span> <span data-ttu-id="6a41a-120">これを `Delete` アクション メソッドで使用する例を以下に示します。基本 `ApiController` に対して `ResponseMessage` ヘルパー メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="6a41a-120">Below is an example of its usage in a `Delete` action method, using the `ResponseMessage` helper method on the base `ApiController`:</span></span>

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

<span data-ttu-id="6a41a-121">ASP.NET Core MVC では、すべての一般的な HTTP 応答状態コードに対して利用可能なヘルパー メソッドが存在するため、上のメソッドは次のコードに移植できます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-121">In ASP.NET Core MVC, there are helper methods available for all of the common HTTP response status codes, so the above method would be ported to the following code:</span></span>

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

<span data-ttu-id="6a41a-122">ヘルパーが存在しないカスタム状態コードを返す必要がある場合は、常に `return StatusCode(int statusCode)` を使用して任意の数値コードを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-122">If you do find that you need to return a custom status code for which no helper exists, you can always use `return StatusCode(int statusCode)` to return any numeric code you like.</span></span>

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a><span data-ttu-id="6a41a-123">コンテンツ ネゴシエーションを ASP.NET Web API から ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="6a41a-123">Migrate content negotiation from ASP.NET Web API to ASP.NET Core</span></span>

<span data-ttu-id="6a41a-124">ASP.NET Web API 2 では、[コンテンツ ネゴシエーション](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)がネイティブでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-124">ASP.NET Web API 2 supports [content negotiation](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) natively.</span></span> <span data-ttu-id="6a41a-125">サンプル アプリには、その結果を XML または JSON で一覧表示することでこのサポートを示す `BrandsController` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a41a-125">The sample app includes a `BrandsController` that demonstrates this support by listing its results in either XML or JSON.</span></span> <span data-ttu-id="6a41a-126">これは要求の `Accept` ヘッダーに基づいており、そこに `application/xml` が含まれるか `application/json` が含まれるかによって変わります。</span><span class="sxs-lookup"><span data-stu-id="6a41a-126">This is based on the request's `Accept` header, and changes when it includes `application/xml` or `application/json`.</span></span>

<span data-ttu-id="6a41a-127">ASP.NET MVC 5 アプリには、コンテンツ ネゴシエーションのサポートが組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="6a41a-127">ASP.NET MVC 5 apps do not have content negotiation support built in.</span></span>

<span data-ttu-id="6a41a-128">コンテンツ ネゴシエーションは、より柔軟性が高く、より多くのクライアントが API を利用できるようになるため、特定のエンコードの種類を返すよりも推奨されます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-128">Content negotiation is preferable to returning a specific encoding type, as it is more flexible and makes the API available to a larger number of clients.</span></span> <span data-ttu-id="6a41a-129">現在、特定の形式を返すアクション メソッドを使用している場合は、コードを ASP.NET Core に移植するときに、コンテンツ ネゴシエーションでサポートされている結果の種類を返すようにそれらを変更することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a41a-129">If you currently have action methods that return a specific format, you should consider modifying them to return a result type that supports content negotiation when you port the code to ASP.NET Core.</span></span>

<span data-ttu-id="6a41a-130">次のコードでは、クライアントの `Accept` ヘッダーのコンテンツに関係なく、データが JSON 形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-130">The following code returns data in JSON format regardless of client `Accept` header content:</span></span>

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

<span data-ttu-id="6a41a-131">ASP.NET Core MVC では、適切な[戻り値の型](/aspnet/core/web-api/action-return-types)が指定されていれば、[コンテンツ ネゴシエーションがネイティブでサポートされます](/aspnet/core/web-api/advanced/formatting)。</span><span class="sxs-lookup"><span data-stu-id="6a41a-131">[ASP.NET Core MVC supports content negotiation natively](/aspnet/core/web-api/advanced/formatting), provided an appropriate [return type](/aspnet/core/web-api/action-return-types) is used.</span></span> <span data-ttu-id="6a41a-132">コンテンツ ネゴシエーションは、コントローラー ヘルパー メソッドによって返される状態コード固有のアクション結果で返される [ObjectResult] によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-132">Content negotiation is implemented by [ObjectResult] which is returned by the status code-specific action results returned by the controller helper methods.</span></span> <span data-ttu-id="6a41a-133">ASP.NET Core MVC に実装された、コンテンツ ネゴシエーションを使用する上記のアクション メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6a41a-133">The previous action method, implemented in ASP.NET Core MVC and using content negotiation, would be:</span></span>

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

<span data-ttu-id="6a41a-134">これにより、データが既定で JSON 形式で返されるようになります。</span><span class="sxs-lookup"><span data-stu-id="6a41a-134">This will default to returning the data in JSON format.</span></span> <span data-ttu-id="6a41a-135">[該当するフォーマッタがアプリに構成されている場合は](/aspnet/core/web-api/advanced/formatting)、XML やその他の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6a41a-135">XML and other formats will be used [if the app has been configured with the appropriate formatter](/aspnet/core/web-api/advanced/formatting).</span></span>

## <a name="references"></a><span data-ttu-id="6a41a-136">リファレンス</span><span class="sxs-lookup"><span data-stu-id="6a41a-136">References</span></span>

- [<span data-ttu-id="6a41a-137">ASP.NET Web API のコンテンツ ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="6a41a-137">ASP.NET Web API Content Negotiation</span></span>](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [<span data-ttu-id="6a41a-138">ASP.NET Core Web API の応答データの書式設定</span><span class="sxs-lookup"><span data-stu-id="6a41a-138">Format response data in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/formatting)

>[!div class="step-by-step"]
><span data-ttu-id="6a41a-139">[前へ](example-migration-eshop.md)
>[次へ](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="6a41a-139">[Previous](example-migration-eshop.md)
[Next](deployment-scenarios.md)</span></span>
