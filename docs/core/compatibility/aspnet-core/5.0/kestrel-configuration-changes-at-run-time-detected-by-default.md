---
title: '破壊的変更:Kestrel: 実行時に構成変更が既定で検出される'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: Kestrel: 実行時に構成変更が既定で検出される'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 35b733cd872b9d6d944896349921c54f672b31b0
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498101"
---
# <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="464f9-103">Kestrel: 実行時に構成変更が既定で検出される</span><span class="sxs-lookup"><span data-stu-id="464f9-103">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="464f9-104">Kestrel では実行時に、プロジェクトの `IConfiguration` インスタンス (*appsettings.json* など) の `Kestrel` セクションに対する変更に対応するようになりました。</span><span class="sxs-lookup"><span data-stu-id="464f9-104">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="464f9-105">*appsettings.json* を使用して Kestrel を構成する方法の詳細については、[エンドポイント構成](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration)の *appsettings.json* 例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="464f9-105">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="464f9-106">Kestrel では、こうした構成変更に対応する目的で必要であれば、エンドポイントをバインド、バインド解除、再バインドします。</span><span class="sxs-lookup"><span data-stu-id="464f9-106">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="464f9-107">ディスカッションについては、イシュー [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="464f9-107">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="464f9-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="464f9-108">Version introduced</span></span>

<span data-ttu-id="464f9-109">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="464f9-109">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="464f9-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="464f9-110">Old behavior</span></span>

<span data-ttu-id="464f9-111">ASP.NET Core 5.0 Preview 6 より前は、Kestrel では、実行時に構成を変更できませんでした。</span><span class="sxs-lookup"><span data-stu-id="464f9-111">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="464f9-112">ASP.NET Core 5.0 Preview 6 では、実行時に構成変更に対応するという新しい既定の動作を選択できます。</span><span class="sxs-lookup"><span data-stu-id="464f9-112">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="464f9-113">選択では、Kestrel の構成を手動でバインドする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="464f9-113">Opting in required binding Kestrel's configuration manually:</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.Extensions.Hosting;

public class Program
{
    public static void Main(string[] args) =>
        CreateHostBuilder(args).Build().Run();

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

## <a name="new-behavior"></a><span data-ttu-id="464f9-114">新しい動作</span><span class="sxs-lookup"><span data-stu-id="464f9-114">New behavior</span></span>

<span data-ttu-id="464f9-115">Kestrel では既定で、実行時に構成変更に対応します。</span><span class="sxs-lookup"><span data-stu-id="464f9-115">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="464f9-116">この変更をサポートする目的で、<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> では既定で `reloadOnChange: true` を指定して `KestrelServerOptions.Configure(IConfiguration, bool)` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="464f9-116">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="464f9-117">変更理由</span><span class="sxs-lookup"><span data-stu-id="464f9-117">Reason for change</span></span>

<span data-ttu-id="464f9-118">サーバーを完全に再起動しなくても実行時のエンドポイント再構成がサポートされるように変更が行われました。</span><span class="sxs-lookup"><span data-stu-id="464f9-118">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="464f9-119">サーバーの完全再起動の場合とは異なり、変更のないエンドポイントは一時的でもバインド解除されません。</span><span class="sxs-lookup"><span data-stu-id="464f9-119">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="464f9-120">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="464f9-120">Recommended action</span></span>

* <span data-ttu-id="464f9-121">Kestrel の既定の構成セクションが実行時に変更されない大抵のシナリオはこの変更の影響を受けず、何の措置も必要ありません。</span><span class="sxs-lookup"><span data-stu-id="464f9-121">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="464f9-122">Kestrel の既定の構成セクションが実行時に変更され、Kestrel がそれに対応しなければならないシナリオでは、これが既定の動作になります。</span><span class="sxs-lookup"><span data-stu-id="464f9-122">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="464f9-123">Kestrel の既定の構成セクションが実行時に変更されるが、Kestrel はそれに対応する必要がないシナリオでは、次のようにオプトアウトできます。</span><span class="sxs-lookup"><span data-stu-id="464f9-123">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="464f9-124">**注:**</span><span class="sxs-lookup"><span data-stu-id="464f9-124">**Notes:**</span></span>

<span data-ttu-id="464f9-125">依然として `reloadOnChange: false` 動作の既定である `KestrelServerOptions.Configure(IConfiguration)` オーバーロードの動作がこの変更によって修正されることはありません。</span><span class="sxs-lookup"><span data-stu-id="464f9-125">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="464f9-126">構成ソースで再読み込みがサポートされることを確認することも重要です。</span><span class="sxs-lookup"><span data-stu-id="464f9-126">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="464f9-127">JSON ソースの場合、再読み込みは `AddJsonFile(path, reloadOnChange: true)` を呼び出すことで構成されます。</span><span class="sxs-lookup"><span data-stu-id="464f9-127">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="464f9-128">*appsettings.json* と *appsettings.{Environment}.json* については、再読み込みが既定で構成されています。</span><span class="sxs-lookup"><span data-stu-id="464f9-128">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="464f9-129">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="464f9-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
