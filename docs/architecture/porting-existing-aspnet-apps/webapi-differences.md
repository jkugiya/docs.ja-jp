---
title: ASP.NET Web API 2 と ASP.NET Core の比較
description: ASP.NET Web API 2 アプリと ASP.NET Core アプリとで、Web API はどのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 93aa917174bce24fdf924f6372312c3972473289
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401344"
---
# <a name="compare-aspnet-web-api-2-and-aspnet-core"></a><span data-ttu-id="630cd-103">ASP.NET Web API 2 と ASP.NET Core の比較</span><span class="sxs-lookup"><span data-stu-id="630cd-103">Compare ASP.NET Web API 2 and ASP.NET Core</span></span>

<span data-ttu-id="630cd-104">ASP.NET Core では ASP.NET Web API 2 に対する反復的な機能強化が提供されますが、Web API 2 を使用してきた開発者にとっては馴染みやすいでしょう。</span><span class="sxs-lookup"><span data-stu-id="630cd-104">ASP.NET Core offers iterative improvements to ASP.NET Web API 2, but should feel familiar to developers who have used Web API 2.</span></span> <span data-ttu-id="630cd-105">ASP.NET Web API 2 は ASP.NET MVC と共に開発され、出荷されました。</span><span class="sxs-lookup"><span data-stu-id="630cd-105">ASP.NET Web API 2 was developed and shipped alongside ASP.NET MVC.</span></span> <span data-ttu-id="630cd-106">したがって、これらの 2 つのアプローチでは、属性ルーティングや依存関係の挿入などに対して似ているが異なるアプローチが採用されています。</span><span class="sxs-lookup"><span data-stu-id="630cd-106">This meant the two approaches had similar-but-different approaches to things like attribute routing and dependency injection.</span></span> <span data-ttu-id="630cd-107">ASP.NET Core では、MVC と Web API の区別がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="630cd-107">In ASP.NET Core, there's no longer any distinction between MVC and Web APIs.</span></span> <span data-ttu-id="630cd-108">存在するのは ASP.NET MVC のみで、これにはビューベースのシナリオ、API エンドポイント、Razor Pages (および正常性チェックや SignalR などのその他のバリエーション) のサポートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="630cd-108">There's only ASP.NET MVC, which includes support for view-based scenarios, API endpoints, and Razor Pages (and other variations like health checks and SignalR).</span></span>

<span data-ttu-id="630cd-109">.NET Core に組み込まれている API は、ASP.NET Core 内で一貫していて統合されているのに加えて、ASP.NET Web API 2 上に構築されたものよりもはるかにテストが簡単です。</span><span class="sxs-lookup"><span data-stu-id="630cd-109">In addition to being consistent and unified within ASP.NET Core, APIs built in .NET Core are much easier to test than those built on ASP.NET Web API 2.</span></span> <span data-ttu-id="630cd-110">[テストの違い](testing-differences.md)については、後で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="630cd-110">We'll cover [testing differences](testing-differences.md) in more detail in a moment.</span></span> <span data-ttu-id="630cd-111">アプリに対してメモリ内の要求を行う `HttpClient` を作成できるテスト ホスト内の、ASP.NET Core アプリをホストするための組み込みのサポートは、自動テストに関して非常に大きなベネフィットとなります。</span><span class="sxs-lookup"><span data-stu-id="630cd-111">The built-in support for hosting ASP.NET Core apps, in a test host that can create an `HttpClient` that makes in-memory requests to the app, is a huge benefit when it comes to automated testing.</span></span>

<span data-ttu-id="630cd-112">ASP.NET Web API 2 から ASP.NET Core に移行する場合、切り替えは簡単です。</span><span class="sxs-lookup"><span data-stu-id="630cd-112">When migrating from ASP.NET Web API 2 to ASP.NET Core, the transition is straightforward.</span></span> <span data-ttu-id="630cd-113">大規模な、肥大化したコントローラーがある場合、それを分割するために検討できる 1 つのアプローチは、[Ardalis.ApiEndpoints](https://www.nuget.org/packages/Ardalis.ApiEndpoints/) NuGet パッケージを使用することです。</span><span class="sxs-lookup"><span data-stu-id="630cd-113">If you have large, bloated controllers, one approach you may consider to break them up is the use of the [Ardalis.ApiEndpoints](https://www.nuget.org/packages/Ardalis.ApiEndpoints/) NuGet packages.</span></span> <span data-ttu-id="630cd-114">このパッケージは、各エンドポイントを、必要に応じて関連する要求および応答の種類と共に、独自の固有のクラスに分割します。</span><span class="sxs-lookup"><span data-stu-id="630cd-114">This package breaks up each endpoint into its own specific class, with associated request and response types as appropriate.</span></span> <span data-ttu-id="630cd-115">このアプローチでは、ビューベースのコード編成と比べたときに [Razor Pages で得られるのと同じベネフィット](comparing-razor-pages-aspnet-mvc.md)の多くが得られます。</span><span class="sxs-lookup"><span data-stu-id="630cd-115">This approach yields many of [the same benefits as Razor Pages offer over view-based code organization](comparing-razor-pages-aspnet-mvc.md).</span></span>

## <a name="references"></a><span data-ttu-id="630cd-116">リファレンス</span><span class="sxs-lookup"><span data-stu-id="630cd-116">References</span></span>

- [<span data-ttu-id="630cd-117">ASP.NET Web API から ASP.NET Core への移行</span><span class="sxs-lookup"><span data-stu-id="630cd-117">Migrate from ASP.NET Web API to ASP.NET Core</span></span>](/aspnet/core/migration/webapi)
- [<span data-ttu-id="630cd-118">Ardalis.ApiEndpoints NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="630cd-118">Ardalis.ApiEndpoints NuGet package</span></span>](https://www.nuget.org/packages/Ardalis.ApiEndpoints/)

>[!div class="step-by-step"]
><span data-ttu-id="630cd-119">[前へ](comparing-razor-pages-aspnet-mvc.md)
>[次へ](authentication-differences.md)</span><span class="sxs-lookup"><span data-stu-id="630cd-119">[Previous](comparing-razor-pages-aspnet-mvc.md)
[Next](authentication-differences.md)</span></span>
