---
title: コンテナーとして実行するデータベース サーバーの使用
description: コンテナーとして実行されているデータベース サーバーの使用は開発時に限定することの重要性を理解します。 運用環境向けではありません。
ms.date: 01/13/2021
ms.openlocfilehash: 1292bf37e3baaeb6284f6fba15b4bc7c9c17b4a7
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188739"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="82128-104">コンテナーとして実行するデータベース サーバーの使用</span><span class="sxs-lookup"><span data-stu-id="82128-104">Use a database server running as a container</span></span>

<span data-ttu-id="82128-105">データベース (SQL Server、PostgreSQL、MySQL など) は、通常のスタンドアロン サーバー上、オンプレミス クラスター内、または Azure SQL DB などのクラウド内の PaaS サービスとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="82128-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="82128-106">ただし、開発およびテスト環境では、データベースをコンテナーとして実行すると便利です。これは、外部の依存関係がなく、`docker-compose up` コマンドを実行するだけで、アプリケーション全体が起動するためです。</span><span class="sxs-lookup"><span data-stu-id="82128-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="82128-107">それらのデータベースをコンテナーとして使用することは、統合テストにも有効です。これは、データベースがコンテナー内で起動され、常に同じサンプル データが格納されるので、テストの予測精度が向上するためです。</span><span class="sxs-lookup"><span data-stu-id="82128-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="82128-108">マイクロサービスに関連するデータベースを含むコンテナーとして実行している SQL Server</span><span class="sxs-lookup"><span data-stu-id="82128-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="82128-109">eShopOnContainers には、[docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) ファイルに定義される `sqldata` という名前のコンテナーがあり、これによって Linux インスタンス用の SQL サーバーとすべてのマイクロサービスに必要な SQL データベースが実行されます。</span><span class="sxs-lookup"><span data-stu-id="82128-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="82128-110">マイクロサービスの重要な点は、各マイクロサービスで関連データが所有されるため、専用のデータベースを用意する必要があることです。</span><span class="sxs-lookup"><span data-stu-id="82128-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="82128-111">ただし、データベースは任意の場所に置くことができます。</span><span class="sxs-lookup"><span data-stu-id="82128-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="82128-112">ここでは、Docker のメモリ要件をできるだけ低く保つために、これらはすべて同じコンテナー内にあります。</span><span class="sxs-lookup"><span data-stu-id="82128-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="82128-113">これは開発にとって (おそらくテストにとっても) 十分なソリューションですが、運用環境には適していないことに留意してください。</span><span class="sxs-lookup"><span data-stu-id="82128-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="82128-114">サンプル アプリケーションの SQL Server コンテナーは、docker-compose.yml ファイル内で次の YAML コードで構成され、`docker-compose up` を実行したときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="82128-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="82128-115">YAML コードは、汎用の docker compose.yml ファイルと docker compose.override.yml ファイルから構成情報を統合されていることに注意してください</span><span class="sxs-lookup"><span data-stu-id="82128-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="82128-116">(通常は、SQL Server イメージに関連する基本情報または静的情報から、環境の設定を分離します)。</span><span class="sxs-lookup"><span data-stu-id="82128-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="82128-117">同様の方法で、`docker-compose` を使用する代わりに、次の `docker run` コマンドでそのコンテナーを実行できます。</span><span class="sxs-lookup"><span data-stu-id="82128-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="82128-118">ただし、eShopOnContainers などのマルチコンテナー アプリケーションを展開する場合は、アプリケーションに必要なすべてのコンテナーを展開する `docker-compose up` コマンドを使う方が便利です。</span><span class="sxs-lookup"><span data-stu-id="82128-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="82128-119">初めてこの SQL Server のコンテナーを起動するときに、コンテナーが、指定したパスワードを使用して SQL Server を初期化します。</span><span class="sxs-lookup"><span data-stu-id="82128-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="82128-120">SQL Server がコンテナーとして実行されたら、SQL Server Management Studio、Visual Studio、C\# コードなどの通常の SQL 接続を介して接続することでデータベースを更新できます。</span><span class="sxs-lookup"><span data-stu-id="82128-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="82128-121">eShopOnContainers アプリケーションは、次のセクションで説明するように、起動時にデータをシードすることにより、各マイクロサービス データベースをサンプル データで初期化します。</span><span class="sxs-lookup"><span data-stu-id="82128-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="82128-122">SQL Server のコンテナーとしての実行は、SQL Server のインスタンスにアクセスできない場合があるデモに役に立つだけではありません。</span><span class="sxs-lookup"><span data-stu-id="82128-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="82128-123">説明したように、新しいサンプル データをシードすることによってクリーンな SQL Server イメージと既知のデータから統合テストを簡単に実行できるので開発やテストの環境にも有効です。</span><span class="sxs-lookup"><span data-stu-id="82128-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="82128-124">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="82128-124">Additional resources</span></span>

- <span data-ttu-id="82128-125">**Linux、Mac、Windows で SQL Server Docker イメージを実行する** </span><span class="sxs-lookup"><span data-stu-id="82128-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="82128-126">**Linux で sqlcmd を使用して SQL Server に接続してクエリする** </span><span class="sxs-lookup"><span data-stu-id="82128-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="82128-127">Web アプリケーションの起動時のテスト データのシード処理</span><span class="sxs-lookup"><span data-stu-id="82128-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="82128-128">アプリケーションの起動時にデータベースにデータを追加するには、Web API プロジェクトの `Program` クラス内の `Main` メソッドに次のようなコードを追加できます。</span><span class="sxs-lookup"><span data-stu-id="82128-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

<span data-ttu-id="82128-129">コンテナーの起動時に移行を適用し、データベースをシード処理する際の重要な注意事項があります。</span><span class="sxs-lookup"><span data-stu-id="82128-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="82128-130">データベース サーバーが何らかの理由で使用できない可能性があるため、サーバーが使用可能になるまで待機している間、再試行を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82128-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="82128-131">この再試行ロジックは、次のコードに示すように、`MigrateDbContext()` 拡張メソッドによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="82128-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

```csharp
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

<span data-ttu-id="82128-132">カスタムの CatalogContextSeed クラスの次のコードはデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="82128-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

<span data-ttu-id="82128-133">統合テストを実行するときには、統合テストと一貫性のあるデータを生成する方法があると便利です。</span><span class="sxs-lookup"><span data-stu-id="82128-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="82128-134">コンテナーで実行されている SQL Server のインスタンスを含む、すべてのものを新規に作成できると、テスト環境に非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="82128-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="82128-135">EF Core InMemory データベースとコンテナーとして実行される SQL Server</span><span class="sxs-lookup"><span data-stu-id="82128-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="82128-136">テストの実行時に適した別の選択肢として、Entity Framework InMemory データベース プロバイダーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="82128-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="82128-137">Web API プロジェクトのスタートアップ クラスの ConfigureServices メソッドでその構成を指定できます。</span><span class="sxs-lookup"><span data-stu-id="82128-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }

    // Other Startup code ...
}
```

<span data-ttu-id="82128-138">ただし、重要な落とし穴があります。</span><span class="sxs-lookup"><span data-stu-id="82128-138">There is an important catch, though.</span></span> <span data-ttu-id="82128-139">メモリ内データベースは、特定のデータベースに固有な多くの制約をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="82128-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="82128-140">たとえば、EF Core モデルで列に一意のインデックスを追加し、重複する値の追加を許可しないことを確認するためのテストをインメモリ データベースに対して記述する場合があります。</span><span class="sxs-lookup"><span data-stu-id="82128-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="82128-141">しかし、メモリ内データベースを使用している場合は、列で一意のインデックスを処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="82128-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="82128-142">そのため、メモリ内データベースは、実際の SQL Server データベースとまったく同じようには動作せず、データベース固有の制約をエミュレートしません。</span><span class="sxs-lookup"><span data-stu-id="82128-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="82128-143">それでも、テストやプロトタイプ作成にはメモリ内データベースが依然として役立ちます。</span><span class="sxs-lookup"><span data-stu-id="82128-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="82128-144">特定のデータベースの実装の動作を考慮する正確な統合テストを作成する場合は、SQL Server のような実際のデータベースを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82128-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="82128-145">その目的のために、コンテナー内での SQL Server の実行は優れた選択肢であり、EF Core InMemory データベース プロバイダーよりも正確です。</span><span class="sxs-lookup"><span data-stu-id="82128-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="82128-146">コンテナーで実行されている Redis キャッシュ サービスの使用</span><span class="sxs-lookup"><span data-stu-id="82128-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="82128-147">特に開発およびテストや概念実証のシナリオで、Redis をコンテナー上で実行できます。</span><span class="sxs-lookup"><span data-stu-id="82128-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="82128-148">このシナリオは、ローカルの開発用コンピューターだけでなく、CI/CD パイプラインのテスト環境向けにも、コンテナーですべての依存関係を実行できるので便利です。</span><span class="sxs-lookup"><span data-stu-id="82128-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="82128-149">ただし、実稼働環境で Redis を実行するときは、PaaS (サービスとしてのプラットフォーム) として実行される Redis Microsoft Azure のような高可用性ソリューションを探すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="82128-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="82128-150">コード内で、接続文字列だけを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82128-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="82128-151">Redis は、Redis と共に Docker イメージを提供します。</span><span class="sxs-lookup"><span data-stu-id="82128-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="82128-152">そのイメージは、次の URL での Docker Hub から入手できます。</span><span class="sxs-lookup"><span data-stu-id="82128-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="82128-153">コマンド プロンプトで次の Docker CLI コマンドを実行することによって、Docker Redis コンテナーを直接実行できます。</span><span class="sxs-lookup"><span data-stu-id="82128-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="82128-154">Redis イメージには expose:6379 (Redis によって使用されるポート) が含まれているので、標準のコンテナーのリンクを、リンクされたコンテナーが自動的に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="82128-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="82128-155">eShopOnContainers では、`basket-api` マイクロサービスによって、コンテナーとして実行される Redis キャッシュが使用されます。</span><span class="sxs-lookup"><span data-stu-id="82128-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="82128-156">その `basketdata` コンテナーは、次の例に示すように、マルチコンテナー *docker-compose.yml* ファイルの一部として定義されます。</span><span class="sxs-lookup"><span data-stu-id="82128-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="82128-157">docker-compose.yml 内のこのコードにより、redis イメージに基づいて `basketdata` という名前のコンテナーが定義され、ポート 6379 が内部的に公開されます。</span><span class="sxs-lookup"><span data-stu-id="82128-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="82128-158">この構成は、Docker ホスト内で実行されている他のコンテナーからのみアクセス可能であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="82128-158">This configuration means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="82128-159">最後に、*docker-compose.override.yml* ファイルの eShopOnContainers サンプル用の `basket-api` マイクロサービスによって、その Redis コンテナーに使用する接続文字列が定義されます。</span><span class="sxs-lookup"><span data-stu-id="82128-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="82128-160">前述のように、マイクロサービス `basketdata` の名前は、Docker の内部ネットワーク DNS によって解決されます。</span><span class="sxs-lookup"><span data-stu-id="82128-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="82128-161">[前へ](multi-container-applications-docker-compose.md)
>[次へ](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="82128-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
