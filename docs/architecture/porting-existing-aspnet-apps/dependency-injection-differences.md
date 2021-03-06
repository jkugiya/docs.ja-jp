---
title: ASP.NET MVC と ASP.NET Core の依存関係挿入の違い
description: ASP.NET MVC と ASP.NET Core での依存関係の挿入のしくみ、それらの違い、および ASP.NET MVC から ASP.NET Core への移行方法について説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: aa1c7dd2f70e1a545352feb6560177bc6e2baa2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401390"
---
# <a name="dependency-injection-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="58865-103">ASP.NET MVC と ASP.NET Core の依存関係挿入の違い</span><span class="sxs-lookup"><span data-stu-id="58865-103">Dependency injection differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="58865-104">依存関係の注入 (DI) は ASP.NET MVC または Web API には組み込まれていませんが、多くのアプリでは、コントロールの反転 (IOC) コンテナーを含む NuGet パッケージを追加することで有効になります。</span><span class="sxs-lookup"><span data-stu-id="58865-104">Although dependency injection (DI) isn't built into ASP.NET MVC or Web API, many apps enable it by adding a NuGet package with an inversion of control (IOC) container.</span></span> <span data-ttu-id="58865-105">これらは、依存関係の挿入 (または反転) のために DI コンテナーと呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="58865-105">These are sometimes referred to as DI containers, for dependency injection (or inversion).</span></span> <span data-ttu-id="58865-106">ASP.NET MVC アプリで使用される最も一般的なコンテナーには、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="58865-106">Some of the most popular containers used in ASP.NET MVC apps include:</span></span>

- [<span data-ttu-id="58865-107">Autofac</span><span class="sxs-lookup"><span data-stu-id="58865-107">Autofac</span></span>](https://www.autofac.org/)
- [<span data-ttu-id="58865-108">Unity</span><span class="sxs-lookup"><span data-stu-id="58865-108">Unity</span></span>](https://unitycontainer.github.io/)
- [<span data-ttu-id="58865-109">Ninject</span><span class="sxs-lookup"><span data-stu-id="58865-109">Ninject</span></span>](http://www.ninject.org/)
- <span data-ttu-id="58865-110">[構造体マップ](http://structuremap.github.io/) *(非推奨)*</span><span class="sxs-lookup"><span data-stu-id="58865-110">[StructureMap](http://structuremap.github.io/) *(deprecated)*</span></span>
- [<span data-ttu-id="58865-111">城 Windsor</span><span class="sxs-lookup"><span data-stu-id="58865-111">Castle Windsor</span></span>](http://www.castleproject.org/projects/windsor/)

<span data-ttu-id="58865-112">ASP.NET MVC アプリで DI を使用していない場合は、ASP.NET Core で DI の組み込みサポートを調査することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58865-112">If your ASP.NET MVC app isn't using DI, you will probably want to investigate the built-in support for DI in ASP.NET Core.</span></span> <span data-ttu-id="58865-113">DI では、アプリ内のモジュールの疎結合が促進され、 [堅牢](https://www.weeklydevtips.com/episodes/047)性というような、より優れたテスト性と原則への準拠が可能になります。</span><span class="sxs-lookup"><span data-stu-id="58865-113">DI promotes loose coupling of modules in your app and enables better testability and adherence to principles like [SOLID](https://www.weeklydevtips.com/episodes/047).</span></span>

<span data-ttu-id="58865-114">アプリで DI を使用している場合は、使用しているコンテナーが ASP.NET Core をサポートしているかどうかを確認するのが最善の方法です。</span><span class="sxs-lookup"><span data-stu-id="58865-114">If your app does use DI, then probably your best course of action is to see if the container you're using supports ASP.NET Core.</span></span> <span data-ttu-id="58865-115">その場合は、そのまま使用することも、型マッピングと有効期間を記述したカスタム構成ルールを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="58865-115">If so, you may be able to continue using it and your custom configuration rules describing your type mappings and lifetimes.</span></span>

<span data-ttu-id="58865-116">どちらの場合も、ASP.NET Core に付属している DI の組み込みサポートを使用することを検討する必要があります。これは、アプリのニーズを満たす可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="58865-116">Either way, you should consider using the built-in support for DI that ships with ASP.NET Core, as it may meet your app's needs.</span></span>

## <a name="dependency-injection-in-aspnet-core"></a><span data-ttu-id="58865-117">ASP.NET Core での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="58865-117">Dependency injection in ASP.NET Core</span></span>

<span data-ttu-id="58865-118">ASP.NET Core は、アプリが DI を使用することを前提としています。</span><span class="sxs-lookup"><span data-stu-id="58865-118">ASP.NET Core assumes apps will use DI.</span></span> <span data-ttu-id="58865-119">フレームワークに組み込まれているだけでなく、フレームワークの機能のサポートを ASP.NET Core アプリに導入するために必要です。</span><span class="sxs-lookup"><span data-stu-id="58865-119">It's not just built into the framework, but is required in order to bring support for framework features into your ASP.NET Core apps.</span></span> <span data-ttu-id="58865-120">アプリの起動時に、 `ConfigureServices` DI コンテナー (サービスコレクション/サービスプロバイダー) が作成してアプリで挿入できるすべての型を登録するための呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="58865-120">In app startup, a call is made to `ConfigureServices` which is responsible for registering all of the types that the DI container (service collection/service provider) can create and inject in the app.</span></span> <span data-ttu-id="58865-121">Entity Framework Core、Id、MVC などの組み込みの ASP.NET Core 機能は、メソッドでサービスとして構成することで、アプリに取り込まれ `ConfigureServices` ます。</span><span class="sxs-lookup"><span data-stu-id="58865-121">Built-in ASP.NET Core features like Entity Framework Core, Identity, and even MVC are brought into the app by configuring them as services in the `ConfigureServices` method.</span></span>

<span data-ttu-id="58865-122">既定の実装を使用するだけでなく、アプリでもカスタムコンテナーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="58865-122">In addition to using the default implementation, apps can still use custom containers.</span></span> <span data-ttu-id="58865-123">このドキュメントでは、 [既定のサービスコンテナーを置き換える方法について説明](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement)します。</span><span class="sxs-lookup"><span data-stu-id="58865-123">The [documentation covers how to replace the default service container](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement).</span></span>

<span data-ttu-id="58865-124">DI は、ASP.NET Core の基礎となります。</span><span class="sxs-lookup"><span data-stu-id="58865-124">DI is fundamental to ASP.NET Core.</span></span> <span data-ttu-id="58865-125">チームがこの実践に精通していない場合は、アプリを移植する前に理解しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58865-125">If your team isn't already well-versed in this practice, you'll want to understand it before porting your app.</span></span>

## <a name="references"></a><span data-ttu-id="58865-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="58865-126">References</span></span>

- [<span data-ttu-id="58865-127">.NET での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="58865-127">Dependency Injection in .NET</span></span>](../../core/extensions/dependency-injection.md)
- [<span data-ttu-id="58865-128">ASP.NET Core での依存関係の挿入</span><span class="sxs-lookup"><span data-stu-id="58865-128">Dependency Injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)

>[!div class="step-by-step"]
><span data-ttu-id="58865-129">[前へ](serving-static-files.md)
>[次へ](middleware-modules-handlers.md)</span><span class="sxs-lookup"><span data-stu-id="58865-129">[Previous](serving-static-files.md)
[Next](middleware-modules-handlers.md)</span></span>
