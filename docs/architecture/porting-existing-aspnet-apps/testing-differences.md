---
title: ASP.NET MVC と ASP.NET Core のテスト オプションの比較
description: ASP.NET MVC アプリと ASP.NET Core アプリでは、テストはどのように異なるでしょうか?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: f0907d09df058c07ed993c251868f00bc28b0736
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401346"
---
# <a name="compare-testing-options-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="6c707-103">ASP.NET MVC と ASP.NET Core のテスト オプションの比較</span><span class="sxs-lookup"><span data-stu-id="6c707-103">Compare testing options between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="6c707-104">ASP.NET MVC アプリではコントローラーの単体テストがサポートされていますが、このアプローチでは多くの場合、ルーティング、認可、モデル バインド、モデル検証、フィルターなどの多くの MVC 機能が省略されます。</span><span class="sxs-lookup"><span data-stu-id="6c707-104">ASP.NET MVC apps support unit testing of controllers, but this approach often omits many MVC features like routing, authorization, model binding, model validation, filters, and more.</span></span> <span data-ttu-id="6c707-105">コントローラー アクション自体に含まれるロジックに加えてこれらの MVC 機能をテストするには、多くの場合、アプリを展開してから Selenium などのツールを使用してテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c707-105">To test these MVC features in addition to the logic within the controller action itself, frequently the app would need to be deployed and then tested with a tool like Selenium.</span></span> <span data-ttu-id="6c707-106">これらのテストは、アプリ全体をホストして実行しなくても実行できる一般的な単体テストよりもはるかにコストが高く、より不安定で低速です。</span><span class="sxs-lookup"><span data-stu-id="6c707-106">These tests are substantially more expensive, more brittle, and slower than typical unit tests that can be run without the need for hosting and running the entire app.</span></span>

<span data-ttu-id="6c707-107">ASP.NET MVC コントローラーと同様に [ASP.NET Core コントローラーを単体テストする](/aspnet/core/mvc/controllers/testing)ことは可能ですが、同じ制限があります。</span><span class="sxs-lookup"><span data-stu-id="6c707-107">[ASP.NET Core controllers can be unit tested](/aspnet/core/mvc/controllers/testing) just like ASP.NET MVC controllers, but with the same limitations.</span></span> <span data-ttu-id="6c707-108">しかし、[ASP.NET Core では、高速で作成が簡単な統合テスト](/aspnet/core/test/integration-tests)もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="6c707-108">However, [ASP.NET Core supports fast, easy-to-author integration tests](/aspnet/core/test/integration-tests) as well.</span></span> <span data-ttu-id="6c707-109">統合テストは `TestHost` クラスによってホストされ、通常は、アプリの依存関係をオーバーライドまたは置換できるカスタム `WebApplicationFactory` 内で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6c707-109">Integration tests are hosted by a `TestHost` class and are typically configured in a custom `WebApplicationFactory` that can override or replace app dependencies.</span></span> <span data-ttu-id="6c707-110">たとえば、統合テスト中にアプリが別のデータ ソースをターゲットとし、電子メールを送信するサービスをフェイクまたはモックの実装に置き換えることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="6c707-110">For instance, frequently during integration tests the app will target a different data source and may replace services that send emails with fake or mock implementations.</span></span>

<span data-ttu-id="6c707-111">ASP.NET MVC と Web API では、ASP.NET Core で利用できる統合テスト シナリオのようなものはサポートされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="6c707-111">ASP.NET MVC and Web API did not support anything like the integration testing scenarios available in ASP.NET Core.</span></span> <span data-ttu-id="6c707-112">移行作業では、新しく移行したシステム用の統合テストを作成するための時間を取って、そのシステムが現在および将来も想定どおりに動作することを確認できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c707-112">In any migration effort, you should allocate time to write some integration tests for your newly migrated system to ensure it's working as expected and continues to do so.</span></span> <span data-ttu-id="6c707-113">移行前に Web アプリのロジックのテストを作成していなかった場合でも、ASP.NET Core に移行する際にそうすることを検討すべきです。</span><span class="sxs-lookup"><span data-stu-id="6c707-113">Even if you weren't writing tests of your web app logic before the migration, you should strongly consider doing so as you move to ASP.NET Core.</span></span>

## <a name="references"></a><span data-ttu-id="6c707-114">リファレンス</span><span class="sxs-lookup"><span data-stu-id="6c707-114">References</span></span>

- [<span data-ttu-id="6c707-115">ASP.NET MVC アプリケーションの単体テストを作成する</span><span class="sxs-lookup"><span data-stu-id="6c707-115">Creating Unit Tests for ASP.NET MVC Applications</span></span>](/aspnet/mvc/overview/older-versions-1/unit-testing/creating-unit-tests-for-asp-net-mvc-applications-cs)
- [<span data-ttu-id="6c707-116">ASP.NET Core でコントローラーのロジックの単体テストを行う</span><span class="sxs-lookup"><span data-stu-id="6c707-116">Unit test controller logic in ASP.NET Core</span></span>](/aspnet/core/mvc/controllers/testing)
- [<span data-ttu-id="6c707-117">ASP.NET Core での統合テスト</span><span class="sxs-lookup"><span data-stu-id="6c707-117">Integration tests in ASP.NET Core</span></span>](/aspnet/core/test/integration-tests)

>[!div class="step-by-step"]
><span data-ttu-id="6c707-118">[前へ](signalr-differences.md)
>[次へ](migrate-large-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="6c707-118">[Previous](signalr-differences.md)
[Next](migrate-large-solutions.md)</span></span>
