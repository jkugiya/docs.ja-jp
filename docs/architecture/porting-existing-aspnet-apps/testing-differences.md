---
title: ASP.NET MVC と ASP.NET Core 間のテストオプションを比較する
description: ASP.NET MVC アプリと ASP.NET Core アプリでは、テストはどのように異なりますか。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: f0907d09df058c07ed993c251868f00bc28b0736
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401346"
---
# <a name="compare-testing-options-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="d4874-103">ASP.NET MVC と ASP.NET Core 間のテストオプションを比較する</span><span class="sxs-lookup"><span data-stu-id="d4874-103">Compare testing options between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="d4874-104">ASP.NET MVC アプリはコントローラーの単体テストをサポートしていますが、このアプローチでは多くの場合、ルーティング、承認、モデルバインド、モデル検証、フィルターなどの多くの MVC 機能が省略されます。</span><span class="sxs-lookup"><span data-stu-id="d4874-104">ASP.NET MVC apps support unit testing of controllers, but this approach often omits many MVC features like routing, authorization, model binding, model validation, filters, and more.</span></span> <span data-ttu-id="d4874-105">コントローラーアクション自体内のロジックに加えてこれらの MVC 機能をテストするには、多くの場合、アプリをデプロイし、Selenium などのツールでテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4874-105">To test these MVC features in addition to the logic within the controller action itself, frequently the app would need to be deployed and then tested with a tool like Selenium.</span></span> <span data-ttu-id="d4874-106">これらのテストは、アプリ全体をホストして実行しなくても、実行できる一般的な単体テストよりもはるかにコストが高く、不安定で、動作が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="d4874-106">These tests are substantially more expensive, more brittle, and slower than typical unit tests that can be run without the need for hosting and running the entire app.</span></span>

<span data-ttu-id="d4874-107">[ASP.NET Core コントローラー](/aspnet/core/mvc/controllers/testing) は、ASP.NET MVC コントローラーと同様に単体テストが可能ですが、同じ制限があります。</span><span class="sxs-lookup"><span data-stu-id="d4874-107">[ASP.NET Core controllers can be unit tested](/aspnet/core/mvc/controllers/testing) just like ASP.NET MVC controllers, but with the same limitations.</span></span> <span data-ttu-id="d4874-108">ただし、 [ASP.NET Core は、高速で使いやすい統合テストもサポート](/aspnet/core/test/integration-tests) しています。</span><span class="sxs-lookup"><span data-stu-id="d4874-108">However, [ASP.NET Core supports fast, easy-to-author integration tests](/aspnet/core/test/integration-tests) as well.</span></span> <span data-ttu-id="d4874-109">統合テストはクラスによってホストされ、 `TestHost` 通常は、 `WebApplicationFactory` アプリの依存関係をオーバーライドまたは置き換えることができるカスタムで構成されます。</span><span class="sxs-lookup"><span data-stu-id="d4874-109">Integration tests are hosted by a `TestHost` class and are typically configured in a custom `WebApplicationFactory` that can override or replace app dependencies.</span></span> <span data-ttu-id="d4874-110">たとえば、統合テスト中に多くの場合、アプリは別のデータソースを対象とし、フェイクまたはモックの実装で電子メールを送信するサービスを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="d4874-110">For instance, frequently during integration tests the app will target a different data source and may replace services that send emails with fake or mock implementations.</span></span>

<span data-ttu-id="d4874-111">ASP.NET MVC および Web API は、ASP.NET Core で使用できる統合テストシナリオのようなものをサポートしていませんでした。</span><span class="sxs-lookup"><span data-stu-id="d4874-111">ASP.NET MVC and Web API did not support anything like the integration testing scenarios available in ASP.NET Core.</span></span> <span data-ttu-id="d4874-112">移行作業では、新しく移行されたシステムの統合テストを作成するための時間を割り当てて、想定どおりに動作することを確認し、そのまま続行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4874-112">In any migration effort, you should allocate time to write some integration tests for your newly migrated system to ensure it's working as expected and continues to do so.</span></span> <span data-ttu-id="d4874-113">移行の前に web アプリのロジックのテストを作成していない場合でも、ASP.NET Core に移行する際には、これを行うことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d4874-113">Even if you weren't writing tests of your web app logic before the migration, you should strongly consider doing so as you move to ASP.NET Core.</span></span>

## <a name="references"></a><span data-ttu-id="d4874-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4874-114">References</span></span>

- [<span data-ttu-id="d4874-115">ASP.NET MVC アプリケーションの単体テストを作成する</span><span class="sxs-lookup"><span data-stu-id="d4874-115">Creating Unit Tests for ASP.NET MVC Applications</span></span>](/aspnet/mvc/overview/older-versions-1/unit-testing/creating-unit-tests-for-asp-net-mvc-applications-cs)
- [<span data-ttu-id="d4874-116">ASP.NET Core でコントローラーのロジックの単体テストを行う</span><span class="sxs-lookup"><span data-stu-id="d4874-116">Unit test controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [<span data-ttu-id="d4874-117">ASP.NET Core での統合テスト</span><span class="sxs-lookup"><span data-stu-id="d4874-117">Integration tests in ASP.NET Core</span></span>](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
><span data-ttu-id="d4874-118">[前へ](signalr-differences.md)
>[次へ](migrate-large-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="d4874-118">[Previous](signalr-differences.md)
[Next](migrate-large-solutions.md)</span></span>
