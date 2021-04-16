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
# <a name="work-with-data"></a>データの処理

データ アクセスは、ASP.NET Web Forms アプリの根幹をなすものです。 Web 用のフォームを構築する場合、そのデータはどのようになるでしょうか。 Web Forms では、データベースの操作に使用できるデータ アクセスの手法が複数存在していました。

- ソリューション エクスプローラー
- ADO.NET
- Entity Framework

Data Sources は、Web Forms のページ上に配置して他のコントロールのように構成できるコントロールでした。 Visual Studio には、コントロールを構成して Web Forms のページにバインドするための一連の便利なダイアログが用意されていました。 "低コード" または "コードなし" のアプローチを利用している開発者は、Web Forms が最初にリリースされたときにこの手法を好んで使用しました。

![ソリューション エクスプローラー](media/data/datasources.png)

ADO.NET は、データベースと対話するための下位レベルのアプローチです。 アプリでは、対話用のコマンド、レコードセット、およびデータセットを使用して、データベースへの接続を作成できます。 結果はコードをあまり記述せずに画面上のフィールドにバインドできます。 この方法の欠点は、ADO.NET オブジェクトの各セット (`Connection`、`Command`、および `Recordset`) が、データベース ベンダーによって提供されるライブラリにバインドされていることでした。 これらのコンポーネントを使用すると、コードが固定され、別のデータベースへの移行が困難になっていました。

## <a name="entity-framework"></a>Entity Framework

Entity Framework (EF) は、.NET Foundation によって管理されるオープンソースのオブジェクト リレーショナル マッピング フレームワークです。 当初 .NET Framework と共にリリースされた EF では、データベース接続、ストレージ スキーマ、および対話のためのコードを生成できます。 この抽象化により、ユーザーは自分のアプリのビジネス ルールに集中でき、データベースは信頼されたデータベース管理者に管理させることが可能になります。 .NET では、EF Core と呼ばれる更新バージョンの EF を使用できます。 EF Core は、`dotnet ef` コマンドライン ツールを使用して利用できる一連のコマンドを使用して、コードとデータベースの間の対話を生成および維持するのに役立ちます。 データベースを操作するためのいくつかのサンプルを見てみましょう。

### <a name="ef-code-first"></a>EF の Code First

データベースとの対話の構築を簡単に開始する 1 つの方法は、操作するクラス オブジェクトを使用して開始することです。 EF には、クラスに適したデータベース コードを生成するために役立つツールが用意されています。 このアプローチは、"Code First" 開発と呼ばれます。 Microsoft SQL Server のようなリレーショナル データベースに格納するサンプルの店舗アプリに対し、次の `Product` クラスを考えてみます。

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

Product では、1 つの主キーと 3 つの追加フィールドがデータベースに作成されます。  

- EF では慣例によって `Id` プロパティが主キーとして識別されます。
- `Name` は、テキスト ストレージ用に構成された列に格納されます。 このプロパティを修飾する `[Required]` 属性により、プロパティのこの宣言された動作を強制するための `not null` 制約が追加されます。
- `Description` は、テキスト ストレージ用に構成された列に格納され、最大長は `[MaxLength]` 属性で指定された 4000 文字に設定されます。 データベース スキーマは、データ型 `MaxLength` を使用して `varchar(4000)` という名前の列で構成されます。
- `Price` プロパティは通貨として格納されます。 `[Range]` 属性により、宣言された最小値と最大値の範囲外でのデータの格納を防ぐための適切な制約が生成されます。

この `Product` クラスは、データベースでの接続操作と変換操作を定義するデータベース コンテキスト クラスに追加する必要があります。

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

`MyDbContext` クラスには、`Product` クラスのアクセスと変換を定義する 1 つのプロパティが用意されています。  ユーザーのアプリケーションでは、`Startup` クラスの `ConfigureServices` メソッドの次のエントリを使用して、データベースとの対話のためにこのクラスを構成します。

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

上記のコードにより、指定された接続文字列を使用して SQL Server データベースに接続されます。 接続文字列を、*appsettings.json* ファイル、環境変数、またはその他の構成ストレージの場所に配置し、この埋め込み文字列を適切に置き換えることができます。

その後、次のコマンドを使用して、このクラスに適したデータベース テーブルを生成できます。

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

最初のコマンドにより、`Create Product table` という新しい EF 移行としてデータベース スキーマに対して行う変更が定義されます。  移行では、新しいデータベースの変更を適用および削除する方法が定義されます。

適用すると、データベース内の単純な `Product` テーブルと、データベース スキーマの管理に役立つ新しいクラスがプロジェクトに追加されます。  これらの生成されたクラスは、既定では *Migrations* という名前の新しいフォルダーにあります。  `Product` クラスに変更を加えたり、データベースと対話する関連するクラスを追加したりする場合は、移行の新しい名前を指定してコマンドライン コマンドを再度実行する必要があります。  このコマンドでは、データベース スキーマを更新するための別の一連の移行クラスが生成されます。

### <a name="ef-database-first"></a>EF Database First

既存のデータベースの場合は、.NET コマンドライン ツールを使用して EF Core のクラスを生成できます。 クラスをスキャフォールディングするには、次のコマンドのバリエーションを使用します。

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

上記のコマンドでは、指定された接続文字列と `Microsoft.EntityFrameworkCore.SqlServer` プロバイダーを使用してデータベースに接続します。 接続されると、`MyDbContext` という名前のデータベース コンテキスト クラスが作成されます。 また、`-t` オプションで指定された `Product` テーブルおよび `Customer` テーブルに対してサポート クラスが作成されます。 このコマンドには、データベースに適したクラス階層を生成するための多くの構成オプションがあります。 完全なリファレンスについては、[コマンドのドキュメント](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)を参照してください。

[EF Core](/ef/core/) の詳細については、Microsoft Docs のサイトを参照してください。

## <a name="interact-with-web-services"></a>Web サービスを使用した対話

ASP.NET が最初にリリースされたとき、Web サーバーとクライアントがデータを交換するための推奨される方法は SOAP サービスでした。 それ以来、多くの変更が行われ、推奨されるサービスとの対話は HTTP クライアントとの直接対話に変わりました。 ASP.NET Core および Blazor を使用すると、`Startup` クラスの `ConfigureServices` メソッドに `HttpClient` の構成を登録できます。 HTTP エンドポイントと対話する必要がある場合は、その構成を使用します。 次の構成コードについて考えてみましょう。

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

GitHub からデータにアクセスする必要がある場合は常に、`github` という名前のクライアントを作成します。 クライアントはベース アドレスを使用して構成され、要求ヘッダーが適切に設定されます。 `@inject` ディレクティブまたはプロパティの `[Inject]` 属性を使用して、`IHttpClientFactory` を Blazor コンポーネントに挿入します。 次の構文を使用して、名前付きクライアントを作成し、サービスと対話します。

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

このメソッドでは、*dotnet/docs* GitHub リポジトリ内の問題のコレクションを記述する文字列が返されます。 コンテンツは JSON 形式で返され、適切な GitHub 問題オブジェクトに逆シリアル化されます。 事前に構成された `HttpClient` オブジェクトを配信するように `HttpClientFactory` を構成するには、さまざまな方法があります。 使用するさまざまな Web サービスに対して、異なる名前とエンドポイントで複数の `HttpClient` インスタンスを構成してみてください。 この方法により、これらのサービスとのやり取りを各ページで簡単に操作できるようになります。 詳細については、 [IHttpClientFactory のドキュメント](/aspnet/core/fundamentals/http-requests)を参照してください。

>[!div class="step-by-step"]
>[前へ](forms-validation.md)
>[次へ](middleware.md)
