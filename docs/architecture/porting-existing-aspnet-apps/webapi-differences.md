---
title: ASP.NET Web API 2 と ASP.NET Core の比較
description: ASP.NET Web API 2 つのアプリと ASP.NET Core アプリの間で web Api はどのように異なりますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 93aa917174bce24fdf924f6372312c3972473289
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401344"
---
# <a name="compare-aspnet-web-api-2-and-aspnet-core"></a><span data-ttu-id="1b36a-103">ASP.NET Web API 2 と ASP.NET Core の比較</span><span class="sxs-lookup"><span data-stu-id="1b36a-103">Compare ASP.NET Web API 2 and ASP.NET Core</span></span>

<span data-ttu-id="1b36a-104">ASP.NET Core は ASP.NET Web API 2 に対する反復的な機能強化を提供しますが、Web API 2 を使用している開発者には慣れているはずです。</span><span class="sxs-lookup"><span data-stu-id="1b36a-104">ASP.NET Core offers iterative improvements to ASP.NET Web API 2, but should feel familiar to developers who have used Web API 2.</span></span> <span data-ttu-id="1b36a-105">ASP.NET Web API 2 は ASP.NET MVC と共に開発および出荷されました。</span><span class="sxs-lookup"><span data-stu-id="1b36a-105">ASP.NET Web API 2 was developed and shipped alongside ASP.NET MVC.</span></span> <span data-ttu-id="1b36a-106">このため、2つのアプローチには、属性ルーティングや依存関係の挿入など、似たような方法があります。</span><span class="sxs-lookup"><span data-stu-id="1b36a-106">This meant the two approaches had similar-but-different approaches to things like attribute routing and dependency injection.</span></span> <span data-ttu-id="1b36a-107">ASP.NET Core では、MVC と Web Api が区別されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="1b36a-107">In ASP.NET Core, there's no longer any distinction between MVC and Web APIs.</span></span> <span data-ttu-id="1b36a-108">ASP.NET MVC には、ビューベースのシナリオ、API エンドポイント、Razor Pages (および正常性チェックや SignalR などのその他のバリエーション) のサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1b36a-108">There's only ASP.NET MVC, which includes support for view-based scenarios, API endpoints, and Razor Pages (and other variations like health checks and SignalR).</span></span>

<span data-ttu-id="1b36a-109">.NET Core に組み込まれている Api は ASP.NET Core 内で一貫性と統合されるだけでなく、ASP.NET Web API 2 に構築された Api よりもはるかに簡単にテストできます。</span><span class="sxs-lookup"><span data-stu-id="1b36a-109">In addition to being consistent and unified within ASP.NET Core, APIs built in .NET Core are much easier to test than those built on ASP.NET Web API 2.</span></span> <span data-ttu-id="1b36a-110">[テストの違い](testing-differences.md)については、後で詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="1b36a-110">We'll cover [testing differences](testing-differences.md) in more detail in a moment.</span></span> <span data-ttu-id="1b36a-111">アプリケーションに対してメモリ内の要求を行うを作成できるテストホストで ASP.NET Core アプリをホストするための組み込みのサポート `HttpClient` は、自動テストを行う場合に大きな利点となります。</span><span class="sxs-lookup"><span data-stu-id="1b36a-111">The built-in support for hosting ASP.NET Core apps, in a test host that can create an `HttpClient` that makes in-memory requests to the app, is a huge benefit when it comes to automated testing.</span></span>

<span data-ttu-id="1b36a-112">ASP.NET Web API 2 から ASP.NET Core に移行する場合、移行は簡単です。</span><span class="sxs-lookup"><span data-stu-id="1b36a-112">When migrating from ASP.NET Web API 2 to ASP.NET Core, the transition is straightforward.</span></span> <span data-ttu-id="1b36a-113">大規模な膨張コントローラーがある場合は、それを分割する方法の1つとして、パッケージを使用する方法があります[。](https://www.nuget.org/packages/Ardalis.ApiEndpoints/)</span><span class="sxs-lookup"><span data-stu-id="1b36a-113">If you have large, bloated controllers, one approach you may consider to break them up is the use of the [Ardalis.ApiEndpoints](https://www.nuget.org/packages/Ardalis.ApiEndpoints/) NuGet packages.</span></span> <span data-ttu-id="1b36a-114">このパッケージは、各エンドポイントを独自の特定のクラスに分割し、必要に応じて、要求と応答の種類を関連付けます。</span><span class="sxs-lookup"><span data-stu-id="1b36a-114">This package breaks up each endpoint into its own specific class, with associated request and response types as appropriate.</span></span> <span data-ttu-id="1b36a-115">このアプローチで [は、ビューベースのコード編成での Razor Pages プランと同じ特典](comparing-razor-pages-aspnet-mvc.md)の多くが得られます。</span><span class="sxs-lookup"><span data-stu-id="1b36a-115">This approach yields many of [the same benefits as Razor Pages offer over view-based code organization](comparing-razor-pages-aspnet-mvc.md).</span></span>

## <a name="references"></a><span data-ttu-id="1b36a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b36a-116">References</span></span>

- [<span data-ttu-id="1b36a-117">ASP.NET Web API から ASP.NET Core への移行</span><span class="sxs-lookup"><span data-stu-id="1b36a-117">Migrate from ASP.NET Web API to ASP.NET Core</span></span>](/aspnet/core/migration/webapi)
- [<span data-ttu-id="1b36a-118">シャードのエンドポイント NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="1b36a-118">Ardalis.ApiEndpoints NuGet package</span></span>](https://www.nuget.org/packages/Ardalis.ApiEndpoints/)

>[!div class="step-by-step"]
><span data-ttu-id="1b36a-119">[前へ](comparing-razor-pages-aspnet-mvc.md)
>[次へ](authentication-differences.md)</span><span class="sxs-lookup"><span data-stu-id="1b36a-119">[Previous](comparing-razor-pages-aspnet-mvc.md)
[Next](authentication-differences.md)</span></span>
