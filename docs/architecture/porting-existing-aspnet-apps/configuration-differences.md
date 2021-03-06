---
title: ASP.NET MVC と ASP.NET Core の構成の違い
description: ASP.NET と ASP.NET Core の間で、構成値の格納方法と読み取り方法が大きく変化しました。 このセクションでは、詳細と、ASP.NET から ASP.NET Core に構成を移行する方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 1e8e4d4ac408862f0216a5744476047186222304
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401395"
---
# <a name="configuration-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="d5645-104">ASP.NET MVC と ASP.NET Core の構成の違い</span><span class="sxs-lookup"><span data-stu-id="d5645-104">Configuration differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="d5645-105">ASP.NET と ASP.NET Core の間で、構成値の格納方法と読み取り方法が大きく変化しました。</span><span class="sxs-lookup"><span data-stu-id="d5645-105">How configuration values are stored and read changed dramatically between ASP.NET and ASP.NET Core.</span></span>

## <a name="aspnet-mvc-configuration"></a><span data-ttu-id="d5645-106">ASP.NET MVC の構成</span><span class="sxs-lookup"><span data-stu-id="d5645-106">ASP.NET MVC configuration</span></span>

<span data-ttu-id="d5645-107">ASP.NET apps では、構成は組み込みの .NET 構成ファイルを使用し、アプリフォルダー内の *web.config* とサーバー上の *machine.config* ます。</span><span class="sxs-lookup"><span data-stu-id="d5645-107">In ASP.NET apps, configuration uses the built-in .NET configuration files, *web.config* in the app folder and *machine.config* on the server.</span></span> <span data-ttu-id="d5645-108">ほとんどの ASP.NET MVC および Web API アプリの設定は、構成ファイルの `appSettings` 要素または要素に格納さ `connectionStrings` れます。</span><span class="sxs-lookup"><span data-stu-id="d5645-108">Most ASP.NET MVC and Web API apps store their settings in the configuration file's `appSettings` or `connectionStrings` elements.</span></span> <span data-ttu-id="d5645-109">また、設定クラスにマップできるカスタム構成セクションも使用します。</span><span class="sxs-lookup"><span data-stu-id="d5645-109">Some also use custom configuration sections that can be mapped to a settings class.</span></span>

<span data-ttu-id="d5645-110">.NET Framework アプリの構成には、クラスを使用してアクセスし `System.Configuration.ConfigurationManager` ます。</span><span class="sxs-lookup"><span data-stu-id="d5645-110">Configuration in a .NET Framework app is accessed using the `System.Configuration.ConfigurationManager` class.</span></span> <span data-ttu-id="d5645-111">残念ながら、このクラスは構成要素への静的アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d5645-111">Unfortunately, this class provides static access to the configuration elements.</span></span> <span data-ttu-id="d5645-112">その結果、ASP.NET MVC アプリは、構成設定へのアクセスを抽象化したり、必要に応じてそれらを挿入したりする傾向があります。</span><span class="sxs-lookup"><span data-stu-id="d5645-112">As a result, very few ASP.NET MVC apps tend to abstract access to their configuration settings or inject them where needed.</span></span> <span data-ttu-id="d5645-113">その代わり、ほとんどの .NET Framework アプリは、アプリが設定を使用する必要があるどこでも、構成システムに直接アクセスする傾向があります。</span><span class="sxs-lookup"><span data-stu-id="d5645-113">Instead, most .NET Framework apps tend to directly access the configuration system anywhere the app needs to use a setting.</span></span>

<span data-ttu-id="d5645-114">標準的な ASP.NET MVC 構成アクセス:</span><span class="sxs-lookup"><span data-stu-id="d5645-114">Typical ASP.NET MVC configuration access:</span></span>

```csharp
string connectionString =
    ConfigurationManager.ConnectionStrings["DefaultConnection"]
        .ConnectionString;
```

## <a name="aspnet-core-configuration"></a><span data-ttu-id="d5645-115">ASP.NET Core 構成</span><span class="sxs-lookup"><span data-stu-id="d5645-115">ASP.NET Core configuration</span></span>

<span data-ttu-id="d5645-116">ASP.NET Core アプリでは、構成がそれ自体で構成可能です。</span><span class="sxs-lookup"><span data-stu-id="d5645-116">In ASP.NET Core apps, configuration is, itself, configurable.</span></span> <span data-ttu-id="d5645-117">ただし、ほとんどのアプリでは、標準のプロジェクトテンプレートの一部として提供される既定のセットと、 `ConfigureWebHostDefaults` それらで使用されるメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d5645-117">However, most apps use a set of defaults provided as part of the standard project templates and the `ConfigureWebHostDefaults` method used in them.</span></span> <span data-ttu-id="d5645-118">既定の設定では、JSON 形式のファイルを使用します。ファイル *の基本appsettings.js* の設定は、 *のappsettings.Development.jsの* ような環境固有のファイルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="d5645-118">The default settings use JSON formatted files, with the ability to override settings in the base *appsettings.json* file with environment-specific files like *appsettings.Development.json*.</span></span> <span data-ttu-id="d5645-119">また、既定の構成システムでは、同じ名前付き設定に存在する環境変数を使用して、すべてのファイルベースの設定がさらに優先されます。</span><span class="sxs-lookup"><span data-stu-id="d5645-119">Additionally, the default configuration system further overrides all file-based settings with any environment variable that exists for the same named setting.</span></span> <span data-ttu-id="d5645-120">これは多くのシナリオで便利であり、ホスト環境に展開するときに特に便利です。これは、構成ファイルの展開によって重要な運用構成設定が誤って上書きされるかどうかを心配する必要がなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="d5645-120">This is useful in many scenarios and is especially useful when deploying to a hosting environment, since it eliminates the need to worry about whether deploying configuration files will accidentally overwrite important production configuration settings.</span></span> <span data-ttu-id="d5645-121">構成値は、コマンドライン引数として指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d5645-121">Configuration values can also be provided as command line arguments.</span></span>

<span data-ttu-id="d5645-122">.NET Core では、さまざまな方法で構成値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d5645-122">Accessing configuration values can be done in many ways in .NET Core.</span></span> <span data-ttu-id="d5645-123">依存関係の挿入は .NET Core に組み込まれているため、構成値は、必要なクラスに挿入されるインターフェイスを使用して一般にアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="d5645-123">Because dependency injection is built into .NET Core, configuration values are generally accessed through an interface that is injected into classes that need them.</span></span> <span data-ttu-id="d5645-124">これには、のようなインターフェイスを渡すことが含まれます <xref:Microsoft.Extensions.Configuration.IConfiguration> が、通常は、 [オプションパターン](/aspnet/core/fundamentals/configuration/options)を使用して、クラスに必要な設定だけを渡すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d5645-124">This can involve passing a interface like <xref:Microsoft.Extensions.Configuration.IConfiguration>, but usually it's better to pass just the settings required by the class using the [options pattern](/aspnet/core/fundamentals/configuration/options).</span></span>

<span data-ttu-id="d5645-125">図2-2 は、 `IConfiguration` Razor ページに渡し、そこから構成設定にアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d5645-125">Figure 2-2 shows how to pass `IConfiguration` into a Razor Page and access configuration settings from it:</span></span>

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

<span data-ttu-id="d5645-126">**図 2-2**</span><span class="sxs-lookup"><span data-stu-id="d5645-126">**Figure 2-2.**</span></span> <span data-ttu-id="d5645-127">を使用した構成値へのアクセス `IConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="d5645-127">Accessing configuration values with `IConfiguration`.</span></span>

<span data-ttu-id="d5645-128">オプションパターンを使用すると、設定アクセスは似ていますが、図2-3 に示すように、使用するクラスで必要な設定に厳密に型指定され、さらに具体的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="d5645-128">Using the options pattern, settings access is similar but is strongly typed and more specific to the setting(s) needed by the consuming class, as Figure 2-3 demonstrates.</span></span>

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

<span data-ttu-id="d5645-129">**図 2-3**</span><span class="sxs-lookup"><span data-stu-id="d5645-129">**Figure 2-3.**</span></span> <span data-ttu-id="d5645-130">ASP.NET Core のオプションパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="d5645-130">Using the options pattern in ASP.NET Core.</span></span>

<span data-ttu-id="d5645-131">オプションパターンを機能させるには、アプリの起動時にオプションの種類をで構成する必要があり `ConfigureServices` ます。</span><span class="sxs-lookup"><span data-stu-id="d5645-131">For the options pattern to work, the options type must be configured in `ConfigureServices` when the app starts up:</span></span>

```csharp
// required in ConfigureServices
services.Configure<PositionOptions>(Configuration.GetSection(PositionOptions.Position));
```

## <a name="migrate-configuration"></a><span data-ttu-id="d5645-132">構成の移行</span><span class="sxs-lookup"><span data-stu-id="d5645-132">Migrate configuration</span></span>

<span data-ttu-id="d5645-133">アプリの構成設定を .NET Framework から .NET Core に移植する方法を検討する場合、最初の手順は、使用されているすべての構成設定を特定することです。</span><span class="sxs-lookup"><span data-stu-id="d5645-133">When considering how to port an app's configuration settings from .NET Framework to .NET Core, the first step is to identify all of the configuration settings that are being used.</span></span> <span data-ttu-id="d5645-134">これらのほとんどは、アプリのルートフォルダーにある *web.config* ファイルに含まれますが、一部のアプリでは、共有 *machine.config* ファイルにも設定が必要です。</span><span class="sxs-lookup"><span data-stu-id="d5645-134">Most of these will be in the *web.config* file in the app's root folder, but some apps expect settings to be found in the shared *machine.config* file as well.</span></span>

<span data-ttu-id="d5645-135">構成ファイルのすべての設定がカタログ化されたら、次の手順では、アプリ自体で設定を使用する場所と方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="d5645-135">Once all settings in the config files have been cataloged, the next step should be to identify where and how the settings are used in the app itself.</span></span> <span data-ttu-id="d5645-136">一部の設定が使用されていない場合は、移行から除外される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d5645-136">If some settings aren't being used, these can probably be omitted from the migration.</span></span> <span data-ttu-id="d5645-137">各設定については、使用されているすべての場所に注意してください。これにより、コードを移行するときに、それが漏れないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d5645-137">For each setting, note all of the places it's being used so you can be sure you don't miss any when you migrate the code.</span></span>

<span data-ttu-id="d5645-138">ASP.NET アプリを引き続き維持している場合は、への静的参照を回避 `ConfigurationManager` し、インターフェイスを使用してアクセスに置き換えることが役に立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="d5645-138">If you're still maintaining the ASP.NET app, it may be helpful to avoid static references to `ConfigurationManager` and replace them with access through interfaces.</span></span> <span data-ttu-id="d5645-139">これにより、ASP.NET Core の構成システムへの移行が容易になります。</span><span class="sxs-lookup"><span data-stu-id="d5645-139">This will ease the transition to ASP.NET Core's configuration system.</span></span> <span data-ttu-id="d5645-140">一般に、外部リソースへの静的アクセスでは、コードのテストと保守が困難になります。そのため、他の場所では、アプリがこのパターンに従う可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d5645-140">In general, static access to external resources makes code harder to test and maintain, so be on the lookout for anywhere else the app may be following this pattern.</span></span>

## <a name="references"></a><span data-ttu-id="d5645-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5645-141">References</span></span>

- [<span data-ttu-id="d5645-142">ASP.NET Core での構成</span><span class="sxs-lookup"><span data-stu-id="d5645-142">Configuration in ASP.NET Core</span></span>](/aspnet/core/fundamentals/configuration/)
- [<span data-ttu-id="d5645-143">ASP.NET Core のオプション パターン</span><span class="sxs-lookup"><span data-stu-id="d5645-143">Options pattern in ASP.NET Core</span></span>](/aspnet/core/fundamentals/configuration/options)
- [<span data-ttu-id="d5645-144">構成を ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="d5645-144">Migrate configuration to ASP.NET Core</span></span>](/aspnet/core/migration/configuration)
- [<span data-ttu-id="d5645-145">静的構成アクセスのリファクタリング</span><span class="sxs-lookup"><span data-stu-id="d5645-145">Refactoring Static Config Access</span></span>](https://ardalis.com/refactoring-static-config-access/)

>[!div class="step-by-step"]
><span data-ttu-id="d5645-146">[前へ](middleware-modules-handlers.md)
>[次へ](routing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="d5645-146">[Previous](middleware-modules-handlers.md)
[Next](routing-differences.md)</span></span>
