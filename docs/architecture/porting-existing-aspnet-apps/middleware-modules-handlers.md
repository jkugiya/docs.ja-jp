---
title: ミドルウェアとモジュールおよびハンドラーの比較
description: このセクションでは、ハンドラーとモジュールを使用する ASP.NET アプリと、要求処理パイプライン用にミドルウェアを定義する ASP.NET Core アプリ間の構造の違いについて説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 040ae49d1307ef4dcc9dbf49b20544e9cd2bc913
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401361"
---
# <a name="compare-middleware-to-modules-and-handlers"></a><span data-ttu-id="2dedc-103">ミドルウェアとモジュールおよびハンドラーの比較</span><span class="sxs-lookup"><span data-stu-id="2dedc-103">Compare middleware to modules and handlers</span></span>

<span data-ttu-id="2dedc-104">既存の ASP.NET MVC アプリや Web API アプリで OWIN/Katana を使用している方はおそらく、ミドルウェアの概念と、それを ASP.NET Core に移植するのは非常に簡単であることを既によくご存知でしょう。</span><span class="sxs-lookup"><span data-stu-id="2dedc-104">If your existing ASP.NET MVC or Web API app uses OWIN/Katana, you're most likely already familiar with the concept of middleware and porting it to ASP.NET Core should be fairly straightforward.</span></span> <span data-ttu-id="2dedc-105">しかし、ほとんどの ASP.NET アプリでは、ミドルウェアではなく HTTP モジュールと HTTP ハンドラーが使用されています。</span><span class="sxs-lookup"><span data-stu-id="2dedc-105">However, most ASP.NET apps rely on HTTP modules and HTTP handlers instead of middleware.</span></span> <span data-ttu-id="2dedc-106">これらを ASP.NET Core に移行するには、追加の作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="2dedc-106">Migrating these to ASP.NET Core requires extra effort.</span></span>

## <a name="aspnet-modules-and-handlers"></a><span data-ttu-id="2dedc-107">ASP.NET のモジュールとハンドラー</span><span class="sxs-lookup"><span data-stu-id="2dedc-107">ASP.NET modules and handlers</span></span>

<span data-ttu-id="2dedc-108">[HTTP モジュールと HTTP ハンドラー](/troubleshoot/aspnet/http-modules-handlers)は、ASP.NET アーキテクチャに不可欠な部分です。</span><span class="sxs-lookup"><span data-stu-id="2dedc-108">[HTTP modules and HTTP handlers](/troubleshoot/aspnet/http-modules-handlers) are an integral part of the ASP.NET architecture.</span></span> <span data-ttu-id="2dedc-109">要求が処理されている間、各要求は複数の HTTP モジュール (たとえば、認証モジュールとセッション モジュール) によって処理され、その後、1 つの HTTP ハンドラーによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="2dedc-109">While a request is being processed, each request is processed by multiple HTTP modules (for example, the authentication module and the session module) and is then processed by a single HTTP handler.</span></span> <span data-ttu-id="2dedc-110">ハンドラーが要求を処理した後、要求は HTTP モジュールを経由して戻されます。</span><span class="sxs-lookup"><span data-stu-id="2dedc-110">After the handler has processed the request, the request flows back through the HTTP modules.</span></span>

<span data-ttu-id="2dedc-111">アプリでカスタムの HTTP モジュールまたは HTTP ハンドラーを使用している場合は、それらを ASP.NET Core に移行するための計画が必要になります。</span><span class="sxs-lookup"><span data-stu-id="2dedc-111">If your app is using custom HTTP modules or HTTP handlers, you'll need a plan to migrate them to ASP.NET Core.</span></span> <span data-ttu-id="2dedc-112">ASP.NET Core での最も有力な代替候補となるのは、ミドルウェアです。</span><span class="sxs-lookup"><span data-stu-id="2dedc-112">The most likely replacement in ASP.NET Core is middleware.</span></span>

## <a name="aspnet-core-middleware"></a><span data-ttu-id="2dedc-113">ASP.NET Core のミドルウェア</span><span class="sxs-lookup"><span data-stu-id="2dedc-113">ASP.NET Core middleware</span></span>

<span data-ttu-id="2dedc-114">ASP.NET Core では、各アプリの `Configure` メソッド内で要求パイプラインが定義されます。</span><span class="sxs-lookup"><span data-stu-id="2dedc-114">ASP.NET Core defines a request pipeline in each app's `Configure` method.</span></span> <span data-ttu-id="2dedc-115">この要求パイプラインでは、アプリでの受信要求の処理方法が定義されます。パイプライン内の各メソッドは、最終的に 1 つのメソッドが終了し、"*ミドルウェア*" のチェーンが終了してスタックの上位に戻るまで、次のメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2dedc-115">This request pipeline defines how an incoming request is handled by the app, with each method in the pipeline calling the next method until eventually a method terminates, and the chain of *middleware* terminates and returns back up the stack.</span></span> <span data-ttu-id="2dedc-116">ミドルウェアはすべての要求をターゲットにすることも、要求されたパスまたはその他の要素に基づいて特定の要求のみにマップするように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2dedc-116">Middleware can target all requests, or can be configured to only map to certain requests based on the requested path or other factors.</span></span> <span data-ttu-id="2dedc-117">アプリの `Configure` メソッド内に完全に構成することも、別のクラスに実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="2dedc-117">It can be configured wholly in the `Configure` method of an app, or implemented in a separate class.</span></span>

<span data-ttu-id="2dedc-118">HTTP モジュールを使用する ASP.NET MVC アプリでの動作は、おそらく[カスタム ミドルウェア](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)に最も適しています。</span><span class="sxs-lookup"><span data-stu-id="2dedc-118">Behavior in an ASP.NET MVC app that uses HTTP modules is probably best suited to [custom middleware](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span></span> <span data-ttu-id="2dedc-119">カスタム HTTP ハンドラーは、同じパスに応答するカスタムのルートまたはエンドポイントに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="2dedc-119">Custom HTTP handlers can be replaced with custom routes or endpoints that respond to the same path.</span></span>

## <a name="references"></a><span data-ttu-id="2dedc-120">リファレンス</span><span class="sxs-lookup"><span data-stu-id="2dedc-120">References</span></span>

- [<span data-ttu-id="2dedc-121">ASP.NET HTTP モジュールと HTTP ハンドラー</span><span class="sxs-lookup"><span data-stu-id="2dedc-121">ASP.NET HTTP modules and HTTP handlers</span></span>](/troubleshoot/aspnet/http-modules-handlers)
- [<span data-ttu-id="2dedc-122">ASP.NET Core のミドルウェア</span><span class="sxs-lookup"><span data-stu-id="2dedc-122">ASP.NET Core middleware</span></span>](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
><span data-ttu-id="2dedc-123">[前へ](dependency-injection-differences.md)
>[次へ](configuration-differences.md)</span><span class="sxs-lookup"><span data-stu-id="2dedc-123">[Previous](dependency-injection-differences.md)
[Next](configuration-differences.md)</span></span>
