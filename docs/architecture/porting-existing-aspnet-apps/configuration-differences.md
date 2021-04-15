---
title: ASP.NET MVC と ASP.NET Core の構成の相違点
description: 構成値の格納と読み取りの方法は、ASP.NET と ASP.NET Core の間で大きく変わりました。 ここでは、その詳細および ASP.NET から ASP.NET Core に構成を移行する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 3d721c028b1e760a6227855451e2194d9e471a58
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122951"
---
# <a name="configuration-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="00620-104">ASP.NET MVC と ASP.NET Core の構成の相違点</span><span class="sxs-lookup"><span data-stu-id="00620-104">Configuration differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="00620-105">構成値の格納と読み取りの方法は、ASP.NET と ASP.NET Core の間で大きく変わりました。</span><span class="sxs-lookup"><span data-stu-id="00620-105">How configuration values are stored and read changed dramatically between ASP.NET and ASP.NET Core.</span></span>

## <a name="aspnet-mvc-configuration"></a><span data-ttu-id="00620-106">ASP.NET MVC の構成</span><span class="sxs-lookup"><span data-stu-id="00620-106">ASP.NET MVC configuration</span></span>

<span data-ttu-id="00620-107">ASP.NET アプリでは、構成はアプリ フォルダー内の組み込みの .NET 構成ファイルである *web.config* とサーバー上の *machine.config* を使用します。</span><span class="sxs-lookup"><span data-stu-id="00620-107">In ASP.NET apps, configuration uses the built-in .NET configuration files, *web.config* in the app folder and *machine.config* on the server.</span></span> <span data-ttu-id="00620-108">ほとんどの ASP.NET MVC アプリおよび Web API アプリの設定は、構成ファイルの `appSettings` 要素または `connectionStrings` 要素に格納されます。</span><span class="sxs-lookup"><span data-stu-id="00620-108">Most ASP.NET MVC and Web API apps store their settings in the configuration file's `appSettings` or `connectionStrings` elements.</span></span> <span data-ttu-id="00620-109">一部のアプリは、設定クラスにマップできるカスタム構成セクションも使用します。</span><span class="sxs-lookup"><span data-stu-id="00620-109">Some also use custom configuration sections that can be mapped to a settings class.</span></span>

<span data-ttu-id="00620-110">.NET Framework アプリ内の構成には、`System.Configuration.ConfigurationManager` クラスを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="00620-110">Configuration in a .NET Framework app is accessed using the `System.Configuration.ConfigurationManager` class.</span></span> <span data-ttu-id="00620-111">残念ながら、このクラスが提供するのは構成要素への静的アクセスです。</span><span class="sxs-lookup"><span data-stu-id="00620-111">Unfortunately, this class provides static access to the configuration elements.</span></span> <span data-ttu-id="00620-112">そのため、構成設定へのアクセスを抽象化したり、必要に応じて構成設定を挿入したりする傾向のある ASP.NET MVC アプリはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="00620-112">As a result, very few ASP.NET MVC apps tend to abstract access to their configuration settings or inject them where needed.</span></span> <span data-ttu-id="00620-113">代わりに、ほとんどの .NET Framework アプリは、アプリが設定を使用する必要のあるすべての場所で構成システムに直接アクセスする傾向があります。</span><span class="sxs-lookup"><span data-stu-id="00620-113">Instead, most .NET Framework apps tend to directly access the configuration system anywhere the app needs to use a setting.</span></span>

<span data-ttu-id="00620-114">一般的な ASP.NET MVC の構成アクセスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="00620-114">Typical ASP.NET MVC configuration access:</span></span>

```csharp
string connectionString =
    ConfigurationManager.ConnectionStrings["DefaultConnection"]
        .ConnectionString;
```

## <a name="aspnet-core-configuration"></a><span data-ttu-id="00620-115">ASP.NET Core 構成</span><span class="sxs-lookup"><span data-stu-id="00620-115">ASP.NET Core configuration</span></span>

<span data-ttu-id="00620-116">ASP.NET Core アプリでは、構成自体を構成できます。</span><span class="sxs-lookup"><span data-stu-id="00620-116">In ASP.NET Core apps, configuration is, itself, configurable.</span></span> <span data-ttu-id="00620-117">ただし、ほとんどのアプリでは、標準のプロジェクト テンプレートの一部として提供される既定値のセットと、それらで使用される `ConfigureWebHostDefaults` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="00620-117">However, most apps use a set of defaults provided as part of the standard project templates and the `ConfigureWebHostDefaults` method used in them.</span></span> <span data-ttu-id="00620-118">既定の設定では、JSON 形式のファイルを使用します。これにより、基本ファイル *appsettings.json* 内の設定を *appsettings.Development.json* などの環境固有のファイルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="00620-118">The default settings use JSON formatted files, with the ability to override settings in the base *appsettings.json* file with environment-specific files like *appsettings.Development.json*.</span></span> <span data-ttu-id="00620-119">また、既定の構成システムでは、同じ名前付き設定用の環境変数を使用して、ファイル ベースのすべての設定がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="00620-119">Additionally, the default configuration system further overrides all file-based settings with any environment variable that exists for the same named setting.</span></span> <span data-ttu-id="00620-120">構成ファイルのデプロイによって運用環境の重要な構成設定が誤って上書きされるかどうかを心配する必要がなくなるため、これは多くのシナリオ (特にホスティング環境へのデプロイ時) に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="00620-120">This is useful in many scenarios and is especially useful when deploying to a hosting environment, since it eliminates the need to worry about whether deploying configuration files will accidentally overwrite important production configuration settings.</span></span> <span data-ttu-id="00620-121">構成値をコマンド ライン引数として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="00620-121">Configuration values can also be provided as command line arguments.</span></span>

<span data-ttu-id="00620-122">.NET Core では、さまざまな方法で構成値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="00620-122">Accessing configuration values can be done in many ways in .NET Core.</span></span> <span data-ttu-id="00620-123">依存関係の挿入が .NET Core に組み込まれているため、通常は、構成値を必要とするクラスに挿入されるインターフェイスを使用してその値にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="00620-123">Because dependency injection is built into .NET Core, configuration values are generally accessed through an interface that is injected into classes that need them.</span></span> <span data-ttu-id="00620-124">その際、<xref:Microsoft.Extensions.Configuration.IConfiguration> などのインターフェイスを渡す場合がありますが、通常は[オプション パターン](/aspnet/core/fundamentals/configuration/options)を使用して、クラスに必要な設定だけを渡すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="00620-124">This can involve passing a interface like <xref:Microsoft.Extensions.Configuration.IConfiguration>, but usually it's better to pass just the settings required by the class using the [options pattern](/aspnet/core/fundamentals/configuration/options).</span></span>

<span data-ttu-id="00620-125">図 2-2 は、`IConfiguration` を Razor ページに渡し、そこから構成設定にアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="00620-125">Figure 2-2 shows how to pass `IConfiguration` into a Razor Page and access configuration settings from it:</span></span>

```csharp
using Microsoft.Extensions.Configuration;

public class TestModel : PageModel
{
    private readonly IConfiguration _configuration;

    public TestModel(IConfiguration configuration)
    {
        _configuration= configuration;
    }

    public ContentResult OnGet()
    {
        var myKeyValue = _configuration["MyKey"];

        // ...
    }
}
```

<span data-ttu-id="00620-126">**図 2-2**</span><span class="sxs-lookup"><span data-stu-id="00620-126">**Figure 2-2.**</span></span> <span data-ttu-id="00620-127">`IConfiguration` を使用した構成値へのアクセス。</span><span class="sxs-lookup"><span data-stu-id="00620-127">Accessing configuration values with `IConfiguration`.</span></span>

<span data-ttu-id="00620-128">[オプション パターン](/dotnet/core/extensions/options)を使用した設定へのアクセスも同様ですが、図 2-3 に示すように、厳密に型指定されており、使用するクラスで必要な設定に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="00620-128">Using the [options pattern](/dotnet/core/extensions/options), settings access is similar but is strongly typed and more specific to the setting(s) needed by the consuming class, as Figure 2-3 demonstrates.</span></span>

```csharp
public class PositionOptions
{
    public const string Position = nameof(Position);

    public string Title { get; set; }
    public string Name { get; set; }
}

public class Test2Model : PageModel
{
    private readonly PositionOptions _options;

    public Test2Model(IOptions<PositionOptions> options)
    {
        _options = options.Value;
    }

    public ContentResult OnGet()
    {
        return Content($"Title: {_options.Title}\nName: {_options.Name}");
    }
}
```

<span data-ttu-id="00620-129">**図 2-3**</span><span class="sxs-lookup"><span data-stu-id="00620-129">**Figure 2-3.**</span></span> <span data-ttu-id="00620-130">ASP.NET Core でのオプション パターンの使用。</span><span class="sxs-lookup"><span data-stu-id="00620-130">Using the options pattern in ASP.NET Core.</span></span>

<span data-ttu-id="00620-131">オプション パターンを機能させるには、アプリの起動時にオプションの型を `ConfigureServices` で構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="00620-131">For the options pattern to work, the options type must be configured in `ConfigureServices` when the app starts up:</span></span>

```csharp
// required in ConfigureServices
services.Configure<PositionOptions>(Configuration.GetSection(PositionOptions.Position));
```

## <a name="migrate-configuration"></a><span data-ttu-id="00620-132">構成の移行</span><span class="sxs-lookup"><span data-stu-id="00620-132">Migrate configuration</span></span>

<span data-ttu-id="00620-133">アプリの構成設定を .NET Framework から .NET Core に移植する方法を検討する場合は、最初の手順として、使用されているすべての構成設定を特定します。</span><span class="sxs-lookup"><span data-stu-id="00620-133">When considering how to port an app's configuration settings from .NET Framework to .NET Core, the first step is to identify all of the configuration settings that are being used.</span></span> <span data-ttu-id="00620-134">これらのほとんどは、アプリのルート フォルダーにある *web.config* ファイルに含まれていますが、一部のアプリでは共有ファイル *machine.config* にも設定が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="00620-134">Most of these will be in the *web.config* file in the app's root folder, but some apps expect settings to be found in the shared *machine.config* file as well.</span></span> <span data-ttu-id="00620-135">これらの設定には、`appSettings` 要素の要素、`connectionStrings` 要素、および任意のカスタム構成要素も含まれます。</span><span class="sxs-lookup"><span data-stu-id="00620-135">These settings will include elements of the `appSettings` element, the `connectionStrings` element, and any custom configuration elements as well.</span></span> <span data-ttu-id="00620-136">.NET Core では、これらのすべての設定は通常 *appsettings.js* ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="00620-136">In .NET Core, all of these settings are typically stored in the *appsettings.json* file.</span></span>

<span data-ttu-id="00620-137">構成ファイル内のすべての設定がカタログ化されたら、次の手順では、アプリ自体で設定を使用する場所と方法を特定します。</span><span class="sxs-lookup"><span data-stu-id="00620-137">Once all settings in the config files have been cataloged, the next step should be to identify where and how the settings are used in the app itself.</span></span> <span data-ttu-id="00620-138">一部の設定が使用されていない場合は、移行から除外される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00620-138">If some settings aren't being used, these can probably be omitted from the migration.</span></span> <span data-ttu-id="00620-139">コードの移行時に設定の漏れが発生しないように、それぞれの設定が使用されているすべての場所に注意してください。</span><span class="sxs-lookup"><span data-stu-id="00620-139">For each setting, note all of the places it's being used so you can be sure you don't miss any when you migrate the code.</span></span>

<span data-ttu-id="00620-140">ASP.NET アプリを引き続き維持する場合は、`ConfigurationManager` への静的参照を回避し、それらをインターフェイスを使用したアクセスに置き換えると役立つ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00620-140">If you're still maintaining the ASP.NET app, it may be helpful to avoid static references to `ConfigurationManager` and replace them with access through interfaces.</span></span> <span data-ttu-id="00620-141">これにより、ASP.NET Core の構成システムへの移行が容易になります。</span><span class="sxs-lookup"><span data-stu-id="00620-141">This will ease the transition to ASP.NET Core's configuration system.</span></span> <span data-ttu-id="00620-142">一般に、外部リソースへの静的アクセスでは、コードのテストと保守が困難になります。そのため、アプリがこのパターンに従っている可能性のある他の場所に注意してください。</span><span class="sxs-lookup"><span data-stu-id="00620-142">In general, static access to external resources makes code harder to test and maintain, so be on the lookout for anywhere else the app may be following this pattern.</span></span>

## <a name="references"></a><span data-ttu-id="00620-143">References</span><span class="sxs-lookup"><span data-stu-id="00620-143">References</span></span>

- [<span data-ttu-id="00620-144">ASP.NET Core での構成</span><span class="sxs-lookup"><span data-stu-id="00620-144">Configuration in ASP.NET Core</span></span>](/aspnet/core/fundamentals/configuration/)
- [<span data-ttu-id="00620-145">ASP.NET Core のオプション パターン</span><span class="sxs-lookup"><span data-stu-id="00620-145">Options pattern in ASP.NET Core</span></span>](/aspnet/core/fundamentals/configuration/options)
- [<span data-ttu-id="00620-146">構成を ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="00620-146">Migrate configuration to ASP.NET Core</span></span>](/aspnet/core/migration/configuration)
- [<span data-ttu-id="00620-147">Refactoring Static Config Access (静的構成アクセスのリファクタリング)</span><span class="sxs-lookup"><span data-stu-id="00620-147">Refactoring Static Config Access</span></span>](https://ardalis.com/refactoring-static-config-access/)

>[!div class="step-by-step"]
><span data-ttu-id="00620-148">[前へ](middleware-modules-handlers.md)
>[次へ](routing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="00620-148">[Previous](middleware-modules-handlers.md)
[Next](routing-differences.md)</span></span>
