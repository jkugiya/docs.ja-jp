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
# <a name="more-migration-scenarios"></a><span data-ttu-id="6e17a-103">その他の移行シナリオ</span><span class="sxs-lookup"><span data-stu-id="6e17a-103">More migration scenarios</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="6e17a-104">このセクションでは、ASP.NET アプリのさまざまなシナリオについて説明し、そのそれぞれを解決するための固有の手法を示します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-104">This section describes several different ASP.NET app scenarios, and offers specific techniques for solving each of them.</span></span> <span data-ttu-id="6e17a-105">このセクションを使用して、ご自分のアプリに当てはまるシナリオを特定し、ご自分のアプリとそのホスト環境にどの手法が適しているかを評価することができます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-105">You can use this section to identify scenarios applicable to your app, and evaluate which techniques will work for your app and its hosting environment.</span></span>

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a><span data-ttu-id="6e17a-106">ASP.NET MVC 5 と WebApi 2 を ASP.NET Core MVC に移行する</span><span class="sxs-lookup"><span data-stu-id="6e17a-106">Migrate ASP.NET MVC 5 and WebApi 2 to ASP.NET Core MVC</span></span>

<span data-ttu-id="6e17a-107">ASP.NET MVC 5 アプリと Web API 2 アプリでの一般的なシナリオは、両方の製品を同じアプリケーションにインストールするためのものでした。</span><span class="sxs-lookup"><span data-stu-id="6e17a-107">A common scenario in ASP.NET MVC 5 and Web API 2 apps was for both products to be installed in the same application.</span></span> <span data-ttu-id="6e17a-108">これはサポートされている比較的一般的なアプローチで、多くのチームで使用されていますが、2 つの製品で異なる抽象化が使用されるため、いくつかの余分な作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-108">This is a supported and relatively common approach used by many teams, but because the two products use different abstractions, there is some redundant effort needed.</span></span> <span data-ttu-id="6e17a-109">たとえば、ASP.NET MVC 用のルートの設定は、`RouteCollection` に対して `MapMvcAttributeRoutes()` や `MapRoute()` などのメソッドを使用することで行います。</span><span class="sxs-lookup"><span data-stu-id="6e17a-109">For example, setting up routes for ASP.NET MVC is done using methods on `RouteCollection`, such as `MapMvcAttributeRoutes()` and `MapRoute()`.</span></span> <span data-ttu-id="6e17a-110">しかし、ASP.NET Web API 2 のルーティングは、`HttpConfiguration` と `MapHttpAttributeRoutes()` や `MapHttpRoute()` などのメソッドを使用して管理されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-110">But ASP.NET Web API 2 routing is managed with `HttpConfiguration` and methods like `MapHttpAttributeRoutes()` and `MapHttpRoute()`.</span></span>

<span data-ttu-id="6e17a-111">`eShopLegacyMVC` アプリには ASP.NET MVC と Web API の両方が含まれており、その `App_Start` フォルダー内には両方のルートを設定するためのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-111">The `eShopLegacyMVC` app includes both ASP.NET MVC and Web API, and includes methods in its `App_Start` folder for setting up routes for both.</span></span> <span data-ttu-id="6e17a-112">Autofac を使用した依存関係の挿入もサポートされており、この場合もまた、構成のために 2 組の類似した作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-112">It also supports dependency injection using Autofac, which also requires two sets of similar work to configure:</span></span>

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

<span data-ttu-id="6e17a-113">これらのアプリを ASP.NET Core を使用するようにアップグレードすると、この重複した作業とそれに伴うことがある混乱を排除できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-113">When upgrading these apps to use ASP.NET Core, this duplicate effort and the confusion that sometimes accompanies it is eliminated.</span></span> <span data-ttu-id="6e17a-114">ASP.NET Core MVC は、ルーティング、フィルターなどに関する 1 組の規則を備えた統合フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-114">ASP.NET Core MVC is a unified framework with one set of rules for routing, filters, and more.</span></span> <span data-ttu-id="6e17a-115">依存関係の挿入は、.NET Core 自体に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-115">Dependency injection is built into .NET Core itself.</span></span> <span data-ttu-id="6e17a-116">サンプル内の `eShopPorted` アプリで示されているように、これらすべてを `Startup.cs` 内で構成できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-116">All of this can can be configured in `Startup.cs`, as is shown in the `eShopPorted` app in the sample.</span></span>

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a><span data-ttu-id="6e17a-117">HttpResponseMessage を ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="6e17a-117">Migrate HttpResponseMessage to ASP.NET Core</span></span>

<span data-ttu-id="6e17a-118">ASP.NET Web API アプリの中には、`HttpResponseMessage` を返すアクション メソッドが含まれているものもあります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-118">Some ASP.NET Web API apps may have action methods that return `HttpResponseMessage`.</span></span> <span data-ttu-id="6e17a-119">この型は ASP.NET Core には存在しません。</span><span class="sxs-lookup"><span data-stu-id="6e17a-119">This type does not exist in ASP.NET Core.</span></span> <span data-ttu-id="6e17a-120">これを `Delete` アクション メソッドで使用する例を以下に示します。基本 `ApiController` に対して `ResponseMessage` ヘルパー メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-120">Below is an example of its usage in a `Delete` action method, using the `ResponseMessage` helper method on the base `ApiController`:</span></span>

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

<span data-ttu-id="6e17a-121">ASP.NET Core MVC では、すべての一般的な HTTP 応答状態コードに対して利用可能なヘルパー メソッドが存在するため、上のメソッドは次のコードに移植できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-121">In ASP.NET Core MVC, there are helper methods available for all of the common HTTP response status codes, so the above method would be ported to the following code:</span></span>

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

<span data-ttu-id="6e17a-122">ヘルパーが存在しないカスタム状態コードを返す必要がある場合は、常に `return StatusCode(int statusCode)` を使用して任意の数値コードを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-122">If you do find that you need to return a custom status code for which no helper exists, you can always use `return StatusCode(int statusCode)` to return any numeric code you like.</span></span>

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a><span data-ttu-id="6e17a-123">コンテンツ ネゴシエーションを ASP.NET Web API から ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="6e17a-123">Migrate content negotiation from ASP.NET Web API to ASP.NET Core</span></span>

<span data-ttu-id="6e17a-124">ASP.NET Web API 2 では、[コンテンツ ネゴシエーション](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)がネイティブでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-124">ASP.NET Web API 2 supports [content negotiation](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) natively.</span></span> <span data-ttu-id="6e17a-125">サンプル アプリには、その結果を XML または JSON で一覧表示することでこのサポートを示す `BrandsController` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-125">The sample app includes a `BrandsController` that demonstrates this support by listing its results in either XML or JSON.</span></span> <span data-ttu-id="6e17a-126">これは要求の `Accept` ヘッダーに基づいており、そこに `application/xml` が含まれるか `application/json` が含まれるかによって変わります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-126">This is based on the request's `Accept` header, and changes when it includes `application/xml` or `application/json`.</span></span>

<span data-ttu-id="6e17a-127">ASP.NET MVC 5 アプリには、コンテンツ ネゴシエーションのサポートが組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="6e17a-127">ASP.NET MVC 5 apps do not have content negotiation support built in.</span></span>

<span data-ttu-id="6e17a-128">コンテンツ ネゴシエーションは、より柔軟性が高く、より多くのクライアントが API を利用できるようになるため、特定のエンコードの種類を返すよりも推奨されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-128">Content negotiation is preferable to returning a specific encoding type, as it is more flexible and makes the API available to a larger number of clients.</span></span> <span data-ttu-id="6e17a-129">現在、特定の形式を返すアクション メソッドを使用している場合は、コードを ASP.NET Core に移植するときに、コンテンツ ネゴシエーションでサポートされている結果の種類を返すようにそれらを変更することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-129">If you currently have action methods that return a specific format, you should consider modifying them to return a result type that supports content negotiation when you port the code to ASP.NET Core.</span></span>

<span data-ttu-id="6e17a-130">次のコードでは、クライアントの `Accept` ヘッダーのコンテンツに関係なく、データが JSON 形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-130">The following code returns data in JSON format regardless of client `Accept` header content:</span></span>

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

<span data-ttu-id="6e17a-131">ASP.NET Core MVC では、適切な[戻り値の型](/aspnet/core/web-api/action-return-types)が指定されていれば、[コンテンツ ネゴシエーションがネイティブでサポートされます](/aspnet/core/web-api/advanced/formatting)。</span><span class="sxs-lookup"><span data-stu-id="6e17a-131">[ASP.NET Core MVC supports content negotiation natively](/aspnet/core/web-api/advanced/formatting), provided an appropriate [return type](/aspnet/core/web-api/action-return-types) is used.</span></span> <span data-ttu-id="6e17a-132">コンテンツ ネゴシエーションは、コントローラー ヘルパー メソッドによって返される状態コード固有のアクション結果で返される [ObjectResult] によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-132">Content negotiation is implemented by [ObjectResult] which is returned by the status code-specific action results returned by the controller helper methods.</span></span> <span data-ttu-id="6e17a-133">ASP.NET Core MVC に実装された、コンテンツ ネゴシエーションを使用する上記のアクション メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-133">The previous action method, implemented in ASP.NET Core MVC and using content negotiation, would be:</span></span>

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

<span data-ttu-id="6e17a-134">これにより、データが既定で JSON 形式で返されるようになります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-134">This will default to returning the data in JSON format.</span></span> <span data-ttu-id="6e17a-135">[該当するフォーマッタがアプリに構成されている場合は](/aspnet/core/web-api/advanced/formatting)、XML やその他の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-135">XML and other formats will be used [if the app has been configured with the appropriate formatter](/aspnet/core/web-api/advanced/formatting).</span></span>

## <a name="custom-model-binding"></a><span data-ttu-id="6e17a-136">カスタム モデル バインド</span><span class="sxs-lookup"><span data-stu-id="6e17a-136">Custom model binding</span></span>

<span data-ttu-id="6e17a-137">ほとんどの ASP.NET MVC および Web API アプリでは、モデル バインドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-137">Most ASP.NET MVC and Web API apps make use of model binding.</span></span> <span data-ttu-id="6e17a-138">既定のモデル バインド構文は、これらのアプリと ASP.NET Core MVC との間でシームレスに移行できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-138">The default model binding syntax migrates fairly seamlessly between these apps and ASP.NET Core MVC.</span></span> <span data-ttu-id="6e17a-139">しかし、場合によっては、特定のモデルの型または使用シナリオをサポートするために、お客様が[カスタム モデル バインダー](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders)を作成していることがあります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-139">However, in some cases customers have written [custom model binders](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders) to support specific model types or usage scenarios.</span></span> <span data-ttu-id="6e17a-140">ASP.NET MVC および Web API プロジェクトのカスタム モデル バインダーでは、`System.Web.Mvc` および `System.Web.Http` 名前空間でそれぞれ定義されている個別の `IModelBinder` インターフェイスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-140">Custom model binders in ASP.NET MVC and Web API projects use separate `IModelBinder` interfaces defined in `System.Web.Mvc` and `System.Web.Http` namespaces, respectively.</span></span> <span data-ttu-id="6e17a-141">どちらの場合も、カスタム バインダーでは、コントローラーまたはアクション コンテキストとモデル バインド コンテキストを引数として受け取る `Bind` メソッドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-141">In both cases, the custom binder exposes a `Bind` method that accepts a controller or action context and a model binding context as arguments.</span></span>

<span data-ttu-id="6e17a-142">カスタム バインダーを作成したら、アプリに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-142">Once the custom binder is created, it must be registered with the app.</span></span> <span data-ttu-id="6e17a-143">この手順では、別の型 `ModelBinderProvider` を作成する必要があります。これはファクトリとして機能し、要求の間にモデル バインダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-143">This step requires creating another type, a `ModelBinderProvider`, which acts as a factory and creates the model binder during a request.</span></span> <span data-ttu-id="6e17a-144">次に示すように、MVC アプリでは `ApplicationStart` の間にバインダーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-144">Binders can be added during `ApplicationStart` in MVC apps as shown:</span></span>

```csharp
ModelBinderProviders.BinderProviders.Insert(0, new MyCustomBinderProvider()); // MVC
```

<span data-ttu-id="6e17a-145">Web API アプリでは、属性を使用してカスタム バインダーを参照できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-145">In Web API apps, custom binders can be referenced using attributes.</span></span> <span data-ttu-id="6e17a-146">次に示すように、`ModelBinder` 属性をアクション メソッドのパラメーターまたはパラメーターの型定義に追加できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-146">The `ModelBinder` attribute can be added to action method parameters or to the parameter's type definition, as shown:</span></span>

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

<span data-ttu-id="6e17a-147">ASP.NET Web API でモデル バインダーをグローバルに登録するには、アプリの起動時にそのプロバイダーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-147">To register a model binder globally in ASP.NET Web API, its provider must be added during app startup:</span></span>

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

<span data-ttu-id="6e17a-148">[カスタム モデル プロバイダーを ASP.NET Core に](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)移行する場合、Web API パターンの方が ASP.NET MVC 5 よりも ASP.NET Core のアプローチに近くなります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-148">When migrating [custom model providers to ASP.NET Core](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample), the Web API pattern is closer to the ASP.NET Core approach than the ASP.NET MVC 5.</span></span> <span data-ttu-id="6e17a-149">ASP.NET Core の `IModelBinder` インターフェイスと Web API のものとの主な違いは、ASP.NET Core のメソッドは非同期 (`BindModelAsync`) であり、Web API 版で必要な 2 つのパラメーターではなく、1 つの `BindingModelContext` パラメーターのみを必要とすることです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-149">The main differences between ASP.NET Core's `IModelBinder` interface and Web API's is that the ASP.NET Core method is async (`BindModelAsync`) and it only requires a single `BindingModelContext` parameter instead of two parameters like Web API's version required.</span></span> <span data-ttu-id="6e17a-150">ASP.NET Core では、個々のアクション メソッド パラメーターまたはそれらに関連付けられている型に対して `[ModelBinder]` 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-150">In ASP.NET Core, you can use a `[ModelBinder]` attribute on individual action method parameters or their associated types.</span></span> <span data-ttu-id="6e17a-151">また、必要に応じてアプリ内でグローバルに使用される `ModelBinderProvider` を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-151">You can also create a `ModelBinderProvider` that will be used globally within the app where appropriate.</span></span> <span data-ttu-id="6e17a-152">このようなプロバイダーを構成するには、`Startup` の `ConfigureServices` にコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-152">To configure such a provider, you would add code to `Startup` in `ConfigureServices`:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers(options =>
    {
        options.ModelBinderProviders.Insert(0, new CustomModelBinderProvider());
    });
}
```

## <a name="media-formatters"></a><span data-ttu-id="6e17a-153">メディア フォーマッタ</span><span class="sxs-lookup"><span data-stu-id="6e17a-153">Media formatters</span></span>

<span data-ttu-id="6e17a-154">ASP.NET Web API では複数のメディア形式がサポートされていて、カスタム メディア フォーマッタを使用して拡張できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-154">ASP.NET Web API supports multiple media formats and can be extended by using custom media formatters.</span></span> <span data-ttu-id="6e17a-155">このドキュメントでは、[CSV メディア フォーマッタの例](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter)について説明します。これを使うと、コンマ区切り値の形式でデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-155">The docs describe an [example CSV Media Formatter](/aspnet/web-api/overview/formats-and-model-binding/media-formatters#example-creating-a-csv-media-formatter) that can be used to send data in a comma-separated value format.</span></span> <span data-ttu-id="6e17a-156">Web API アプリでカスタム メディア フォーマッタを使用する場合は、それらを [ASP.NET Core カスタム フォーマッタ](/aspnet/core/web-api/advanced/custom-formatters)に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-156">If your Web API app uses custom media formatters, you'll need to convert them to [ASP.NET Core custom formatters](/aspnet/core/web-api/advanced/custom-formatters).</span></span>

<span data-ttu-id="6e17a-157">Web API 2 でカスタム フォーマッタを作成するためには、適切な基底クラスから継承した後、`HttpConfiguration` オブジェクトを使用して Web API パイプラインにフォーマッタを追加しました。</span><span class="sxs-lookup"><span data-stu-id="6e17a-157">To create a custom formatter in Web API 2, you inherited from an appropriate base class and then added the formatter to the Web API pipeline using the `HttpConfiguration` object:</span></span>

```csharp
public static void ConfigureApis(HttpConfiguration config)
{
    config.Formatters.Add(new ProductCsvFormatter());
}
```

<span data-ttu-id="6e17a-158">ASP.NET Core でも、プロセスは似ています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-158">In ASP.NET Core, the process is similar.</span></span> <span data-ttu-id="6e17a-159">ASP.NET Core では、入力フォーマッタ (モデル バインドで使用される) と出力フォーマッタ (応答の書式設定に使用される) の両方がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-159">ASP.NET Core supports both input formatters (used by model binding) and output formatters (used to format responses).</span></span> <span data-ttu-id="6e17a-160">特定の方法で出力応答にカスタム フォーマッタを追加するには、適切な基底クラスから継承し、`Startup` の MVC にフォーマッタを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-160">Adding a custom formatter to output responses in a specific way involves inheriting from an appropriate base class and adding the formatter to MVC in `Startup`:</span></span>

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

<span data-ttu-id="6e17a-161">基底クラスの完全な一覧は、[Microsoft.AspNetCore.Mvc.Formatters](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-161">You'll find a complete list of base classes in the [Microsoft.AspNetCore.Mvc.Formatters](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.mvc.formatters) namespace.</span></span>

<span data-ttu-id="6e17a-162">Web API フォーマッタから ASP.NET Core MVC フォーマッタに移行する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-162">The steps to migrate from a Web API formatter to an ASP.NET Core MVC formatter are:</span></span>

1. <span data-ttu-id="6e17a-163">新しいフォーマッタに適した基底クラスを特定する。</span><span class="sxs-lookup"><span data-stu-id="6e17a-163">Identify an appropriate base class for the new formatter.</span></span>
1. <span data-ttu-id="6e17a-164">基底クラスの新しいインスタンスを作成し、その必須メソッドを実装する。</span><span class="sxs-lookup"><span data-stu-id="6e17a-164">Create a new instance of the base class and implement its required methods.</span></span>
1. <span data-ttu-id="6e17a-165">Web API フォーマッタから新しい実装に機能をコピーする。</span><span class="sxs-lookup"><span data-stu-id="6e17a-165">Copy over the functionality from the Web API formatter to the new implementation.</span></span>
1. <span data-ttu-id="6e17a-166">新しいフォーマッタを使用するように、ASP.NET Core アプリの `ConfigureServices` メソッドで MVC を構成する。</span><span class="sxs-lookup"><span data-stu-id="6e17a-166">Configure MVC in the ASP.NET Core App's `ConfigureServices` method to use the new formatter.</span></span>

## <a name="custom-filters"></a><span data-ttu-id="6e17a-167">カスタム フィルター</span><span class="sxs-lookup"><span data-stu-id="6e17a-167">Custom filters</span></span>

<span data-ttu-id="6e17a-168">ASP.NET Core アプリでは、要求処理パイプラインの特定のステージの前または後にコードを実行するために、フィルターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-168">Filters are used in ASP.NET Core apps to execute code before and/or after certain stages in the request processing pipeline.</span></span> <span data-ttu-id="6e17a-169">ASP.NET MVC と Web API でもほぼ同じ方法でフィルターが使用されますが、細部は異なります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-169">ASP.NET MVC and Web API also use filters in much the same way, but the details vary.</span></span> <span data-ttu-id="6e17a-170">たとえば、[ASP.NET MVC では 4 種類のフィルターがサポートされています](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters)。</span><span class="sxs-lookup"><span data-stu-id="6e17a-170">For instance, [ASP.NET MVC supports four kinds of filters](/aspnet/mvc/overview/older-versions-1/controllers-and-routing/understanding-action-filters-cs#the-different-types-of-filters).</span></span> <span data-ttu-id="6e17a-171">ASP.NET Web API 2 でも同様のフィルターがサポートされており、MVC と Web API の両方に[フィルターをオーバーライドする](/dotnet/api/system.web.mvc.filters.ioverridefilter)属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-171">ASP.NET Web API 2 supports similar filters, and both MVC and Web API included attributes to [override filters](/dotnet/api/system.web.mvc.filters.ioverridefilter).</span></span>

<span data-ttu-id="6e17a-172">ASP.NET MVC と Web API アプリで使用される最も一般的なフィルターは、アクション フィルターです。これは [IActionFilter インターフェイス](/dotnet/api/system.web.mvc.iactionfilter)によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-172">The most common filter used in ASP.NET MVC and Web API apps is the action filter, which is defined by an [IActionFilter interface](/dotnet/api/system.web.mvc.iactionfilter).</span></span> <span data-ttu-id="6e17a-173">このインターフェイスには、前 (`OnActionExecuting`) と後 (`OnActionExecuted`) 用のメソッドが用意されています。各メソッドに示されているように、アクションの実行の前後にコードを実行するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-173">This interface provides methods for before (`OnActionExecuting`) and after (`OnActionExecuted`) which can be used to execute code before and/or after an action executes, as noted for each method.</span></span>

<span data-ttu-id="6e17a-174">ASP.NET Core でも引き続きフィルターがサポートされ、その MVC と Web API の統合は、それらの実装に対するアプローチが 1 つだけであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-174">ASP.NET Core continues to support filters, and its unification of MVC and Web API means there is only one approach to their implementation.</span></span> <span data-ttu-id="6e17a-175">こちらの[ドキュメントには、ASP.NET Core MVC に組み込まれている 5 種類のフィルターの詳細な説明が記載されています](/aspnet/core/mvc/controllers/filters#filter-types)。</span><span class="sxs-lookup"><span data-stu-id="6e17a-175">The [docs include detailed coverage of the five (5) kinds of filters built into ASP.NET Core MVC](/aspnet/core/mvc/controllers/filters#filter-types).</span></span> <span data-ttu-id="6e17a-176">ASP.NET MVC と ASP.NET Web API でサポートされているすべてのフィルターのバリアントには、ASP.NET Core の関連バージョンがあるため、移行は通常、適切なインターフェイスや基底クラスを特定してコードを移行するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-176">All of the filter variants supported in ASP.NET MVC and ASP.NET Web API have associated versions in ASP.NET Core, so migration is generally just a matter of identifying the appropriate interface and/or base class and migrating the code over.</span></span>

<span data-ttu-id="6e17a-177">同期インターフェイスに加えて、ASP.NET Core には `IAsyncActionFilter` などの非同期インターフェイスも用意されており、次に示すように、アクションの前と後両方に実行するコードを組み込むために使用できる、単一の非同期メソッドが提供されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-177">In addition to the synchronous interfaces, ASP.NET Core also provides async interfaces like `IAsyncActionFilter` which provide a single async method that can be used to incorporate code to run both before and after the action, as shown:</span></span>

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

<span data-ttu-id="6e17a-178">非同期コード (または非同期にする必要のあるコード) を移行する場合、チームでは、この目的のために用意されている組み込みの非同期型の利用を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-178">When migrating async code (or code that should be async), teams should consider leveraging the built in async types that are provided for this purpose.</span></span>

<span data-ttu-id="6e17a-179">ほとんどの ASP.NET MVC および Web API アプリでは、多数のカスタム フィルターが使用されることはありません。</span><span class="sxs-lookup"><span data-stu-id="6e17a-179">Most ASP.NET MVC and Web API apps do not use a large number of custom filters.</span></span> <span data-ttu-id="6e17a-180">ASP.NET Core MVC でのフィルターに対するアプローチは ASP.NET MVC および Web API でのフィルターと密接に適合するため、カスタム フィルターの移行は通常、非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="6e17a-180">Since the approach to filters in ASP.NET Core MVC is closely aligned with filters in ASP.NET MVC and Web API, the migration of custom filters is generally fairly straightforward.</span></span> <span data-ttu-id="6e17a-181">ASP.NET Core のドキュメントに記載されているフィルターに関する詳細なドキュメントを必ずお読みください。確実に十分に理解できたら、古いシステムから新しいシステムのフィルターにロジックを移植します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-181">Be sure to read the detailed documentation on filters in ASP.NET Core's docs, and once you're sure you have a good understanding of them, port the logic from the old system to the new system's filters.</span></span>

## <a name="route-constraints"></a><span data-ttu-id="6e17a-182">ルート制約</span><span class="sxs-lookup"><span data-stu-id="6e17a-182">Route constraints</span></span>

<span data-ttu-id="6e17a-183">ASP.NET Core では、要求をルーティングするために、ルート制約を使用して要求が適切にルーティングされるようにします。</span><span class="sxs-lookup"><span data-stu-id="6e17a-183">ASP.NET Core uses route constraints to help ensure requests are routed properly to route a request.</span></span> <span data-ttu-id="6e17a-184">[ASP.NET Core では、この目的のためにさまざまなルート制約が多数サポートされています]/aspnet/core/fundamentals/routing#route-constraint-reference)。</span><span class="sxs-lookup"><span data-stu-id="6e17a-184">[ASP.NET Core supports a large number of different route constraints for this purpose]/aspnet/core/fundamentals/routing#route-constraint-reference).</span></span> <span data-ttu-id="6e17a-185">ルート制約はルート テーブルで適用できますが、ASP.NET MVC 5 や [ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) を使用して構築されたほとんどのアプリでは、属性ルートに適用されたインライン ルート制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-185">Route constraints can be applied in the route table, but most apps built with ASP.NET MVC 5 and/or [ASP.NET Web API 2](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints) use inline route constraints applied to attribute routes.</span></span> <span data-ttu-id="6e17a-186">インライン ルート制約では、次のような形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-186">Inline route constraints use a format like this one:</span></span>

```csharp
[Route("/customer/{id:int}")]
```

<span data-ttu-id="6e17a-187">`id` ルート パラメーターの後の `:int` によって、値が `int` 型に一致するように制約されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-187">The `:int` after the `id` route parameter constrains the value to match the the `int` type.</span></span> <span data-ttu-id="6e17a-188">ルート制約を使用する利点の 1 つは、パラメーターの型が異なるだけで他は等しい 2 つのルートが存在できるようになることです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-188">One benefit of using route constraints is that they allow for two otherwise-identical routes to exist where the parameters differ only by their type.</span></span> <span data-ttu-id="6e17a-189">これにより、パラメーターの型のみに基づくルートの[メソッドのオーバーロード](/dotnet/standard/design-guidelines/member-overloading)に相当するものが可能になります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-189">This allows for the equivalent of [method overloading](/dotnet/standard/design-guidelines/member-overloading) of routes based solely on parameter type.</span></span>

<span data-ttu-id="6e17a-190">ルート制約、その構文、および使用法のセットは、3 つのアプローチすべてにおいて非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-190">The set of route constraints, their syntax, and usage is very similar between all three approaches.</span></span> <span data-ttu-id="6e17a-191">カスタム ルート制約は、お客様のアプリケーションでは非常にまれです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-191">Custom route constraints are fairly rare in customer applications.</span></span> <span data-ttu-id="6e17a-192">アプリでカスタム ルート制約を使用していて ASP.NET Core に移植する必要がある場合は、こちらのドキュメントに [ASP.NET Core でカスタム ルート制約を作成する方法](/aspnet/core/fundamentals/routing#custom-route-constraints)を示す例が記載されています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-192">If your app uses a custom route constraint and needs to port to ASP.NET Core, the docs include examples showing [how to create custom route constraints in ASP.NET Core](/aspnet/core/fundamentals/routing#custom-route-constraints).</span></span> <span data-ttu-id="6e17a-193">基本的に、必要なすべての操作は、`IRouteConstraint` とその `Match` メソッドを実装した後、アプリのルーティングを構成するときにカスタム制約を追加することだけです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-193">Essentially all that's required is to implement `IRouteConstraint` and its `Match` method, and then add the custom constraint when configuring routing for the app:</span></span>

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

<span data-ttu-id="6e17a-194">これは、ASP.NET Web API でカスタム制約を使用する方法とよく似ています。その場合 `IHttpRouteConstraint` を使用し、リゾルバーと `HttpConfiguration.MapHttpAttributeRoutes` への呼び出しを使用してそれを構成します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-194">This is very similar to how custom constraints are used in ASP.NET Web API, which uses `IHttpRouteConstraint` and configures it using a resolver and a call to `HttpConfiguration.MapHttpAttributeRoutes`:</span></span>

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

<span data-ttu-id="6e17a-195">ASP.NET MVC 5 でもよく似た方法に従います。インターフェイス名として `IRouteConstraint` を使用し、ルート構成の一部として制約を構成します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-195">ASP.NET MVC 5 follows a very similar approach, using `IRouteConstraint` for its interface name and configuring the constraint as part of route configuration:</span></span>

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

<span data-ttu-id="6e17a-196">通常、ルート制約の使用方法およびカスタム ルート制約を ASP.NET Core に移行するのは、非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="6e17a-196">Migrating route constraint usage as well as custom route constraints to ASP.NET Core is typically very straightforward.</span></span>

## <a name="custom-route-handlers"></a><span data-ttu-id="6e17a-197">カスタム ルート ハンドラー</span><span class="sxs-lookup"><span data-stu-id="6e17a-197">Custom route handlers</span></span>

<span data-ttu-id="6e17a-198">ASP.NET MVC 5 のもう 1 つのかなり高度な機能は、ルート ハンドラーです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-198">Another fairly advanced feature of ASP.NET MVC 5 is route handlers.</span></span> <span data-ttu-id="6e17a-199">カスタム ルート ハンドラーでは `IRouteHandler` を実装します。これには、指定された要求に対して `IHttpHandler` を返す 1 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-199">Custom route handlers implement `IRouteHandler`, which includes a single method that returns an `IHttpHandler` for a give request.</span></span> <span data-ttu-id="6e17a-200">次に、`IHttpHandler` によって、`IsReusable` プロパティと 1 つの `ProcessRequest` メソッドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-200">The `IHttpHandler`, in turn, exposes an `IsReusable` property and a single `ProcessRequest` method.</span></span> <span data-ttu-id="6e17a-201">ASP.NET MVC 5 では、カスタム ハンドラーを使用するようにルート テーブルで特定のルートを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-201">In ASP.NET MVC 5, you can configure a particular route in the route table to use your custom handler:</span></span>

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.Add(new Route("custom", new CustomRouteHandler()));
}
```

<span data-ttu-id="6e17a-202">カスタム ルート ハンドラーを ASP.NET MVC 5 から ASP.NET Core に移行する場合、フィルター (アクション フィルターなど) またはカスタムの [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter) のいずれかを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-202">To migrate custom route handlers from ASP.NET MVC 5 to ASP.NET Core, you can either use a filter (such as an action filter) or a custom [`IRouter`](/dotnet/api/microsoft.aspnetcore.routing.irouter).</span></span> <span data-ttu-id="6e17a-203">フィルターの方法は比較的簡単であり、*Startup.cs* の `ConfigureServices` に MVC を追加するときにグローバル フィルターとして追加できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-203">The filter approach is relatively straightforward, and can be added as a global filter when MVC is added to `ConfigureServices` in *Startup.cs*.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(CustomActionFilter));
    });
}
```

<span data-ttu-id="6e17a-204">`IRouter` オプションの場合は、インターフェイスの `RouteAsync` メソッドと `GetVirtualPath` メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-204">The `IRouter` option requires implementing the interface's `RouteAsync` and `GetVirtualPath` methods.</span></span> <span data-ttu-id="6e17a-205">カスタム ルーターは、*Startup.cs* の `Configure` メソッドで要求パイプラインに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-205">The custom router is added to the request pipeline in the `Configure` method in *Startup.cs*.</span></span>

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

<span data-ttu-id="6e17a-206">ASP.NET Web API では、これらのハンドラーは [カスタム メッセージ ハンドラー](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)と呼ばれ、*ルート ハンドラー* とは呼ばれません。</span><span class="sxs-lookup"><span data-stu-id="6e17a-206">In ASP.NET Web API, these handlers are referred to as [custom message handlers](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers), rather than *route handlers*.</span></span> <span data-ttu-id="6e17a-207">メッセージ ハンドラーは `DelegatingHandler` から派生し、その `SendAsync` メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-207">Message handlers must derive from `DelegatingHandler` and override its `SendAsync` method.</span></span> <span data-ttu-id="6e17a-208">メッセージ ハンドラーを連結して、ASP.NET Core のミドルウェアおよびその要求パイプラインと非常によく似た方法でパイプラインを形成できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-208">Message handlers can be chained together to form a pipeline in a fashion that is very similar to ASP.NET Core middleware and its request pipeline.</span></span>

<span data-ttu-id="6e17a-209">ASP.NET Core には、`DelegatingHandler` 型や、個別のメッセージ ハンドラー パイプラインがありません。</span><span class="sxs-lookup"><span data-stu-id="6e17a-209">ASP.NET Core has no `DelegatingHandler` type or separate message handler pipeline.</span></span> <span data-ttu-id="6e17a-210">代わりに、グローバル フィルター、カスタム `IRouter` インスタンス (上記を参照)、またはカスタム ミドルウェアを使用して、そのようなハンドラーを移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-210">Instead, such handlers should be migrated using global filters, custom `IRouter` instances (see above), or custom middleware.</span></span> <span data-ttu-id="6e17a-211">ASP.NET Core MVC フィルターと `IRouter` 型には、コントローラーやアクションなどの MVC 構成要素に対する組み込みアクセスを持つという利点があります。一方、ミドルウェアは MVC とは関係ない下位レベルのアプローチです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-211">ASP.NET Core MVC filters and `IRouter` types have the advantage of having built-in access to MVC constructs like controllers and actions, while middleware is a lower level approach that has no ties to MVC.</span></span> <span data-ttu-id="6e17a-212">これにより柔軟性が向上しますが、MVC の構成要素にアクセスする必要がある場合はより多くの労力が必要になります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-212">This makes it more flexible but also requires more effort if you need to access MVC components.</span></span>

## <a name="cors-support"></a><span data-ttu-id="6e17a-213">CORS のサポート</span><span class="sxs-lookup"><span data-stu-id="6e17a-213">CORS support</span></span>

<span data-ttu-id="6e17a-214">CORS (クロスオリジン リソース共有) は、サーバーが、提供した応答からのものではない要求を受け入れることを許可する W3C 標準です。</span><span class="sxs-lookup"><span data-stu-id="6e17a-214">CORS, or Cross-Origin Resource Sharing, is a W3C standard that allows servers to accept requests that don't originate from responses they've served.</span></span> <span data-ttu-id="6e17a-215">ASP.NET MVC 5 および ASP.NET Web API 2 では、さまざまな方法で CORS がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-215">ASP.NET MVC 5 and ASP.NET Web API 2 support CORS in different ways.</span></span> <span data-ttu-id="6e17a-216">ASP.NET MVC 5 で CORS サポートを有効にする最も簡単な方法は、次のようなアクション フィルターを使用することです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-216">The simplest way to enable CORS support in ASP.NET MVC 5 is with an action filter like this one:</span></span>

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

<span data-ttu-id="6e17a-217">ASP.NET Web API でもこのようなフィルターを使用することができますが、[CORS を有効にするための組み込みサポート](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors)も用意されています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-217">ASP.NET Web API can also use such a filter, but it has [built-in support for enabling CORS](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors) as well:</span></span>

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

<span data-ttu-id="6e17a-218">これを追加した後は、次のように、`EnableCors` 属性を使用して許可されたオリジン、ヘッダー、およびメソッドを構成できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-218">Once this is added, you can configure allowed origins, headers, and methods using the `EnableCors` attribute, like so:</span></span>

```csharp
[EnableCors(origins: "https://dot.net", headers: "*", methods: "*")]
public class TestController : ApiController
{
    // Controller methods not shown...
}
```

<span data-ttu-id="6e17a-219">ASP.NET MVC 5 または ASP.NET Web API 2 から CORS の実装を移行する前に、必ず [CORS のしくみ](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) を確認し、現在のシステムで CORS が期待どおりに動作していることを示す自動テストを作成してください。</span><span class="sxs-lookup"><span data-stu-id="6e17a-219">Before migrating your CORS implementation from ASP.NET MVC 5 or ASP.NET Web API 2, be sure to review [how CORS works](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#how-cors-works) and create some automated tests that demonstrate CORS is working as expected in your current system.</span></span>

<span data-ttu-id="6e17a-220">ASP.NET Core には、CORS を有効にするための組み込みの方法が 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-220">In ASP.NET Core, there are three built-in ways to enable CORS:</span></span>

- <span data-ttu-id="6e17a-221">`ConfigureServices` で[ポリシーを使用して構成する](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware)</span><span class="sxs-lookup"><span data-stu-id="6e17a-221">[Configured via policy](/aspnet/core/security/cors?#cors-with-named-policy-and-middleware) in `ConfigureServices`</span></span>
- <span data-ttu-id="6e17a-222">[エンドポイント ルーティング](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing)を使用して有効にする</span><span class="sxs-lookup"><span data-stu-id="6e17a-222">Enabled with [endpoint routing](/aspnet/core/security/cors?#enable-cors-with-endpoint-routing)</span></span>
- <span data-ttu-id="6e17a-223">[`EnableCors` 属性](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes)を使用して有効にする</span><span class="sxs-lookup"><span data-stu-id="6e17a-223">Enabled with the [`EnableCors` attribute](/aspnet/core/security/cors?view=aspnetcore-5.0#enable-cors-with-attributes)</span></span>

<span data-ttu-id="6e17a-224">これらの各方法については、上記のオプションのリンク先のドキュメントで詳しく説明されています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-224">Each of these approaches is covered in detail in the docs, which are linked from the above options.</span></span> <span data-ttu-id="6e17a-225">どれを選択するかは、既存のアプリで CORS がどのようにサポートされているかによって大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-225">Which one you choose will largely depend on how your existing app supports CORS.</span></span> <span data-ttu-id="6e17a-226">アプリで属性を使用している場合は、おそらく `EnableCors` 属性を使用するように移行するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="6e17a-226">If the app uses attributes, you can probably migrate to use the `EnableCors` attribute most easily.</span></span> <span data-ttu-id="6e17a-227">アプリでフィルターを使用している場合は、その方法を使用し続ける (ただしこれは ASP.NET Core で使用される一般的な方法ではありません) か、属性またはポリシーを使用するように移行することができます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-227">If your app uses filters, you could continue using that approach (though it's not the typical approach used in ASP.NET Core), or migrate to use attributes or policies.</span></span> <span data-ttu-id="6e17a-228">エンドポイント ルーティングは、ASP.NET Core 3 で導入された比較的新しい機能です。そのため、ASP.NET MVC 5 や ASP.NET Web API 2 アプリには同様の機能はありません。</span><span class="sxs-lookup"><span data-stu-id="6e17a-228">Endpoint routing is a relatively new feature introduced with ASP.NET Core 3 and as such it doesn't have a close analog in ASP.NET MVC 5 or ASP.NET Web API 2 apps.</span></span>

## <a name="custom-areas"></a><span data-ttu-id="6e17a-229">カスタム エリア</span><span class="sxs-lookup"><span data-stu-id="6e17a-229">Custom areas</span></span>

<span data-ttu-id="6e17a-230">多くの ASP.NET MVC アプリでは、エリアを使用してプロジェクトを整理します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-230">Many ASP.NET MVC apps use Areas to organize the project.</span></span> <span data-ttu-id="6e17a-231">エリアは通常、プロジェクトのルートの *Areas* フォルダー内に配置し、アプリケーションの起動時に、通常は `Application_Start()` で登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-231">Areas typically reside in the root of the project in an *Areas* folder, and must be registered when the application starts, typically in `Application_Start()`:</span></span>

```csharp
AreaRegistration.RegisterAllAreas();
```

<span data-ttu-id="6e17a-232">起動時にすべてのエリアを登録する代わりに、個々のコントローラーで `RouteArea` 属性を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-232">An alternative to registering all areas in startup is to use the `RouteArea` attribute on individual controllers:</span></span>

```csharp
[RouteArea("Admin")]
public class SomeController : Controller
```

<span data-ttu-id="6e17a-233">エリアを使用する場合は、別のエリアにあるアクションへのリンクを生成するために、追加の引数が HTML ヘルパー メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-233">When using Areas, additional arguments are passed into HTML helper methods to generate links to actions in different areas:</span></span>

```cshtml
@Html.ActionLink("News", "Index", "News", new { area = "News" }, null)
```

<span data-ttu-id="6e17a-234">通常、ASP.NET Web API アプリでは、エリアを明示的に使用しません。プロジェクト内の任意のフォルダーにコントローラーを配置できるためです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-234">ASP.NET Web API apps don't typically use areas explicitly, since their controllers can be placed in any folder in the project.</span></span> <span data-ttu-id="6e17a-235">チームでは、任意のフォルダー構造を使用して、使用する API コントローラーを整理することができます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-235">Teams can use any folder structure they like to organize their API controllers.</span></span>

<span data-ttu-id="6e17a-236">[エリア](/aspnet/core/mvc/controllers/areas)は ASP.NET Core MVC でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6e17a-236">[Areas](/aspnet/core/mvc/controllers/areas) are supported in ASP.NET Core MVC.</span></span> <span data-ttu-id="6e17a-237">使用されるアプローチは、ASP.NET MVC 5 におけるエリアの使用とほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-237">The approach used is nearly identical to the use of areas in ASP.NET MVC 5.</span></span> <span data-ttu-id="6e17a-238">エリアを使用したコードを移行する開発者は、次の相違点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="6e17a-238">Developers migrating code using areas should keep in mind the following differences:</span></span>

- <span data-ttu-id="6e17a-239">`AreaRegistration.RegisterAllAreas` は ASP.NET Core MVC では使用されません</span><span class="sxs-lookup"><span data-stu-id="6e17a-239">`AreaRegistration.RegisterAllAreas` is not used in ASP.NET Core MVC</span></span>
- <span data-ttu-id="6e17a-240">エリアは `[Area("name")]` 属性を使用して適用されます (ASP.NET MVC 5 のように `RouteArea` ではありません)</span><span class="sxs-lookup"><span data-stu-id="6e17a-240">Areas are applied using the `[Area("name")]` attribute (not `RouteArea` as in ASP.NET MVC 5)</span></span>
- <span data-ttu-id="6e17a-241">必要に応じて、ルート テーブル テンプレートにエリアを追加できます (または、属性ルーティングを使用できます)</span><span class="sxs-lookup"><span data-stu-id="6e17a-241">Areas can be added to the route table templates, if desired (or they can use attribute routing)</span></span>

<span data-ttu-id="6e17a-242">ASP.NET Core MVC でルート テーブルにエリアのサポートを追加するには、以下を *Startup.cs* の `Configure` に追加します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-242">To add area support to the route table in ASP.NET Core MVC, you would add the following in `Configure` in *Startup.cs*:</span></span>

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

<span data-ttu-id="6e17a-243">また、属性ルーティングでエリアを使用することもできます。その場合、ルート定義で `{area}` キーワードを使用します (ルート テンプレートで使用できるいくつかの[予約済みルーティング名](/aspnet/core/mvc/controllers/routing#reserved-routing-names)の 1 つです)。</span><span class="sxs-lookup"><span data-stu-id="6e17a-243">Areas can also be used with attribute routing, using the `{area}` keyword in the route definition (it's one of several [reserved routing names](/aspnet/core/mvc/controllers/routing#reserved-routing-names) that can be used with route templates).</span></span>

<span data-ttu-id="6e17a-244">タグ ヘルパーでは、`asp-area` 属性でエリアがサポートされています。これを使用して、Razor ビューおよびページ内でリンクを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-244">Tag helpers support areas with the `asp-area` attribute, which can be used to generate links in Razor views and pages:</span></span>

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

<span data-ttu-id="6e17a-245">Razor Pages に移行する場合は、*Pages* フォルダー内の *Areas* フォルダーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-245">If you're migrating to Razor Pages you will need to use an *Areas* folder in your *Pages* folder.</span></span> <span data-ttu-id="6e17a-246">詳細については、「[Razor Pages でのエリア](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e17a-246">For more information, see [Areas with Razor Pages](/aspnet/core/mvc/controllers/areas#areas-with-razor-pages).</span></span>

<span data-ttu-id="6e17a-247">上記のガイダンスに加えて、チームでは移行計画プロセスの一環として、[ASP.NET Core のルーティングがエリアと連携するしくみ](/aspnet/core/mvc/controllers/routing#areas)を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-247">In addition to the above guidance, teams should review [how routing in ASP.NET Core works with areas](/aspnet/core/mvc/controllers/routing#areas) as part of their migration planning process.</span></span>

## <a name="integration-tests-for-aspnet-mvc-and-aspnet-web-api"></a><span data-ttu-id="6e17a-248">ASP.NET MVC と ASP.NET Web API 用の統合テスト</span><span class="sxs-lookup"><span data-stu-id="6e17a-248">Integration tests for ASP.NET MVC and ASP.NET Web API</span></span>

<span data-ttu-id="6e17a-249">統合テストは、アプリの異なるいくつかの部分が正しく連携して動作することを検証する自動テストです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-249">Integration tests are automated tests that verify several different parts of an app work together correctly.</span></span> <span data-ttu-id="6e17a-250">通常、ASP.NET MVC と ASP.NET Web API 用の統合テストを作成する場合は、実際の Web サーバー (IIS や IIS Express のローカル インスタンスなど) にアプリを配置した後、HTTP クライアントを使用してこのホストされたアプリケーションに要求を行う必要がありました。</span><span class="sxs-lookup"><span data-stu-id="6e17a-250">Writing integration tests for ASP.NET MVC and ASP.NET Web API usually involved deploying the app to a real web server, such as a local instance of IIS or IIS Express, and then making requests to this hosted application using an HTTP client.</span></span> <span data-ttu-id="6e17a-251">このようなテストの一部では、[Selenium](https://www.selenium.dev/) などのブラウザー自動化ツールを使用して、クライアント側のユーザー インターフェイスと対話する場合があります。ただし、それらは多くの場合、統合テストではなく *UI テスト* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-251">Some of these tests may interact with the client-side user interface using browser automation tools like [Selenium](https://www.selenium.dev/), though often these are referred to as *UI tests* rather than integration tests.</span></span>

<span data-ttu-id="6e17a-252">移行したアプリがその元のバージョンと同じ動作をする場合、統合テスト (および UI テスト) を実行するためにチームで使用している既存のテクノロジは、すべて以前と同じように機能し続けます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-252">If your migrated app shares the same behavior as its original version, whatever existing technology the team is using to perform integration tests (and UI tests) should continue to work just as it did before.</span></span> <span data-ttu-id="6e17a-253">通常、これらのテストは、テスト対象のアプリをホストするために使用されている基になるテクノロジには関心がなく、HTTP 要求を介してのみ対話が行われます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-253">These tests are usually indifferent to the underlying technology used to host the app they're testing, and interact with it only through HTTP requests.</span></span> <span data-ttu-id="6e17a-254">より困難になる可能性があるのは、テストがアプリと対話し、各テストの前に既知の良好な状態になるようにする方法に関してです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-254">Where things may get more challenging is with how the tests interact with the app to get it into a known good state prior to each test.</span></span> <span data-ttu-id="6e17a-255">これにはいくつかの移行作業が必要になる場合があります。ASP.NET Core では、ASP.NET MVC や ASP.NET Web API と比較して、構成と起動が大きく異なるためです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-255">This may require some migration effort, since configuration and startup are significantly different in ASP.NET Core compared to ASP.NET MVC or ASP.NET Web API.</span></span>

<span data-ttu-id="6e17a-256">[ASP.NET Core の組み込み統合テスト](/aspnet/core/test/integration-tests) サポートを使用するように統合テストを移行することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6e17a-256">Teams should strongly consider migrating their integration tests to use [ASP.NET Core's built-in integration testing](/aspnet/core/test/integration-tests) support.</span></span> <span data-ttu-id="6e17a-257">ASP.NET Core では、アプリを `TestHost` に配置することで、アプリをテストできます。これは `WebApplicationFactory` を使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-257">In ASP.NET Core, apps can be tested by deploying them to a `TestHost`, which is configured using a `WebApplicationFactory`.</span></span> <span data-ttu-id="6e17a-258">テスト用にアプリをホストするために必要なセットアップが少しありますが、一度設定すれば、個々の統合テストの作成が非常に簡単になります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-258">There's a little bit of setup required to host the app for testing, but once this is in place, creating individual integration tests is very straightforward.</span></span>

<span data-ttu-id="6e17a-259">ASP.NET Core の統合テスト サポートの最も優れた機能の 1 つは、アプリがメモリ内でホストされることです。</span><span class="sxs-lookup"><span data-stu-id="6e17a-259">One of the best features of ASP.NET Core's integration testing support is that the app is hosted in memory.</span></span> <span data-ttu-id="6e17a-260">アプリをホストするために実際の Web サーバーを構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6e17a-260">There's no need to configure a real webserver to host the app.</span></span> <span data-ttu-id="6e17a-261">ブラウザー自動化ツールを使用する必要はありません (ASP.NET Core のみをテストし、クライアント側の動作はテストしない場合)。</span><span class="sxs-lookup"><span data-stu-id="6e17a-261">There's no need to use a browser automation tool (if you're only testing ASP.NET Core and not client-side behavior).</span></span> <span data-ttu-id="6e17a-262">ファイアウォールの問題やプロセスの開始と停止に関する問題など、自動化された統合テストのために実際の Web サーバーを使用しようとしたときに発生する可能性のある問題の多くが、この方法によって排除されます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-262">Many of the problems that can be encountered when trying to use a real web server for automated integration tests, such as firewall issues or process start/stop issues, are eliminated with this approach.</span></span> <span data-ttu-id="6e17a-263">また、要求はすべてメモリ内で、ネットワーク要件なしで作成されるため、個別の Web サーバーを設定して (同じコンピューター上で実行されていても) ネットワーク経由で通信する必要があるテストよりも、テストの実行がずっと高速になる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-263">Since the requests are all made in memory with no network requirement, the tests also tend to run much faster than tests that must set up a separate webserver and communicate with it over the network (even if it's running on the same machine).</span></span>

<span data-ttu-id="6e17a-264">[eShopOnWeb 参照アプリケーション](https://github.com/dotnet-architecture/eShopOnWeb)からの ASP.NET Core 統合テスト (下位レベルの統合テストと区別するため "*機能テスト*" と呼ばれることもあります) の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-264">Below you can see an example ASP.NET Core integration test (sometimes referred to as *functional tests* to distinguish them from lower-level integration tests) from the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb):</span></span>

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

<span data-ttu-id="6e17a-265">移行しているアプリに統合テストがない場合、移行プロセスはそれらを追加する良い機会となります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-265">If the app being migrated has no integration tests, the migration process can be a great opportunity to add some.</span></span> <span data-ttu-id="6e17a-266">これらのテストでは、移行されたアプリがチームの想定どおりに動作することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-266">These tests can verify that the migrated app behaves as the team expects.</span></span> <span data-ttu-id="6e17a-267">このようなテストを移行の早い段階で実行すると、後の移行作業によってアプリの以前に移行された部分が破損しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-267">When such tests are in place early in a migration, they can ensure that later migration efforts do not break previously migrated portions of the app.</span></span> <span data-ttu-id="6e17a-268">ASP.NET Core で統合テストを設定して実行するのがいかに簡単であるかを考えると、通常、そのようなテストの設定に費やした投資に対する利益は、非常に高くなります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-268">Given how easy it is to set up and run integration tests in ASP.NET Core, the return on the investment spent setting up such tests is usually pretty high.</span></span>

## <a name="wcf-client-configuration"></a><span data-ttu-id="6e17a-269">WCF クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="6e17a-269">WCF client configuration</span></span>

<span data-ttu-id="6e17a-270">アプリで現在、クライアントとして WCF サービスに依存している場合、このシナリオはサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-270">If your app currently relies on WCF services as a client, this scenario is supported.</span></span> <span data-ttu-id="6e17a-271">ただし、*web.config* から新しい *appsettings.json* ファイルを使用するように[構成を移行する](/aspnet/core/migration/configuration)必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e17a-271">However, you will need to [migrate your configuration](/aspnet/core/migration/configuration) from *web.config* to use the new *appsettings.json* file.</span></span> <span data-ttu-id="6e17a-272">別の方法として、クライアントの作成時にプログラムによって必要な構成を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="6e17a-272">Another option is to add any necessary configuration to your clients programmatically when you create them.</span></span> <span data-ttu-id="6e17a-273">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6e17a-273">For example:</span></span>

```csharp
var wcfClient = new OrderServiceClient(
    new BasicHttpBinding(BasicHttpSecurityMode.None),
    new EndpointAddress("http://localhost:5050/OrderService.svc"));
```

<span data-ttu-id="6e17a-274">アプリが依存している、WCF を使用して構築された広範なサービスが組織にある場合は、代わりに gRPC を使用するように移行することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="6e17a-274">If your organization has extensive services built using WCF that your app relies on, consider migrating them to use gRPC instead.</span></span> <span data-ttu-id="6e17a-275">gRPC の詳細、移行が必要な理由、および詳細な移行ガイドについては、[WCF 開発者向け gRPC](/dotnet/architecture/grpc-for-wcf-developers/) に関する電子ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e17a-275">For more details on gRPC, why you may wish to migrate, and a detailed migration guide, consult the [gRPC for WCF Developers](/dotnet/architecture/grpc-for-wcf-developers/) eBook.</span></span>

## <a name="references"></a><span data-ttu-id="6e17a-276">References</span><span class="sxs-lookup"><span data-stu-id="6e17a-276">References</span></span>

- [<span data-ttu-id="6e17a-277">ASP.NET Web API のコンテンツ ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="6e17a-277">ASP.NET Web API Content Negotiation</span></span>](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [<span data-ttu-id="6e17a-278">ASP.NET Core Web API の応答データの書式設定</span><span class="sxs-lookup"><span data-stu-id="6e17a-278">Format response data in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/formatting)
- [<span data-ttu-id="6e17a-279">ASP.NET Web API のカスタム モデル バインダー</span><span class="sxs-lookup"><span data-stu-id="6e17a-279">Custom Model Binders in ASP.NET Web API</span></span>](/aspnet/web-api/overview/formats-and-model-binding/parameter-binding-in-aspnet-web-api#model-binders)
- [<span data-ttu-id="6e17a-280">ASP.NET Core のカスタム モデル バインダー</span><span class="sxs-lookup"><span data-stu-id="6e17a-280">Custom Model Binders in ASP.NET Core</span></span>](/aspnet/core/mvc/advanced/custom-model-binding#custom-model-binder-sample)
- <span data-ttu-id="6e17a-281">[ASP.NET Web API 2 のメディア フォーマッタ](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)</span><span class="sxs-lookup"><span data-stu-id="6e17a-281">[Media Formatters in ASP.NET Web API 2](/aspnet/web-api/overview/formats-and-model-binding/media-formatters)</span></span>\
- [<span data-ttu-id="6e17a-282">ASP.NET Core Web API のカスタム フォーマッタ</span><span class="sxs-lookup"><span data-stu-id="6e17a-282">Custom formatters in ASP.NET Core Web API</span></span>](/aspnet/core/web-api/advanced/custom-formatters)
- [<span data-ttu-id="6e17a-283">ASP.NET Core フィルター</span><span class="sxs-lookup"><span data-stu-id="6e17a-283">Filters in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/filters)
- [<span data-ttu-id="6e17a-284">ASP.NET Web API 2 のルート制約</span><span class="sxs-lookup"><span data-stu-id="6e17a-284">Route constraints in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2#route-constraints)
- [<span data-ttu-id="6e17a-285">ASP.NET MVC 5 のルート制約</span><span class="sxs-lookup"><span data-stu-id="6e17a-285">Route constraints in ASP.NET MVC 5</span></span>](https://devblogs.microsoft.com/aspnet/attribute-routing-in-asp-net-mvc-5/#route-constraints)
- [<span data-ttu-id="6e17a-286">ASP.NET Core ルート制約のリファレンス</span><span class="sxs-lookup"><span data-stu-id="6e17a-286">ASP.NET Core Route Constraint Reference</span></span>](/aspnet/core/fundamentals/routing#route-constraint-reference)
- [<span data-ttu-id="6e17a-287">ASP.NET Web API 2 のカスタム メッセージ ハンドラー</span><span class="sxs-lookup"><span data-stu-id="6e17a-287">Custom message handlers in ASP.NET Web API 2</span></span>](/aspnet/web-api/overview/advanced/http-message-handlers#custom-message-handlers)
- [<span data-ttu-id="6e17a-288">MVC 5 と Web API 2 のシンプルな CORS コントロール</span><span class="sxs-lookup"><span data-stu-id="6e17a-288">Simple CORS control in MVC 5 and Web API 2</span></span>](https://stackoverflow.com/questions/6290053/setting-access-control-allow-origin-in-asp-net-mvc-simplest-possible-method)
- [<span data-ttu-id="6e17a-289">Web API でクロスオリジン要求を有効にする</span><span class="sxs-lookup"><span data-stu-id="6e17a-289">Enabling Cross-Origin Requests in Web API</span></span>](/aspnet/web-api/overview/security/enabling-cross-origin-requests-in-web-api#enable-cors)
- [<span data-ttu-id="6e17a-290">ASP.NET Core でクロスオリジン要求 (CORS) を有効にする</span><span class="sxs-lookup"><span data-stu-id="6e17a-290">Enable Cross-Origin Requests (CORS) in ASP.NET Core</span></span>](/aspnet/core/security/cors)
- [<span data-ttu-id="6e17a-291">ASP.NET Core の区分</span><span class="sxs-lookup"><span data-stu-id="6e17a-291">Areas in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/areas)
- [<span data-ttu-id="6e17a-292">ASP.NET Core での統合テスト</span><span class="sxs-lookup"><span data-stu-id="6e17a-292">Integration tests in ASP.NET Core</span></span>](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
><span data-ttu-id="6e17a-293">[前へ](example-migration-eshop.md)
>[次へ](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="6e17a-293">[Previous](example-migration-eshop.md)
[Next](deployment-scenarios.md)</span></span>
