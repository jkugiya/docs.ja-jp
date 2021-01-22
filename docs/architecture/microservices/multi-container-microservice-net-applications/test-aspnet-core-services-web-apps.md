---
title: ASP.NET Core サービスと Web アプリのテスト
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | コンテナーで ASP.NET Core サービスと Web アプリをテストするためのアーキテクチャについて調べる。
ms.date: 01/13/2021
ms.openlocfilehash: dfd0a320491f92154bc9e2804d56c00120224e62
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188004"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="06ea8-103">ASP.NET Core サービスと Web アプリのテスト</span><span class="sxs-lookup"><span data-stu-id="06ea8-103">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="06ea8-104">コントローラーは、すべての ASP.NET Core API サービスと ASP.NET MVC Web アプリケーションの中心になるものです。</span><span class="sxs-lookup"><span data-stu-id="06ea8-104">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="06ea8-105">そのため、アプリケーションが意図するとおりに動作するという信頼が必要です。</span><span class="sxs-lookup"><span data-stu-id="06ea8-105">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="06ea8-106">自動テストを行うと、この信頼が得られ、運用環境に提供する前にエラーを検出できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-106">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="06ea8-107">有効または無効な入力に基づくコントローラーの動作、および実行するビジネス操作の結果に基づくコントローラーの応答をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-107">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="06ea8-108">ただし、マイクロサービスに対してこれらの種類のテストを実行すべきです。</span><span class="sxs-lookup"><span data-stu-id="06ea8-108">However, you should have these types of tests for your microservices:</span></span>

- <span data-ttu-id="06ea8-109">単体テスト。</span><span class="sxs-lookup"><span data-stu-id="06ea8-109">Unit tests.</span></span> <span data-ttu-id="06ea8-110">これらのテストにより、アプリケーションの個々のコンポーネントが想定どおりに動作することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-110">These tests ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="06ea8-111">アサーションは、コンポーネント API をテストします。</span><span class="sxs-lookup"><span data-stu-id="06ea8-111">Assertions test the component API.</span></span>

- <span data-ttu-id="06ea8-112">統合テスト。</span><span class="sxs-lookup"><span data-stu-id="06ea8-112">Integration tests.</span></span> <span data-ttu-id="06ea8-113">これらのテストにより、コンポーネント間の相互作用が、データベースなどの外部成果物に対して想定どおりに動作することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-113">These tests ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="06ea8-114">アサーションは、コンポーネント API や UI をテストしたり、データベース I/O やログ記録などの操作の副作用をテストしたりできます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-114">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

- <span data-ttu-id="06ea8-115">各マイクロサービスの機能テスト。</span><span class="sxs-lookup"><span data-stu-id="06ea8-115">Functional tests for each microservice.</span></span> <span data-ttu-id="06ea8-116">これらのテストにより、ユーザーの観点から、アプリケーションが想定どおりに動作することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-116">These tests ensure that the application works as expected from the user's perspective.</span></span>

- <span data-ttu-id="06ea8-117">サービス テスト。</span><span class="sxs-lookup"><span data-stu-id="06ea8-117">Service tests.</span></span> <span data-ttu-id="06ea8-118">これらのテストでは、複数のサービスを同時にテストするなど、エンドツーエンド サービスのユース ケースが確実にテストされます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-118">These tests ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="06ea8-119">この種類のテストでは、まず環境を準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-119">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="06ea8-120">この場合、サービスを開始することを意味します (たとえば、docker-compose up を使用します)。</span><span class="sxs-lookup"><span data-stu-id="06ea8-120">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="06ea8-121">ASP.NET Core Web API の単体テストの実装</span><span class="sxs-lookup"><span data-stu-id="06ea8-121">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="06ea8-122">単体テストでは、アプリケーションの一部をインフラストラクチャや依存関係から切り離してテストします。</span><span class="sxs-lookup"><span data-stu-id="06ea8-122">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="06ea8-123">コントローラー ロジックの単体テストを行うときは、それが依存しているものやフレームワーク自体の動作ではなく、単一のアクションやメソッドの内容のみをテストします。</span><span class="sxs-lookup"><span data-stu-id="06ea8-123">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="06ea8-124">単体テストではコンポーネント間の相互作用の問題は検出しません。これは、統合テストの目的です。</span><span class="sxs-lookup"><span data-stu-id="06ea8-124">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="06ea8-125">コントローラーのアクションの単体テストでは、その動作にだけ注目するようにします。</span><span class="sxs-lookup"><span data-stu-id="06ea8-125">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="06ea8-126">コント ローラーの単体テストは、フィルター、ルーティング、モデル バインド (ViewModel または DTO への要求データのマッピング) などを回避できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-126">A controller unit test avoids things like filters, routing, or model binding (the mapping of request data to a ViewModel or DTO).</span></span> <span data-ttu-id="06ea8-127">1 つの事柄だけに注目してテストするため、一般に、単体テストは簡単に記述してすばやく実行できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-127">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="06ea8-128">適切に記述された一連の単体テストは、大きなオーバーヘッドなしに頻繁に実行できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-128">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="06ea8-129">単体テストは、xUnit.net、MSTest、Moq、NUnit などのテスト フレームワークに基づいて実装されます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-129">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="06ea8-130">eShopOnContainers サンプル アプリケーションでは、xUnit を使用します。</span><span class="sxs-lookup"><span data-stu-id="06ea8-130">For the eShopOnContainers sample application, we are using xUnit.</span></span>

<span data-ttu-id="06ea8-131">Web API コントローラーの単体テストを記述する際には、C\# で new キーワードを直接使用してコントローラー クラスをインスタンス化することにより、できるだけ速くテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="06ea8-131">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="06ea8-132">次の例では、[xUnit](https://xunit.net/) をテスト フレームワークとして使用し、これを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="06ea8-132">The following example shows how to do this when using [xUnit](https://xunit.net/) as the Test framework.</span></span>

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();

    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object,
        _basketServiceMock.Object,
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);

    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="06ea8-133">各マイクロサービスの統合テストと機能テストの実装</span><span class="sxs-lookup"><span data-stu-id="06ea8-133">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="06ea8-134">前述のように、統合テストと機能テストにはさまざまな目的と目標があります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-134">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="06ea8-135">しかし、ASP.NET Core コントローラーをテストするときにそれらのテストを実装する方法は似ているため、このセクションでは統合テストに注目します。</span><span class="sxs-lookup"><span data-stu-id="06ea8-135">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="06ea8-136">統合テストは、アプリケーションのコンポーネントが、組み立てたときに正しく動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="06ea8-136">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="06ea8-137">ASP.NET Core は、単体テスト フレームワークと組み込みのテスト Web ホストを使用した統合テストをサポートします。これは、ネットワークのオーバーヘッドなしで要求を処理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-137">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="06ea8-138">単体テストとは異なり、統合テストにはしばしば、データベース、ファイル システム、ネットワーク リソース、Web 要求と応答などのアプリケーション インフラストラクチャの問題があります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-138">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="06ea8-139">単体テストでは、これらの問題の代わりにフェイクやモック オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="06ea8-139">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="06ea8-140">しかし、統合テストの目的は、対象のシステムがこれらの問題のシステムで期待どおりに動作することを確認することであるため、統合テストではフェイクやモック オブジェクトを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="06ea8-140">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="06ea8-141">代わりに、データベース アクセスや他のサービスからのサービス呼び出しなどのインフラストラクチャを含めます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-141">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="06ea8-142">統合テストは、単体テストより大きなコード セグメントを実行し、インフラストラクチャ要素に依存するため、多くの場合、単体テストと比べて桁違いに低速になります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-142">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="06ea8-143">そのため、記述して実行する統合テストの数を制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="06ea8-143">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="06ea8-144">ASP.NET Core には、ネットワークのオーバーヘッドなしで HTTP 要求を処理するために使用できる、組み込みのテスト Web ホストが含まれています。これは、実際の Web ホストの使用時よりもそれらのテストをより速く実行できるということです。</span><span class="sxs-lookup"><span data-stu-id="06ea8-144">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster than when using a real web host.</span></span> <span data-ttu-id="06ea8-145">テスト Web ホスト (TestServer) は、Microsoft.AspNetCore.TestHost として NuGet コンポーネントでご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-145">The test web host (TestServer) is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="06ea8-146">これを統合テスト プロジェクトに追加して、ASP.NET Core アプリケーションをホストするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-146">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="06ea8-147">次のコードからわかるように、ASP.NET Core コントローラーの統合テストを作成すると、テスト ホストによってコントローラーがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-147">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="06ea8-148">この機能は、HTTP 要求に相当しますが、より速く実行されます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-148">This functionality is comparable to an HTTP request, but it runs faster.</span></span>

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a><span data-ttu-id="06ea8-149">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="06ea8-149">Additional resources</span></span>

- <span data-ttu-id="06ea8-150">**Steve Smith。コントローラーのテスト** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="06ea8-150">**Steve Smith. Testing controllers** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/mvc/controllers/testing](/aspnet/core/mvc/controllers/testing)

- <span data-ttu-id="06ea8-151">**Steve Smith。統合テスト** (ASP.NET Core) </span><span class="sxs-lookup"><span data-stu-id="06ea8-151">**Steve Smith. Integration testing** (ASP.NET Core) </span></span>\
    [https://docs.microsoft.com/aspnet/core/test/integration-tests](/aspnet/core/test/integration-tests)

- <span data-ttu-id="06ea8-152">**dotnet テストを使用した .NET での単体テスト** </span><span class="sxs-lookup"><span data-stu-id="06ea8-152">**Unit testing in .NET using dotnet test** </span></span>\
    [https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test](../../../core/testing/unit-testing-with-dotnet-test.md)

- <span data-ttu-id="06ea8-153">**xUnit.net**。</span><span class="sxs-lookup"><span data-stu-id="06ea8-153">**xUnit.net**.</span></span> <span data-ttu-id="06ea8-154">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="06ea8-154">Official site.</span></span> \
    <https://xunit.net/>

- <span data-ttu-id="06ea8-155">**単体テストの基本。**</span><span class="sxs-lookup"><span data-stu-id="06ea8-155">**Unit Test Basics.**</span></span> \
    [https://docs.microsoft.com/visualstudio/test/unit-test-basics](/visualstudio/test/unit-test-basics)

- <span data-ttu-id="06ea8-156">**Moq**。</span><span class="sxs-lookup"><span data-stu-id="06ea8-156">**Moq**.</span></span> <span data-ttu-id="06ea8-157">GitHub リポジトリ。</span><span class="sxs-lookup"><span data-stu-id="06ea8-157">GitHub repo.</span></span> \
    <https://github.com/moq/moq>

- <span data-ttu-id="06ea8-158">**NUnit**。</span><span class="sxs-lookup"><span data-stu-id="06ea8-158">**NUnit**.</span></span> <span data-ttu-id="06ea8-159">公式サイト。</span><span class="sxs-lookup"><span data-stu-id="06ea8-159">Official site.</span></span> \
    <https://nunit.org/>

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="06ea8-160">マルチコンテナー アプリケーションでのサービス テストの実装</span><span class="sxs-lookup"><span data-stu-id="06ea8-160">Implementing service tests on a multi-container application</span></span>

<span data-ttu-id="06ea8-161">前述のとおり、マルチコンテナー アプリケーションをテストする際、すべてのマイクロサービスを Docker ホスト内やコンテナー クラスター内で実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-161">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="06ea8-162">いくつかのマイクロサービスが関係する複数の操作を含むエンド ツー エンドのサービス テストでは、docker-compose up (または、オーケストレーターを使用している場合は相当するメカニズム) を実行して、Docker ホストでアプリケーション全体を展開して起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-162">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="06ea8-163">アプリケーション全体とそのすべてのサービスが実行されると、エンド ツー エンドの統合テストと機能のテストを実行できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-163">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="06ea8-164">使用できる方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-164">There are a few approaches you can use.</span></span> <span data-ttu-id="06ea8-165">アプリケーションの展開に使用する docker-compose.yml ファイルでは、ソリューション レベルで [dotnet test](../../../core/tools/dotnet-test.md) を使用してエントリ ポイントを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-165">In the docker-compose.yml file that you use to deploy the application at the solution level you can expand the entry point to use [dotnet test](../../../core/tools/dotnet-test.md).</span></span> <span data-ttu-id="06ea8-166">対象とするイメージで、テストを実行する別の Compose ファイルを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-166">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="06ea8-167">コンテナー上のマイクロサービスとデータベースを含む統合テストで別の Compose ファイルを使用すれば、テストを実行する前に、関連するデータが元の状態に常にリセットされることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-167">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="06ea8-168">Compose アプリケーションが起動し実行されると、Visual Studio を実行している場合はブレークポイントと例外を活用できます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-168">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="06ea8-169">または、Azure DevOps Services の CI パイプラインや Docker コンテナーをサポートする他の CI/CD システムで、統合テストを自動的に実行することができます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-169">Or you can run the integration tests automatically in your CI pipeline in Azure DevOps Services or any other CI/CD system that supports Docker containers.</span></span>

## <a name="testing-in-eshoponcontainers"></a><span data-ttu-id="06ea8-170">eShopOnContainers でテストする</span><span class="sxs-lookup"><span data-stu-id="06ea8-170">Testing in eShopOnContainers</span></span>

<span data-ttu-id="06ea8-171">参照アプリケーション (eShopOnContainers) のテストが再構築され、次の 4 つのカテゴリができました。</span><span class="sxs-lookup"><span data-stu-id="06ea8-171">The reference application (eShopOnContainers) tests were recently restructured and now there are four categories:</span></span>

1. <span data-ttu-id="06ea8-172">**単体** テスト。 **{MicroserviceName}.UnitTests** プロジェクトに含まれている、従来の単純で定期的な単体テスト</span><span class="sxs-lookup"><span data-stu-id="06ea8-172">**Unit** tests, just plain old regular unit tests, contained in the **{MicroserviceName}.UnitTests** projects</span></span>

2. <span data-ttu-id="06ea8-173">**マイクロサービスの機能/統合テスト**。各マイクロサービスのインフラストラクチャに関するテスト ケースを含みます。他からは分離されていて、 **{MicroserviceName}.FunctionalTests** プロジェクトに含まれています。</span><span class="sxs-lookup"><span data-stu-id="06ea8-173">**Microservice functional/integration tests**, with test cases involving the infrastructure for each microservice but isolated from the others and are contained in the **{MicroserviceName}.FunctionalTests** projects.</span></span>

3. <span data-ttu-id="06ea8-174">**アプリケーションの機能/統合テスト**。マイクロサービスの統合に集中します。複数のマイクロサービスを実行するテスト ケースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="06ea8-174">**Application functional/integration tests**, which focus on microservices integration, with test cases that exert several microservices.</span></span> <span data-ttu-id="06ea8-175">これらのテストはプロジェクト **Application.FunctionalTests** にあります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-175">These tests are located in project **Application.FunctionalTests**.</span></span>

<span data-ttu-id="06ea8-176">図 6-25 に示すように、単体テストと統合テストはマイクロサービス プロジェクト内のテスト フォルダーに編成されますが、アプリケーションとロード テストはルート フォルダー下で個別に管理されます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-176">While unit and integration tests are organized in a test folder within the microservice project, application and load tests are managed separately under the root folder, as shown in Figure 6-25.</span></span>

![ソリューション内のテスト プロジェクトの一部を指している VS のスクリーンショット。](./media/test-aspnet-core-services-web-apps/eshoponcontainers-test-folder-structure.png)

<span data-ttu-id="06ea8-178">**図 6-25**。</span><span class="sxs-lookup"><span data-stu-id="06ea8-178">**Figure 6-25**.</span></span> <span data-ttu-id="06ea8-179">eShopOnContainers のテスト フォルダーの構造</span><span class="sxs-lookup"><span data-stu-id="06ea8-179">Test folder structure in eShopOnContainers</span></span>

<span data-ttu-id="06ea8-180">マイクロサービスとアプリケーションの機能または統合テストは定期テスト ランナーを使用して Visual Studio から実行されますが、最初にソリューションの test フォルダーに含まれる一連の docker-compose ファイルを用いて必要なインフラストラクチャ サービスを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-180">Microservice and Application functional/integration tests are run from Visual Studio, using the regular tests runner, but first you need to start the required infrastructure services, with a set of docker-compose files contained in the solution test folder:</span></span>

<span data-ttu-id="06ea8-181">**docker-compose-test.yml**</span><span class="sxs-lookup"><span data-stu-id="06ea8-181">**docker-compose-test.yml**</span></span>

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
  nosqldata:
    image: mongo
```

<span data-ttu-id="06ea8-182">**docker-compose-test.override.yml**</span><span class="sxs-lookup"><span data-stu-id="06ea8-182">**docker-compose-test.override.yml**</span></span>

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
```

<span data-ttu-id="06ea8-183">そのため、機能/統合テストを実行するには、最初にソリューションの test フォルダーから次のコマンドを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="06ea8-183">So, to run the functional/integration tests you must first run this command, from the solution test folder:</span></span>

```console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

<span data-ttu-id="06ea8-184">ご覧のように、これらの docker-compose ファイルでは Redis、RabbitMQ、SQL Server、および MongoDB のマイクロサービスのみが開始されます。</span><span class="sxs-lookup"><span data-stu-id="06ea8-184">As you can see, these docker-compose files only start the Redis, RabbitMQ, SQL Server, and MongoDB microservices.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="06ea8-185">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="06ea8-185">Additional resources</span></span>

- <span data-ttu-id="06ea8-186">eShopOnContainers の **ユニットと統合テスト** </span><span class="sxs-lookup"><span data-stu-id="06ea8-186">**Unit & Integration testing** on the eShopOnContainers </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/wiki/Unit-and-integration-testing>

- <span data-ttu-id="06ea8-187">eShopOnContainers の **ロード テスト** </span><span class="sxs-lookup"><span data-stu-id="06ea8-187">**Load testing** on the eShopOnContainers </span></span>\
    <https://github.com/dotnet-architecture/eShopOnContainers/wiki/Load-testing>

> [!div class="step-by-step"]
> <span data-ttu-id="06ea8-188">[前へ](subscribe-events.md)
> [次へ](background-tasks-with-ihostedservice.md)</span><span class="sxs-lookup"><span data-stu-id="06ea8-188">[Previous](subscribe-events.md)
[Next](background-tasks-with-ihostedservice.md)</span></span>
