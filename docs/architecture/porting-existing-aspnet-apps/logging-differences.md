---
title: ASP.NET MVC と ASP.NET Core でのログの相違点
description: ASP.NET MVC および Web API アプリと ASP.NET Core アプリで、ログはどのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0ad12463c8d13d13516ab027e56f809b67f713e4
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401362"
---
# <a name="logging-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="de4c7-103">ASP.NET MVC と ASP.NET Core でのログの相違点</span><span class="sxs-lookup"><span data-stu-id="de4c7-103">Logging differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="de4c7-104">アプリケーション ログは、特に運用環境で実行されているアプリに対して、重要な診断情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="de4c7-104">Application logging provides important diagnostic information, especially for apps running in production.</span></span> <span data-ttu-id="de4c7-105">ASP.NET Core では、標準化されたログをアプリに追加するための新しいシステムが導入されています。</span><span class="sxs-lookup"><span data-stu-id="de4c7-105">ASP.NET Core introduces a new system for adding standardized logging to any app.</span></span> <span data-ttu-id="de4c7-106">多くの場合、既存の ASP.NET MVC アプリや Web API アプリではサードパーティのログ ソリューションが使用されていますが、これはおそらく ASP.NET Core でも引き続きサポートされるでしょう。</span><span class="sxs-lookup"><span data-stu-id="de4c7-106">Existing ASP.NET MVC and Web API apps most likely use third-party logging solutions, which likely continue to be supported on ASP.NET Core.</span></span>

## <a name="aspnet-mvc-logging"></a><span data-ttu-id="de4c7-107">ASP.NET MVC のログ記録</span><span class="sxs-lookup"><span data-stu-id="de4c7-107">ASP.NET MVC logging</span></span>

<span data-ttu-id="de4c7-108">ASP.NET MVC アプリと Web API アプリには、組み込みのログ ソリューションがありません。</span><span class="sxs-lookup"><span data-stu-id="de4c7-108">There's no built-in logging solution in ASP.NET MVC and Web API apps.</span></span> <span data-ttu-id="de4c7-109">代わりに、ほとんどのアプリで、サードパーティのログ ソリューション ([log4net](https://www.nuget.org/packages/log4net/)、[NLog](https://www.nuget.org/packages/NLog/)、[Serilog](https://www.nuget.org/packages/Serilog) など) が使用されています。</span><span class="sxs-lookup"><span data-stu-id="de4c7-109">Instead, most apps use third-party logging solutions like [log4net](https://www.nuget.org/packages/log4net/), [NLog](https://www.nuget.org/packages/NLog/), or [Serilog](https://www.nuget.org/packages/Serilog).</span></span> <span data-ttu-id="de4c7-110">また、多くのチームが、独自のログ ソリューションを展開することを選択しています。</span><span class="sxs-lookup"><span data-stu-id="de4c7-110">Many teams also choose to roll their own logging solution.</span></span> <span data-ttu-id="de4c7-111">ログ フレームワークでは通常、テキスト ファイル、データベース、電子メールなど、ログ出力のための複数の "シンク" (ターゲットやアペンダーとも呼ばれます) がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="de4c7-111">Logging frameworks typically support multiple "sinks" (or targets or appenders) for log output, such as text files, databases, or even emails.</span></span> <span data-ttu-id="de4c7-112">これらは構成を使用して、システムのどの部分からどのレベルのログ メッセージをさまざまなリンクにルーティングするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="de4c7-112">They use configuration to determine which levels of log messages from which parts of the system are routed to different sinks.</span></span> <span data-ttu-id="de4c7-113">アプリのログを .NET Core に移行する方法を検討する際は、アプリ内でログがどのように実行および[構成](configuration-differences.md)されているかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="de4c7-113">When considering how to migrate an app's logging to .NET Core, review how logging is performed and [configured](configuration-differences.md) in the app.</span></span>

## <a name="aspnet-core-logging"></a><span data-ttu-id="de4c7-114">ASP.NET Core のログ記録</span><span class="sxs-lookup"><span data-stu-id="de4c7-114">ASP.NET Core logging</span></span>

<span data-ttu-id="de4c7-115">ASP.NET Core では、[ログは組み込みの機能であり](/aspnet/core/fundamentals/logging/)、アプリの起動時に構成および拡張できます。</span><span class="sxs-lookup"><span data-stu-id="de4c7-115">In ASP.NET Core, [logging is a built-in feature](/aspnet/core/fundamentals/logging/) that can be configured and extended when the app starts up.</span></span> <span data-ttu-id="de4c7-116">前述のようなサードパーティのロガーを ASP.NET Core と統合して、その機能を強化できます。</span><span class="sxs-lookup"><span data-stu-id="de4c7-116">Third-party loggers, including those mentioned above, can be integrated with ASP.NET Core to enhance its functionality.</span></span>

<span data-ttu-id="de4c7-117">ASP.NET Core のログでは、カテゴリとレベルを使用してログの対象と方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="de4c7-117">ASP.NET Core logging uses categories and levels to control what is logged and how.</span></span> <span data-ttu-id="de4c7-118">通常、クラスでは `ILogger<T>` インターフェイスのインスタンスが使用され、クラスの型がジェネリック `T` 型として使用されます。</span><span class="sxs-lookup"><span data-stu-id="de4c7-118">Classes typically use instances of the `ILogger<T>` interface, with the class's type used as the generic `T` type.</span></span> <span data-ttu-id="de4c7-119">このシナリオでは、クラスの完全修飾名がカテゴリとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="de4c7-119">In this scenario, the class's fully qualified name is used as the category.</span></span> <span data-ttu-id="de4c7-120">`ILoggerFactory` を使用して、カスタム カテゴリでロガーを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="de4c7-120">Loggers can also be created with a custom category using an `ILoggerFactory`.</span></span> <span data-ttu-id="de4c7-121">ログのレベルには、最も詳細な `Trace` から、最も重要な `Critical` までがあります。</span><span class="sxs-lookup"><span data-stu-id="de4c7-121">Log levels range from the most detailed, `Trace`, to the most important, `Critical`.</span></span> <span data-ttu-id="de4c7-122">アプリでは、構成を使用して、カテゴリごと (ワイルドカードを含む) に含めるログの最小レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="de4c7-122">Using configuration, apps can specify what minimum level of logging should be included on a per-category (with wildcards) basis.</span></span>

<span data-ttu-id="de4c7-123">一般的なログの構成では、既定では `Information` 以上の情報をログしますが、`Microsoft` のプレフィックスが付いたカテゴリからのみ `Warning` 以上の情報をログします。</span><span class="sxs-lookup"><span data-stu-id="de4c7-123">A typical logging configuration could log `Information` and above information by default, but only `Warning` or above from `Microsoft`-prefixed categories:</span></span>

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

<span data-ttu-id="de4c7-124">ASP.NET Core でのログのサポートは広範囲で柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="de4c7-124">Support for logging in ASP.NET Core is extensive and flexible.</span></span> <span data-ttu-id="de4c7-125">詳細については、[ドキュメントを参照してください](/aspnet/core/fundamentals/logging/)。</span><span class="sxs-lookup"><span data-stu-id="de4c7-125">For more detailed information, [refer to the docs](/aspnet/core/fundamentals/logging/).</span></span>

## <a name="migrate-logging"></a><span data-ttu-id="de4c7-126">ログの移行</span><span class="sxs-lookup"><span data-stu-id="de4c7-126">Migrate logging</span></span>

<span data-ttu-id="de4c7-127">.NET Framework アプリのログを .NET Core に移行する方法は、アプリで現在どのようにログが行われているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="de4c7-127">How you migrate your .NET Framework app's logging to .NET Core depends on how the app is logging now.</span></span> <span data-ttu-id="de4c7-128">サードパーティの NuGet パッケージを使用している場合は、そのパッケージのアップグレードに関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="de4c7-128">If it's using a third-party NuGet package, refer to the upgrade documentation for that package.</span></span> <span data-ttu-id="de4c7-129">ほとんどの場合、アップグレード パスは非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="de4c7-129">Most likely the upgrade path will be fairly straightforward.</span></span> <span data-ttu-id="de4c7-130">独自のログ ソリューションを使用している場合は、次のいずれかのアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="de4c7-130">If you're using your own logging solution, take one of the following actions:</span></span>

1. <span data-ttu-id="de4c7-131">ログ ソリューションを自分で移行する</span><span class="sxs-lookup"><span data-stu-id="de4c7-131">Migrate the logging solution yourself</span></span>
1. <span data-ttu-id="de4c7-132">サードパーティのログ ソリューションに移行する</span><span class="sxs-lookup"><span data-stu-id="de4c7-132">Migrate to a third-party logging solution</span></span>
1. <span data-ttu-id="de4c7-133">ASP.NET Core に組み込まれているログ サポートを使用する</span><span class="sxs-lookup"><span data-stu-id="de4c7-133">Use the built-in logging support in ASP.NET Core</span></span>

<span data-ttu-id="de4c7-134">.NET Framework アプリが NuGet 4.3 以降を使用していて、.NET Framework 4.6.1 以降で実行されている場合は、アプリから `Microsoft.Extensions.Logging` パッケージを参照できます。</span><span class="sxs-lookup"><span data-stu-id="de4c7-134">You can reference the `Microsoft.Extensions.Logging` package from .NET Framework apps as long as they're using NuGet 4.3 or later and are on .NET Framework 4.6.1 or later.</span></span> <span data-ttu-id="de4c7-135">アプリがこのパッケージを参照したら、アプリを .NET Core に移行する前に、新しい拡張機能を使用するようにログ ステートメントを変換できます。</span><span class="sxs-lookup"><span data-stu-id="de4c7-135">Once your app has referenced this package, you can convert your logging statements to use the new extensions before migrating the app to .NET Core.</span></span> <span data-ttu-id="de4c7-136">これにより、アプリを引き続き .NET Framework 上で実行しながら新しい拡張機能パッケージを使用してログできるため、完全な移行への足がかりとなります。</span><span class="sxs-lookup"><span data-stu-id="de4c7-136">This can provide a stepping stone toward full migration, since the app can continue running on .NET Framework while logging using the newer extensions package.</span></span>

## <a name="references"></a><span data-ttu-id="de4c7-137">リファレンス</span><span class="sxs-lookup"><span data-stu-id="de4c7-137">References</span></span>

- [<span data-ttu-id="de4c7-138">.NET Core と ASP.NET Core のログ</span><span class="sxs-lookup"><span data-stu-id="de4c7-138">Logging in .NET Core and ASP.NET Core</span></span>](/aspnet/core/fundamentals/logging/)
- [<span data-ttu-id="de4c7-139">Microsoft.Extensions.Logging NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="de4c7-139">Microsoft.Extensions.Logging NuGet Package</span></span>](https://www.nuget.org/packages/microsoft.extensions.logging/)

>[!div class="step-by-step"]
><span data-ttu-id="de4c7-140">[前へ](middleware-modules-handlers.md)
>[次へ](routing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="de4c7-140">[Previous](middleware-modules-handlers.md)
[Next](routing-differences.md)</span></span>
