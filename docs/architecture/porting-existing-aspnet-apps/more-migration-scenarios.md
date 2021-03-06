---
title: その他の移行シナリオ
description: このセクションでは、.NET Framework アプリを .NET Core/.NET 5 にアップグレードするためのその他の移行シナリオと手法について説明します。
author: ardalis
ms.date: 02/11/2021
ms.openlocfilehash: fa1b756d8852854e50127ae3e7443e2949cceaa8
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401358"
---
# <a name="more-migration-scenarios"></a><span data-ttu-id="18f36-103">その他の移行シナリオ</span><span class="sxs-lookup"><span data-stu-id="18f36-103">More migration scenarios</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="18f36-104">このセクションでは、いくつかの異なる ASP.NET アプリシナリオについて説明し、それぞれの解決方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="18f36-104">This section describes several different ASP.NET app scenarios, and offers specific techniques for solving each of them.</span></span> <span data-ttu-id="18f36-105">このセクションを使用すると、アプリに適用されるシナリオを特定し、アプリとそのホスティング環境でどの手法が機能するかを評価できます。</span><span class="sxs-lookup"><span data-stu-id="18f36-105">You can use this section to identify scenarios applicable to your app, and evaluate which techniques will work for your app and its hosting environment.</span></span>

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a><span data-ttu-id="18f36-106">ASP.NET MVC 5 と WebApi 2 を ASP.NET Core MVC に移行する</span><span class="sxs-lookup"><span data-stu-id="18f36-106">Migrate ASP.NET MVC 5 and WebApi 2 to ASP.NET Core MVC</span></span>

<span data-ttu-id="18f36-107">ASP.NET MVC 5 アプリと Web API 2 アプリの一般的なシナリオは、両方の製品を同じアプリケーションにインストールすることでした。</span><span class="sxs-lookup"><span data-stu-id="18f36-107">A common scenario in ASP.NET MVC 5 and Web API 2 apps was for both products to be installed in the same application.</span></span> <span data-ttu-id="18f36-108">これは、多くのチームが使用する、サポートされている比較的一般的なアプローチですが、2つの製品では異なる抽象化が使用されるため、余分な作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="18f36-108">This is a supported and relatively common approach used by many teams, but because the two products use different abstractions, there is some redundant effort needed.</span></span> <span data-ttu-id="18f36-109">たとえば、ASP.NET MVC のルートの設定は、やなどののメソッドを使用して行い `RouteCollection` `MapMvcAttributeRoutes()` `MapRoute()` ます。</span><span class="sxs-lookup"><span data-stu-id="18f36-109">For example, setting up routes for ASP.NET MVC is done using methods on `RouteCollection`, such as `MapMvcAttributeRoutes()` and `MapRoute()`.</span></span> <span data-ttu-id="18f36-110">ただし ASP.NET Web API 2 のルーティングは、およびのような方法で管理され `HttpConfiguration` `MapHttpAttributeRoutes()` `MapHttpRoute()` ます。</span><span class="sxs-lookup"><span data-stu-id="18f36-110">But ASP.NET Web API 2 routing is managed with `HttpConfiguration` and methods like `MapHttpAttributeRoutes()` and `MapHttpRoute()`.</span></span>

<span data-ttu-id="18f36-111">このアプリには、 `eShopLegacyMVC` ASP.NET MVC と WEB API の両方が含まれており、 `App_Start` 両方のルートを設定するためのフォルダーにメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="18f36-111">The `eShopLegacyMVC` app includes both ASP.NET MVC and Web API, and includes methods in its `App_Start` folder for setting up routes for both.</span></span> <span data-ttu-id="18f36-112">また、Autofac を使用した依存関係の注入もサポートしています。これには、2つの類似した構成作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="18f36-112">It also supports dependency injection using Autofac, which also requires two sets of similar work to configure:</span></span>

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

<span data-ttu-id="18f36-113">ASP.NET Core を使用するようにこれらのアプリをアップグレードすると、重複する作業と、それに付随する可能性がある混乱が排除されます。</span><span class="sxs-lookup"><span data-stu-id="18f36-113">When upgrading these apps to use ASP.NET Core, this duplicate effort and the confusion that sometimes accompanies it is eliminated.</span></span> <span data-ttu-id="18f36-114">ASP.NET Core MVC は、ルーティングやフィルターなどのルールの1つのセットを備えた統合フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="18f36-114">ASP.NET Core MVC is a unified framework with one set of rules for routing, filters, and more.</span></span> <span data-ttu-id="18f36-115">依存関係の注入は、.NET Core 自体に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="18f36-115">Dependency injection is built into .NET Core itself.</span></span> <span data-ttu-id="18f36-116">これらはすべて `Startup.cs` 、「」のサンプルのアプリに示すように、で構成できます `eShopPorted` 。</span><span class="sxs-lookup"><span data-stu-id="18f36-116">All of this can can be configured in `Startup.cs`, as is shown in the `eShopPorted` app in the sample.</span></span>

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a><span data-ttu-id="18f36-117">HttpResponseMessage を ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="18f36-117">Migrate HttpResponseMessage to ASP.NET Core</span></span>

<span data-ttu-id="18f36-118">一部の ASP.NET Web API アプリには、を返すアクションメソッドが含まれている場合があり `HttpResponseMessage` ます。</span><span class="sxs-lookup"><span data-stu-id="18f36-118">Some ASP.NET Web API apps may have action methods that return `HttpResponseMessage`.</span></span> <span data-ttu-id="18f36-119">この型は ASP.NET Core に存在しません。</span><span class="sxs-lookup"><span data-stu-id="18f36-119">This type does not exist in ASP.NET Core.</span></span> <span data-ttu-id="18f36-120">次に、 `Delete` 基本のヘルパーメソッドを使用した、アクションメソッドでの使用例を示し `ResponseMessage` `ApiController` ます。</span><span class="sxs-lookup"><span data-stu-id="18f36-120">Below is an example of its usage in a `Delete` action method, using the `ResponseMessage` helper method on the base `ApiController`:</span></span>

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

<span data-ttu-id="18f36-121">ASP.NET Core MVC では、すべての一般的な HTTP 応答ステータスコードに使用できるヘルパーメソッドがあるため、上記のメソッドは次のコードに移植されます。</span><span class="sxs-lookup"><span data-stu-id="18f36-121">In ASP.NET Core MVC, there are helper methods available for all of the common HTTP response status codes, so the above method would be ported to the following code:</span></span>

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

<span data-ttu-id="18f36-122">ヘルパーが存在しないカスタムステータスコードを返す必要がある場合は、常にを使用して任意の数値コードを返すことができ `return StatusCode(int statusCode)` ます。</span><span class="sxs-lookup"><span data-stu-id="18f36-122">If you do find that you need to return a custom status code for which no helper exists, you can always use `return StatusCode(int statusCode)` to return any numeric code you like.</span></span>

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a><span data-ttu-id="18f36-123">ASP.NET Web API から ASP.NET Core へのコンテンツネゴシエーションの移行</span><span class="sxs-lookup"><span data-stu-id="18f36-123">Migrate content negotiation from ASP.NET Web API to ASP.NET Core</span></span>

<span data-ttu-id="18f36-124">ASP.NET Web API 2 では、 [コンテンツネゴシエーション](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) がネイティブでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="18f36-124">ASP.NET Web API 2 supports [content negotiation](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) natively.</span></span> <span data-ttu-id="18f36-125">このサンプルアプリには、 `BrandsController` 結果を XML または JSON で一覧表示することによって、このサポートを示すが含まれています。</span><span class="sxs-lookup"><span data-stu-id="18f36-125">The sample app includes a `BrandsController` that demonstrates this support by listing its results in either XML or JSON.</span></span> <span data-ttu-id="18f36-126">これは要求のヘッダーに基づいて `Accept` おり、またはが含まれている場合は変更され `application/xml` `application/json` ます。</span><span class="sxs-lookup"><span data-stu-id="18f36-126">This is based on the request's `Accept` header, and changes when it includes `application/xml` or `application/json`.</span></span>

<span data-ttu-id="18f36-127">ASP.NET MVC 5 アプリでは、コンテンツネゴシエーションのサポートは組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="18f36-127">ASP.NET MVC 5 apps do not have content negotiation support built in.</span></span>

<span data-ttu-id="18f36-128">コンテンツネゴシエーションは、より柔軟性が高く、API をより多くのクライアントで使用できるようにするため、特定のエンコードの種類を返す方が望ましいと言えます。</span><span class="sxs-lookup"><span data-stu-id="18f36-128">Content negotiation is preferable to returning a specific encoding type, as it is more flexible and makes the API available to a larger number of clients.</span></span> <span data-ttu-id="18f36-129">現在、特定の形式を返すアクションメソッドがある場合は、コードを ASP.NET Core に移植するときに、コンテンツネゴシエーションをサポートする結果の型を返すように変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="18f36-129">If you currently have action methods that return a specific format, you should consider modifying them to return a result type that supports content negotiation when you port the code to ASP.NET Core.</span></span>

<span data-ttu-id="18f36-130">次のコードは、クライアントのヘッダーコンテンツに関係なく、JSON 形式でデータを返し `Accept` ます。</span><span class="sxs-lookup"><span data-stu-id="18f36-130">The following code returns data in JSON format regardless of client `Accept` header content:</span></span>

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

<span data-ttu-id="18f36-131">適切な[戻り値の型](/aspnet/core/web-api/action-return-types)が使用されている場合、MVC では、[コンテンツネゴシエーションがネイティブでサポート](/aspnet/core/web-api/advanced/formatting)されます。 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="18f36-131">[ASP.NET Core MVC supports content negotiation natively](/aspnet/core/web-api/advanced/formatting), provided an appropriate [return type](/aspnet/core/web-api/action-return-types) is used.</span></span> <span data-ttu-id="18f36-132">コンテンツネゴシエーションは、コントローラーヘルパーメソッドによって返されるステータスコード固有のアクション結果によって返される [ObjectResult] によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="18f36-132">Content negotiation is implemented by [ObjectResult] which is returned by the status code-specific action results returned by the controller helper methods.</span></span> <span data-ttu-id="18f36-133">前のアクションメソッドは ASP.NET Core MVC で実装され、コンテンツネゴシエーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="18f36-133">The previous action method, implemented in ASP.NET Core MVC and using content negotiation, would be:</span></span>

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

<span data-ttu-id="18f36-134">これにより、既定ではデータが JSON 形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="18f36-134">This will default to returning the data in JSON format.</span></span> <span data-ttu-id="18f36-135">[アプリが適切なフォーマッタで構成されている場合](/aspnet/core/web-api/advanced/formatting)は、XML およびその他の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="18f36-135">XML and other formats will be used [if the app has been configured with the appropriate formatter](/aspnet/core/web-api/advanced/formatting).</span></span>

## <a name="references"></a><span data-ttu-id="18f36-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="18f36-136">References</span></span>

- [<span data-ttu-id="18f36-137">ASP.NET Web API コンテンツネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="18f36-137">ASP.NET Web API Content Negotiation</span></span>](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [<span data-ttu-id="18f36-138">ASP.NET Core Web API の応答データの書式設定</span><span class="sxs-lookup"><span data-stu-id="18f36-138">Format response data in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/formatting)

>[!div class="step-by-step"]
><span data-ttu-id="18f36-139">[前へ](example-migration-eshop.md)
>[次へ](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="18f36-139">[Previous](example-migration-eshop.md)
[Next](deployment-scenarios.md)</span></span>
