---
title: データ アクセスと管理
description: ASP.NET Web Forms および Blazor でデータにアクセスして処理する方法について説明します。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 66e6001cbcac612cb556e90fb86fd694ca7d1459
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509755"
---
# <a name="work-with-data"></a><span data-ttu-id="6bf2d-103">データの処理</span><span class="sxs-lookup"><span data-stu-id="6bf2d-103">Work with data</span></span>

<span data-ttu-id="6bf2d-104">データ アクセスは、ASP.NET Web Forms アプリの根幹をなすものです。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="6bf2d-105">Web 用のフォームを構築する場合、そのデータはどのようになるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="6bf2d-106">Web Forms では、データベースの操作に使用できるデータ アクセスの手法が複数存在していました。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="6bf2d-107">ソリューション エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="6bf2d-107">Data Sources</span></span>
- <span data-ttu-id="6bf2d-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6bf2d-108">ADO.NET</span></span>
- <span data-ttu-id="6bf2d-109">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6bf2d-109">Entity Framework</span></span>

<span data-ttu-id="6bf2d-110">Data Sources は、Web Forms のページ上に配置して他のコントロールのように構成できるコントロールでした。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="6bf2d-111">Visual Studio には、コントロールを構成して Web Forms のページにバインドするための一連の便利なダイアログが用意されていました。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="6bf2d-112">"低コード" または "コードなし" のアプローチを利用している開発者は、Web Forms が最初にリリースされたときにこの手法を好んで使用しました。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![ソリューション エクスプローラー](media/data/datasources.png)

<span data-ttu-id="6bf2d-114">ADO.NET は、データベースと対話するための下位レベルのアプローチです。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="6bf2d-115">アプリでは、対話用のコマンド、レコードセット、およびデータセットを使用して、データベースへの接続を作成できます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="6bf2d-116">結果はコードをあまり記述せずに画面上のフィールドにバインドできます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="6bf2d-117">この方法の欠点は、ADO.NET オブジェクトの各セット (`Connection`、`Command`、および `Recordset`) が、データベース ベンダーによって提供されるライブラリにバインドされていることでした。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="6bf2d-118">これらのコンポーネントを使用すると、コードが固定され、別のデータベースへの移行が困難になっていました。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="6bf2d-119">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6bf2d-119">Entity Framework</span></span>

<span data-ttu-id="6bf2d-120">Entity Framework (EF) は、.NET Foundation によって管理されるオープンソースのオブジェクト リレーショナル マッピング フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="6bf2d-121">当初 .NET Framework と共にリリースされた EF では、データベース接続、ストレージ スキーマ、および対話のためのコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="6bf2d-122">この抽象化により、ユーザーは自分のアプリのビジネス ルールに集中でき、データベースは信頼されたデータベース管理者に管理させることが可能になります。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="6bf2d-123">.NET では、EF Core と呼ばれる更新バージョンの EF を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-123">In .NET, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="6bf2d-124">EF Core は、`dotnet ef` コマンドライン ツールを使用して利用できる一連のコマンドを使用して、コードとデータベースの間の対話を生成および維持するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="6bf2d-125">データベースを操作するためのいくつかのサンプルを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="6bf2d-126">EF の Code First</span><span class="sxs-lookup"><span data-stu-id="6bf2d-126">EF Code First</span></span>

<span data-ttu-id="6bf2d-127">データベースとの対話の構築を簡単に開始する 1 つの方法は、操作するクラス オブジェクトを使用して開始することです。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="6bf2d-128">EF には、クラスに適したデータベース コードを生成するために役立つツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="6bf2d-129">このアプローチは、"Code First" 開発と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="6bf2d-130">Microsoft SQL Server のようなリレーショナル データベースに格納するサンプルの店舗アプリに対し、次の `Product` クラスを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

<span data-ttu-id="6bf2d-131">Product では、1 つの主キーと 3 つの追加フィールドがデータベースに作成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="6bf2d-132">EF では慣例によって `Id` プロパティが主キーとして識別されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="6bf2d-133">`Name` は、テキスト ストレージ用に構成された列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="6bf2d-134">このプロパティを修飾する `[Required]` 属性により、プロパティのこの宣言された動作を強制するための `not null` 制約が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="6bf2d-135">`Description` は、テキスト ストレージ用に構成された列に格納され、最大長は `[MaxLength]` 属性で指定された 4000 文字に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="6bf2d-136">データベース スキーマは、データ型 `MaxLength` を使用して `varchar(4000)` という名前の列で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="6bf2d-137">`Price` プロパティは通貨として格納されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="6bf2d-138">`[Range]` 属性により、宣言された最小値と最大値の範囲外でのデータの格納を防ぐための適切な制約が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="6bf2d-139">この `Product` クラスは、データベースでの接続操作と変換操作を定義するデータベース コンテキスト クラスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="6bf2d-140">`MyDbContext` クラスには、`Product` クラスのアクセスと変換を定義する 1 つのプロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="6bf2d-141">ユーザーのアプリケーションでは、`Startup` クラスの `ConfigureServices` メソッドの次のエントリを使用して、データベースとの対話のためにこのクラスを構成します。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="6bf2d-142">上記のコードにより、指定された接続文字列を使用して SQL Server データベースに接続されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="6bf2d-143">接続文字列を、*appsettings.json* ファイル、環境変数、またはその他の構成ストレージの場所に配置し、この埋め込み文字列を適切に置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="6bf2d-144">その後、次のコマンドを使用して、このクラスに適したデータベース テーブルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="6bf2d-145">最初のコマンドにより、`Create Product table` という新しい EF 移行としてデータベース スキーマに対して行う変更が定義されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="6bf2d-146">移行では、新しいデータベースの変更を適用および削除する方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="6bf2d-147">適用すると、データベース内の単純な `Product` テーブルと、データベース スキーマの管理に役立つ新しいクラスがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="6bf2d-148">これらの生成されたクラスは、既定では *Migrations* という名前の新しいフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="6bf2d-149">`Product` クラスに変更を加えたり、データベースと対話する関連するクラスを追加したりする場合は、移行の新しい名前を指定してコマンドライン コマンドを再度実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="6bf2d-150">このコマンドでは、データベース スキーマを更新するための別の一連の移行クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="6bf2d-151">EF Database First</span><span class="sxs-lookup"><span data-stu-id="6bf2d-151">EF Database First</span></span>

<span data-ttu-id="6bf2d-152">既存のデータベースの場合は、.NET コマンドライン ツールを使用して EF Core のクラスを生成できます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="6bf2d-153">クラスをスキャフォールディングするには、次のコマンドのバリエーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="6bf2d-154">上記のコマンドでは、指定された接続文字列と `Microsoft.EntityFrameworkCore.SqlServer` プロバイダーを使用してデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="6bf2d-155">接続されると、`MyDbContext` という名前のデータベース コンテキスト クラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="6bf2d-156">また、`-t` オプションで指定された `Product` テーブルおよび `Customer` テーブルに対してサポート クラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="6bf2d-157">このコマンドには、データベースに適したクラス階層を生成するための多くの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="6bf2d-158">完全なリファレンスについては、[コマンドのドキュメント](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="6bf2d-159">[EF Core](/ef/core/) の詳細については、Microsoft Docs のサイトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="6bf2d-160">Web サービスを使用した対話</span><span class="sxs-lookup"><span data-stu-id="6bf2d-160">Interact with web services</span></span>

<span data-ttu-id="6bf2d-161">ASP.NET が最初にリリースされたとき、Web サーバーとクライアントがデータを交換するための推奨される方法は SOAP サービスでした。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="6bf2d-162">それ以来、多くの変更が行われ、推奨されるサービスとの対話は HTTP クライアントとの直接対話に変わりました。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="6bf2d-163">ASP.NET Core および Blazor を使用すると、`Startup` クラスの `ConfigureServices` メソッドに `HttpClient` の構成を登録できます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="6bf2d-164">HTTP エンドポイントと対話する必要がある場合は、その構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="6bf2d-165">次の構成コードについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-165">Consider the following configuration code:</span></span>

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

<span data-ttu-id="6bf2d-166">GitHub からデータにアクセスする必要がある場合は常に、`github` という名前のクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="6bf2d-167">クライアントはベース アドレスを使用して構成され、要求ヘッダーが適切に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="6bf2d-168">`@inject` ディレクティブまたはプロパティの `[Inject]` 属性を使用して、`IHttpClientFactory` を Blazor コンポーネントに挿入します。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="6bf2d-169">次の構文を使用して、名前付きクライアントを作成し、サービスと対話します。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-169">Create your named client and interact with services using the following syntax:</span></span>

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = await response.Content.ReadAsStringAsync();
    }
}
```

<span data-ttu-id="6bf2d-170">このメソッドでは、*dotnet/docs* GitHub リポジトリ内の問題のコレクションを記述する文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="6bf2d-171">コンテンツは JSON 形式で返され、適切な GitHub 問題オブジェクトに逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="6bf2d-172">事前に構成された `HttpClient` オブジェクトを配信するように `HttpClientFactory` を構成するには、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="6bf2d-173">使用するさまざまな Web サービスに対して、異なる名前とエンドポイントで複数の `HttpClient` インスタンスを構成してみてください。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="6bf2d-174">この方法により、これらのサービスとのやり取りを各ページで簡単に操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="6bf2d-175">詳細については、 [IHttpClientFactory のドキュメント](/aspnet/core/fundamentals/http-requests)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bf2d-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6bf2d-176">[前へ](forms-validation.md)
>[次へ](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="6bf2d-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
