---
title: 正常性の監視
description: 正常性の監視を実施する 1 つの方法を探ります。
ms.date: 01/13/2021
ms.openlocfilehash: 4b85193c260b950b0c7a1c97ca5c83dfc87e5fb3
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189064"
---
# <a name="health-monitoring"></a><span data-ttu-id="6266c-103">正常性の監視</span><span class="sxs-lookup"><span data-stu-id="6266c-103">Health monitoring</span></span>

<span data-ttu-id="6266c-104">正常性を監視することで、コンテナーとマイクロサービスの状態に関する情報をほぼリアルタイムに得ることができます。</span><span class="sxs-lookup"><span data-stu-id="6266c-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="6266c-105">正常性の監視はマイクロサービス運用の複数の側面において不可欠であり、オーケストレーターで段階的に部分的なアプリケーションのアップグレードを行う際に特に重要です。</span><span class="sxs-lookup"><span data-stu-id="6266c-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="6266c-106">マイクロサービス ベースのアプリケーションでは、多くの場合、ハートビートまたは正常性チェックを使用して、パフォーマンス モニター、スケジューラー、およびオーケストレーターで多数のサービスを追跡できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6266c-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="6266c-107">サービスが必要に応じて、またはスケジュールに従って、ある種の "アライブ" シグナルを送信できない場合、更新プログラムの展開時にアプリケーションがリスクに直面する可能性があります。あるいは、単に障害の検出が遅すぎたために障害の連鎖を防ぐことができず、最終的に大規模な停止が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6266c-107">If services cannot send some sort of "I'm alive" signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="6266c-108">標準的なモデルでは、サービスは状態に関するレポートを送信し、その情報が集約され、アプリケーションの正常性状態の概要が提供されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="6266c-109">オーケストレーターを使用する場合は、オーケストレーターのクラスターに正常性情報を提供することができるため、クラスターは適切に機能できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-109">If you're using an orchestrator, you can provide health information to your orchestrator's cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="6266c-110">アプリケーション用にカスタマイズされている高品質の正常性レポートに投資する場合、実行中のアプリケーションの問題をはるかに簡単に検出して修正することができます。</span><span class="sxs-lookup"><span data-stu-id="6266c-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="6266c-111">ASP.NET Core サービスでの正常性チェックを実装する</span><span class="sxs-lookup"><span data-stu-id="6266c-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="6266c-112">ASP.NET Core のマイクロサービスまたは Web アプリケーションを開発するとき、ASP .NET Core 2.2 でリリースされた組み込みの正常性チェック機能 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span></span> <span data-ttu-id="6266c-113">多くの ASP.NET Core 機能と同様に、正常性チェックには一連のサービスとミドルウェアが伴います。</span><span class="sxs-lookup"><span data-stu-id="6266c-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="6266c-114">正常性チェックのサービスとミドルウェアは使いやすく、アプリケーションに必要な外部リソースがあれば (SQL Server データベースやリモート API など)、それが正しく動作していることを検証できる機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="6266c-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="6266c-115">この機能を使用すれば、リソースが正常であるかどうかを判断することもできます。これについては後で説明します。</span><span class="sxs-lookup"><span data-stu-id="6266c-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="6266c-116">この機能を効果的に使用するには、まず、マイクロサービスでサービスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6266c-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="6266c-117">次に、正常性レポートのクエリを実行するフロント エンド アプリケーションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="6266c-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="6266c-118">このフロント エンド アプリケーションはカスタム レポート アプリケーションである場合があります。また、正常性状態に応じて対応できるオーケストレーター自体である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6266c-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="6266c-119">バック エンド ASP.NET マイクロサービス内で HealthChecks 機能を使用する</span><span class="sxs-lookup"><span data-stu-id="6266c-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="6266c-120">このセクションでは、[Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) パッケージを使用するときに、サンプル ASP.NET Core 3.1 Web API アプリケーションに HealthChecks 機能を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6266c-120">In this section, you'll learn how to implement the HealthChecks feature in a sample ASP.NET Core 3.1 Web API application when using the [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) package.</span></span> <span data-ttu-id="6266c-121">eShopOnContainers のような大規模のマイクロサービスでこの機能を実装する方法については、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="6266c-121">The Implementation of this feature in a large-scale microservices like the eShopOnContainers is explained in the next section.</span></span>

<span data-ttu-id="6266c-122">開始するには、各マイクロサービスの正常性状態の構成要素を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6266c-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="6266c-123">このサンプル アプリケーションでは、API が HTTP 経由でアクセス可能であり、関連する SQL Server データベースも使用できる場合、マイクロサービスが正常であると定義します。</span><span class="sxs-lookup"><span data-stu-id="6266c-123">In the sample application, we define the microservice is healthy if its API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="6266c-124">.NET 5 では、組み込み API を使用することで、次のようにサービスを構成し、マイクロサービスとそれに依存している SQL Server データベースに対する正常性チェックを追加できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-124">In .NET 5, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

```csharp
// Startup.cs from .NET 5 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddCheck(
            "OrderingDB-check",
            new SqlConnectionHealthCheck(Configuration["ConnectionString"]),
            HealthStatus.Unhealthy,
            new string[] { "orderingdb" });
}
```

<span data-ttu-id="6266c-125">前のコードでは、`services.AddHealthChecks()` メソッドによって、ステータス コード **200** と "正常" を返す基本的な HTTP チェックが構成されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with "Healthy".</span></span>  <span data-ttu-id="6266c-126">さらに、`AddCheck()` 拡張メソッドによって、関連 SQL Database の正常性をチェックするカスタム `SqlConnectionHealthCheck` が構成されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database's health.</span></span>

<span data-ttu-id="6266c-127">`AddCheck()` メソッドによって、指定の名前と型 `IHealthCheck` の実装を利用して新しい正常性チェックが追加されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="6266c-128">AddCheck メソッドを利用して複数の正常性チェックを追加できます。そのため、そのチェックがすべて正常となるまで、"正常" ステータスはマイクロサービスから出されません。</span><span class="sxs-lookup"><span data-stu-id="6266c-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a "healthy" status until all its checks are healthy.</span></span>

<span data-ttu-id="6266c-129">`SqlConnectionHealthCheck` は `IHealthCheck` を実装するカスタム クラスです。これはコンストラクター パラメーターとして接続文字列を受け取り、簡単なクエリを実行し、SQL データベースに正常に接続できたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6266c-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="6266c-130">クエリが正常に実行された場合、`HealthCheckResult.Healthy()` が返され、失敗した場合、`FailureStatus` と実際の例外が返されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

<span data-ttu-id="6266c-131">前のコードでは、データベースの正常性確認に使用されたクエリが `Select 1` であることにご留意ください。</span><span class="sxs-lookup"><span data-stu-id="6266c-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="6266c-132">マイクロサービスの可用性を監視するために、Kubernetes などのオーケストレーターでは、要求を送信してマイクロサービスをテストすることで、定期的に正常性チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="6266c-132">To monitor the availability of your microservices, orchestrators like Kubernetes periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="6266c-133">そのような操作が速く行われ、リソースの利用率が上がることがないように、データベース クエリを効率的にすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="6266c-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="6266c-134">最後に、URL パス `/hc` に応答するミドルウェアを追加します。</span><span class="sxs-lookup"><span data-stu-id="6266c-134">Finally, add a middleware that responds to the url path `/hc`:</span></span>

```csharp
// Startup.cs from .NET 5 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc");
        //...
    });
    //…
}
```

<span data-ttu-id="6266c-135">エンドポイント `<yourmicroservice>/hc` が呼び出されると、スタートアップ クラスの `AddHealthChecks()` メソッドで構成されているすべての正常性チェックがすべて実行され、結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="6266c-136">eShopOnContainers の HealthChecks 実装</span><span class="sxs-lookup"><span data-stu-id="6266c-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="6266c-137">eShopOnContainers のマイクロサービスは、そのタスクを実行するために複数のサービスに依存しています。</span><span class="sxs-lookup"><span data-stu-id="6266c-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="6266c-138">たとえば、eShopOnContainers の `Catalog.API` マイクロサービスは、Azure Blob Storage、SQL Server、RabbitMQ など、さまざまなサービスに依存しています。</span><span class="sxs-lookup"><span data-stu-id="6266c-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="6266c-139">そのため、`AddCheck()` メソッドを使用していくつかの正常性チェックが追加されています。</span><span class="sxs-lookup"><span data-stu-id="6266c-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="6266c-140">あらゆる従属サービスに対して、それぞれの正常性状態を定義するカスタム `IHealthCheck` 実装を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6266c-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status would need to be added.</span></span>

<span data-ttu-id="6266c-141">オープンソース プロジェクト [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) により、.NET 5 の上に構築されるそれぞれのエンタープライズ サービス向けのカスタムの正常性チェックが実装され、この問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services, that are built on top of .NET 5.</span></span> <span data-ttu-id="6266c-142">各正常性チェックは、プロジェクトに簡単に追加できる個別の NuGet パッケージとして利用できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="6266c-143">eShopOnContainers では、そのすべてのマイクロサービスでそれらが広範囲に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-143">eShopOnContainers uses them extensively in all its microservices.</span></span>

<span data-ttu-id="6266c-144">たとえば、`Catalog.API` マイクロ サービスでは、次の NuGet パッケージが追加されています。</span><span class="sxs-lookup"><span data-stu-id="6266c-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![AspNetCore.Diagnostics.HealthChecks NuGet パッケージのスクリーンショット。](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="6266c-146">**図 8-7**</span><span class="sxs-lookup"><span data-stu-id="6266c-146">**Figure 8-7**.</span></span> <span data-ttu-id="6266c-147">AspNetCore.Diagnostics.HealthChecks を使用して Catalog.API に実装されたカスタム正常性チェック</span><span class="sxs-lookup"><span data-stu-id="6266c-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="6266c-148">次のコードでは、従属サービスごとに正常性チェック実装が追加され、それからミドルウェアが構成されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

<span data-ttu-id="6266c-149">最後に、"/hc" エンドポイントをリッスンする HealthCheck ミドルウェアを追加します。</span><span class="sxs-lookup"><span data-stu-id="6266c-149">Finally, add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="6266c-150">マイクロサービスでクエリを実行してその正常性状態についてレポートする</span><span class="sxs-lookup"><span data-stu-id="6266c-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="6266c-151">この記事の説明に従って正常性チェックを構成し、マイクロサービスを Docker で実行した後、正常かどうかをブラウザーから直接確認することができます。</span><span class="sxs-lookup"><span data-stu-id="6266c-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="6266c-152">図 8-8 に示すように、Docker ホスト内でコンテナー ポートを公開し、外部の Docker ホスト IP または `localhost` を介してコンテナーにアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6266c-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![正常性チェックから返された JSON 応答のスクリーンショット。](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="6266c-154">**図 8-8**</span><span class="sxs-lookup"><span data-stu-id="6266c-154">**Figure 8-8**.</span></span> <span data-ttu-id="6266c-155">ブラウザーからの単一サービスの正常性状態の確認</span><span class="sxs-lookup"><span data-stu-id="6266c-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="6266c-156">このテストでは、`Catalog.API` マイクロサービス (ポート 5101 で実行されている) が正常であり、JSON で HTTP ステータス 200 とステータス情報が返されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="6266c-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="6266c-157">サービスによってその SQL Server データベースの依存関係と RabbitMQ の正常性も確認されました。つまり、その正常性チェック自体が正常とレポートされました。</span><span class="sxs-lookup"><span data-stu-id="6266c-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="6266c-158">ウォッチドッグを使用する</span><span class="sxs-lookup"><span data-stu-id="6266c-158">Use watchdogs</span></span>

<span data-ttu-id="6266c-159">ウォッチドッグは、サービス間の正常性と負荷を監視し、前述の `HealthChecks` ライブラリを使用してクエリを実行することでマイクロサービスに関する正常性をレポートできる別個のサービスです。</span><span class="sxs-lookup"><span data-stu-id="6266c-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="6266c-160">これは、単一サービスのビューに基づいて検出されないエラーを防ぐのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6266c-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="6266c-161">また、ウォッチドッグは、ユーザーの介入なしで既知の状態に応じて修復アクションを実行できるコードをホストする場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="6266c-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="6266c-162">eShopOnContainers サンプルには、図 8-9 に示すように、サンプルの正常性チェック レポートを表示する Web ページが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6266c-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="6266c-163">これは、eShopOnContainers でマイクロサービスと Web アプリケーションの状態を表示するだけなので、使用可能な最も単純なウォッチドッグです。</span><span class="sxs-lookup"><span data-stu-id="6266c-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="6266c-164">通常、ウォッチドッグは異常状態の検出時にもアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="6266c-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="6266c-165">幸い、[AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) からは [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet パッケージも提供されます。このパッケージを利用し、構成された URI から正常性チェックの結果を表示できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Health Checks UI の eShopOnContainers の正常性状態のスクリーンショット。](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="6266c-167">**図 8-9**</span><span class="sxs-lookup"><span data-stu-id="6266c-167">**Figure 8-9**.</span></span> <span data-ttu-id="6266c-168">eShopOnContainers のサンプルの正常性チェック レポート</span><span class="sxs-lookup"><span data-stu-id="6266c-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="6266c-169">まとめると、このウォッチドッグ サービスは各マイクロサービスの "/hc" エンドポイントをクエリします。</span><span class="sxs-lookup"><span data-stu-id="6266c-169">In summary, this watchdog service queries each microservice's "/hc" endpoint.</span></span> <span data-ttu-id="6266c-170">これにより、定義されているすべての正常性チェックが実行され、これらすべてのチェックに応じて、全体的な正常性状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="6266c-171">HealthChecksUI は、ウォッチドッグ サービスの *Startup.cs* に追加する必要があるいくつかの構成エントリと 2 つのコード行と共に簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the *Startup.cs* of the watchdog service.</span></span>

<span data-ttu-id="6266c-172">正常性チェック UI のサンプル構成ファイル:</span><span class="sxs-lookup"><span data-stu-id="6266c-172">Sample configuration file for health check UI:</span></span>

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

<span data-ttu-id="6266c-173">HealthChecksUI を追加する *Startup.cs* ファイル:</span><span class="sxs-lookup"><span data-stu-id="6266c-173">*Startup.cs* file that adds HealthChecksUI:</span></span>

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config => config.UIPath = "/hc-ui");
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="6266c-174">オーケストレーターを使用する場合の正常性チェック</span><span class="sxs-lookup"><span data-stu-id="6266c-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="6266c-175">マイクロサービスの可用性を監視するために、Kubernetes、Service Fabric などのオーケストレーターではマイクロサービスのテスト要求を送信して、定期的に正常性チェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="6266c-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="6266c-176">オーケストレーターでサービス/コンテナーが異常であると判断された場合、そのインスタンスへの要求のルーティングが停止します。</span><span class="sxs-lookup"><span data-stu-id="6266c-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="6266c-177">通常は、そのコンテナーの新しいインスタンスも作成されます。</span><span class="sxs-lookup"><span data-stu-id="6266c-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="6266c-178">たとえば、ほとんどのオーケストレーターでは、ダウンタイムなしの展開を管理するために正常性チェックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="6266c-179">サービス/コンテナーの状態が正常に変わった場合にのみ、オーケストレーターはサービス/コンテナー インスタンスへのトラフィックのルーティングを開始します。</span><span class="sxs-lookup"><span data-stu-id="6266c-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="6266c-180">正常性の監視は、オーケストレーターがアプリケーションのアップグレードを実行する場合に特に重要です。</span><span class="sxs-lookup"><span data-stu-id="6266c-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="6266c-181">いくつかのオーケストレーター (Azure Service Fabric など) ではサービスを段階的に更新します。たとえば、アプリケーションのアップグレードごとに 5 分の 1 のクラスター サーフェスを更新する場合があります。</span><span class="sxs-lookup"><span data-stu-id="6266c-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="6266c-182">同時にアップグレードされるノード セットは *アップグレード ドメイン* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="6266c-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="6266c-183">各アップグレード ドメインがアップグレードされ、ユーザーが使用できるようになったら、そのアップグレード ドメインは、展開が次のアップグレード ドメインに移る前に正常性チェックを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6266c-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="6266c-184">サービスの正常性のもう 1 つの側面は、サービスからのメトリックのレポートです。</span><span class="sxs-lookup"><span data-stu-id="6266c-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="6266c-185">これは、Service Fabric などの一部のオーケストレーターの正常性モデルの高度な機能です。</span><span class="sxs-lookup"><span data-stu-id="6266c-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="6266c-186">メトリックは、リソース使用量のバランスをとるために使用されるため、オーケストレーターの使用時に重要になります。</span><span class="sxs-lookup"><span data-stu-id="6266c-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="6266c-187">メトリックをシステム正常性のインジケーターにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="6266c-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="6266c-188">たとえば、アプリケーションに多くのマイクロサービスがあり、各インスタンスで要求/秒 (RPS) メトリックをレポートするとします。</span><span class="sxs-lookup"><span data-stu-id="6266c-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="6266c-189">1 つのサービスが別のサービスより多くのリソース (メモリやプロセッサなど) を使用している場合、オーケストレーターはクラスター内でサービス インスタンスを移動して、リソース使用率を均一に保つことができます。</span><span class="sxs-lookup"><span data-stu-id="6266c-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="6266c-190">Azure Service Fabric には、単純な正常性チェックよりも高度な独自の[正常性の監視モデル](/azure/service-fabric/service-fabric-health-introduction)が提供されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6266c-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="6266c-191">高度な監視: 視覚化、分析、およびアラート</span><span class="sxs-lookup"><span data-stu-id="6266c-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="6266c-192">監視の最後の部分は、イベント ストリームの視覚化、サービス パフォーマンスのレポート、および問題の検出時のアラートです。</span><span class="sxs-lookup"><span data-stu-id="6266c-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="6266c-193">監視のこの部分ではさまざまなソリューションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="6266c-194">[AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) の説明の際に示したカスタム ページのように、サービスの状態を示す単純なカスタム アプリケーションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6266c-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="6266c-195">または、[Azure Monitor](https://azure.microsoft.com/services/monitor/) などのより高度なツールを使用して、イベントのストリームに基づいてアラートを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="6266c-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="6266c-196">最後に、すべてのイベント ストリームを格納していた場合、Microsoft Power BI、または Kibana や Splunk などの他のソリューションを使用して、データを視覚化することができます。</span><span class="sxs-lookup"><span data-stu-id="6266c-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6266c-197">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="6266c-197">Additional resources</span></span>

- <span data-ttu-id="6266c-198">**ASP.NET Core の HealthChecks と HealthChecks UI** </span><span class="sxs-lookup"><span data-stu-id="6266c-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="6266c-199">**Service Fabric 正常性監視の概要** </span><span class="sxs-lookup"><span data-stu-id="6266c-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="6266c-200">**Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="6266c-200">**Azure Monitor** </span></span>\
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="6266c-201">[前へ](implement-circuit-breaker-pattern.md)
>[次へ](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="6266c-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
