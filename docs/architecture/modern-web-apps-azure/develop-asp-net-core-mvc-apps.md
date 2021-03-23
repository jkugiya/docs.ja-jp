---
title: ASP.NET Core MVC アプリの開発
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | ASP.NET Core MVC アプリの開発
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
no-loc:
- Blazor
- WebAssembly
ms.openlocfilehash: 494e73bd32ac6793d355b6828408b61bb09ca880
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873121"
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="c175f-103">ASP.NET Core MVC アプリを開発する</span><span class="sxs-lookup"><span data-stu-id="c175f-103">Develop ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="c175f-104">"最初から正しく理解する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="c175f-105">しかし、最後に正しく理解していることは極めて重要です。"</span><span class="sxs-lookup"><span data-stu-id="c175f-105">It's vitally important to get it right the last time."</span></span>
> <span data-ttu-id="c175f-106">_- Andrew Hunt、David Thomas_</span><span class="sxs-lookup"><span data-stu-id="c175f-106">_- Andrew Hunt and David Thomas_</span></span>

<span data-ttu-id="c175f-107">ASP.NET Core は、最新のクラウド向けに最適化された Web アプリケーションを構築するための、クロス プラットフォームのオープン ソース フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="c175f-107">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="c175f-108">ASP.NET Core アプリは、軽量なモジュール形式であり、依存関係の挿入の組み込みサポートを備え、テストと保守の容易性を大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-108">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling greater testability and maintainability.</span></span> <span data-ttu-id="c175f-109">ビュー ベースのアプリだけでなく最新の Web API の構築をサポートする MVC と組み合わせて、ASP.NET Core は、エンタープライズ Web アプリケーション構築のための強力なフレームワークになります。</span><span class="sxs-lookup"><span data-stu-id="c175f-109">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mvc-and-razor-pages"></a><span data-ttu-id="c175f-110">MVC と Razor Pages</span><span class="sxs-lookup"><span data-stu-id="c175f-110">MVC and Razor Pages</span></span>

<span data-ttu-id="c175f-111">ASP.NET Core MVC は、Web ベースの API やアプリを構築する際に便利な機能をたくさん備えています。</span><span class="sxs-lookup"><span data-stu-id="c175f-111">ASP.NET Core MVC offers many features that are useful for building web-based APIs and apps.</span></span> <span data-ttu-id="c175f-112">MVC という用語は "Model-View-Controller" の略です。これは、ユーザーからの要求に応答する責任をいくつかの部分に分割する UI パターンです。</span><span class="sxs-lookup"><span data-stu-id="c175f-112">The term MVC stands for "Model-View-Controller", a UI pattern that breaks up the responsibilities of responding to user requests into several parts.</span></span> <span data-ttu-id="c175f-113">このパターンに従うだけでなく、ASP.NET Core アプリに各種機能を Razor Pages として実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-113">In addition to following this pattern, you can also implement features in your ASP.NET Core apps as Razor Pages.</span></span> <span data-ttu-id="c175f-114">Razor Pages は ASP.NET Core MVC に組み込まれ、ルーティング、モデル バインド、フィルター、承認などに同じ機能が使用されます。ただし、コントローラー、モデル、ビューなどに個別のフォルダーやファイルを使用したり、属性に基づくルーティングを行ったりする代わりに、Razor Pages は 1 つのフォルダー ("/Pages") に配置され、このフォルダー内の相対的な位置に基づいてルーティングを行い、コントローラー アクションではなくハンドラーで要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="c175f-114">Razor Pages are built into ASP.NET Core MVC, and use the same features for routing, model binding, filters, authorization, etc. However, instead of having separate folders and files for Controllers, Models, Views, etc. and using attribute-based routing, Razor Pages are placed in a single folder ("/Pages"), route based on their relative location in this folder, and handle requests with handlers instead of controller actions.</span></span> <span data-ttu-id="c175f-115">そのため、Razor Pages を使用すると、通常、必要なファイルやクラスはすべて併置され、Web プロジェクト全体に分散しません。</span><span class="sxs-lookup"><span data-stu-id="c175f-115">As a result, when working with Razor Pages, all of the files and classes you need are typically colocated, not spread throughout the web project.</span></span>

<span data-ttu-id="c175f-116">新しい ASP.NET Core App を作成するとき、構築するアプリの書類に関して計画を立ててください。</span><span class="sxs-lookup"><span data-stu-id="c175f-116">When you create a new ASP.NET Core App, you should have a plan in mind for the kind of app you want to build.</span></span> <span data-ttu-id="c175f-117">Visual Studio では、いくつかのテンプレートの中から選択します。</span><span class="sxs-lookup"><span data-stu-id="c175f-117">In Visual Studio, you'll choose from several templates.</span></span> <span data-ttu-id="c175f-118">プロジェクト テンプレートとして最も一般的な 3 つは、Web API、Web アプリケーション、Web アプリケーション (Model-View-Controller) です。</span><span class="sxs-lookup"><span data-stu-id="c175f-118">The three most common project templates are Web API, Web Application, and Web Application (Model-View-Controller).</span></span> <span data-ttu-id="c175f-119">これを決定できるのは最初にプロジェクトを作成するときのみですが、取り消し不可能な決定ではありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-119">Although you can only make this decision when you first create a project, it's not an irrevocable decision.</span></span> <span data-ttu-id="c175f-120">Web API プロジェクトでは、標準の Model-View-Controller コントローラーが使用されます。既定ではビューだけがありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-120">The Web API project uses standard Model-View-Controller controllers – it just lacks Views by default.</span></span> <span data-ttu-id="c175f-121">同様に、既定の Web アプリケーション テンプレートでは Razor Pages が使用され、Views フォルダーがありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-121">Likewise, the default Web Application template uses Razor Pages, and so also lacks a Views folder.</span></span> <span data-ttu-id="c175f-122">このようなプロジェクトには Views フォルダーを後で追加し、ビューを基盤とする動作に対応できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-122">You can add a Views folder to these projects later to support view-based behavior.</span></span> <span data-ttu-id="c175f-123">Web API プロジェクトと Model-View-Controller プロジェクトには既定で Pages フォルダーがありませんが、後で追加し、Razor Pages を基盤とする動作に対応できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-123">Web API and Model-View-Controller projects don't include a Pages folder by default, but you can add one later to support Razor Pages-based behavior.</span></span> <span data-ttu-id="c175f-124">以上の 3 つのテンプレートは、データ (Web API)、ページ ベース、ビュー ベースという 3 つの異なるデフォルト ユーザー インタラクションをサポートするものであると考えることができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-124">You can think of these three templates as supporting three different kinds of default user interaction: data (web API), page-based, and view-based.</span></span> <span data-ttu-id="c175f-125">しかし、必要であれば、これらのテンプレートのいずれかまたは全部を 1 つのプロジェクトに混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-125">However, you can mix and match any or all of these templates within a single project if you wish.</span></span>

### <a name="why-razor-pages"></a><span data-ttu-id="c175f-126">Razor Pages とは</span><span class="sxs-lookup"><span data-stu-id="c175f-126">Why Razor Pages?</span></span>

<span data-ttu-id="c175f-127">Razor Pages は、Visual Studio における新しい Web アプリケーションの既定の手法です。</span><span class="sxs-lookup"><span data-stu-id="c175f-127">Razor Pages is the default approach for new web applications in Visual Studio.</span></span> <span data-ttu-id="c175f-128">Razor Pages では、非 SPA フォームなど、ページ ベースのアプリケーション機能を一層簡単に構築できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-128">Razor Pages offers a simpler way of building page-based application features, such as non-SPA forms.</span></span> <span data-ttu-id="c175f-129">コントローラーやビューを使用し、さまざまな依存関係やビュー モデルと連動し、さまざまなビューを返す大掛かりなコントローラーをアプリケーションに与えることが一般的でした。</span><span class="sxs-lookup"><span data-stu-id="c175f-129">Using controllers and views, it was common for applications to have very large controllers that worked with many different dependencies and view models and returned many different views.</span></span> <span data-ttu-id="c175f-130">これにより、複雑さが増加しました。また、単一責任の原則または開放/閉鎖原則に効果的に従わないコントローラーが生じることがよくありました。</span><span class="sxs-lookup"><span data-stu-id="c175f-130">This resulted in more complexity and often resulted in controllers that didn't follow the Single Responsibility Principle or Open/Closed Principles effectively.</span></span> <span data-ttu-id="c175f-131">Razor Pages では、その Razor マークアップを使用し、Web アプリケーションで特定の論理 "ページ" に対してサーバー側ロジックをカプセル化することでこの問題に対処しています。</span><span class="sxs-lookup"><span data-stu-id="c175f-131">Razor Pages addresses this issue by encapsulating the server-side logic for a given logical "page" in a web application with its Razor markup.</span></span> <span data-ttu-id="c175f-132">サーバー側ロジックのない Razor ページは 1 つの Razor ファイル ("Index.cshtml" など) のみから構成されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-132">A Razor Page that has no server-side logic can only consist of a Razor file (for instance, "Index.cshtml").</span></span> <span data-ttu-id="c175f-133">ただし、重要な Razor Pages にはほとんどの場合、ページ モデル クラスが関連付けられます。これには慣例として Razor ファイルと同じ名前と ".cs" 拡張子が付けられます。たとえば、"Index.cshtml.cs" のようになります。</span><span class="sxs-lookup"><span data-stu-id="c175f-133">However, most non-trivial Razor Pages will have an associated page model class, which by convention is named the same as the Razor file with a ".cs" extension (for example, "Index.cshtml.cs").</span></span>

<span data-ttu-id="c175f-134">Razor ページのページ モデルでは、MVC コントローラーとビューモデルの責任が組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="c175f-134">A Razor Page's page model combines the responsibilities of an MVC controller and a viewmodel.</span></span> <span data-ttu-id="c175f-135">コントローラー アクションのメソッドで要求を処理する代わりに、"OnGet()" のようなページ モデル ハンドラーが実行され、関連付けられているページが既定でレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="c175f-135">Instead of handling requests with controller action methods, page model handlers like "OnGet()" are executed, rendering their associated page by default.</span></span> <span data-ttu-id="c175f-136">Razor Pages では、ASP.NET Core アプリで個々のページを構築するプロセスが簡単になります。それでありながら、ASP.NET Core MVC のアーキテクチャ機能をすべて備えています。</span><span class="sxs-lookup"><span data-stu-id="c175f-136">Razor Pages simplifies the process of building individual pages in an ASP.NET Core app, while still providing all the architectural features of ASP.NET Core MVC.</span></span> <span data-ttu-id="c175f-137">新しいページ ベース機能の既定の選択肢として最適です。</span><span class="sxs-lookup"><span data-stu-id="c175f-137">They're a good default choice for new page-based functionality.</span></span>

### <a name="when-to-use-mvc"></a><span data-ttu-id="c175f-138">MVC を使用する場面</span><span class="sxs-lookup"><span data-stu-id="c175f-138">When to use MVC</span></span>

<span data-ttu-id="c175f-139">Web API を構築する場合、Razor Pages を使用してみるより、MVC パターンの方が合理的です。</span><span class="sxs-lookup"><span data-stu-id="c175f-139">If you're building web APIs, the MVC pattern makes more sense than trying to use Razor Pages.</span></span> <span data-ttu-id="c175f-140">ご自分のプロジェクトで Web API エンドポイントだけを公開する場合は、Web API のプロジェクト テンプレートから始めるのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="c175f-140">If your project will only expose web API endpoints, you should ideally start from the Web API project template.</span></span> <span data-ttu-id="c175f-141">それ以外の場合は、任意の ASP.NET Core アプリに、コントローラーと関連付けらた API エンドポイントを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-141">Otherwise, it's easy to add controllers and associated API endpoints to any ASP.NET Core app.</span></span> <span data-ttu-id="c175f-142">バージョン 5 以前の ASP.NET MVC から ASP.NET Core MVC に既存のアプリケーションを移行する場合、その作業量を最小限に抑えるには、ビュー ベースの MVC 手法を使用します。</span><span class="sxs-lookup"><span data-stu-id="c175f-142">Use the view-based MVC approach if you're migrating an existing application from ASP.NET MVC 5 or earlier to ASP.NET Core MVC and you want to do so with the least amount of effort.</span></span> <span data-ttu-id="c175f-143">最初の移行後、新しい機能のために、さらには大規模な移行として Razor Pages を採用することが合理的かどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-143">Once you've made the initial migration, you can evaluate whether it makes sense to adopt Razor Pages for new features or even as a wholesale migration.</span></span>

<span data-ttu-id="c175f-144">Web アプリの構築方法として Razor Pages を選択した場合でも MVC ビューを選択した場合でも、アプリのパフォーマンスは同じようなものになり、依存関係の注入、フィルター、モデル バインド、妥当性確認などのサポートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-144">Whether you choose to build your web app using Razor Pages or MVC views, your app will have similar performance and will include support for dependency injection, filters, model binding, validation, and so on.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="c175f-145">応答と要求のマッピング</span><span class="sxs-lookup"><span data-stu-id="c175f-145">Mapping requests to responses</span></span>

<span data-ttu-id="c175f-146">ASP.NET Core アプリの中心となる機能は、受信した要求を送信する応答にマップすることです。</span><span class="sxs-lookup"><span data-stu-id="c175f-146">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="c175f-147">下位のレベルではこのマッピングはミドルウェアによって行われ、カスタム ミドルウェアのみで簡単な ASP.NET Core アプリとマイクロサービスを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-147">At a low level, this mapping is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="c175f-148">ASP.NET Core MVC を使うと、"_ルート_"、"_コントローラー_"、"_アクション_" など、さらに上位のレベルで操作することができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-148">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of _routes_, _controllers_, and _actions_.</span></span> <span data-ttu-id="c175f-149">着信した各要求はアプリケーションのルーティング テーブルと比較され、一致するルートが見つかった場合、関連付けられている (コントローラーに属する) アクション メソッドが呼び出されて要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="c175f-149">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="c175f-150">一致するルートが見つからない場合は、エラー ハンドラーが呼び出されます (この場合、NotFound の結果を返します)。</span><span class="sxs-lookup"><span data-stu-id="c175f-150">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="c175f-151">ASP.NET Core MVC アプリは、規則ルートと属性ルートのどちらか一方または両方を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-151">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="c175f-152">規則ルートはコードで定義されており、次の例のような構文を使ってルーティングの "_規則_" を指定します。</span><span class="sxs-lookup"><span data-stu-id="c175f-152">Conventional routes are defined in code, specifying routing _conventions_ using syntax like in the example below:</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="c175f-153">この例では、"default" という名前のルートがルーティング テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-153">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="c175f-154">`controller`、`action`、`id` のプレースホルダーでルート テンプレートを定義します。</span><span class="sxs-lookup"><span data-stu-id="c175f-154">It defines a route template with placeholders for `controller`, `action`, and `id`.</span></span> <span data-ttu-id="c175f-155">`controller` と `action` のプレースホルダーには既定値が指定されており (それぞれ、`Home` と `Index`)、`id` プレースホルダーは ("?" が適用されているので) 省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c175f-155">The `controller` and `action` placeholders have the default specified (`Home` and `Index`, respectively), and the `id` placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="c175f-156">ここで定義されている規則は、要求の最初の部分はコントローラーの名前に対応する必要があり、2 番目の部分はアクションに対応する必要があり、3 番目の部分は必要に応じて ID パラメーターを表す、というものです。</span><span class="sxs-lookup"><span data-stu-id="c175f-156">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an ID parameter.</span></span> <span data-ttu-id="c175f-157">規則ルートは通常、`Startup` クラスの `Configure` メソッドなど、アプリケーションに対して 1 か所で定義されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-157">Conventional routes are typically defined in one place for the application, such as in the `Configure` method in the `Startup` class.</span></span>

<span data-ttu-id="c175f-158">属性ルートは、グローバルに指定されるのではなく、コントローラーとアクションに直接適用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-158">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="c175f-159">この方法の場合、特定のメソッドを探しているときに検出しやすいという利点がありますが、ルーティング情報がアプリケーション内の 1 か所に保持されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="c175f-159">This approach has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="c175f-160">属性ルートでは、特定のアクションに対する複数ルートや、コントローラーとアクションの組み合わせルートを、簡単に指定できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-160">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="c175f-161">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c175f-161">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

<span data-ttu-id="c175f-162">ルートは [HttpGet] や同様の属性で指定することができ、[Route] 属性を別途追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-162">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route] attributes.</span></span> <span data-ttu-id="c175f-163">次に示すように、属性ルートではトークンを使って、コントローラーやアクションの名前を繰り返し指定する必要性を軽減することもできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-163">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

<span data-ttu-id="c175f-164">Razor Pages では、属性ルーティングは使用されません。</span><span class="sxs-lookup"><span data-stu-id="c175f-164">Razor Pages doesn't use attribute routing.</span></span> <span data-ttu-id="c175f-165">Razor Pages には、その `@page` ディレクティブの一部として追加の経路テンプレート情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-165">You can specify additional route template information for a Razor Page as part of its `@page` directive:</span></span>

```csharp
@page "{id:int}"
```

<span data-ttu-id="c175f-166">前の例の問題のページではルートと整数 `id` パラメーターが一致します。</span><span class="sxs-lookup"><span data-stu-id="c175f-166">In the previous example, the page in question would match a route with an integer `id` parameter.</span></span> <span data-ttu-id="c175f-167">たとえば、`/Pages` のルートに置かれている *Products.cshtml* ページにはこの経路が与えられます。</span><span class="sxs-lookup"><span data-stu-id="c175f-167">For example, the *Products.cshtml* page located in the root of `/Pages` would have this route:</span></span>

```csharp
"/Products/123"
```

<span data-ttu-id="c175f-168">特定の要求がルートと一致した後、アクション メソッドが呼び出される前に、ASP.NET Core MVC は要求に対して[モデル バインド](/aspnet/core/mvc/models/model-binding)と[モデル検証](/aspnet/core/mvc/models/validation)を実行します。</span><span class="sxs-lookup"><span data-stu-id="c175f-168">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](/aspnet/core/mvc/models/model-binding) and [model validation](/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="c175f-169">モデル バインドでは、着信した HTTP データが、呼び出されるアクション メソッドのパラメーターとして指定されている .NET 型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-169">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="c175f-170">たとえば、アクション メソッドが `int id` パラメーターを必要としている場合、モデル バインドは要求の一部として指定された値からこのパラメーターを提供しようとします。</span><span class="sxs-lookup"><span data-stu-id="c175f-170">For example, if the action method expects an `int id` parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="c175f-171">そのために、モデル バインドは、ポストされたフォーム内、ルート自体、クエリ文字列で値を検索します。</span><span class="sxs-lookup"><span data-stu-id="c175f-171">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="c175f-172">`id` 値が見つかった場合は、整数に変換されてからアクション メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-172">Assuming an `id` value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="c175f-173">モデルをバインドした後、アクション メソッドを呼び出す前に、モデルの検証が行われます。</span><span class="sxs-lookup"><span data-stu-id="c175f-173">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="c175f-174">モデルの検証では、モデルの種類に対するオプション属性が使われ、指定されたモデル オブジェクトが特定のデータ要件に準拠していることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-174">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="c175f-175">特定の値を必須として指定したり、特定の長さや数値範囲に制限したりすることができます。検証属性が指定されていて、モデルがその要件に準拠していない場合は、ModelState.IsValid プロパティが false に設定され、準拠していない検証規則のセットを要求元のクライアントに送信できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-175">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="c175f-176">モデルの検証を使う場合は常に、状態変更コマンドを実行する前にモデルが有効であることを確認し、無効なデータによってアプリが破損しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-176">If you're using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="c175f-177">[フィルター](/aspnet/core/mvc/controllers/filters)を使用すると、すべてのアクションにこの検証のコードを追加する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="c175f-177">You can use a [filter](/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this validation in every action.</span></span> <span data-ttu-id="c175f-178">ASP.NET Core MVC フィルターを使うと、要求のグループをインターセプトして、共通のポリシーや横断的な事柄を特定の対象にだけ適用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-178">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="c175f-179">フィルターは、個々のアクション、コントローラー全体、またはアプリケーション全体に適用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-179">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="c175f-180">Web API に対しては、ASP.NET Core MVC は [_コンテンツ ネゴシエーション_](/aspnet/core/mvc/models/formatting)をサポートしており、応答の書式設定方法を要求で指定することができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-180">For web APIs, ASP.NET Core MVC supports [_content negotiation_](/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="c175f-181">要求で指定されたヘッダーに基づき、データを返すアクションは、XML、JSON、または他のサポートされている形式で応答を書式設定します。</span><span class="sxs-lookup"><span data-stu-id="c175f-181">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="c175f-182">この機能を使うと、同じ API を、データ形式要件が異なる複数のクライアントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-182">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

<span data-ttu-id="c175f-183">Web API プロジェクトでは `[ApiController]` 属性の使用を検討してください。この属性は個々のコントローラー、ベース コントローラー クラス、アセンブリ全体に適用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-183">Web API projects should consider using the `[ApiController]` attribute, which can be applied to individual controllers, to a base controller class, or to the entire assembly.</span></span> <span data-ttu-id="c175f-184">この属性によって、自動モデル検証が追加されます。アクションのモデルが無効な場合、BadRequest と検証エラーの詳細が返されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-184">This attribute adds automatic model validation checking and any action with an invalid model will return a BadRequest with the details of the validation errors.</span></span> <span data-ttu-id="c175f-185">この属性ではまた、あらゆるアクションに、従来の経路を使用せず、属性経路を与えることが要求され、エラーに対する応答で、さらに詳しい ProblemDetails 情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-185">The attribute also requires all actions have an attribute route, rather than using a conventional route, and returns more detailed ProblemDetails information in response to errors.</span></span>

### <a name="keeping-controllers-under-control"></a><span data-ttu-id="c175f-186">コントローラーの制御</span><span class="sxs-lookup"><span data-stu-id="c175f-186">Keeping controllers under control</span></span>

<span data-ttu-id="c175f-187">ページベースのアプリケーションの場合、Razor Pages は、コントローラーが大きくなりすぎないようにするために大いに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c175f-187">For page-based applications, Razor Pages do a great job of keeping controllers from getting too large.</span></span> <span data-ttu-id="c175f-188">個々のページには、専用のファイルとハンドラー専用のクラスが用意されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-188">Each individual page is given its own files and classes dedicated just to its handler(s).</span></span> <span data-ttu-id="c175f-189">Razor Pages が導入される前は、多くのビュー中心のアプリケーションには、多数の異なるアクションやビューを担当する大きなコントローラー クラスがありました。</span><span class="sxs-lookup"><span data-stu-id="c175f-189">Prior to the introduction of Razor Pages, many view-centric applications would have large controller classes responsible for many different actions and views.</span></span> <span data-ttu-id="c175f-190">当然、これらのクラスは、多くの責任と依存関係を含めるために拡張され、保守が困難になっていきます。</span><span class="sxs-lookup"><span data-stu-id="c175f-190">These classes would naturally grow to have many responsibilities and dependencies, making them harder to maintain.</span></span> <span data-ttu-id="c175f-191">ビューベースのコントローラーが大きくなりすぎていることがわかった場合は、リファクタリングして Razor Pages を使用するか、メディエーターなどのパターンを導入することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="c175f-191">If you find your view-based controllers are growing too large, consider refactoring them to use Razor Pages, or introducing a pattern like a mediator.</span></span>

<span data-ttu-id="c175f-192">メディエーター設計パターンを使用して、クラス間の通信を可能にしながら、クラス間の結合を削減します。</span><span class="sxs-lookup"><span data-stu-id="c175f-192">The mediator design pattern is used to reduce coupling between classes while allowing communication between them.</span></span> <span data-ttu-id="c175f-193">ASP.NET Core MVC アプリケーションで、"*ハンドラー*" を使用してアクション メソッドの作業を行うことにより、コントローラーをより小さな部分に分割するために、このパターンが頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-193">In ASP.NET Core MVC applications, this pattern is frequently employed to break up controllers into smaller pieces by using *handlers* to do the work of action methods.</span></span> <span data-ttu-id="c175f-194">これを実現するには、多くの場合、一般的な [MediatR NuGet パッケージ](https://www.nuget.org/packages/MediatR/)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-194">The popular [MediatR NuGet package](https://www.nuget.org/packages/MediatR/) is often used to accomplish this.</span></span> <span data-ttu-id="c175f-195">通常、コントローラーには、それぞれが特定の依存関係を必要とする多数の異なるアクション メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-195">Typically, controllers include many different action methods, each of which may require certain dependencies.</span></span> <span data-ttu-id="c175f-196">アクションで必要となるすべての依存関係のセットをコントローラーのコンストラクターに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-196">The set of all dependencies required by any action must be passed into the controller's constructor.</span></span> <span data-ttu-id="c175f-197">MediatR を使用する場合、コントローラーが持つ唯一の依存関係は、メディエーターのインスタンス上にあります。</span><span class="sxs-lookup"><span data-stu-id="c175f-197">When using MediatR, the only dependency a controller has is on an instance of the mediator.</span></span> <span data-ttu-id="c175f-198">各アクションによって、メディエーター インスタンスを使用してメッセージが送信され、メッセージはハンドラーによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-198">Each action then uses the mediator instance to send a message, which is processed by a handler.</span></span> <span data-ttu-id="c175f-199">ハンドラーは 1 つのアクション固有のものであるため、そのアクションに必要な依存関係のみを必要とします。</span><span class="sxs-lookup"><span data-stu-id="c175f-199">The handler is specific to a single action and thus only needs the dependencies required by that action.</span></span> <span data-ttu-id="c175f-200">MediatR を使用するコントローラーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c175f-200">An example of a controller using MediatR is shown here:</span></span>

```csharp
public class OrderController : Controller
{
    private readonly IMediator _mediator;

    public OrderController(IMediator mediator)
    {
        _mediator = mediator;
    }

    [HttpGet]
    public async Task<IActionResult> MyOrders()
    {
        var viewModel = await _mediator.Send(new GetMyOrders(User.Identity.Name));

        return View(viewModel);
    }

    // other actions implemented similarly
}
```

<span data-ttu-id="c175f-201">`MyOrders` アクションでは、`GetMyOrders`メッセージの `Send` の呼び出しが、このクラスによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-201">In the `MyOrders` action, the call to `Send` a `GetMyOrders` message is handled by this class:</span></span>

```csharp
public class GetMyOrdersHandler : IRequestHandler<GetMyOrders, IEnumerable<OrderViewModel>>
{
    private readonly IOrderRepository _orderRepository;

    public GetMyOrdersHandler(IOrderRepository orderRepository)
    {
        _orderRepository = orderRepository;
    }

    public async Task<IEnumerable<OrderViewModel>> Handle(GetMyOrders request, CancellationToken cancellationToken)
    {
        var specification = new CustomerOrdersWithItemsSpecification(request.UserName);
        var orders = await _orderRepository.ListAsync(specification);

        return orders.Select(o => new OrderViewModel
        {
            OrderDate = o.OrderDate,
            OrderItems = o.OrderItems?.Select(oi => new OrderItemViewModel()
            {
                PictureUrl = oi.ItemOrdered.PictureUri,
                ProductId = oi.ItemOrdered.CatalogItemId,
                ProductName = oi.ItemOrdered.ProductName,
                UnitPrice = oi.UnitPrice,
                Units = oi.Units
            }).ToList(),
            OrderNumber = o.Id,
            ShippingAddress = o.ShipToAddress,
            Total = o.Total()
        });
    }
}
```

<span data-ttu-id="c175f-202">このアプローチの最終的な結果として、コントローラーがはるかに小さくなり、主にルーティングとモデル バインドに集中し、個々のハンドラーが特定のエンドポイントに必要な特定のタスクを担当するようになります。</span><span class="sxs-lookup"><span data-stu-id="c175f-202">The end result of this approach is for controllers to be much smaller and focused primarily on routing and model binding, while individual handlers are responsible for the specific tasks needed by a given endpoint.</span></span> <span data-ttu-id="c175f-203">このアプローチは、[ApiEndpoints NuGet パッケージ](https://www.nuget.org/packages/Ardalis.ApiEndpoints/)を使用すると、これにより Razor Pages でビューベースのコントローラーにもたらされるのと同じ利点を API コントローラーに提供することが試みられるため、MediatR を使用しなくても実現できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-203">This approach can also be achieved without MediatR by using the [ApiEndpoints NuGet package](https://www.nuget.org/packages/Ardalis.ApiEndpoints/), which attempts to bring to API controllers the same benefits Razor Pages brings to view-based controllers.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="c175f-204">参照 – 応答と要求のマッピング</span><span class="sxs-lookup"><span data-stu-id="c175f-204">References – Mapping Requests to Responses</span></span>
>
> - <span data-ttu-id="c175f-205">**コントローラー アクションへのルーティング**</span><span class="sxs-lookup"><span data-stu-id="c175f-205">**Routing to Controller Actions**</span></span>\
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - <span data-ttu-id="c175f-206">**モデル バインド**</span><span class="sxs-lookup"><span data-stu-id="c175f-206">**Model Binding**</span></span>\
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - <span data-ttu-id="c175f-207">**モデル検証**</span><span class="sxs-lookup"><span data-stu-id="c175f-207">**Model Validation**</span></span>\
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - <span data-ttu-id="c175f-208">**フィルター**</span><span class="sxs-lookup"><span data-stu-id="c175f-208">**Filters**</span></span>\
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - <span data-ttu-id="c175f-209">**ApiController 属性**</span><span class="sxs-lookup"><span data-stu-id="c175f-209">**ApiController Attribute**</span></span>\
 > <https://docs.microsoft.com/aspnet/core/web-api/>

## <a name="working-with-dependencies"></a><span data-ttu-id="c175f-210">依存関係の使用</span><span class="sxs-lookup"><span data-stu-id="c175f-210">Working with dependencies</span></span>

<span data-ttu-id="c175f-211">ASP.NET Core は、[依存関係の挿入](/aspnet/core/fundamentals/dependency-injection)と呼ばれる手法の組み込みサポートを備えており、内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="c175f-211">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="c175f-212">依存関係の挿入は、アプリケーションの異なる部分間を疎結合できる手法です。</span><span class="sxs-lookup"><span data-stu-id="c175f-212">Dependency injection is a technique that enables loose coupling between different parts of an application.</span></span> <span data-ttu-id="c175f-213">結合を緩くすることを、アプリケーションの各部分の分離が容易になり、部分ごとにテストや置換が可能になるため、望ましいことです。</span><span class="sxs-lookup"><span data-stu-id="c175f-213">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="c175f-214">また、アプリケーションの 1 つの部分に対する変更が、アプリケーションの別の場所に予期しない影響を与える可能性も低くなります。</span><span class="sxs-lookup"><span data-stu-id="c175f-214">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="c175f-215">依存関係の挿入は、依存関係逆転 (Dependency Inversion) の原則に基づいており、多くの場合、開放/閉鎖 (Open/closed) の原則の実現に不可欠です。</span><span class="sxs-lookup"><span data-stu-id="c175f-215">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="c175f-216">アプリケーションによる依存関係の処理方法を評価するときは、[静的な結び付き](https://deviq.com/static-cling/)を持つコードのにおいに注意し、"[new は接着剤である](https://ardalis.com/new-is-glue)" という格言を思い出してください。</span><span class="sxs-lookup"><span data-stu-id="c175f-216">When evaluating how your application works with its dependencies, beware of the [static cling](https://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](https://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="c175f-217">静的な結び付きは、クラスが静的メソッドを呼び出したとき、または静的プロパティにアクセスしたときに発生し、インフラストラクチャに対する副作用または依存関係があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-217">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="c175f-218">たとえば、あるメソッドが静的メソッドを呼び出し、その静的メソッドがデータベースに書き込む場合、元のメソッドはデータベースに密に結合されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-218">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="c175f-219">何かによってデータベース呼び出しが中断されると、メソッドも中断されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-219">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="c175f-220">このようなメソッドのテストは、静的な呼び出しを模倣するために市販のモック ライブラリが必要になるか、またはテスト データベースを使ってしかテストできないため、非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="c175f-220">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="c175f-221">インフラストラクチャに対する依存関係のない静的呼び出しは (特に、完全にステートレスな呼び出し)、問題なく呼び出すことができて、結合や (コードの結合だけでなく静的な呼び出し自体の) テスト可能性に影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="c175f-221">Static calls that don't have any dependence on infrastructure, especially those calls that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="c175f-222">多くの開発者は、静的な結び付きとグローバルな状態のリスクを理解していますが、それでも直接的なインスタンス化によって特定の実装にコードを密接に結合します。</span><span class="sxs-lookup"><span data-stu-id="c175f-222">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="c175f-223">"new は接着剤である" という格言は、この結合を喚起するものであり、`new` キーワードの使用を全般に非難しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-223">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the `new` keyword.</span></span> <span data-ttu-id="c175f-224">静的メソッドの呼び出しと同様に、外部依存関係を持たない型の新しいインスタンスは通常、実装の詳細にコードを密接に結合したり、テストを困難にしたりすることはありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-224">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="c175f-225">ただし、クラスをインスタンス化するたびに、その特定のインスタンスをその特定の場所にハード コーディングすることに意味があるかどうか、またはそのインスタンスを依存関係として要求する方が優れた設計ではないかということを、少し検討してください。</span><span class="sxs-lookup"><span data-stu-id="c175f-225">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="c175f-226">依存関係の宣言</span><span class="sxs-lookup"><span data-stu-id="c175f-226">Declare your dependencies</span></span>

<span data-ttu-id="c175f-227">ASP.NET Core のメソッドとクラスは依存関係を宣言するようになっており、引数としてそれを要求します。</span><span class="sxs-lookup"><span data-stu-id="c175f-227">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="c175f-228">通常、ASP.NET アプリケーションは Startup クラスにおいてセットアップされ、Startup クラス自体が複数のポイントで依存関係の挿入をサポートするように構成されています。</span><span class="sxs-lookup"><span data-stu-id="c175f-228">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="c175f-229">Startup クラスにコンストラクターがある場合は、次のように、コンストラクターで依存関係を要求できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-229">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
            .SetBasePath(env.ContentRootPath)
            .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
            .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

<span data-ttu-id="c175f-230">Startup クラスの興味深い点は、明示的な型の要件がないことです。</span><span class="sxs-lookup"><span data-stu-id="c175f-230">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="c175f-231">特別な Startup 基底クラスを継承することなく、特定のインターフェイスも実装していません。</span><span class="sxs-lookup"><span data-stu-id="c175f-231">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="c175f-232">コンストラクターを提供してもしなくてもよく、コンストラクターでは必要なだけいくつでもパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-232">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="c175f-233">アプリケーション用に構成した Web ホストは、開始するとき、使うように指示された Startup クラスを呼び出し、依存関係の挿入を使って Startup クラスに必要なすべての依存関係を設定します。</span><span class="sxs-lookup"><span data-stu-id="c175f-233">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="c175f-234">もちろん、ASP.NET Core によって使われるサービス コンテナーで構成されていないパラメーターを要求すると、例外が発生しますが、コンテナーが認識している依存関係を使っている限り、何でも自由に要求できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-234">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="c175f-235">依存関係の挿入は、最初に Startup インスタンスを作成したときから、ASP.NET Core アプリに組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="c175f-235">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="c175f-236">依存関係の挿入は Startup クラスだけの機能ではありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-236">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="c175f-237">Configure メソッドで依存関係を要求することもできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-237">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="c175f-238">ただし、ConfigureServices メソッドはこの動作の例外であり、IServiceCollection 型のパラメーターを 1 つだけ受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-238">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="c175f-239">このメソッドは、サービス コンテナーにオブジェクトを追加する役割を持ち、IServiceCollection パラメーターを介して現在構成されているすべてのサービスにアクセスできるため、依存関係の挿入をサポートする必要はまったくありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-239">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="c175f-240">したがって、必要なサービスをパラメーターとして要求するか、ConfigureServices で IServiceCollection を使うことにより、Startup クラスのすべての部分で、ASP.NET Core のサービス コレクションで定義されている依存関係を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-240">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="c175f-241">特定のサービスを Startup クラスで確実に利用できるようにする必要がある場合は、CreateDefaultBuilder 呼び出しの中で IWebHostBuilder とその ConfigureServices メソッドを使用して、それらを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-241">If you need to ensure certain services are available to your Startup class, you can configure them using an IWebHostBuilder and its ConfigureServices method inside the CreateDefaultBuilder call.</span></span>

<span data-ttu-id="c175f-242">Startup クラスは、独自のサービスに対するコントローラーからミドルウェアやフィルターまで、ASP.NET Core アプリケーションの他の部分で必要な構成方法のモデルになります。</span><span class="sxs-lookup"><span data-stu-id="c175f-242">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="c175f-243">いずれの場合も、[明示的な依存関係の原則](https://deviq.com/explicit-dependencies-principle/)に従い、依存関係を直接作成するのではなく要求し、アプリケーション全体で依存関係の挿入を利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-243">In each case, you should follow the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="c175f-244">実装を直接インスタンス化する場所と方法に注意する必要があります (特に、インフラストラクチャを使用する、または副作用があるサービスとオブジェクトの場合)。</span><span class="sxs-lookup"><span data-stu-id="c175f-244">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="c175f-245">特定の実装の種類に対する参照をハードコーディングするのではなく、抽象化をアプリケーション コアで定義し、引数として渡すようにします。</span><span class="sxs-lookup"><span data-stu-id="c175f-245">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="c175f-246">アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="c175f-246">Structuring the application</span></span>

<span data-ttu-id="c175f-247">通常、モノリシックなアプリケーションのエントリ ポイントは 1 つです。</span><span class="sxs-lookup"><span data-stu-id="c175f-247">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="c175f-248">ASP.NET Core Web アプリケーションの場合は、ASP.NET Core Web プロジェクトがエントリ ポイントになります。</span><span class="sxs-lookup"><span data-stu-id="c175f-248">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="c175f-249">ただし、これは、ソリューションは 1 つのプロジェクトだけで構成する必要があるという意味ではありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-249">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="c175f-250">懸念事項の分離に従って、アプリケーションを複数の異なるレイヤーに分割するのは役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="c175f-250">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="c175f-251">レイヤーに分割した後は、フォルダーだけでなくプロジェクトも分割して、カプセル化を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-251">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="c175f-252">ASP.NET Core アプリケーションでこれらの目標を実現するための最善の方法は、第 5 章で説明されているクリーン アーキテクチャのバリエーションです。</span><span class="sxs-lookup"><span data-stu-id="c175f-252">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="c175f-253">この方法に従うと、アプリケーションのソリューションは、UI、Infrastructure、ApplicationCore に対する個別のライブラリで構成されるようになります。</span><span class="sxs-lookup"><span data-stu-id="c175f-253">Following this approach, the application's solution will comprise separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="c175f-254">これらのプロジェクトだけでなく、テスト プロジェクトも別に含まれます (テストについては 9 章で説明します)。</span><span class="sxs-lookup"><span data-stu-id="c175f-254">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="c175f-255">アプリケーションのオブジェクト モデルとインターフェイスは、ApplicationCore プロジェクトに置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-255">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="c175f-256">このプロジェクトはできるだけ少ない依存関係を持つようにして、ソリューション内の他のプロジェクトはそれを参照します。</span><span class="sxs-lookup"><span data-stu-id="c175f-256">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="c175f-257">永続化する必要があるビジネス エンティティと、インフラストラクチャに直接依存していないサービスは、ApplicationCore プロジェクトで定義します。</span><span class="sxs-lookup"><span data-stu-id="c175f-257">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="c175f-258">永続化を実行する方法や、ユーザーに通知を送信する方法など、実装の詳細は、Infrastructure プロジェクトで保持します。</span><span class="sxs-lookup"><span data-stu-id="c175f-258">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="c175f-259">このプロジェクトは、Entity Framework Core などの実装固有のパッケージを参照しますが、これらの実装に関する詳細をプロジェクトの外部に公開しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-259">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="c175f-260">インフラストラクチャ サービスとリポジトリは ApplicationCore プロジェクトで定義されているインターフェイスを実装する必要があり、このプロジェクトの永続化の実装が、ApplicationCore で定義されているエンティティの取得と格納を行います。</span><span class="sxs-lookup"><span data-stu-id="c175f-260">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="c175f-261">ASP.NET Core UI プロジェクトは、UI レベルの処理を行いますが、ビジネス ロジックまたはインフラストラクチャの詳細を含まないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-261">The ASP.NET Core UI project is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="c175f-262">実際に、理想的なのは Infrastructure プロジェクトに対する依存関係さえ持つべきではなく、これにより 2 つのプロジェクト間に誤って依存関係が発生するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-262">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="c175f-263">これは、Autofac などのサード パーティ製 DI コンテナーを使って実現でき、各プロジェクトの Module クラスで DI 規則を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-263">This can be achieved using a third-party DI container like Autofac, which allows you to define DI rules in Module classes in each project.</span></span>

<span data-ttu-id="c175f-264">実装の詳細からアプリケーションを分離するもう 1 つの方法は、通常は個別の Docker コンテナーで展開されているマイクロサービスをアプリケーションで呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="c175f-264">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="c175f-265">この方法を使うと、2 つのプロジェクト間に DI を利用する場合より、懸念事項の分離と分割はさらに大きくなりますが、複雑さは増大します。</span><span class="sxs-lookup"><span data-stu-id="c175f-265">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="c175f-266">機能の編成</span><span class="sxs-lookup"><span data-stu-id="c175f-266">Feature organization</span></span>

<span data-ttu-id="c175f-267">既定では、ASP.NET Core アプリケーションは、コントローラーとビューさらに多くの場合は ViewModels を含むように、フォルダー構造を編成します。</span><span class="sxs-lookup"><span data-stu-id="c175f-267">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="c175f-268">通常、これらのサーバー側構造をサポートするためのクライアント側のコードは、wwwroot フォルダーに個別に格納されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-268">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="c175f-269">ただし、大規模なアプリケーションでは、特定の機能を使用するためにこれらのフォルダー間を移動する必要があるため、このような編成では問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-269">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="c175f-270">各フォルダー内のファイルとサブフォルダーの数が増えるとますます困難になり、ソリューション エクスプローラーのスクロール量が膨大になります。</span><span class="sxs-lookup"><span data-stu-id="c175f-270">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="c175f-271">この問題の 1 つの解決策は、アプリケーションのコードをファイルの種類別ではなく "_機能_" 別に整理することです。</span><span class="sxs-lookup"><span data-stu-id="c175f-271">One solution to this problem is to organize application code by _feature_ instead of by file type.</span></span> <span data-ttu-id="c175f-272">この編成スタイルは、通常、機能フォルダーまたは[機能スライス](/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc)と呼ばれます ([垂直スライス](https://deviq.com/vertical-slices/)も参照してください)。</span><span class="sxs-lookup"><span data-stu-id="c175f-272">This organizational style is typically referred to as feature folders or [feature slices](/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc) (see also: [Vertical Slices](https://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="c175f-273">ASP.NET Core MVC では、この目的のために区分 (Area) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c175f-273">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="c175f-274">区分を使うと、各区分フォルダー内にコントローラー フォルダーとビュー フォルダー (および関連するすべてのモデル) のセットを個別に作成できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-274">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="c175f-275">図 7-1 は、区分を使用したフォルダー構造の例です。</span><span class="sxs-lookup"><span data-stu-id="c175f-275">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![区分編成の例](./media/image7-1.png)

<span data-ttu-id="c175f-277">**図 7-1**。</span><span class="sxs-lookup"><span data-stu-id="c175f-277">**Figure 7-1**.</span></span> <span data-ttu-id="c175f-278">区分編成の例</span><span class="sxs-lookup"><span data-stu-id="c175f-278">Sample Area Organization</span></span>

<span data-ttu-id="c175f-279">区分を使う場合は、属性を使って、コントローラーが属する区分の名前でコントローラーを装飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-279">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="c175f-280">また、区分のサポートをルートに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-280">You also need to add area support to your routes:</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "areaRoute", pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="c175f-281">区分の組み込みサポートに加えて、独自のフォルダー構造を作成し、属性とカスタム ルートの代わりの規則を使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-281">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="c175f-282">このようにすると、機能フォルダーにビューやコントローラーなどのフォルダーが個別に含まれないようにして、フラットな階層を維持し、各機能について 1 つの場所ですべての関連ファイルを簡単に見ることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="c175f-282">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="c175f-283">ASP.NET Core は、組み込みの規則の種類を使って、その動作を制御します。</span><span class="sxs-lookup"><span data-stu-id="c175f-283">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="c175f-284">これらの規則は変更したり置き換えたりできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-284">You can modify or replace these conventions.</span></span> <span data-ttu-id="c175f-285">たとえば、名前空間に基づいて特定のコントローラーの機能名を自動的に取得する規則を作成できます (これは通常、コントローラーが存在するフォルダーに関連付けられます)。</span><span class="sxs-lookup"><span data-stu-id="c175f-285">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

```csharp
public class FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

<span data-ttu-id="c175f-286">その後、ConfigureServices でアプリケーションに MVC のサポートを追加するときに、オプションとしてこの規則を指定します。</span><span class="sxs-lookup"><span data-stu-id="c175f-286">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="c175f-287">また、ASP.NET Core MVC はビューを配置する場合にも規則を使います。</span><span class="sxs-lookup"><span data-stu-id="c175f-287">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="c175f-288">これをカスタム規則でオーバーライドして、ビューが独自の機能フォルダーに配置されるようにすることができます (上の FeatureConvention によって提供される機能名を使用)。</span><span class="sxs-lookup"><span data-stu-id="c175f-288">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="c175f-289">この方法について詳しくは、MSDN Magazine の記事「[ASP.NET Core MVC 向け機能スライス](/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc)」をご覧ください。実際に動くサンプルをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-289">You can learn more about this approach and download a working sample from the MSDN Magazine article, [Feature Slices for ASP.NET Core MVC](/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc).</span></span>

### <a name="apis-and-blazor-applications"></a><span data-ttu-id="c175f-290">API と Blazor アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c175f-290">APIs and Blazor applications</span></span>

<span data-ttu-id="c175f-291">セキュリティ保護が必要な一連の Web API がアプリケーションに含まれている場合、これらの API をビューまたは Razor Pages アプリケーションとは別のプロジェクトとして構成するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="c175f-291">If your application includes a set of web APIs, which must be secured, these apis should ideally be configured as a separate project from your View or Razor Pages application.</span></span> <span data-ttu-id="c175f-292">API (特にパブリック API) をサーバー側の Web アプリケーションから分離すると、多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-292">Separating APIs, especially public APIs, from your server-side web application has a number of benefits.</span></span> <span data-ttu-id="c175f-293">多くの場合、これらのアプリケーションには、固有のデプロイと負荷特性があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-293">These applications often will have unique deployment and load characteristics.</span></span> <span data-ttu-id="c175f-294">また、さまざまなセキュリティ メカニズムを採用する可能性も非常に高く、標準のフォームベースのアプリケーションによって、Cookie ベースの認証と、トークンベースの認証を使用する可能性が最も高い API が利用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-294">They're also very likely to adopt different mechanisms for security, with standard form-based applications leveraging cookie-based authentication and APIs most likely using token-based authentication.</span></span>

<span data-ttu-id="c175f-295">さらに、Blazor サーバーと Blazor WebAssembly のどちらを使用するかにかかわらず、Blazor は、個別のプロジェクトとして構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-295">Additionally, Blazor applications, whether using Blazor Server or Blazor WebAssembly, should be built as separate projects.</span></span> <span data-ttu-id="c175f-296">アプリケーションのランタイム特性とセキュリティ モデルは異なります。</span><span class="sxs-lookup"><span data-stu-id="c175f-296">The applications have different runtime characteristics as well as security models.</span></span> <span data-ttu-id="c175f-297">これらによって、サーバー側の Web アプリケーション (または API プロジェクト) と共通の種類が共有される可能性があるため、これらの種類は共通の共用プロジェクトで定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-297">They're likely to share common types with the server-side web application (or API project), and these types should be defined in a common shared project.</span></span>

<span data-ttu-id="c175f-298">Blazor WebAssembly 管理インターフェイスを eShopOnWeb に追加するには、いくつかの新しいプロジェクトを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-298">The addition of a Blazor WebAssembly admin interface to eShopOnWeb required adding several new projects.</span></span> <span data-ttu-id="c175f-299">Blazor WebAssembly プロジェクト自体 (`BlazorAdmin`) です。</span><span class="sxs-lookup"><span data-stu-id="c175f-299">The Blazor WebAssembly project itself, `BlazorAdmin`.</span></span> <span data-ttu-id="c175f-300">`BlazorAdmin` で使用され、トークンベースの認証を使用するように構成されている新しいパブリック API エンドポイント セットは、`PublicApi` プロジェクトで定義されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-300">A new set of public API endpoints, used by `BlazorAdmin` and configured to use token-based authentication, is defined in the `PublicApi` project.</span></span> <span data-ttu-id="c175f-301">さらに、これらの両方のプロジェクトで使用される特定の共有の種類は、新しい `BlazorShared` プロジェクトに保持されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-301">And certain shared types used by both of these projects are kept in a new `BlazorShared` project.</span></span>

<span data-ttu-id="c175f-302">`PublicApi` と `BlazorAdmin` の両方で必要とされる種類を共有するために使用できる共通の `ApplicationCore` プロジェクトが既にあるのに、なぜ別の `BlazorShared` プロジェクトを追加するか、と疑問に思う人もいるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="c175f-302">One might ask, why add a separate `BlazorShared` project when there is already a common `ApplicationCore` project that could be used to share any types required by both `PublicApi` and `BlazorAdmin`?</span></span> <span data-ttu-id="c175f-303">その答えは、このプロジェクトには、アプリケーションのすべてのビジネス ロジックが含まれているため、必要以上に大きく、サーバー上でセキュリティを維持する必要がある可能性がはるかに高いということです。</span><span class="sxs-lookup"><span data-stu-id="c175f-303">The answer is that this project includes all of the application's business logic and is thus much larger than necessary and also much more likely to need to be kept secure on the server.</span></span> <span data-ttu-id="c175f-304">Blazor アプリケーションが読み込まれると、`BlazorAdmin` で参照されるすべてのライブラリがユーザーのブラウザーにダウンロードされることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="c175f-304">Remember that any library referenced by `BlazorAdmin` will be downloaded to users' browsers when they load the Blazor application.</span></span>

<span data-ttu-id="c175f-305">[フロント エンド用バックエンド (BFF) パターン](/azure/architecture/patterns/backends-for-frontends)を使用しているかどうかによって、Blazor WebAssembly アプリで使用される API で、その種類を 100% Blazor と共有しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-305">Depending on whether one is using the [Backends-For-Frontends (BFF) pattern](/azure/architecture/patterns/backends-for-frontends), the APIs consumed by the Blazor WebAssembly app may not share their types 100% with Blazor.</span></span> <span data-ttu-id="c175f-306">特に、多くの異なるクライアントで使用することを目的としたパブリック API では、クライアント固有の共有プロジェクト内で共有するのではなく、独自の要求と結果の種類を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-306">In particular, a public API that's meant to be consumed by many different clients may define its own request and result types, rather than sharing them in a client-specific shared project.</span></span> <span data-ttu-id="c175f-307">eShopOnWeb サンプルの場合、`PublicApi` プロジェクトによって、実際にはパブリック API がホストされていると想定されているため、その要求と応答の種類のすべてが `BlazorShared` プロジェクトから取得されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="c175f-307">In the eShopOnWeb sample, the assumption is being made that the `PublicApi` project is, in fact, hosting a public API, so not all of its request and response types come from the `BlazorShared` project.</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="c175f-308">横断的な問題</span><span class="sxs-lookup"><span data-stu-id="c175f-308">Cross-cutting concerns</span></span>

<span data-ttu-id="c175f-309">アプリケーションが大きくなるほど、横断的な事柄を抽出して、重複を排除し、整合性を維持することの重要性が増します。</span><span class="sxs-lookup"><span data-stu-id="c175f-309">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="c175f-310">ASP.NET Core アプリケーションでの横断的な事柄の例としては、認証、モデル検証規則、出力キャッシュ、エラー処理などがありますが、その他にも多くのことがあります。</span><span class="sxs-lookup"><span data-stu-id="c175f-310">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="c175f-311">ASP.NET Core MVC で[フィルター](/aspnet/core/mvc/controllers/filters)を使うと、要求処理パイプラインの特定のステップの前または後にコードを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-311">ASP.NET Core MVC [filters](/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="c175f-312">たとえば、フィルターは、モデル バインドの前後、アクションの前後、またはアクションの結果の前後に実行できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-312">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="c175f-313">また、承認フィルターを使って、パイプラインの残りの部分へのアクセスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-313">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="c175f-314">図 7-2 では、フィルターを構成した場合に要求の実行がそれをどのように通過するかを示します。</span><span class="sxs-lookup"><span data-stu-id="c175f-314">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![要求は、承認フィルター、リソース フィルター、モデル バインド、アクション フィルター、アクションの実行とアクション結果の変換、例外フィルター、結果フィルター、結果の実行を介して処理されます。](./media/image7-2.png)

<span data-ttu-id="c175f-317">**図 7-2**。</span><span class="sxs-lookup"><span data-stu-id="c175f-317">**Figure 7-2**.</span></span> <span data-ttu-id="c175f-318">フィルターと要求パイプラインを通過する要求実行の流れ。</span><span class="sxs-lookup"><span data-stu-id="c175f-318">Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="c175f-319">通常、フィルターは属性として実装されるので、コントローラーまたはアクションにフィルターを適用できます (グローバルでも可能)。</span><span class="sxs-lookup"><span data-stu-id="c175f-319">Filters are usually implemented as attributes, so you can apply them to controllers or actions (or even globally).</span></span> <span data-ttu-id="c175f-320">この方法で追加したフィルターをアクション レベルで指定すると、コントローラー レベルで指定されたフィルターをオーバーライドするか、その上に構築されて、それ自体がグローバル フィルターをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="c175f-320">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="c175f-321">たとえば、\[Route\] 属性を使って、コントローラーとアクションの間にルートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-321">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="c175f-322">同様に、コントローラー レベルで承認を構成した後、次の例に示すように、個々のアクションでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-322">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="c175f-323">最初の Login メソッドでは、AllowAnonymous フィルター (属性) を使って、コントローラー レベルで設定されている Authorize フィルターをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="c175f-323">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="c175f-324">ForgotPassword アクション (および AllowAnonymous 属性を持たないクラスの他のすべてのアクション) では、認証された要求が必要です。</span><span class="sxs-lookup"><span data-stu-id="c175f-324">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="c175f-325">フィルターを使うと、API に対する共通エラー処理ポリシーの形式で、重複を除去できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-325">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="c175f-326">たとえば、一般的な API ポリシーでは、存在しないキーを参照している要求に対しては NotFound 応答を返し、モデルの検証が失敗した場合は BadRequest 応答を返します。</span><span class="sxs-lookup"><span data-stu-id="c175f-326">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="c175f-327">次の例では、アクションでのこれら 2 つのポリシーを示します。</span><span class="sxs-lookup"><span data-stu-id="c175f-327">The following example demonstrates these two policies in action:</span></span>

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="c175f-328">このような条件付きコードで、アクション メソッドを乱雑にしないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c175f-328">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="c175f-329">代わりに、必要に応じて適用できるフィルターにポリシーを格納します。</span><span class="sxs-lookup"><span data-stu-id="c175f-329">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="c175f-330">この例では、コマンドが API に送られるたびに実行する必要があるモデルの検証チェックを、次の属性で置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-330">In this example, the model validation check, which should occur anytime a command is sent to the API, can be replaced by the following attribute:</span></span>

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

<span data-ttu-id="c175f-331">[Ardalis.ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) パッケージを含めることで、NuGet 依存関係として `ValidateModelAttribute` をプロジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-331">You can add the `ValidateModelAttribute` to your project as a NuGet dependency by including the [Ardalis.ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel) package.</span></span> <span data-ttu-id="c175f-332">API の場合、`ApiController` 属性を使用することで、別個の `ValidateModel` フィルターがなくてもこの動作を強制できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-332">For APIs, you can use the `ApiController` attribute to enforce this behavior without the need for a separate `ValidateModel` filter.</span></span>

<span data-ttu-id="c175f-333">同様に、フィルターを使ってレコードが存在するかどうかをチェックし、アクションが実行される前に 404 を返して、アクションでこれらのチェックを実行する必要がないようにできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-333">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="c175f-334">共通の規則を抽出し、インフラストラクチャ コードとビジネス ロジックを UI から分離するようにソリューションを構成すると、MVC アクション メソッドは非常にスリムになるはずです。</span><span class="sxs-lookup"><span data-stu-id="c175f-334">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="c175f-335">フィルターの実装の詳細については、MSDN Magazine の記事「[実際の ASP.NET Core MVC フィルター](/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters)」を参照してください。また、実際に動作するサンプルをダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-335">You can read more about implementing filters and download a working sample from the MSDN Magazine article, [Real-World ASP.NET Core MVC Filters](/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="c175f-336">参照 – アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="c175f-336">References – Structuring applications</span></span>
>
> - <span data-ttu-id="c175f-337">**領域**</span><span class="sxs-lookup"><span data-stu-id="c175f-337">**Areas**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - <span data-ttu-id="c175f-338">**MSDN マガジン – ASP.NET Core MVC 向け機能スライス**</span><span class="sxs-lookup"><span data-stu-id="c175f-338">**MSDN Magazine – Feature Slices for ASP.NET Core MVC**</span></span>\
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc>
> - <span data-ttu-id="c175f-339">**フィルター**</span><span class="sxs-lookup"><span data-stu-id="c175f-339">**Filters**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - <span data-ttu-id="c175f-340">**MSDN Magazine – 実際の ASP.NET Core MVC フィルター**</span><span class="sxs-lookup"><span data-stu-id="c175f-340">**MSDN Magazine – Real World ASP.NET Core MVC Filters**</span></span>\
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters>

## <a name="security"></a><span data-ttu-id="c175f-341">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c175f-341">Security</span></span>

<span data-ttu-id="c175f-342">Web アプリケーションのセキュリティ保護は大きなトピックであり、さまざまな考慮事項があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-342">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="c175f-343">最も基本的なレベルのセキュリティには、特定の要求を行ったユーザーを認識し、その要求が必要なリソースだけにアクセスできるようにすることが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-343">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that the request only has access to resources it should.</span></span> <span data-ttu-id="c175f-344">認証は、要求で提供された資格情報を、信頼できるデータ ストア内の資格情報と比較して、要求を既知のエンティティから送信されたものとして扱う必要があるかどうかを確認するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="c175f-344">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="c175f-345">承認は、ユーザーの ID に基づいて特定のリソースへのアクセスを制限するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="c175f-345">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="c175f-346">セキュリティに関する 3 番目の考慮事項は、第三者による傍受から要求を保護することであり、少なくとも[アプリケーションが SSL を使っていることを確認する](/aspnet/core/security/enforcing-ssl)必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-346">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="identity"></a><span data-ttu-id="c175f-347">ID</span><span class="sxs-lookup"><span data-stu-id="c175f-347">Identity</span></span>

<span data-ttu-id="c175f-348">ASP.NET Core Identity は、アプリケーションのログイン機能をサポートするために使うことができるメンバーシップ システムです。</span><span class="sxs-lookup"><span data-stu-id="c175f-348">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="c175f-349">ローカル ユーザー アカウントをサポートするだけでなく、Microsoft アカウント、Twitter、Facebook、Google などのプロバイダーからの外部ログイン プロバイダーもサポートします。</span><span class="sxs-lookup"><span data-stu-id="c175f-349">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="c175f-350">ASP.NET Core Identity だけでなく、アプリケーションでは Windows 認証や、[Identity Server](https://github.com/IdentityServer/IdentityServer4) のようなサード パーティの ID プロバイダーを使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-350">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="c175f-351">[個別のユーザー アカウント] オプションを選択した場合、新しいプロジェクト テンプレートには ASP.NET Core Identity が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-351">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="c175f-352">このテンプレートには、登録、ログイン、外部ログイン、パスワードを忘れた場合、および追加機能のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c175f-352">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![[個別のユーザー アカウント] を選択して Identity を事前構成する](./media/image7-3.png)

<span data-ttu-id="c175f-354">**図 7-3**。</span><span class="sxs-lookup"><span data-stu-id="c175f-354">**Figure 7-3**.</span></span> <span data-ttu-id="c175f-355">[個別のユーザー アカウント] を選択して Identity を事前構成する。</span><span class="sxs-lookup"><span data-stu-id="c175f-355">Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="c175f-356">Identity のサポートは、Startup の ConfigureServices と Configure の両方で構成されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-356">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
        .AddEntityFrameworkStores<ApplicationDbContext>()
        .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="c175f-357">Configure メソッドで UseMvc の前に UseIdentity を指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="c175f-357">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="c175f-358">ConfigureServices で Identity を構成すると、AddDefaultTokenProviders の呼び出しがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="c175f-358">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="c175f-359">これは、Web 通信をセキュリティ保護するために使われる場合があるトークンとは関係なく、ユーザーによる ID 確認のために SMS またはメールでユーザーに送信できるプロンプトを作成するプロバイダーを参照しています。</span><span class="sxs-lookup"><span data-stu-id="c175f-359">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="c175f-360">詳しくは、ASP.NET Core の公式ドキュメントで [2 要素認証の構成](/aspnet/core/security/authentication/2fa)および[外部ログイン プロバイダーの有効化](/aspnet/core/security/authentication/social/)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c175f-360">You can learn more about [configuring two-factor authentication](/aspnet/core/security/authentication/2fa) and [enabling external login providers](/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authentication"></a><span data-ttu-id="c175f-361">認証</span><span class="sxs-lookup"><span data-stu-id="c175f-361">Authentication</span></span>

<span data-ttu-id="c175f-362">認証は、システムにアクセスしているユーザーを判別するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="c175f-362">Authentication is the process of determining who is accessing the system.</span></span> <span data-ttu-id="c175f-363">前のセクションで示した ASP.NET Core Identity と構成メソッドを使用すると、アプリケーションの一部の認証の既定値が自動的に構成されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-363">If you're using ASP.NET Core Identity and the configuration methods shown in the previous section, it will automatically configure some authentication defaults in the application.</span></span> <span data-ttu-id="c175f-364">ただし、これらの既定値を手動で構成することも、AddIdentity で設定された値をオーバーライドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-364">However, you can also configure these defaults manually, or override the ones set by AddIdentity.</span></span> <span data-ttu-id="c175f-365">Identity を使用している場合、既定の "*スキーム*" として Cookie ベースの認証が構成されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-365">If you're using Identity, it configures cookie-based authentication as the default *scheme*.</span></span>

<span data-ttu-id="c175f-366">Web ベースの認証では、通常、システムのクライアントを認証する過程で、最大 5 つのアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-366">In web-based authentication, there are typically up to five actions that may be performed in the course of authenticating a client of a system.</span></span> <span data-ttu-id="c175f-367">次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c175f-367">These are:</span></span>

- <span data-ttu-id="c175f-368">認証。</span><span class="sxs-lookup"><span data-stu-id="c175f-368">Authenticate.</span></span> <span data-ttu-id="c175f-369">クライアントから提供された情報を使用して、アプリケーション内で使用する ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="c175f-369">Use the information provided by the client to create an identity for them to use within the application.</span></span>
- <span data-ttu-id="c175f-370">チャレンジ。</span><span class="sxs-lookup"><span data-stu-id="c175f-370">Challenge.</span></span> <span data-ttu-id="c175f-371">このアクションを使用して、クライアントに自身を識別する世に要求します。</span><span class="sxs-lookup"><span data-stu-id="c175f-371">This action is used to require the client to identify themselves.</span></span>
- <span data-ttu-id="c175f-372">禁止。</span><span class="sxs-lookup"><span data-stu-id="c175f-372">Forbid.</span></span> <span data-ttu-id="c175f-373">アクションの実行が禁止されていることをクライアントに通知します。</span><span class="sxs-lookup"><span data-stu-id="c175f-373">Inform the client they are forbidden from performing an action.</span></span>
- <span data-ttu-id="c175f-374">サインイン。</span><span class="sxs-lookup"><span data-stu-id="c175f-374">Sign-in.</span></span> <span data-ttu-id="c175f-375">何らかの方法で既存のクライアントを保持します。</span><span class="sxs-lookup"><span data-stu-id="c175f-375">Persist the existing client in some way.</span></span>
- <span data-ttu-id="c175f-376">サインアウト。クライアントを永続化から削除します。</span><span class="sxs-lookup"><span data-stu-id="c175f-376">Sign-out. Remove the client from persistence.</span></span>

<span data-ttu-id="c175f-377">Web アプリケーションで認証を実行するには、いくつかの一般的な手法があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-377">There are a number of common techniques for performing authentication in web applications.</span></span> <span data-ttu-id="c175f-378">これらは、スキームと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-378">These are referred to as schemes.</span></span> <span data-ttu-id="c175f-379">特定のスキームで、上記のオプションの一部またはすべてのアクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="c175f-379">A given scheme will define actions for some or all of the above options.</span></span> <span data-ttu-id="c175f-380">一部のスキームでは、アクションのサブセットのみがサポートされ、サポートされていないアクションを実行するために個別のスキームが必要になります。</span><span class="sxs-lookup"><span data-stu-id="c175f-380">Some schemes only support a subset of actions, and may require a separate scheme to perform those it does not support.</span></span> <span data-ttu-id="c175f-381">たとえば、OpenId-Connect (OIDC) スキームによって、サインインとサインアウトはサポートされませんが、一般的に、この永続化には Cookie 認証を使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-381">For example, the OpenId-Connect (OIDC) scheme doesn't support Sign-in or Sign-out, but is commonly configured to use Cookie authentication for this persistence.</span></span>

<span data-ttu-id="c175f-382">ASP.NET Core アプリケーションでは、前述の各アクションに対して `DefaultAuthenticateScheme` とオプションの特定のスキームを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-382">In your ASP.NET Core application, you can configure a `DefaultAuthenticateScheme` as well as optional specific schemes for each of the actions described above.</span></span> <span data-ttu-id="c175f-383">たとえば、`DefaultChallengeScheme`、`DefaultForbidScheme` などです。[`AddIdentity<TUser,TRole>`](https://github.com/dotnet/aspnetcore/blob/release/3.1/src/Identity/Core/src/IdentityServiceCollectionExtensions.cs#L38-L102) を呼び出すと、アプリケーションのさまざまな側面が構成され、多くの必要なサービスが追加されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-383">For example, `DefaultChallengeScheme`, `DefaultForbidScheme`, etc. Calling [`AddIdentity<TUser,TRole>`](https://github.com/dotnet/aspnetcore/blob/release/3.1/src/Identity/Core/src/IdentityServiceCollectionExtensions.cs#L38-L102) configures a number of aspects of the application and adds many required services.</span></span> <span data-ttu-id="c175f-384">これには、認証スキームを構成するためのこの呼び出しも含まれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-384">It also includes this call to configure the authentication scheme:</span></span>

```csharp
services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = IdentityConstants.ApplicationScheme;
    options.DefaultChallengeScheme = IdentityConstants.ApplicationScheme;
    options.DefaultSignInScheme = IdentityConstants.ExternalScheme;
});
```

<span data-ttu-id="c175f-385">これらのスキームにより、既定で、永続化と認証用のログインページへのリダイレクトに Cookie が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-385">These schemes use cookies for persistence and redirection to login pages for authentication by default.</span></span> <span data-ttu-id="c175f-386">これらのスキームは、Web ブラウザーを介してユーザーとやりとりする Web アプリケーションに適していますが、API には推奨されません。</span><span class="sxs-lookup"><span data-stu-id="c175f-386">These schemes are appropriate for web applications that interact with users via web browsers, but not recommended for APIs.</span></span> <span data-ttu-id="c175f-387">代わりに、API では、通常、別の形式の認証 (たとえば、JWT ベアラー トークン) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-387">Instead, APIs will typically use another form of authentication, such as JWT bearer tokens.</span></span>

<span data-ttu-id="c175f-388">Web API は、.NET アプリケーションの `HttpClient` や他のフレームワークの同等の型などのコードによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-388">Web APIs are consumed by code, such as `HttpClient` in .NET applications and equivalent types in other frameworks.</span></span> <span data-ttu-id="c175f-389">これらのクライアントでは、API 呼び出しからの使用可能な応答、または発生した問題がある場合は、それを示す状態コードを想定しています。</span><span class="sxs-lookup"><span data-stu-id="c175f-389">These clients expect a usable response from an API call, or a status code indicating what, if any, problem has occurred.</span></span> <span data-ttu-id="c175f-390">これらのクライアントでは、ブラウザーを介してやりとりしておらず、API が返す可能性のある HTML をレンダリングまたは操作することもありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-390">These clients are not interacting through a browser and do not render or interact with any HTML that an API might return.</span></span> <span data-ttu-id="c175f-391">このため、クライアントが認証されない場合、API エンドポイントによってそれらをログイン ページにリダイレクトするのは適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-391">Thus, it is not appropriate for API endpoints to redirect their clients to login pages if they are not authenticated.</span></span> <span data-ttu-id="c175f-392">別のスキームの方が適切です。</span><span class="sxs-lookup"><span data-stu-id="c175f-392">Another scheme is more appropriate.</span></span>

<span data-ttu-id="c175f-393">API の認証を構成するには、次のような認証を設定できます。これは、eShopOnWeb 参照アプリケーションの `PublicApi` プロジェクトで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-393">To configure authentication for APIs, you might set up authentication like the following, used by the `PublicApi` project in the eShopOnWeb reference application:</span></span>

```csharp
services.AddAuthentication(config =>
{
    config.DefaultScheme = JwtBearerDefaults.AuthenticationScheme;
})
    .AddJwtBearer(config =>
    {
        config.RequireHttpsMetadata = false;
        config.SaveToken = true;
        config.TokenValidationParameters = new TokenValidationParameters
        {
            ValidateIssuerSigningKey = true,
            IssuerSigningKey = new SymmetricSecurityKey(key),
            ValidateIssuer = false,
            ValidateAudience = false
        };
    });
```

<span data-ttu-id="c175f-394">1 つのプロジェクト内に複数の異なる認証スキームを構成できますが、1 つの既定のスキームを構成する方がはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="c175f-394">While it is possible to configure multiple different authentication schemes within a single project, it is much simpler to configure a single default scheme.</span></span> <span data-ttu-id="c175f-395">このため、特に、eShopOnWeb 参照アプリケーションでは、アプリケーションのビューと Razor Pages を含むメインの `Web` プロジェクトとは別個の独自のプロジェクト `PublicApi` に API を分離します。</span><span class="sxs-lookup"><span data-stu-id="c175f-395">For this reason, among others, the eShopOnWeb reference application separates its APIs into their own project, `PublicApi`, separate from the main `Web` project that includes the application's views and Razor Pages.</span></span>

#### <a name="authentication-in-blazor-apps"></a><span data-ttu-id="c175f-396">Blazor アプリでの認証</span><span class="sxs-lookup"><span data-stu-id="c175f-396">Authentication in Blazor apps</span></span>

<span data-ttu-id="c175f-397">Blazor サーバー アプリケーションでは、他の ASP.NET Core アプリケーションと同じ認証機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-397">Blazor Server applications can leverage the same authentication features as any other ASP.NET Core application.</span></span> <span data-ttu-id="c175f-398">ただし、Blazor WebAssembly アプリケーションはブラウザーで実行されるため、組み込みの ID および認証プロバイダーを使用できません。</span><span class="sxs-lookup"><span data-stu-id="c175f-398">Blazor WebAssembly applications cannot use the built-in Identity and Authentication providers, however, since they run in the browser.</span></span> <span data-ttu-id="c175f-399">Blazor WebAssembly アプリケーションによって、ユーザーの認証状態がローカルに保存し、要求にアクセスされ、ユーザーが実行する必要があるアクションが決定されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-399">Blazor WebAssembly applications can store user authentication status locally and can access claims to determine what actions users should be able to perform.</span></span> <span data-ttu-id="c175f-400">ただし、ユーザーは簡単にアプリをバイパスして API と直接やりとりすることができるため、Blazor WebAssembly アプリ内に実装されているロジックに関係なく、すべての認証および承認のチェックをサーバーで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-400">However, all authentication and authorization checks should be performed on the server regardless of any logic implemented inside the Blazor WebAssembly app, since users can easily bypass the app and interact with the APIs directly.</span></span>

> ### <a name="references--authentication"></a><span data-ttu-id="c175f-401">参照 - 認証</span><span class="sxs-lookup"><span data-stu-id="c175f-401">References – Authentication</span></span>
>
> - <span data-ttu-id="c175f-402">**認証アクションと既定値**</span><span class="sxs-lookup"><span data-stu-id="c175f-402">**Authentication Actions and Defaults**</span></span>\
>   <https://stackoverflow.com/a/52493428>
> - <span data-ttu-id="c175f-403">**SPA の認証と承認**</span><span class="sxs-lookup"><span data-stu-id="c175f-403">**Authentication and Authorization for SPAs**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity-api-authorization>
> - <span data-ttu-id="c175f-404">**ASP.NET Core Blazor の認証と承認**</span><span class="sxs-lookup"><span data-stu-id="c175f-404">**ASP.NET Core Blazor Authentication and Authorization**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/blazor/security/>
> - <span data-ttu-id="c175f-405">**セキュリティ:ASP.NET Web Forms および Blazor** \ での認証と承認</span><span class="sxs-lookup"><span data-stu-id="c175f-405">**Security: Authentication and Authorization in ASP.NET Web Forms and Blazor**\</span></span>
>   <https://docs.microsoft.com/dotnet/architecture/blazor-for-web-forms-developers/security-authentication-authorization>

### <a name="authorization"></a><span data-ttu-id="c175f-406">承認</span><span class="sxs-lookup"><span data-stu-id="c175f-406">Authorization</span></span>

<span data-ttu-id="c175f-407">承認の最も単純な形式には、匿名ユーザーに対するアクセスの制限が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-407">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="c175f-408">この機能は、特定のコントローラーまたはアクションに \[Authorize\] 属性を適用すると実現できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-408">This functionality can be achieved by applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="c175f-409">ロールを使っている場合は、次のように、特定のロールに属しているユーザーのアクセス制限まで、属性をさらに拡張できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-409">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="c175f-410">この例では、`HRManager` ロールと `Finance` ロールのどちらか一方または両方に属しているユーザーは、SalaryController にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-410">In this case, users belonging to either the `HRManager` or `Finance` roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="c175f-411">ユーザーが (複数のロールの 1 つだけでなく) 複数のロールに属していることを必要とするには、属性を複数回適用し、そのたびに必要なロールを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-411">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="c175f-412">特定のロール セットを文字列として多くの異なるコントローラーやアクションで指定すると、望ましくない繰り返しにつながります。</span><span class="sxs-lookup"><span data-stu-id="c175f-412">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="c175f-413">少なくとも、これらの文字列リテラルに定数を定義し、その文字列を指定する必要がある場所でその定数を使用します。</span><span class="sxs-lookup"><span data-stu-id="c175f-413">At a minimum, define constants for these string literals and use the constants anywhere you need to specify the string.</span></span> <span data-ttu-id="c175f-414">さらに、承認規則をカプセル化する承認ポリシーを構成し、\[Authorize\] 属性を適用する場合に、そのポリシーを個々のロールの代わりに指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-414">You can also configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="c175f-415">この方法でポリシーを使うと、適用される特定のロールまたは規則から、制限されるアクションの種類を切り離すことができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-415">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="c175f-416">後で、特定のリソースへのアクセスを必要とする新しいロールを作成する場合は、ポリシーを更新するだけでよく、すべての \[Authorize\] 属性ですべてのロール リストを更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-416">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="c175f-417">クレーム</span><span class="sxs-lookup"><span data-stu-id="c175f-417">Claims</span></span>

<span data-ttu-id="c175f-418">クレームは、認証済みユーザーのプロパティを表す名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="c175f-418">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="c175f-419">たとえば、ユーザーの従業員番号をクレームとして格納できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-419">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="c175f-420">その後、承認ポリシーの一部としてクレームを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-420">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="c175f-421">次の例では、"EmployeeNumber" という名前のクレームが存在する必要のある "EmployeeOnly" というポリシーを作成しています。</span><span class="sxs-lookup"><span data-stu-id="c175f-421">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

<span data-ttu-id="c175f-422">その後、上記のように、このポリシーを \[Authorize\] 属性で使って、コントローラーやアクションを保護できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-422">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="c175f-423">Web API のセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="c175f-423">Securing web APIs</span></span>

<span data-ttu-id="c175f-424">ほとんどの Web API は、トークン ベースの認証システムを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-424">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="c175f-425">トークン認証はステートレスであり、拡張できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="c175f-425">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="c175f-426">トークン ベースの認証システムでは、クライアントは最初に認証プロバイダーで認証を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-426">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="c175f-427">それが成功した場合、クライアントはトークンを発行されます。トークンは、単に暗号化された意味のある文字列です。</span><span class="sxs-lookup"><span data-stu-id="c175f-427">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="c175f-428">トークンの最も一般的な形式は、JSON Web トークン (JWT、多くの場合 "ジョット" と発音します) です。</span><span class="sxs-lookup"><span data-stu-id="c175f-428">The most common format for tokens is JSON Web Token, or JWT (often pronounced "jot").</span></span> <span data-ttu-id="c175f-429">その後、クライアントが API に要求を発行する必要があるときは、このトークンを要求のヘッダーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="c175f-429">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="c175f-430">サーバーは、要求を完了する前に、要求ヘッダーに含まれるトークンを検証します。</span><span class="sxs-lookup"><span data-stu-id="c175f-430">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="c175f-431">図 7-4 はこのプロセスを示したものです。</span><span class="sxs-lookup"><span data-stu-id="c175f-431">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="c175f-433">**図 7-4.**</span><span class="sxs-lookup"><span data-stu-id="c175f-433">**Figure 7-4.**</span></span> <span data-ttu-id="c175f-434">Web API に対するトークン ベースの認証。</span><span class="sxs-lookup"><span data-stu-id="c175f-434">Token-based authentication for Web APIs.</span></span>

<span data-ttu-id="c175f-435">独自の認証サービスを作成したり、Azure AD や OAuth と統合したり、[IdentityServer](https://github.com/IdentityServer) のようなオープンソースのツールを利用してサービスを実装したりできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-435">You can create your own authentication service, integrate with Azure AD and OAuth, or implement a service using an open-source tool like [IdentityServer](https://github.com/IdentityServer).</span></span>

<span data-ttu-id="c175f-436">JWT トークンにはユーザーに関する要求を埋め込むことができ、これらはクライアントまたはサーバーで読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-436">JWT tokens can embed claims about the user, which can be read on the client or server.</span></span> <span data-ttu-id="c175f-437">JWT トークンの内容を表示するには、[jwt.io](https://jwt.io/) などのツールを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-437">You can use a tool like [jwt.io](https://jwt.io/) to view the contents of a JWT token.</span></span> <span data-ttu-id="c175f-438">パスワードやキーなどの機密データは、簡単に読み取られてしまうため、JTW トークンに格納しないでください。</span><span class="sxs-lookup"><span data-stu-id="c175f-438">Do not store sensitive data like passwords or keys in JTW tokens, since their contents are easily read.</span></span>

<span data-ttu-id="c175f-439">SPA または Blazor WebAssembly アプリケーションで JWT トークンを使用する場合、クライアント上の任意の場所に格納し、すべての API 呼び出しに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-439">When using JWT tokens with SPA or Blazor WebAssembly applications, you must store the token somewhere on the client and then add it to every API call.</span></span> <span data-ttu-id="c175f-440">次のコードで示すように、通常、このアクティビティはヘッダーとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-440">This activity is typically done as a header, as the following code demonstrates:</span></span>

```csharp
// AuthService.cs in BlazorAdmin project of eShopOnWeb
private async Task SetAuthorizationHeader()
{
    var token = await GetToken();
    _httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", token);
}
```

<span data-ttu-id="c175f-441">上記のメソッドが呼び出されると、`_httpClient` で作成された要求の要求ヘッダーにトークンが埋め込まれます。これにより、サーバー側の API で要求の認証と承認を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c175f-441">After calling the above method, requests made with the `_httpClient` will have the token embedded in the request's headers, allowing the server-side API to authenticate and authorize the request.</span></span>

#### <a name="custom-security"></a><span data-ttu-id="c175f-442">カスタム セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c175f-442">Custom Security</span></span>

<span data-ttu-id="c175f-443">暗号化、ユーザー メンバーシップ、トークン生成システムの実装を "独自に展開する" 場合、特別な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="c175f-443">Be especially careful about "rolling your own" implementation of cryptography, user membership, or token generation system.</span></span> <span data-ttu-id="c175f-444">代案がたくさん売られているし、オープン ソースも利用できます。ほぼ間違いなく、カスタム実装よりセキュリティが優れています。</span><span class="sxs-lookup"><span data-stu-id="c175f-444">There are many commercial and open-source alternatives available, which will almost certainly have better security than a custom implementation.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="c175f-445">参照 – セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c175f-445">References – Security</span></span>
>
> - <span data-ttu-id="c175f-446">**セキュリティ ドキュメントの概要**</span><span class="sxs-lookup"><span data-stu-id="c175f-446">**Security Docs Overview**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/security/>
> - <span data-ttu-id="c175f-447">**ASP.NET Core アプリで SSL を適用する**</span><span class="sxs-lookup"><span data-stu-id="c175f-447">**Enforcing SSL in an ASP.NET Core App**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - <span data-ttu-id="c175f-448">**Identity の概要**</span><span class="sxs-lookup"><span data-stu-id="c175f-448">**Introduction to Identity**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - <span data-ttu-id="c175f-449">**承認の概要**</span><span class="sxs-lookup"><span data-stu-id="c175f-449">**Introduction to Authorization**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - <span data-ttu-id="c175f-450">**Azure App Service での API Apps に対する認証および承認**</span><span class="sxs-lookup"><span data-stu-id="c175f-450">**Authentication and Authorization for API Apps in Azure App Service**</span></span>\
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - <span data-ttu-id="c175f-451">**Identity Server**</span><span class="sxs-lookup"><span data-stu-id="c175f-451">**Identity Server**</span></span>\
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a><span data-ttu-id="c175f-452">クライアントの通信</span><span class="sxs-lookup"><span data-stu-id="c175f-452">Client communication</span></span>

<span data-ttu-id="c175f-453">Web API によりページを提供してデータの要求に応答するだけでなく、ASP.NET Core アプリは接続されているクライアントと直接通信できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-453">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="c175f-454">この送信通信では、さまざまなトランスポート テクノロジを使うことができ、最も一般的なものは WebSocket です。</span><span class="sxs-lookup"><span data-stu-id="c175f-454">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="c175f-455">ASP.NET Core SignalR は、サーバーとクライアントの間のリアルタイム通信機能をアプリケーションに容易に追加できるようにするライブラリです。</span><span class="sxs-lookup"><span data-stu-id="c175f-455">ASP.NET Core SignalR is a library that makes it simple to add real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="c175f-456">SignalR は、WebSocket などのさまざまなトランスポート テクノロジをサポートしており、多くの実装の詳細を開発者から抽象化します。</span><span class="sxs-lookup"><span data-stu-id="c175f-456">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="c175f-457">WebSocket を直接使うか、他の技法を使うかに関係なく、リアルタイムのクライアント通信は、さまざまなアプリケーション シナリオで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="c175f-457">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="c175f-458">次に、それらの例の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="c175f-458">Some examples include:</span></span>

- <span data-ttu-id="c175f-459">ライブ チャット ルーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c175f-459">Live chat room applications</span></span>

- <span data-ttu-id="c175f-460">アプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="c175f-460">Monitoring applications</span></span>

- <span data-ttu-id="c175f-461">ジョブの進行状況の更新</span><span class="sxs-lookup"><span data-stu-id="c175f-461">Job progress updates</span></span>

- <span data-ttu-id="c175f-462">通知</span><span class="sxs-lookup"><span data-stu-id="c175f-462">Notifications</span></span>

- <span data-ttu-id="c175f-463">対話型のフォーム アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c175f-463">Interactive forms applications</span></span>

<span data-ttu-id="c175f-464">クライアント通信をアプリケーションに組み込むときは、通常、2 つのコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="c175f-464">When building client communication into your applications, there are typically two components:</span></span>

- <span data-ttu-id="c175f-465">サーバー側の接続マネージャー (SignalR Hub、WebSocketManager WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="c175f-465">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

- <span data-ttu-id="c175f-466">クライアント側のライブラリ</span><span class="sxs-lookup"><span data-stu-id="c175f-466">Client-side library</span></span>

<span data-ttu-id="c175f-467">クライアントはブラウザーに限定されず、モバイル アプリ、コンソール アプリ、他のネイティブ アプリも SignalR/WebSocket を使って通信できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-467">Clients aren't limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="c175f-468">次の簡単なプログラムは、WebSocketManager サンプル アプリケーションの一部として、チャット アプリケーションに送信されたすべての内容をコンソールにエコーします。</span><span class="sxs-lookup"><span data-stu-id="c175f-468">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>
        {
            Console.WriteLine($"{arguments[0]} said: {arguments[1]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }

    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }

    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
}
```

<span data-ttu-id="c175f-469">アプリケーションがクライアント アプリケーションと直接通信する方法を検討し、リアルタイム通信によってアプリのユーザー エクスペリエンスが向上するかどうかを検討します。</span><span class="sxs-lookup"><span data-stu-id="c175f-469">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="c175f-470">参照 – クライアントの通信</span><span class="sxs-lookup"><span data-stu-id="c175f-470">References – Client Communication</span></span>
>
> - <span data-ttu-id="c175f-471">**ASP.NET Core SignalR**</span><span class="sxs-lookup"><span data-stu-id="c175f-471">**ASP.NET Core SignalR**</span></span>\
>   <https://github.com/dotnet/aspnetcore/tree/main/src/SignalR>
> - <span data-ttu-id="c175f-472">**WebSocket マネージャー**</span><span class="sxs-lookup"><span data-stu-id="c175f-472">**WebSocket Manager**</span></span>\
>   <https://github.com/radu-matei/websocket-manager>

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="c175f-473">ドメイン駆動設計 – 適用する必要があるか?</span><span class="sxs-lookup"><span data-stu-id="c175f-473">Domain-driven design – Should you apply it?</span></span>

<span data-ttu-id="c175f-474">ドメイン駆動設計 (DDD) は、"_ビジネス ドメイン_" に注目するソフトウェア構築のためのアジャイルな方法です。</span><span class="sxs-lookup"><span data-stu-id="c175f-474">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the _business domain_.</span></span> <span data-ttu-id="c175f-475">実際のシステムのしくみについて開発者に関わることができるビジネス ドメインの専門家とのコミュニケーションと対話に重点が置かれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-475">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="c175f-476">たとえば、株取引を処理するシステムを構築する場合のドメインの専門家は、経験豊富な株式ブローカーなどです。</span><span class="sxs-lookup"><span data-stu-id="c175f-476">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="c175f-477">DDD は、大規模で複雑なビジネスの問題に対処するように設計されており、多くの場合、ドメインの理解とモデリングに対する投資に見合わないため、小さくて単純なアプリケーションには適しません。</span><span class="sxs-lookup"><span data-stu-id="c175f-477">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="c175f-478">DDD 手法でソフトウェアを作成する場合、チーム (非技術的な利害関係者や貢献者を含む) は問題領域のための "_ユビキタス言語_" を開発する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-478">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a _ubiquitous language_ for the problem space.</span></span> <span data-ttu-id="c175f-479">つまり、モデル化される実際の概念、それに相当するソフトウェア、概念を保持するために存在する構造 (データベース テーブルなど) に、同じ用語を使う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-479">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="c175f-480">したがって、ユビキタス言語で説明される概念は、"_ドメイン モデル_" の基礎を形成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-480">Thus, the concepts described in the ubiquitous language should form the basis for your _domain model_.</span></span>

<span data-ttu-id="c175f-481">ドメイン モデルは、相互に対話してシステムの動作を表すオブジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-481">Your domain model comprises objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="c175f-482">これらのオブジェクトは以下のカテゴリに分けられます。</span><span class="sxs-lookup"><span data-stu-id="c175f-482">These objects may fall into the following categories:</span></span>

- <span data-ttu-id="c175f-483">[エンティティ](https://deviq.com/entity/)は、ID のスレッドでオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="c175f-483">[Entities](https://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="c175f-484">エンティティは、通常、後で取得できるキーを使って永続的に格納されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-484">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

- <span data-ttu-id="c175f-485">[集約](https://deviq.com/aggregate-pattern/)は、単位として永続化する必要のあるオブジェクトのグループを表します。</span><span class="sxs-lookup"><span data-stu-id="c175f-485">[Aggregates](https://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

- <span data-ttu-id="c175f-486">[値オブジェクト](https://deviq.com/value-object/)は、プロパティ値の合計に基づいて比較できる概念を表します。</span><span class="sxs-lookup"><span data-stu-id="c175f-486">[Value objects](https://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="c175f-487">たとえば、開始日と終了日で構成される DateRange などです。</span><span class="sxs-lookup"><span data-stu-id="c175f-487">For example, DateRange consisting of a start and end date.</span></span>

- <span data-ttu-id="c175f-488">[ドメイン イベント](https://martinfowler.com/eaaDev/DomainEvent.html)は、システムの他の部分にとって重要な、システム内で発生している出来事を表します。</span><span class="sxs-lookup"><span data-stu-id="c175f-488">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="c175f-489">DDD ドメイン モデルでは、モデル内に複雑な動作をカプセル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-489">A DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="c175f-490">特にエンティティは、プロパティの単なるコレクションであってはなりません。</span><span class="sxs-lookup"><span data-stu-id="c175f-490">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="c175f-491">ドメイン モデルに動作が欠如していて、システムの状態を表しているだけの場合は、[貧血症のモデル](https://deviq.com/anemic-model/)と呼ばれ、DDD では望ましくないことです。</span><span class="sxs-lookup"><span data-stu-id="c175f-491">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](https://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="c175f-492">これらのモデルの種類に加えて、通常、DDD ではさまざまなパターンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-492">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

- <span data-ttu-id="c175f-493">[リポジトリ](https://deviq.com/repository-pattern/)は、永続化の詳細を抽象化します。</span><span class="sxs-lookup"><span data-stu-id="c175f-493">[Repository](https://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

- <span data-ttu-id="c175f-494">[ファクトリ](https://en.wikipedia.org/wiki/Factory_method_pattern)は、複雑なオブジェクトの作成をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="c175f-494">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

- <span data-ttu-id="c175f-495">[サービス](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/)は、複雑な動作やインフラストラクチャの実装の詳細をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="c175f-495">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

- <span data-ttu-id="c175f-496">[コマンド](https://en.wikipedia.org/wiki/Command_pattern)は、コマンドの発行とコマンド自体の実行を切り離します。</span><span class="sxs-lookup"><span data-stu-id="c175f-496">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

- <span data-ttu-id="c175f-497">[仕様](https://deviq.com/specification-pattern/)は、クエリの詳細をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="c175f-497">[Specification](https://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="c175f-498">また、DDD では、疎結合、カプセル化、単体テストを使って簡単に検証できるコードに対応するため、前に説明したクリーン アーキテクチャを使うことも推奨されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-498">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="c175f-499">DDD を適用する必要がある場合</span><span class="sxs-lookup"><span data-stu-id="c175f-499">When should you apply DDD</span></span>

<span data-ttu-id="c175f-500">DDD は、(技術的だけでなく) ビジネス的にも非常に複雑な大規模アプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="c175f-500">DDD is well suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="c175f-501">アプリケーションでは、ドメイン専門家の知識が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c175f-501">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="c175f-502">ドメイン モデル自体にも重要な動作が存在する必要があり、データ ストアからさまざまなレコードの現在の状態を単に取得するだけでなく、ビジネス ルールや相互作用を表します。</span><span class="sxs-lookup"><span data-stu-id="c175f-502">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="c175f-503">DDD を適用してはならない場合</span><span class="sxs-lookup"><span data-stu-id="c175f-503">When shouldn't you apply DDD</span></span>

<span data-ttu-id="c175f-504">DDD では、モデリング、アーキテクチャ、コミュニケーションへの投資が伴い、小規模なアプリケーションや基本的に CRUD (作成/読み取り/更新/削除) だけのアプリケーションでは正当化されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-504">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="c175f-505">アプリケーション開発のアプローチに DDD を選んだ場合でも、ドメインに動作を持たない貧血症のモデルがあることがわかったときは、アプローチの再考が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-505">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="c175f-506">アプリケーションで DDD を使う必要がないか、またはデータベースやユーザー インターフェイスではなくドメイン モデルにビジネス ロジックをカプセル化するためのアプリケーションのリファクタリングにサポートが必要な可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-506">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="c175f-507">ハイブリッド アプローチでは、アプリケーションのトランザクション部分やさらに複雑な部分にだけ DDD を使い、アプリケーションの簡単な CRUD 部分や読み取り専用の部分には使わないようにします。</span><span class="sxs-lookup"><span data-stu-id="c175f-507">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="c175f-508">たとえば、レポートを表示したり、ダッシュボードにデータを視覚化したりするためにデータをクエリする場合、集約を制約する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-508">For instance, you don't need the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="c175f-509">このような要件に対しては、独立したシンプルな読み取りモデルでまったく問題ありません。</span><span class="sxs-lookup"><span data-stu-id="c175f-509">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="c175f-510">参照 – ドメイン駆動設計</span><span class="sxs-lookup"><span data-stu-id="c175f-510">References – Domain-Driven Design</span></span>
>
> - <span data-ttu-id="c175f-511">**わかりやすい英語での DDD (StackOverflow の回答)** </span><span class="sxs-lookup"><span data-stu-id="c175f-511">**DDD in Plain English (StackOverflow Answer)**</span></span>\
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a><span data-ttu-id="c175f-512">配置</span><span class="sxs-lookup"><span data-stu-id="c175f-512">Deployment</span></span>

<span data-ttu-id="c175f-513">ホストされる場所に関係なく、ASP.NET Core アプリケーションを展開するプロセスには複数のステップがあります。</span><span class="sxs-lookup"><span data-stu-id="c175f-513">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="c175f-514">最初のステップであるアプリケーションの発行は、`dotnet publish` CLI コマンドを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-514">The first step is to publish the application, which can be done using the `dotnet publish` CLI command.</span></span> <span data-ttu-id="c175f-515">このステップでは、アプリケーションがコンパイルされて、アプリケーションの実行に必要なすべてのファイルが指定したフォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-515">This step will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="c175f-516">Visual Studio から展開する場合、このステップは自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-516">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="c175f-517">publish フォルダーには、アプリケーションとその依存関係の .exe ファイルと .dll ファイルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-517">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="c175f-518">自己充足型のアプリケーションには、.NET ランタイムのバージョンも含まれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-518">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="c175f-519">ASP.NET Core アプリケーションには、構成ファイル、静的クライアント資産、MVC ビューも含まれます。</span><span class="sxs-lookup"><span data-stu-id="c175f-519">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="c175f-520">ASP.NET Core アプリケーションはコンソール アプリケーションであり、サーバーの起動時、およびアプリケーション (またはサーバー) がクラッシュした場合の再起動時に、起動される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-520">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="c175f-521">プロセス マネージャーを使って、このプロセスを自動化できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-521">A process manager can be used to automate this process.</span></span> <span data-ttu-id="c175f-522">ASP.NET Core の最も一般的なプロセス マネージャーは、Linux の場合は Nginx と Apache、Windows の場合は IIS と Windows Service です。</span><span class="sxs-lookup"><span data-stu-id="c175f-522">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="c175f-523">プロセス マネージャーに加え、ASP.NET Core アプリケーションでは、リバース プロキシ サーバーも使用できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-523">In addition to a process manager, ASP.NET Core applications may use a reverse proxy server.</span></span> <span data-ttu-id="c175f-524">リバース プロキシ サーバーはインターネットから HTTP 要求を受け取り、事前にいくつかの処理を行ってから Kestrel に転送します。</span><span class="sxs-lookup"><span data-stu-id="c175f-524">A reverse proxy server receives HTTP requests from the Internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="c175f-525">リバース プロキシ サーバーによって、アプリケーションにセキュリティ層が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-525">Reverse proxy servers provide a layer of security for the application.</span></span> <span data-ttu-id="c175f-526">また、Kestrel は同じポートでの複数アプリケーションのホストもサポートしていないので、ホスト ヘッダーなどの手法を使って同じポートと IP アドレスで複数のアプリケーションをホストすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c175f-526">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![インターネットに対する Kestrel](./media/image7-5.png)

<span data-ttu-id="c175f-528">**図 7-5**。</span><span class="sxs-lookup"><span data-stu-id="c175f-528">**Figure 7-5**.</span></span> <span data-ttu-id="c175f-529">リバース プロキシ サーバーの背後の Kestrel でホストされている ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c175f-529">ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="c175f-530">リバース プロキシが役に立つもう 1 つのシナリオは、SSL/HTTPS を使って複数のアプリケーションをセキュリティ保護する場合です。</span><span class="sxs-lookup"><span data-stu-id="c175f-530">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="c175f-531">この場合、リバース プロキシでは SSL だけを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c175f-531">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="c175f-532">リバース プロキシ サーバーと Kestrel の間の通信は、HTTP で行われます (図 7-6 を参照)。</span><span class="sxs-lookup"><span data-stu-id="c175f-532">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![HTTPS で保護されたリバース プロキシ サーバーの背後でホストされている ASP.NET](./media/image7-6.png)

<span data-ttu-id="c175f-534">**図 7-6**。</span><span class="sxs-lookup"><span data-stu-id="c175f-534">**Figure 7-6**.</span></span> <span data-ttu-id="c175f-535">HTTPS で保護されたリバース プロキシ サーバーの背後でホストされている ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c175f-535">ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="c175f-536">急速に普及しているアプローチは ASP.NET Core アプリケーションを Docker コンテナーでホストする方法で、ローカルにホストしたり、クラウド ベースのホスト用に Azure に展開したりできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-536">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="c175f-537">Docker コンテナーは、Kestrel で実行されるアプリケーションのコードを格納することができ、上記のように、リバース プロキシ サーバーの背後に展開されます。</span><span class="sxs-lookup"><span data-stu-id="c175f-537">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="c175f-538">Azure でアプリケーションをホストしている場合は、専用の仮想アプライアンスとして Microsoft Azure Application Gateway を使って、複数のサービスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="c175f-538">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="c175f-539">個々のアプリケーションに対するリバース プロキシとして動作するだけでなく、Application Gateway は次の機能を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="c175f-539">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

- <span data-ttu-id="c175f-540">HTTP の負荷分散</span><span class="sxs-lookup"><span data-stu-id="c175f-540">HTTP load balancing</span></span>

- <span data-ttu-id="c175f-541">SSL のオフロード (インターネットに対する SSL のみ)</span><span class="sxs-lookup"><span data-stu-id="c175f-541">SSL offload (SSL only to Internet)</span></span>

- <span data-ttu-id="c175f-542">エンド ツー エンドの SSL</span><span class="sxs-lookup"><span data-stu-id="c175f-542">End to End SSL</span></span>

- <span data-ttu-id="c175f-543">複数サイトのルーティング (最大 20 個のサイトを 1 つの Application Gateway に統合)</span><span class="sxs-lookup"><span data-stu-id="c175f-543">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

- <span data-ttu-id="c175f-544">Web アプリケーション ファイアウォール</span><span class="sxs-lookup"><span data-stu-id="c175f-544">Web application firewall</span></span>

- <span data-ttu-id="c175f-545">WebSocket のサポート</span><span class="sxs-lookup"><span data-stu-id="c175f-545">Websocket support</span></span>

- <span data-ttu-id="c175f-546">高度な診断</span><span class="sxs-lookup"><span data-stu-id="c175f-546">Advanced diagnostics</span></span>

<span data-ttu-id="c175f-547">_Azure のデプロイ オプションについては、[10 章](development-process-for-azure.md)で説明します。_</span><span class="sxs-lookup"><span data-stu-id="c175f-547">_Learn more about Azure deployment options in [Chapter 10](development-process-for-azure.md)._</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="c175f-548">参照 – 展開</span><span class="sxs-lookup"><span data-stu-id="c175f-548">References – Deployment</span></span>
>
> - <span data-ttu-id="c175f-549">**ホスティングとデプロイの概要**</span><span class="sxs-lookup"><span data-stu-id="c175f-549">**Hosting and Deployment Overview**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - <span data-ttu-id="c175f-550">**Kestrel とリバース プロキシを使用するタイミング**</span><span class="sxs-lookup"><span data-stu-id="c175f-550">**When to use Kestrel with a reverse proxy**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - <span data-ttu-id="c175f-551">**Docker で ASP.NET Core アプリをホストする**</span><span class="sxs-lookup"><span data-stu-id="c175f-551">**Host ASP.NET Core apps in Docker**</span></span>\
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - <span data-ttu-id="c175f-552">**Azure Application Gateway の概要**</span><span class="sxs-lookup"><span data-stu-id="c175f-552">**Introducing Azure Application Gateway**</span></span>\
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
><span data-ttu-id="c175f-553">[前へ](common-client-side-web-technologies.md)
>[次へ](work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="c175f-553">[Previous](common-client-side-web-technologies.md)
[Next](work-with-data-in-asp-net-core-apps.md)</span></span>
