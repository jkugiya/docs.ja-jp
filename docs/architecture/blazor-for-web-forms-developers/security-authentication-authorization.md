---
title: セキュリティ:ASP.NET Web Forms および Blazor での認証と認可
description: セキュリティ:ASP.NET Web Forms および Blazor での認証と認可。
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 0344960237a5d9da61eb0d85987c44e136f1be48
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509846"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-blazor"></a>セキュリティ:ASP.NET Web Forms および Blazor  での認証と承認

ASP.NET Web Forms アプリケーションから Blazor に移行すると、アプリケーションに認証が構成されているものとして、ほとんど確実に、認証と認可の実行方法を更新する必要があります。 この章では、ASP.NET Web Forms ユニバーサル プロバイダー モデル (メンバーシップ、ロール、およびユーザー プロファイルの場合) から移行する方法と、Blazor アプリから ASP.NET Core Identity を使用する方法について説明します。 この章では、大まかな手順と考慮事項について説明しますが、詳細な手順とスクリプトについては、参照されているドキュメントで見つけることができます。

## <a name="aspnet-universal-providers"></a>ASP.NET ユニバーサル プロバイダー

ASP.NET 2.0 以降、ASP.NET Web Forms プラットフォームでは、メンバーシップなどの多様な機能のプロバイダー モデルがサポートされています。 ユニバーサル メンバーシップ プロバイダーは、オプションのロール プロバイダーと共に、一般に ASP.NET Web Forms アプリケーションによってデプロイされます。 それによって、現在も十分に機能し続ける、認証と認可を管理するための堅牢で安全な方法が提供されます。 これらのユニバーサル プロバイダーの最新のオファリングは、NuGet パッケージの [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers) として使用できます。

ユニバーサル プロバイダーは、`aspnet_Applications`、`aspnet_Membership`、`aspnet_Roles`、`aspnet_Users` などのテーブルを含む SQL データベース スキーマと連携します。 [aspnet_regsql.exe コマンド](/previous-versions/ms229862(v=vs.140))を実行して構成すると、基になるデータを操作するために必要なすべてのクエリとコマンドを提供するテーブルとストアド プロシージャがプロバイダーによってインストールされます。 データベース スキーマとこれらのストアド プロシージャは、新しい ASP.NET Identity および ASP.NET Core Identity システムと互換性がないため、既存のデータを新しいシステムに移行する必要があります。 図 1 は、ユニバーサル プロバイダー用に構成されたテーブル スキーマの例を示しています。

![ユニバーサル プロバイダー スキーマ](./media/security/membership-tables.png)

ユニバーサル プロバイダーでは、ユーザー、メンバーシップ、ロール、およびプロファイルが処理されます。 ユーザーにはグローバル一意識別子が割り当てられ、ユーザー ID やユーザー名などの基本情報は、`aspnet_Users` テーブルに格納されます。 パスワード、パスワード形式、パスワード ソルト、ロックアウト カウンター、詳細などの認証情報は、`aspnet_Membership` テーブルに格納されます。 ロールは、名前と一意の識別子だけで構成され、`aspnet_UsersInRoles` 関連付けテーブルによって、ユーザーに割り当てられ、多対多のリレーションシップを提供します。

既存のシステムで、メンバーシップに加えてロールを使用している場合は、ユーザー アカウント、関連付けられているパスワード、ロール、およびロール メンバーシップを ASP.NET Core Identity に移行する必要があります。 また、現在 if ステートメントを使用して、ロール チェックを実行しているコードは、代わりに宣言型のフィルター、属性、タグ ヘルパーを利用するように、更新する必要がある可能性があります。 移行の考慮事項については、この章の最後で詳しく確認します。

### <a name="authorization-configuration-in-web-forms&quot;></a>Web Forms での認可構成

ASP.NET Web Forms アプリケーションで特定のページへの認可済みのアクセスを構成するには、一般に特定のページやフォルダーに匿名ユーザーがアクセスできないようにすることを指定します。 この構成は、web.config ファイルで行います。

```xml
<?xml version=&quot;1.0&quot;?>
<configuration>
    <system.web>
      <authentication mode=&quot;Forms&quot;>
        <forms defaultUrl=&quot;~/home.aspx&quot; loginUrl=&quot;~/login.aspx&quot;
          slidingExpiration=&quot;true&quot; timeout=&quot;2880&quot;></forms>
      </authentication>

      <authorization>
        <deny users=&quot;?&quot; />
      </authorization>
    </system.web>
</configuration>
```

`authentication` 構成セクションで、アプリケーションのフォーム認証を設定します。 `authorization` セクションは、アプリケーション全体で匿名ユーザーを許可しない場合に使用します。 ただし、場所単位でよりきめ細かな認可規則を指定したり、ロールベースの認可チェックを適用したりすることもできます。

```xml
<location path=&quot;login.aspx&quot;>
  <system.web>
    <authorization>
      <allow users=&quot;*&quot; />
    </authorization>
  </system.web>
</location>
```

上の構成を最初の構成と組み合わせると、匿名ユーザーがログイン ページにアクセスできるようになり、認証されていないユーザーに対するサイト全体の制限が上書きされます。

```xml
<location path=&quot;/admin&quot;>
  <system.web>
    <authorization>
      <allow roles=&quot;Administrators&quot; />
      <deny users=&quot;*&quot; />
    </authorization>
  </system.web>
</location>
```

上の構成を他の構成と組み合わせると、`/admin` フォルダーとその中のすべてのリソースへのアクセスが &quot;Administrators&quot; ロールのメンバーに制限されます。 この制限は、`/admin` フォルダー ルート内に個別の `web.config` ファイルを配置することでも適用でき ます。

### <a name=&quot;authorization-code-in-web-forms&quot;></a>Web Forms での認可コード

`web.config` を使用してアクセスを構成するだけでなく、Web Forms アプリケーションで、アクセスと動作をプログラムによって構成することもできます。 たとえば、ユーザーのロールに基づいて、特定の操作を実行したり、特定のデータを表示したりする機能を制限できます。

このコードは、コードビハインド ロジックとページ自体の両方で使用できます。

```html
<% if (HttpContext.Current.User.IsInRole(&quot;Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

ユーザー ロール メンバーシップをチェックするだけでなく、ユーザーが認証されているかどうかを判断することもできます (ただし、多くの場合、上記の場所ベースの構成を使用する方がうまく実行されます)。 このアプローチの例を次に示します。

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

上のコードでは、ロールベースのアクセス制御 (RBAC) を使用して、ページの特定の要素 (`SecretPanel` など) が 現在のユーザーのロールに基づいて表示されるかどうかを判断します。

一般に、ASP.NET Web Forms アプリケーションでは、`web.config` ファイル内にセキュリティを構成し、次に、必要な場合に、`.aspx` ページとその関連の `.aspx.cs` 分離コード ファイルにさらにチェックを追加し ます。 ほとんどのアプリケーションでは、多くの場合に追加のロール プロバイダーと共に、ユニバーサル メンバーシップ プロバイダーが利用されています。

## <a name="aspnet-core-identity"></a>ASP.NET Core ID

やはり認証と認可の任務を負っていますが、ASP.NET Core Identity では、ユニバーサル プロバイダーと比べて異なる抽象化と前提条件のセットが使用されます。 たとえば、新しい Identity モデルでは、サードパーティ認証がサポートされているため、ユーザーはソーシャル メディア アカウントまたは他の信頼された認証プロバイダーを使用して認証することができます。 ASP.NET Core Identity では、ログイン、ログアウト、登録など、一般的に必要なページの UI がサポートされています。 そのデータ アクセスには EF Core が利用され、EF Core の移行を使用して、そのデータ モデルをサポートするために必要なスキーマが生成されます。 この [ASP.NET Core の ID の概要](/aspnet/core/security/authentication/identity)では、ASP.NET Core Identity に何が含まれるかと、その使用を開始する方法の概要について説明します。 アプリケーションとそのデータベースに ASP.NET Core Identity をまだセットアップしていない場合、作業の開始に役立ちます。

### <a name="roles-claims-and-policies"></a>ロール、クレーム、ポリシー

ユニバーサル プロバイダーと ASP.NET Core Identity のどちらも、ロールの概念がサポートされています。 ユーザーのロールを作成し、ユーザーをロールに割り当てることができます。 ユーザーは任意の数のロールに属することができ、認可実装の一部として、ロール メンバーシップを検証できます。

ロールに加えて、ASP.NET Core Identity では、クレームとポリシーの概念がサポートされています。 ロールは、そのロールのユーザーがアクセスできる必要がある一連のリソースに具体的に対応していなければなりませんが、クレームはユーザーの ID の一部にすぎません。 クレームは、サブジェクトが何であるかを表す名前と値のペアであり、サブジェクトで何が実行できるかではありません。

ユーザーのクレームを直接検査し、これらの値に基づいて、ユーザーにリソースへのアクセス権を付与するべきかどうかを判断できます。 ただし、このようなチェックは多くの場合に繰り返され、システム全体に分散されます。 より優れたアプローチは、*ポリシー* を定義することです。

認可ポリシーは、1 つまたは複数の要件で構成されます。 ポリシーは、`Startup.cs` の `ConfigureServices` メソッドで認可サービス構成の一部として登録します。 たとえば、次のコード スニペットでは、"CanadiansOnly" というポリシーを構成しており、これには、ユーザーに "Canada" の値の Country クレームがあるという要件があります。

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

[カスタム ポリシーの作成方法の詳細については、ドキュメントを参照](/aspnet/core/security/authorization/policies)してください。

ポリシーやロールを使用しているかどうかに関係なく、Blazor アプリケーションの特定のページには、`@attribute` ディレクティブで適用された `[Authorize]` 属性を持つロールまたはポリシーが必要であることを指定できます。

ロールが必要:

```csharp
@attribute [Authorize(Roles ="administrators")]
```

ポリシーが満たされていることが必要:

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

コードで、ユーザーの認証状態、ロール、またはクレームへのアクセスが必要な場合、この機能を実現するために主に 2 つの方法があります。 1 つ目は、認証状態をカスケード パラメーターとして受け取ることです。 2 つ目は、挿入された `AuthenticationStateProvider` を使用して状態にアクセスすることです。 これらの各アプローチの詳細については、[Blazor のセキュリティに関するドキュメント](/aspnet/core/blazor/security/)を参照してください。

次のコードは、`AuthenticationState` をカスケード パラメーターとして受け取る方法を示しています。

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

このパラメーターを設定すると、次のコードを使用してユーザーを取得できます。

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

次のコードは、`AuthenticationStateProvider` を挿入する方法を示しています。

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

プロバイダーを設定すると、次のコードを使用してユーザーにアクセスできます。

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

**注:** この章の後半で説明する `AuthorizeView` コンポーネントには、ユーザーがページまたはコンポーネントについて見られる内容を、宣言によって制御する方法が用意されています。

(Blazor サーバー アプリケーションで) ユーザーとクレームを操作するには、ユーザーのクレームを列挙および変更するために使用できる `UserManager<T>` を挿入することが必要になる場合もあります (既定では `IdentityUser` を使用します)。 最初に型を挿入し、それをプロパティに割り当てます。

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

次に、それを使用してユーザーのクレームを処理します。 次のサンプルは、ユーザーにクレームを追加して保持する方法を示しています。

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

ロールを使用する必要がある場合は、同じアプローチに従います。 ロール自体の一覧表示と管理のために、`RoleManager<T>` (既定の型には `IdentityRole` を使用) を挿入する必要がある場合があります。

**注:** Blazor Webassembly プロジェクトでは、これらの操作を実行するためにサーバー API を指定する必要があります (`UserManager<T>` または `RoleManager<T>` を直接使用するのではなく)。 Blazor Webassembly クライアント アプリケーションでは、この目的のために公開されている API エンドポイントを安全に呼び出すことによって、クレームやロールを管理できます。

### <a name="migration-guide"></a>移行ガイド

ASP.NET Web Forms とユニバーサル プロバイダーから ASP.NET Core Identity に移行するには、いくつかの手順が必要です。

1. 移行先データベースに ASP.NET Core Identity データベース スキーマを作成する
2. ユニバーサル プロバイダー スキーマから ASP.NET Core Identity スキーマにデータを移行する
3. `web.config` からミドルウェアおよびサービスに、構成を移行します (通常 `Startup.cs` 内)
4. タグ ヘルパーと新しい ID API を使用するように、コントロールと条件を使用して、個々のページを更新します。

以下のセクションでは、これらの各手順について詳しく説明します。

### <a name="creating-the-aspnet-core-identity-schema"></a>ASP.NET Core Identity スキーマの作成

ASP.NET Core Identity で使用される必要なテーブル構造を作成するには、いくつかの方法があります。 最も簡単なのは、新しい ASP.NET Core Web アプリケーションを作成することです。 [Web アプリケーション] を選択し、[認証] を [個人のユーザー アカウント] を使用するように変更します。

![個別のユーザー アカウントによる新しいプロジェクト](./media/security/individual-user-accounts.png)

コマンド ラインから、`dotnet new webapp -au Individual` を実行して、同じことを行うことができます。 アプリが作成されたら、それを実行し、サイトに登録します。 次に示すようなページをトリガーする必要があります。

![移行の適用ページ](./media/security/apply-migrations-page.png)

[移行の適用] ボタンをクリックすると、必要なデータベース テーブルが自動的に作成されるはずです。 また、次のように、移行ファイルがプロジェクトに表示されるはずです。

![移行ファイル](./media/security/migration-files.png)

Web アプリケーションを実行しなくても、次のコマンドライン ツールを使用して、自分で移行を実行できます。

```powershell
dotnet ef database update
```

または新しいスキーマを既存のデータベースに適用するスクリプトを実行する場合は、コマンドラインからこれらの移行をスクリプト化できます。 次のコマンドを実行して、スクリプトを生成します。

```powershell
dotnet ef migrations script -o auth.sql
```

上のコマンドによって、出力ファイル `auth.sql` に SQL スクリプトが生成されるので、それを任意のデータベースに対して実行できます。 `dotnet ef` コマンドの実行で問題が発生した場合は、[EF Core ツールがシステムにインストールされていることを確認](/ef/core/miscellaneous/cli/dotnet)してください。

ソース テーブルに追加の列がある場合は、新しいスキーマでこれらの列の最適な場所を特定する必要があります。 一般に、`aspnet_Membership` テーブルにある列は、`AspNetUsers` テーブルにマッピングされる必要があり ます。 `aspnet_Roles` の列は、`AspNetRoles` にマッピングされる必要があります。 `aspnet_UsersInRoles` テーブルの追加の列は、`AspNetUserRoles` テーブルに追加できます。

または、個別のテーブルに追加の列を配置することも検討する価値があります。 そうすると、今後の移行で、既定の ID スキーマのカスタマイズを考慮する必要がなくなります。

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a>ユニバーサル プロバイダーから ASP.NET Core Identity へのデータの移行

移行先テーブル スキーマを設定したら、次の手順は、ユーザーとロールのレコードを新しいスキーマに移行することです。 スキーマの違い (どの列がどの新しい列にマッピングされるかなど) の完全な一覧については、[こちら](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)を参照してください。

ユーザーをメンバーシップから新しい ID テーブルに移行するには、[ドキュメントに記載されている手順に従う](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)必要があります。 これらの手順と提供されているスクリプトに従った後に、ユーザーは次回ログインするときにパスワードを変更する必要があります。

ユーザーのパスワードを移行することはできますが、プロセスがはるかに複雑になります。 移行プロセスの一環としてユーザーにパスワードの更新を要求し、新しい一意のパスワードを使用するように勧めることは、アプリケーションの全体的なセキュリティを高める可能性があります。

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a>web.config から Startup.cs へのセキュリティ設定の移行

上記のように、ASP.NET のメンバーシップとロール プロバイダーは、アプリケーションの `web.config` ファイルで構成します。 ASP.NET Core アプリは IIS に関連付けられず、構成に個別のシステムが使用されるため、これらの設定を他の場所に構成する必要があります。 ほとんどの場合、ASP.NET Core Identity は `Startup.cs` ファイルで構成します。 (ID テーブル スキーマを作成するために) 前に作成した Web プロジェクトを開き、その `Startup.cs` ファイルを確認します。

既定の ConfigureServices メソッドによって、EF Core と ID のサポートが追加されます。

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

`AddDefaultIdentity` 拡張メソッドは、既定の `ApplicationDbContext` とフレームワークの `IdentityUser` 型を使用するように ID を構成するために使用します。 カスタム `IdentityUser` を使用している場合は、ここでその型を指定してください。 これらの拡張メソッドがアプリケーションで動作していない場合は、適切な using ステートメントがあることと、必要な NuGet パッケージ参照があることを確認してください。 たとえば、プロジェクトには、`Microsoft.AspNetCore.Identity.EntityFrameworkCore` の何らかのバージョンと `Microsoft.AspNetCore.Identity.UI` パッケージが参照されている必要があります。

また、`Startup.cs` に、サイトに必要なミドルウェアが構成されていることが確認されるはずです。 具体的に、`UseAuthentication` と `UseAuthorization` が設定され、適切な場所にあるはずです。

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

ASP.NET Identity では、`Startup.cs` から場所への匿名またはロールベースのアクセスを構成しません。 場所固有の認可構成データは ASP.NET Core のフィルターに移行する必要があります。 このような更新が必要になるフォルダーとページをメモしておきます。 次のセクションでこれらの変更を行います。

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a>ASP.NET Core Identity の抽象化を使用するように個々のページを更新する

ASP.NET Web Forms アプリケーションで、匿名ユーザーに特定のページまたはフォルダーへのアクセスを拒否する `web.config` 設定があった場合、そのようなページに `[Authorize]` 属性を追加することによって、これらの変更を移行できます。

```razor
@attribute [Authorize]
```

特定のロールに属しているユーザーを除くアクセスを拒否していた場合は、ロールを指定する属性を追加して、この動作を移行することもできます。

```razor
@attribute [Authorize(Roles ="administrators")]
```

`[Authorize]` 属性は、Blazor ルーター経由で到達される `@page` コンポーネントに対してのみ機能します。 この属性は子コンポーネントでは動作せず、代わりに `AuthorizeView` を使用する必要があります。

ページ マークアップ内に、特定のユーザーに一部のコードを表示するかどうかを判断するためのロジックがある場合は、これを `AuthorizeView` コンポーネントで置き換えることができます。 [AuthorizeView コンポーネント](/aspnet/core/blazor/security#authorizeview-component)では、ユーザーがそれを表示することを認可されているかどうかに応じて、UI を選択的に表示します。 また、ユーザー情報へのアクセスに使用できる `context` 変数も公開されています。

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

手続き型ロジック内の認証状態にアクセスするには、`[CascadingParameter]` 属性で構成された `Task<AuthenticationState` からユーザーにアクセスします。 この構成により、ユーザーにアクセスできるようになり、ユーザーが認証されているかどうか、および特定のロールに属しているかどうかを判断できます。 ポリシーを手続き上評価する必要がある場合は、`IAuthorizationService` のインスタンスを挿入し、それに対して `AuthorizeAsync` メソッドを呼び出すことができます。 次のサンプル コードは、ユーザー情報を取得し、認可されたユーザーに、`content-editor` ポリシーによって制限されたタスクの実行を許可する方法を示しています。

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

`AuthenticationState` は、このようなカスケード型パラメーターにバインドする前に、まずカスケード値として設定する必要があります。 それは一般に、`CascadingAuthenticationState` コンポーネントを使用して行います。 この構成は、一般に `App.razor` で行います。

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a>まとめ

Blazor では、ASP.NET Core Identity である ASP.NET Core と同じセキュリティ モデルが使用されます。 元のデータ スキーマに過剰なカスタマイズが適用されていないことを前提として、ユニバーサル プロバイダーから ASP.NET Core Identity への移行は比較的簡単です。 データが移行されたら、Blazor アプリでの認証と認可の操作については、ドキュメントに詳しく説明されています。構成可能であるほか、ほとんどのセキュリティ要件に対して、プログラムでサポートされています。

## <a name="references"></a>References

- [ASP.NET Core の ID の概要](/aspnet/core/security/authentication/identity)
- [ASP.NET メンバーシップ認証から ASP.NET Core 2.0 Identity への移行](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [ASP.NET Core への認証と ID の移行](/aspnet/core/migration/identity)
- [ASP.NET Core Blazor の認証と認可](/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
>[前へ](config.md)
>[次へ](migration.md)
