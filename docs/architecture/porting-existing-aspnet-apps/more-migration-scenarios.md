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
# <a name="more-migration-scenarios"></a>その他の移行シナリオ

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

このセクションでは、いくつかの異なる ASP.NET アプリシナリオについて説明し、それぞれの解決方法について説明します。 このセクションを使用すると、アプリに適用されるシナリオを特定し、アプリとそのホスティング環境でどの手法が機能するかを評価できます。

## <a name="migrate-aspnet-mvc-5-and-webapi-2-to-aspnet-core-mvc"></a>ASP.NET MVC 5 と WebApi 2 を ASP.NET Core MVC に移行する

ASP.NET MVC 5 アプリと Web API 2 アプリの一般的なシナリオは、両方の製品を同じアプリケーションにインストールすることでした。 これは、多くのチームが使用する、サポートされている比較的一般的なアプローチですが、2つの製品では異なる抽象化が使用されるため、余分な作業が必要になります。 たとえば、ASP.NET MVC のルートの設定は、やなどののメソッドを使用して行い `RouteCollection` `MapMvcAttributeRoutes()` `MapRoute()` ます。 ただし ASP.NET Web API 2 のルーティングは、およびのような方法で管理され `HttpConfiguration` `MapHttpAttributeRoutes()` `MapHttpRoute()` ます。

このアプリには、 `eShopLegacyMVC` ASP.NET MVC と WEB API の両方が含まれており、 `App_Start` 両方のルートを設定するためのフォルダーにメソッドが含まれています。 また、Autofac を使用した依存関係の注入もサポートしています。これには、2つの類似した構成作業が必要です。

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

ASP.NET Core を使用するようにこれらのアプリをアップグレードすると、重複する作業と、それに付随する可能性がある混乱が排除されます。 ASP.NET Core MVC は、ルーティングやフィルターなどのルールの1つのセットを備えた統合フレームワークです。 依存関係の注入は、.NET Core 自体に組み込まれています。 これらはすべて `Startup.cs` 、「」のサンプルのアプリに示すように、で構成できます `eShopPorted` 。

## <a name="migrate-httpresponsemessage-to-aspnet-core"></a>HttpResponseMessage を ASP.NET Core に移行する

一部の ASP.NET Web API アプリには、を返すアクションメソッドが含まれている場合があり `HttpResponseMessage` ます。 この型は ASP.NET Core に存在しません。 次に、 `Delete` 基本のヘルパーメソッドを使用した、アクションメソッドでの使用例を示し `ResponseMessage` `ApiController` ます。

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

ASP.NET Core MVC では、すべての一般的な HTTP 応答ステータスコードに使用できるヘルパーメソッドがあるため、上記のメソッドは次のコードに移植されます。

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

ヘルパーが存在しないカスタムステータスコードを返す必要がある場合は、常にを使用して任意の数値コードを返すことができ `return StatusCode(int statusCode)` ます。

## <a name="migrate-content-negotiation-from-aspnet-web-api-to-aspnet-core"></a>ASP.NET Web API から ASP.NET Core へのコンテンツネゴシエーションの移行

ASP.NET Web API 2 では、 [コンテンツネゴシエーション](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation) がネイティブでサポートされます。 このサンプルアプリには、 `BrandsController` 結果を XML または JSON で一覧表示することによって、このサポートを示すが含まれています。 これは要求のヘッダーに基づいて `Accept` おり、またはが含まれている場合は変更され `application/xml` `application/json` ます。

ASP.NET MVC 5 アプリでは、コンテンツネゴシエーションのサポートは組み込まれていません。

コンテンツネゴシエーションは、より柔軟性が高く、API をより多くのクライアントで使用できるようにするため、特定のエンコードの種類を返す方が望ましいと言えます。 現在、特定の形式を返すアクションメソッドがある場合は、コードを ASP.NET Core に移植するときに、コンテンツネゴシエーションをサポートする結果の型を返すように変更することを検討してください。

次のコードは、クライアントのヘッダーコンテンツに関係なく、JSON 形式でデータを返し `Accept` ます。

```csharp
[HttpGet]
public ActionResult Index()
{
    return Json(new { Message = "Hello World!" });
}
```

適切な[戻り値の型](/aspnet/core/web-api/action-return-types)が使用されている場合、MVC では、[コンテンツネゴシエーションがネイティブでサポート](/aspnet/core/web-api/advanced/formatting)されます。 ASP.NET Core コンテンツネゴシエーションは、コントローラーヘルパーメソッドによって返されるステータスコード固有のアクション結果によって返される [ObjectResult] によって実装されます。 前のアクションメソッドは ASP.NET Core MVC で実装され、コンテンツネゴシエーションを使用します。

```csharp
public IActionResult Index()
{
    return Ok(new { Message = "Hello World!"} );
}
```

これにより、既定ではデータが JSON 形式で返されます。 [アプリが適切なフォーマッタで構成されている場合](/aspnet/core/web-api/advanced/formatting)は、XML およびその他の形式が使用されます。

## <a name="references"></a>関連項目

- [ASP.NET Web API コンテンツネゴシエーション](/aspnet/web-api/overview/formats-and-model-binding/content-negotiation)
- [ASP.NET Core Web API の応答データの書式設定](/aspnet/core/web-api/advanced/formatting)

>[!div class="step-by-step"]
>[前へ](example-migration-eshop.md)
>[次へ](deployment-scenarios.md)
