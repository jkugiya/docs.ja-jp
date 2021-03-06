---
title: ASP.NET MVC と ASP.NET Core の相違点のログ記録
description: ASP.NET MVC と Web API アプリと ASP.NET Core アプリの間でのログ記録はどのように異なりますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0ad12463c8d13d13516ab027e56f809b67f713e4
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401362"
---
# <a name="logging-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="f429e-103">ASP.NET MVC と ASP.NET Core の相違点のログ記録</span><span class="sxs-lookup"><span data-stu-id="f429e-103">Logging differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="f429e-104">アプリケーションログには、特に運用環境で実行されているアプリに関する重要な診断情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f429e-104">Application logging provides important diagnostic information, especially for apps running in production.</span></span> <span data-ttu-id="f429e-105">ASP.NET Core には、標準化されたログをアプリに追加するための新しいシステムが導入されています。</span><span class="sxs-lookup"><span data-stu-id="f429e-105">ASP.NET Core introduces a new system for adding standardized logging to any app.</span></span> <span data-ttu-id="f429e-106">既存の ASP.NET MVC および Web API アプリでは、ほとんどの場合、サードパーティのログソリューションが使用されますが、これは引き続き ASP.NET Core でサポートされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f429e-106">Existing ASP.NET MVC and Web API apps most likely use third-party logging solutions, which likely continue to be supported on ASP.NET Core.</span></span>

## <a name="aspnet-mvc-logging"></a><span data-ttu-id="f429e-107">ASP.NET MVC のログ記録</span><span class="sxs-lookup"><span data-stu-id="f429e-107">ASP.NET MVC logging</span></span>

<span data-ttu-id="f429e-108">ASP.NET MVC と Web API apps には組み込みのログソリューションがありません。</span><span class="sxs-lookup"><span data-stu-id="f429e-108">There's no built-in logging solution in ASP.NET MVC and Web API apps.</span></span> <span data-ttu-id="f429e-109">代わりに、ほとんどのアプリでは、 [log4net](https://www.nuget.org/packages/log4net/)、 [Nlog](https://www.nuget.org/packages/NLog/)、 [serilog](https://www.nuget.org/packages/Serilog)などのサードパーティ製のログ記録ソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="f429e-109">Instead, most apps use third-party logging solutions like [log4net](https://www.nuget.org/packages/log4net/), [NLog](https://www.nuget.org/packages/NLog/), or [Serilog](https://www.nuget.org/packages/Serilog).</span></span> <span data-ttu-id="f429e-110">多くのチームは、独自のログソリューションをロールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f429e-110">Many teams also choose to roll their own logging solution.</span></span> <span data-ttu-id="f429e-111">ログフレームワークでは、通常、テキストファイル、データベース、電子メールなど、ログ出力用に複数の "シンク" (ターゲットまたはアペンダー) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f429e-111">Logging frameworks typically support multiple "sinks" (or targets or appenders) for log output, such as text files, databases, or even emails.</span></span> <span data-ttu-id="f429e-112">これらは、構成を使用して、システムのどの部分からどのレベルのログメッセージを別のシンクにルーティングするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="f429e-112">They use configuration to determine which levels of log messages from which parts of the system are routed to different sinks.</span></span> <span data-ttu-id="f429e-113">アプリのログ記録を .NET Core に移行する方法を検討するときは、アプリでのログ記録の実行方法と [構成](configuration-differences.md) 方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="f429e-113">When considering how to migrate an app's logging to .NET Core, review how logging is performed and [configured](configuration-differences.md) in the app.</span></span>

## <a name="aspnet-core-logging"></a><span data-ttu-id="f429e-114">ASP.NET Core のログ記録</span><span class="sxs-lookup"><span data-stu-id="f429e-114">ASP.NET Core logging</span></span>

<span data-ttu-id="f429e-115">ASP.NET Core で [は、ログ記録は](/aspnet/core/fundamentals/logging/) 、アプリの起動時に構成および拡張できる組み込みの機能です。</span><span class="sxs-lookup"><span data-stu-id="f429e-115">In ASP.NET Core, [logging is a built-in feature](/aspnet/core/fundamentals/logging/) that can be configured and extended when the app starts up.</span></span> <span data-ttu-id="f429e-116">上記のような logger を含むサードパーティの logger を ASP.NET Core と統合して、その機能を強化することができます。</span><span class="sxs-lookup"><span data-stu-id="f429e-116">Third-party loggers, including those mentioned above, can be integrated with ASP.NET Core to enhance its functionality.</span></span>

<span data-ttu-id="f429e-117">ASP.NET Core ログは、カテゴリとレベルを使用して、ログ記録と方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="f429e-117">ASP.NET Core logging uses categories and levels to control what is logged and how.</span></span> <span data-ttu-id="f429e-118">通常、クラスは、 `ILogger<T>` ジェネリック型として使用されるクラスの型を使用して、インターフェイスのインスタンスを使用し `T` ます。</span><span class="sxs-lookup"><span data-stu-id="f429e-118">Classes typically use instances of the `ILogger<T>` interface, with the class's type used as the generic `T` type.</span></span> <span data-ttu-id="f429e-119">このシナリオでは、クラスの完全修飾名がカテゴリとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f429e-119">In this scenario, the class's fully qualified name is used as the category.</span></span> <span data-ttu-id="f429e-120">また、を使用して、カスタムカテゴリで logger を作成することもでき `ILoggerFactory` ます。</span><span class="sxs-lookup"><span data-stu-id="f429e-120">Loggers can also be created with a custom category using an `ILoggerFactory`.</span></span> <span data-ttu-id="f429e-121">ログレベルは、最も詳細なものから最も重要なものまでの範囲 `Trace` `Critical` です。</span><span class="sxs-lookup"><span data-stu-id="f429e-121">Log levels range from the most detailed, `Trace`, to the most important, `Critical`.</span></span> <span data-ttu-id="f429e-122">アプリでは、構成を使用して、カテゴリごと (ワイルドカードを含む) に含める必要があるログの最小レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f429e-122">Using configuration, apps can specify what minimum level of logging should be included on a per-category (with wildcards) basis.</span></span>

<span data-ttu-id="f429e-123">一般的なログ構成では、既定では情報をログに記録すること `Information` ができますが、先頭にプレフィックスが付いたカテゴリのみが `Warning` `Microsoft` あります。</span><span class="sxs-lookup"><span data-stu-id="f429e-123">A typical logging configuration could log `Information` and above information by default, but only `Warning` or above from `Microsoft`-prefixed categories:</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning"
    }
  }
}
```

<span data-ttu-id="f429e-124">ASP.NET Core でのログインのサポートは広範で柔軟です。</span><span class="sxs-lookup"><span data-stu-id="f429e-124">Support for logging in ASP.NET Core is extensive and flexible.</span></span> <span data-ttu-id="f429e-125">詳細については、 [ドキュメントを参照して](/aspnet/core/fundamentals/logging/)ください。</span><span class="sxs-lookup"><span data-stu-id="f429e-125">For more detailed information, [refer to the docs](/aspnet/core/fundamentals/logging/).</span></span>

## <a name="migrate-logging"></a><span data-ttu-id="f429e-126">ログの移行</span><span class="sxs-lookup"><span data-stu-id="f429e-126">Migrate logging</span></span>

<span data-ttu-id="f429e-127">.NET Framework アプリのログ記録を .NET Core に移行する方法は、アプリがどのようにログに記録されるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f429e-127">How you migrate your .NET Framework app's logging to .NET Core depends on how the app is logging now.</span></span> <span data-ttu-id="f429e-128">サードパーティの NuGet パッケージを使用している場合は、そのパッケージのアップグレードに関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f429e-128">If it's using a third-party NuGet package, refer to the upgrade documentation for that package.</span></span> <span data-ttu-id="f429e-129">ほとんどの場合、アップグレードパスは非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="f429e-129">Most likely the upgrade path will be fairly straightforward.</span></span> <span data-ttu-id="f429e-130">独自のログソリューションを使用している場合は、次のいずれかの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="f429e-130">If you're using your own logging solution, take one of the following actions:</span></span>

1. <span data-ttu-id="f429e-131">ログソリューションを自分で移行する</span><span class="sxs-lookup"><span data-stu-id="f429e-131">Migrate the logging solution yourself</span></span>
1. <span data-ttu-id="f429e-132">サードパーティ製のログ記録ソリューションへの移行</span><span class="sxs-lookup"><span data-stu-id="f429e-132">Migrate to a third-party logging solution</span></span>
1. <span data-ttu-id="f429e-133">ASP.NET Core の組み込みのログ記録のサポートを使用する</span><span class="sxs-lookup"><span data-stu-id="f429e-133">Use the built-in logging support in ASP.NET Core</span></span>

<span data-ttu-id="f429e-134">`Microsoft.Extensions.Logging`NuGet 4.3 以降を使用しており、.NET Framework 4.6.1 以降にある限り、.NET Framework アプリからパッケージを参照できます。</span><span class="sxs-lookup"><span data-stu-id="f429e-134">You can reference the `Microsoft.Extensions.Logging` package from .NET Framework apps as long as they're using NuGet 4.3 or later and are on .NET Framework 4.6.1 or later.</span></span> <span data-ttu-id="f429e-135">アプリがこのパッケージを参照したら、アプリケーションを .NET Core に移行する前に、新しい拡張機能を使用するようにログ記録ステートメントを変換できます。</span><span class="sxs-lookup"><span data-stu-id="f429e-135">Once your app has referenced this package, you can convert your logging statements to use the new extensions before migrating the app to .NET Core.</span></span> <span data-ttu-id="f429e-136">これにより、新しい拡張機能パッケージを使用してログを記録しながら、.NET Framework でアプリを実行し続けることができるため、完全な移行に向けたステップ実行のストーンが提供されます。</span><span class="sxs-lookup"><span data-stu-id="f429e-136">This can provide a stepping stone toward full migration, since the app can continue running on .NET Framework while logging using the newer extensions package.</span></span>

## <a name="references"></a><span data-ttu-id="f429e-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="f429e-137">References</span></span>

- [<span data-ttu-id="f429e-138">.NET Core と ASP.NET Core のログ</span><span class="sxs-lookup"><span data-stu-id="f429e-138">Logging in .NET Core and ASP.NET Core</span></span>](/aspnet/core/fundamentals/logging/)
- [<span data-ttu-id="f429e-139">Microsoft. Extensions. ログ NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="f429e-139">Microsoft.Extensions.Logging NuGet Package</span></span>](https://www.nuget.org/packages/microsoft.extensions.logging/)

>[!div class="step-by-step"]
><span data-ttu-id="f429e-140">[前へ](middleware-modules-handlers.md)
>[次へ](routing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="f429e-140">[Previous](middleware-modules-handlers.md)
[Next](routing-differences.md)</span></span>
