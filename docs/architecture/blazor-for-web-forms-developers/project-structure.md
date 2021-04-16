---
title: Blazor アプリのプロジェクト構造
description: ASP.NET Web Forms のプロジェクト構造と Blazor プロジェクトを比較する方法について説明します。
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: ba7113c88db728f30812821deaf7c06a80663d1f
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "98189090"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="21691-103">Blazor アプリのプロジェクト構造</span><span class="sxs-lookup"><span data-stu-id="21691-103">Project structure for Blazor apps</span></span>

<span data-ttu-id="21691-104">プロジェクト構造が大きく異なるにもかかわらず、ASP.NET Web Forms と Blazor には共通するさまざまな概念があります。</span><span class="sxs-lookup"><span data-stu-id="21691-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="21691-105">ここでは、Blazor プロジェクトの構造を観察し、それを ASP.NET Web Forms プロジェクトと比較します。</span><span class="sxs-lookup"><span data-stu-id="21691-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="21691-106">最初の Blazor アプリを作成するには、[Blazor の開始手順](/aspnet/core/blazor/get-started)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="21691-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="21691-107">指示に従って、ASP.NET Core でホストされている Blazor サーバー アプリまたは Blazor WebAssembly アプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="21691-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="21691-108">ホスティングモデル固有のロジックを除き、両方のプロジェクトのコードはほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="21691-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="21691-109">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="21691-109">Project file</span></span>

<span data-ttu-id="21691-110">Blazor サーバー アプリは .NET プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="21691-110">Blazor Server apps are .NET projects.</span></span> <span data-ttu-id="21691-111">Blazor サーバー アプリのプロジェクト ファイルは、概ね次のような簡単なものです。</span><span class="sxs-lookup"><span data-stu-id="21691-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="21691-112">Blazor WebAssembly アプリのプロジェクト ファイルは少し複雑になります (正確なバージョン番号は異なる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="21691-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="21691-113">Blazor WebAssembly プロジェクトは、WebAssembly ベースの .NET ランタイム上のブラウザーで実行されるため、`Microsoft.NET.Sdk.Web` sdk ではなく `Microsoft.NET.Sdk.BlazorWebAssembly` をターゲットとします。</span><span class="sxs-lookup"><span data-stu-id="21691-113">Blazor WebAssembly project targets `Microsoft.NET.Sdk.BlazorWebAssembly` instead of `Microsoft.NET.Sdk.Web` sdk because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="21691-114">サーバーや開発者コンピューター上で行うように、.NET を Web ブラウザーにインストールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="21691-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="21691-115">その結果、プロジェクトでは個別のパッケージ参照を使用して、Blazor フレームワークが参照されます。</span><span class="sxs-lookup"><span data-stu-id="21691-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="21691-116">これに対し、既定の ASP.NET Web Forms プロジェクトでは、 *.csproj* ファイルに約 300 行の XML が含まれており、そのほとんどはプロジェクト内のさまざまなコードおよびコンテンツ ファイルを明示的に示すものです。</span><span class="sxs-lookup"><span data-stu-id="21691-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="21691-117">`.NET 5` のリリースにより、`Blazor Server` および `Blazor WebAssembly` のアプリは統合された 1 つのランタイムを簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="21691-117">With the release of `.NET 5` both `Blazor Server` and `Blazor WebAssembly` app can easily share one unified runtime.</span></span>

<span data-ttu-id="21691-118">これらはサポートされていますが、個々のアセンブリ参照は .NET プロジェクトではあまり一般的ではありません。</span><span class="sxs-lookup"><span data-stu-id="21691-118">Although they're supported, individual assembly references are less common in .NET projects.</span></span> <span data-ttu-id="21691-119">ほとんどのプロジェクトの依存関係は、NuGet パッケージ参照として処理されます。</span><span class="sxs-lookup"><span data-stu-id="21691-119">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="21691-120">.NET プロジェクトの最上位レベルのパッケージの依存関係のみ参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21691-120">You only need to reference top-level package dependencies in .NET projects.</span></span> <span data-ttu-id="21691-121">推移的な依存関係は自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="21691-121">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="21691-122">ASP.NET Web Forms プロジェクトでよく見られる *packages.config* ファイルを使用してパッケージを参照するのではなく、`<PackageReference>` 要素を使用してパッケージ参照をプロジェクトファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="21691-122">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="21691-123">エントリ ポイント</span><span class="sxs-lookup"><span data-stu-id="21691-123">Entry point</span></span>

<span data-ttu-id="21691-124">Blazor サーバー アプリのエントリ ポイントは、コンソール アプリで見られるように *Program.cs* ファイルで定義されます。</span><span class="sxs-lookup"><span data-stu-id="21691-124">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="21691-125">アプリを実行すると、Web アプリに固有の既定値を使用して Web ホスト インスタンスが作成されて実行されます。</span><span class="sxs-lookup"><span data-stu-id="21691-125">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="21691-126">Web ホストは Blazor サーバー アプリのライフサイクルを管理し、ホストレベルのサービスを設定します。</span><span class="sxs-lookup"><span data-stu-id="21691-126">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="21691-127">このようなサービスの例としては、構成、ログ記録、依存関係の注入、HTTP サーバーなどがあります。</span><span class="sxs-lookup"><span data-stu-id="21691-127">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="21691-128">このコードはほとんどが定型であり、変更されることはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="21691-128">This code is mostly boilerplate and is often left unchanged.</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

<span data-ttu-id="21691-129">Blazor WebAssembly アプリでは、*Program.cs* でエントリ ポイントが定義されます。</span><span class="sxs-lookup"><span data-stu-id="21691-129">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="21691-130">コードは少し異なります。</span><span class="sxs-lookup"><span data-stu-id="21691-130">The code looks slightly different.</span></span> <span data-ttu-id="21691-131">コードは、同じホストレベルのサービスをアプリに提供するようにアプリ ホストを設定するという点で似ています。</span><span class="sxs-lookup"><span data-stu-id="21691-131">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="21691-132">ただし、WebAssembly アプリ ホストはブラウザーで直接実行されるため、HTTP サーバーを設定しません。</span><span class="sxs-lookup"><span data-stu-id="21691-132">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="21691-133">Blazor アプリには、アプリのスタートアップ ロジックを定義するための *global.asax* ファイルではなく `Startup` クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="21691-133">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="21691-134">`Startup` クラスはアプリとアプリ固有のサービスを構成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="21691-134">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="21691-135">Blazor サーバーアプリでは、`Startup` クラスを使用して、クライアント ブラウザーとサーバーの間で Blazor によって使用されるリアルタイム接続のエンドポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="21691-135">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="21691-136">Blazor WebAssembly アプリでは、`Startup` クラスによって、アプリのルート コンポーネントと、それらをレンダリングする場所が定義されます。</span><span class="sxs-lookup"><span data-stu-id="21691-136">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="21691-137">`Startup` クラスについては、「[アプリの起動](./app-startup.md)」セクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="21691-137">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="21691-138">静的ファイル</span><span class="sxs-lookup"><span data-stu-id="21691-138">Static files</span></span>

<span data-ttu-id="21691-139">ASP.NET Web Forms プロジェクトとは異なり、Blazor プロジェクト内のすべてのファイルを静的ファイルとして要求できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="21691-139">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="21691-140">*wwwroot* フォルダー内のファイルのみが Web アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="21691-140">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="21691-141">このフォルダーは、アプリの "Web ルート" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="21691-141">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="21691-142">アプリの Web ルート以外のものは、web アドレスを指定 "*できません*"。</span><span class="sxs-lookup"><span data-stu-id="21691-142">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="21691-143">このセットアップでは、プロジェクト ファイルが Web 経由で誤って公開されないようにするための追加のセキュリティレベルが提供されます。</span><span class="sxs-lookup"><span data-stu-id="21691-143">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="21691-144">構成</span><span class="sxs-lookup"><span data-stu-id="21691-144">Configuration</span></span>

<span data-ttu-id="21691-145">ASP.NET Web Forms アプリの構成は、通常 1 つ以上の *web.config* ファイルを使用して処理されます。</span><span class="sxs-lookup"><span data-stu-id="21691-145">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="21691-146">Blazor アプリには通常、*web.config* ファイルがありません。</span><span class="sxs-lookup"><span data-stu-id="21691-146">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="21691-147">ファイルがある場合、ファイルは IIS でホストされている場合に IIS 固有の設定を構成するためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="21691-147">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="21691-148">その代わりに、Blazor サーバー アプリは ASP.NET Core 構成の抽象化を使用します (Blazor WebAssembly アプリでは現在同じ構成の抽象化はサポートされていませんが、将来追加される機能である可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="21691-148">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="21691-149">たとえば、既定の Blazor サーバー アプリでは、一部の設定が *appsettings.json* に格納されます。</span><span class="sxs-lookup"><span data-stu-id="21691-149">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="21691-150">ASP.NET Core プロジェクトの構成の詳細については、[構成](./config.md)セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="21691-150">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="21691-151">Razor のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="21691-151">Razor components</span></span>

<span data-ttu-id="21691-152">Blazor プロジェクト内のほとんどのファイルは *.razor* ファイルです。</span><span class="sxs-lookup"><span data-stu-id="21691-152">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="21691-153">Razor は、Web UI を動的に生成するために使用される HTML および C# に基づくテンプレート言語です。</span><span class="sxs-lookup"><span data-stu-id="21691-153">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="21691-154">この *.razor* ファイルは、アプリの UI を構成するコンポーネントを定義します。</span><span class="sxs-lookup"><span data-stu-id="21691-154">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="21691-155">コンポーネントの大半は、Blazor サーバーと Blazor WebAssembly アプリの両方で同一です。</span><span class="sxs-lookup"><span data-stu-id="21691-155">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="21691-156">Blazor のコンポーネントは、ASP.NET Web Forms のユーザー コントロールに似ています。</span><span class="sxs-lookup"><span data-stu-id="21691-156">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="21691-157">各 Razor コンポーネント ファイルは、プロジェクトのビルド時に .NET クラスにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="21691-157">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="21691-158">生成されたクラスは、コンポーネントの状態、レンダリング ロジック、ライフサイクル メソッド、イベント ハンドラー、およびその他のロジックをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="21691-158">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="21691-159">「[Blazor を使用して再利用可能な UI コンポーネントを構築する](./components.md)」セクションで、コンポーネントの作成について見ていきます。</span><span class="sxs-lookup"><span data-stu-id="21691-159">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="21691-160">*_Imports.razor* ファイルは Razor コンポーネント ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="21691-160">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="21691-161">代わりに、これらは同じフォルダーおよびそのサブフォルダー内の他の *.razor* ファイルにインポートする Razor ディレクティブのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="21691-161">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="21691-162">たとえば、 *_Imports.razor* ファイルは、一般的に使用される名前空間の `using` ディレクティブを追加する従来の方法です。</span><span class="sxs-lookup"><span data-stu-id="21691-162">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a><span data-ttu-id="21691-163">ページ</span><span class="sxs-lookup"><span data-stu-id="21691-163">Pages</span></span>

<span data-ttu-id="21691-164">Blazor アプリ内のページはどこにあるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="21691-164">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="21691-165">Blazor では、ASP.NET Web Forms アプリの *.aspx* ファイルのように、アドレス指定可能なページに対して個別のファイル拡張子は定義されません。</span><span class="sxs-lookup"><span data-stu-id="21691-165">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="21691-166">代わりに、ページはコンポーネントにルートを割り当てることによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="21691-166">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="21691-167">ルートは通常、`@page` Razor ディレクティブを使用して割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="21691-167">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="21691-168">たとえば、*Pages/Counter.razor* ファイルで作成された `Counter` コンポーネントは、次のルートを定義します。</span><span class="sxs-lookup"><span data-stu-id="21691-168">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="21691-169">Blazor でのルーティングは、サーバー側ではなくクライアント側で処理されます。</span><span class="sxs-lookup"><span data-stu-id="21691-169">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="21691-170">ユーザーがブラウザーで移動すると、Blazor はナビゲーションをインターセプトし、一致するルートを使用してコンポーネントをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="21691-170">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="21691-171">コンポーネントのルートは、 *.aspx* ページのように、コンポーネントのファイルの場所によって現在推測されていません。</span><span class="sxs-lookup"><span data-stu-id="21691-171">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="21691-172">この機能は、今後追加される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="21691-172">This feature may be added in the future.</span></span> <span data-ttu-id="21691-173">各ルートはコンポーネント上で明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21691-173">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="21691-174">ルーティング可能なコンポーネントを *Pages* フォルダーに格納することは、特別な意味を持たず、単なる慣例です。</span><span class="sxs-lookup"><span data-stu-id="21691-174">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="21691-175">Blazor でのルーティングの詳細については、「[ページ、ルーティング、レイアウト](./pages-routing-layouts.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="21691-175">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="21691-176">レイアウト</span><span class="sxs-lookup"><span data-stu-id="21691-176">Layout</span></span>

<span data-ttu-id="21691-177">ASP.NET Web Forms アプリでは、共通ページ レイアウトはマスター ページ (*Site.Master*) を使用して処理されます。</span><span class="sxs-lookup"><span data-stu-id="21691-177">In ASP.NET Web Forms apps, a common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="21691-178">Blazor アプリでは、ページ レイアウトはレイアウト コンポーネント (*Shared/MainLayout.razor*) を使用して処理されます。</span><span class="sxs-lookup"><span data-stu-id="21691-178">In Blazor apps, the page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="21691-179">レイアウト コンポーネントの詳細については、「[ページ、ルーティング、レイアウト](./pages-routing-layouts.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="21691-179">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="21691-180">Blazor をブートストラップする</span><span class="sxs-lookup"><span data-stu-id="21691-180">Bootstrap Blazor</span></span>

<span data-ttu-id="21691-181">Blazor をブートストラップするには、アプリは次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="21691-181">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="21691-182">ページ上でルート コンポーネント (*App.Razor*) がレンダリングされる場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="21691-182">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="21691-183">対応する Blazor フレームワーク スクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="21691-183">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="21691-184">Blazor サーバー アプリでは、ルート コンポーネントのホスト ページは *_Host.cshtml* ファイルに定義されています。</span><span class="sxs-lookup"><span data-stu-id="21691-184">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="21691-185">このファイルはコンポーネントではなく Razor ページを定義します。</span><span class="sxs-lookup"><span data-stu-id="21691-185">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="21691-186">Razor ページでは Razor 構文を使用して、サーバーアドレス指定可能なページを定義します。これは *.aspx* ページと非常によく似ています。</span><span class="sxs-lookup"><span data-stu-id="21691-186">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="21691-187">`Html.RenderComponentAsync<TComponent>(RenderMode)` メソッドは、ルートレベルのコンポーネントをレンダリングする場所を定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="21691-187">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="21691-188">`RenderMode` オプションは、コンポーネントをレンダリングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="21691-188">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="21691-189">次の表に、サポートされる `RenderMode` オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="21691-189">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="21691-190">オプション</span><span class="sxs-lookup"><span data-stu-id="21691-190">Option</span></span>                        |<span data-ttu-id="21691-191">説明</span><span class="sxs-lookup"><span data-stu-id="21691-191">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="21691-192">ブラウザーとの接続が確立されると、対話形式でレンダリングされます</span><span class="sxs-lookup"><span data-stu-id="21691-192">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="21691-193">最初に事前レンダリングされ、次に対話形式でレンダリングされます</span><span class="sxs-lookup"><span data-stu-id="21691-193">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="21691-194">静的コンテンツとしてレンダリングされます</span><span class="sxs-lookup"><span data-stu-id="21691-194">Rendered as static content</span></span>|

<span data-ttu-id="21691-195">*_framework/blazor.server.js* へのスクリプト参照は、サーバーとのリアルタイム接続を確立し、次にすべてのユーザー操作と UI 更新を処理します。</span><span class="sxs-lookup"><span data-stu-id="21691-195">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

<span data-ttu-id="21691-196">Blazor WebAssembly アプリでは、ホスト ページは *wwwroot/index.html* の下の単純な静的 HTML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="21691-196">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="21691-197">`<div>` という id を持つ要素 `app` は、ルート コンポーネントのレンダリング先を示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="21691-197">The `<div>` element with id named `app` is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

<span data-ttu-id="21691-198">レンダリングするルート コンポーネントは、アプリの `Program.Main` メソッドで指定され、依存関係の挿入によってサービスを登録する柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="21691-198">The root component to render is specified in the app's `Program.Main` method with the flexibility to register services through dependency injection.</span></span> <span data-ttu-id="21691-199">詳細については、「[ASP.NET Core Blazor の依存関係の挿入](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21691-199">For more information, see [ASP.NET Core Blazor dependency injection](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly).</span></span>

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a><span data-ttu-id="21691-200">ビルド出力</span><span class="sxs-lookup"><span data-stu-id="21691-200">Build output</span></span>

<span data-ttu-id="21691-201">Blazor プロジェクトをビルドされたら、すべての Razor コンポーネントとコード ファイルが 1 つのアセンブリにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="21691-201">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="21691-202">ASP.NET Web Forms プロジェクトとは異なり、Blazor は UI ロジックのランタイム コンパイルをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="21691-202">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="21691-203">アプリを実行する</span><span class="sxs-lookup"><span data-stu-id="21691-203">Run the app</span></span>

<span data-ttu-id="21691-204">Blazor サーバー アプリを実行するには、Visual Studio で `F5` を押します。</span><span class="sxs-lookup"><span data-stu-id="21691-204">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="21691-205">Blazor アプリはランタイム コンパイルをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="21691-205">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="21691-206">コードとコンポーネントのマークアップの変更結果を表示するには、デバッガーがアタッチされた状態でアプリをリビルドして再起動します。</span><span class="sxs-lookup"><span data-stu-id="21691-206">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="21691-207">デバッガーがアタッチされていない状態で実行した場合 (`Ctrl+F5`)、Visual Studio はファイルの変更を監視し、変更が行われたときにアプリを再起動します。</span><span class="sxs-lookup"><span data-stu-id="21691-207">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="21691-208">変更が行われると、ブラウザーが手動で更新されます。</span><span class="sxs-lookup"><span data-stu-id="21691-208">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="21691-209">Blazor WebAssembly アプリを実行するには、次のいずれかの方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="21691-209">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="21691-210">開発サーバーを使用して、クライアント プロジェクトを直接実行する。</span><span class="sxs-lookup"><span data-stu-id="21691-210">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="21691-211">ASP.NET Core を使用してアプリをホストするときに、サーバー プロジェクトを実行する。</span><span class="sxs-lookup"><span data-stu-id="21691-211">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="21691-212">Blazor WebAssemblyアプリは、ブラウザーと Visual Studio の両方でデバッグできます。詳細については、「[ASP.NET Core Blazor WebAssembly をデバッグする](/aspnet/core/blazor/debug)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21691-212">Blazor WebAssembly apps can be debugged in both browser and Visual Studio.See [Debug ASP.NET Core Blazor WebAssembly](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="21691-213">[前へ](hosting-models.md)
>[次へ](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="21691-213">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
