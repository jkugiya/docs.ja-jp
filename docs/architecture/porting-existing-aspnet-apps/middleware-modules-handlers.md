---
title: ミドルウェアとモジュールおよびハンドラーの比較
description: このセクションでは、要求処理パイプラインのミドルウェアを定義する ASP.NET Core アプリでハンドラーとモジュールを使用する ASP.NET アプリの構造の違いについて説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 040ae49d1307ef4dcc9dbf49b20544e9cd2bc913
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401361"
---
# <a name="compare-middleware-to-modules-and-handlers"></a><span data-ttu-id="7495e-103">ミドルウェアとモジュールおよびハンドラーの比較</span><span class="sxs-lookup"><span data-stu-id="7495e-103">Compare middleware to modules and handlers</span></span>

<span data-ttu-id="7495e-104">既存の ASP.NET MVC または Web API アプリが OWIN/Katana を使用している場合は、ミドルウェアの概念を理解している可能性が高く、ASP.NET Core に移植するのは非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="7495e-104">If your existing ASP.NET MVC or Web API app uses OWIN/Katana, you're most likely already familiar with the concept of middleware and porting it to ASP.NET Core should be fairly straightforward.</span></span> <span data-ttu-id="7495e-105">ただし、ほとんどの ASP.NET アプリは、ミドルウェアではなく HTTP モジュールと HTTP ハンドラーに依存しています。</span><span class="sxs-lookup"><span data-stu-id="7495e-105">However, most ASP.NET apps rely on HTTP modules and HTTP handlers instead of middleware.</span></span> <span data-ttu-id="7495e-106">これらの ASP.NET Core に移行するには、余分な作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="7495e-106">Migrating these to ASP.NET Core requires extra effort.</span></span>

## <a name="aspnet-modules-and-handlers"></a><span data-ttu-id="7495e-107">ASP.NET モジュールとハンドラー</span><span class="sxs-lookup"><span data-stu-id="7495e-107">ASP.NET modules and handlers</span></span>

<span data-ttu-id="7495e-108">[Http モジュールと http ハンドラー](/troubleshoot/aspnet/http-modules-handlers) は、ASP.NET アーキテクチャの不可欠な部分です。</span><span class="sxs-lookup"><span data-stu-id="7495e-108">[HTTP modules and HTTP handlers](/troubleshoot/aspnet/http-modules-handlers) are an integral part of the ASP.NET architecture.</span></span> <span data-ttu-id="7495e-109">要求が処理されている間、各要求は複数の HTTP モジュール (たとえば、認証モジュールとセッションモジュール) によって処理され、1つの HTTP ハンドラーによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="7495e-109">While a request is being processed, each request is processed by multiple HTTP modules (for example, the authentication module and the session module) and is then processed by a single HTTP handler.</span></span> <span data-ttu-id="7495e-110">ハンドラーが要求を処理した後、要求は HTTP モジュールを経由して返されます。</span><span class="sxs-lookup"><span data-stu-id="7495e-110">After the handler has processed the request, the request flows back through the HTTP modules.</span></span>

<span data-ttu-id="7495e-111">アプリでカスタム HTTP モジュールまたは HTTP ハンドラーが使用されている場合は、ASP.NET Core に移行するための計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="7495e-111">If your app is using custom HTTP modules or HTTP handlers, you'll need a plan to migrate them to ASP.NET Core.</span></span> <span data-ttu-id="7495e-112">ASP.NET Core に代わる可能性が高いのはミドルウェアです。</span><span class="sxs-lookup"><span data-stu-id="7495e-112">The most likely replacement in ASP.NET Core is middleware.</span></span>

## <a name="aspnet-core-middleware"></a><span data-ttu-id="7495e-113">ASP.NET Core ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="7495e-113">ASP.NET Core middleware</span></span>

<span data-ttu-id="7495e-114">ASP.NET Core は、各アプリのメソッドで要求パイプラインを定義 `Configure` します。</span><span class="sxs-lookup"><span data-stu-id="7495e-114">ASP.NET Core defines a request pipeline in each app's `Configure` method.</span></span> <span data-ttu-id="7495e-115">この要求パイプラインは、アプリによる受信要求の処理方法を定義します。パイプライン内の各メソッドは、最終的にメソッドが終了するまで次のメソッドを呼び出し、 *ミドルウェア* のチェーンは終了してスタックを戻します。</span><span class="sxs-lookup"><span data-stu-id="7495e-115">This request pipeline defines how an incoming request is handled by the app, with each method in the pipeline calling the next method until eventually a method terminates, and the chain of *middleware* terminates and returns back up the stack.</span></span> <span data-ttu-id="7495e-116">ミドルウェアは、すべての要求を対象にすることも、要求されたパスまたはその他の要因に基づいて特定の要求にのみマップするように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="7495e-116">Middleware can target all requests, or can be configured to only map to certain requests based on the requested path or other factors.</span></span> <span data-ttu-id="7495e-117">アプリのメソッドで完全に構成することも `Configure` 、別のクラスに実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="7495e-117">It can be configured wholly in the `Configure` method of an app, or implemented in a separate class.</span></span>

<span data-ttu-id="7495e-118">HTTP モジュールを使用する ASP.NET MVC アプリでの動作は、 [カスタムミドルウェア](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)に最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7495e-118">Behavior in an ASP.NET MVC app that uses HTTP modules is probably best suited to [custom middleware](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1).</span></span> <span data-ttu-id="7495e-119">カスタム HTTP ハンドラーは、同じパスに応答するカスタムルートまたはエンドポイントに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="7495e-119">Custom HTTP handlers can be replaced with custom routes or endpoints that respond to the same path.</span></span>

## <a name="references"></a><span data-ttu-id="7495e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="7495e-120">References</span></span>

- [<span data-ttu-id="7495e-121">ASP.NET HTTP モジュールと HTTP ハンドラー</span><span class="sxs-lookup"><span data-stu-id="7495e-121">ASP.NET HTTP modules and HTTP handlers</span></span>](/troubleshoot/aspnet/http-modules-handlers)
- [<span data-ttu-id="7495e-122">ASP.NET Core ミドルウェア</span><span class="sxs-lookup"><span data-stu-id="7495e-122">ASP.NET Core middleware</span></span>](/aspnet/core/fundamentals/middleware/?preserve-view=true&view=aspnetcore-3.1)

>[!div class="step-by-step"]
><span data-ttu-id="7495e-123">[前へ](dependency-injection-differences.md)
>[次へ](configuration-differences.md)</span><span class="sxs-lookup"><span data-stu-id="7495e-123">[Previous](dependency-injection-differences.md)
[Next](configuration-differences.md)</span></span>
