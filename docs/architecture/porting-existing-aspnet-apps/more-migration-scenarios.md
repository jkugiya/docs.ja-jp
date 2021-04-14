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

## <a name="references"></a>リファレンス

- [ASP.NET Web API のコンテンツ ネゴシエーション](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [ASP.NET Core Web API の応答データの書式設定](/aspnet/core/web-api/advanced/formatting)

>[!div class="step-by-step"]
>[前へ](example-migration-eshop.md)
>[次へ](deployment-scenarios.md)
