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
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-blazor"></a><span data-ttu-id="c8924-103">セキュリティ:ASP.NET Web Forms および Blazor  での認証と承認</span><span class="sxs-lookup"><span data-stu-id="c8924-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="c8924-104">ASP.NET Web Forms アプリケーションから Blazor に移行すると、アプリケーションに認証が構成されているものとして、ほとんど確実に、認証と認可の実行方法を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization are performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="c8924-105">この章では、ASP.NET Web Forms ユニバーサル プロバイダー モデル (メンバーシップ、ロール、およびユーザー プロファイルの場合) から移行する方法と、Blazor アプリから ASP.NET Core Identity を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8924-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="c8924-106">この章では、大まかな手順と考慮事項について説明しますが、詳細な手順とスクリプトについては、参照されているドキュメントで見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="c8924-106">While this chapter will cover the high-level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="c8924-107">ASP.NET ユニバーサル プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c8924-107">ASP.NET universal providers</span></span>

<span data-ttu-id="c8924-108">ASP.NET 2.0 以降、ASP.NET Web Forms プラットフォームでは、メンバーシップなどの多様な機能のプロバイダー モデルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c8924-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="c8924-109">ユニバーサル メンバーシップ プロバイダーは、オプションのロール プロバイダーと共に、一般に ASP.NET Web Forms アプリケーションによってデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="c8924-109">The universal membership provider, along with the optional role provider, is commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="c8924-110">それによって、現在も十分に機能し続ける、認証と認可を管理するための堅牢で安全な方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c8924-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="c8924-111">これらのユニバーサル プロバイダーの最新のオファリングは、NuGet パッケージの [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers) として使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="c8924-112">ユニバーサル プロバイダーは、`aspnet_Applications`、`aspnet_Membership`、`aspnet_Roles`、`aspnet_Users` などのテーブルを含む SQL データベース スキーマと連携します。</span><span class="sxs-lookup"><span data-stu-id="c8924-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="c8924-113">[aspnet_regsql.exe コマンド](/previous-versions/ms229862(v=vs.140))を実行して構成すると、基になるデータを操作するために必要なすべてのクエリとコマンドを提供するテーブルとストアド プロシージャがプロバイダーによってインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c8924-113">When configured by running the [aspnet_regsql.exe command](/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands to work with the underlying data.</span></span> <span data-ttu-id="c8924-114">データベース スキーマとこれらのストアド プロシージャは、新しい ASP.NET Identity および ASP.NET Core Identity システムと互換性がないため、既存のデータを新しいシステムに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="c8924-115">図 1 は、ユニバーサル プロバイダー用に構成されたテーブル スキーマの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8924-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![ユニバーサル プロバイダー スキーマ](./media/security/membership-tables.png)

<span data-ttu-id="c8924-117&quot;>ユニバーサル プロバイダーでは、ユーザー、メンバーシップ、ロール、およびプロファイルが処理されます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-117&quot;>The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id=&quot;c8924-118&quot;>ユーザーにはグローバル一意識別子が割り当てられ、ユーザー ID やユーザー名などの基本情報は、`aspnet_Users` テーブルに格納されます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-118&quot;>Users are assigned globally unique identifiers and basic information like userId, userName etc. are stored in the `aspnet_Users` table.</span></span> <span data-ttu-id=&quot;c8924-119&quot;>パスワード、パスワード形式、パスワード ソルト、ロックアウト カウンター、詳細などの認証情報は、`aspnet_Membership` テーブルに格納されます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-119&quot;>Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id=&quot;c8924-120&quot;>ロールは、名前と一意の識別子だけで構成され、`aspnet_UsersInRoles` 関連付けテーブルによって、ユーザーに割り当てられ、多対多のリレーションシップを提供します。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-120&quot;>Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id=&quot;c8924-121&quot;>既存のシステムで、メンバーシップに加えてロールを使用している場合は、ユーザー アカウント、関連付けられているパスワード、ロール、およびロール メンバーシップを ASP.NET Core Identity に移行する必要があります。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-121&quot;>If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id=&quot;c8924-122&quot;>また、現在 if ステートメントを使用して、ロール チェックを実行しているコードは、代わりに宣言型のフィルター、属性、タグ ヘルパーを利用するように、更新する必要がある可能性があります。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-122&quot;>You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id=&quot;c8924-123&quot;>移行の考慮事項については、この章の最後で詳しく確認します。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-123&quot;>We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name=&quot;authorization-configuration-in-web-forms&quot;></a><span data-ttu-id=&quot;c8924-124&quot;>Web Forms での認可構成</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-124&quot;>Authorization configuration in Web Forms</span></span>

<span data-ttu-id=&quot;c8924-125&quot;>ASP.NET Web Forms アプリケーションで特定のページへの認可済みのアクセスを構成するには、一般に特定のページやフォルダーに匿名ユーザーがアクセスできないようにすることを指定します。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-125&quot;>To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id=&quot;c8924-126&quot;>この構成は、web.config ファイルで行います。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-126&quot;>This configuration is done in the web.config file:</span></span>

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

<span data-ttu-id=&quot;c8924-127&quot;>`authentication` 構成セクションで、アプリケーションのフォーム認証を設定します。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-127&quot;>The `authentication` configuration section sets up the forms authentication for the application.</span></span> <span data-ttu-id=&quot;c8924-128&quot;>`authorization` セクションは、アプリケーション全体で匿名ユーザーを許可しない場合に使用します。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-128&quot;>The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id=&quot;c8924-129&quot;>ただし、場所単位でよりきめ細かな認可規則を指定したり、ロールベースの認可チェックを適用したりすることもできます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-129&quot;>However, you can provide more granular authorization rules on a per-location basis as well as apply role-based authorization checks.</span></span>

```xml
<location path=&quot;login.aspx&quot;>
  <system.web>
    <authorization>
      <allow users=&quot;*&quot; />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id=&quot;c8924-130&quot;>上の構成を最初の構成と組み合わせると、匿名ユーザーがログイン ページにアクセスできるようになり、認証されていないユーザーに対するサイト全体の制限が上書きされます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-130&quot;>The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

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

<span data-ttu-id=&quot;c8924-131&quot;>上の構成を他の構成と組み合わせると、`/admin` フォルダーとその中のすべてのリソースへのアクセスが &quot;Administrators&quot; ロールのメンバーに制限されます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-131&quot;>The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the &quot;Administrators&quot; role.</span></span> <span data-ttu-id=&quot;c8924-132&quot;>この制限は、`/admin` フォルダー ルート内に個別の `web.config` ファイルを配置することでも適用でき ます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-132&quot;>This restriction could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name=&quot;authorization-code-in-web-forms&quot;></a><span data-ttu-id=&quot;c8924-133&quot;>Web Forms での認可コード</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-133&quot;>Authorization code in Web Forms</span></span>

<span data-ttu-id=&quot;c8924-134&quot;>`web.config` を使用してアクセスを構成するだけでなく、Web Forms アプリケーションで、アクセスと動作をプログラムによって構成することもできます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-134&quot;>In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id=&quot;c8924-135&quot;>たとえば、ユーザーのロールに基づいて、特定の操作を実行したり、特定のデータを表示したりする機能を制限できます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-135&quot;>For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id=&quot;c8924-136&quot;>このコードは、コードビハインド ロジックとページ自体の両方で使用できます。</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;c8924-136&quot;>This code can be used both in code-behind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole(&quot;Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="c8924-137">ユーザー ロール メンバーシップをチェックするだけでなく、ユーザーが認証されているかどうかを判断することもできます (ただし、多くの場合、上記の場所ベースの構成を使用する方がうまく実行されます)。</span><span class="sxs-lookup"><span data-stu-id="c8924-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="c8924-138">このアプローチの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c8924-138">Below is an example of this approach.</span></span>

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

<span data-ttu-id="c8924-139">上のコードでは、ロールベースのアクセス制御 (RBAC) を使用して、ページの特定の要素 (`SecretPanel` など) が 現在のユーザーのロールに基づいて表示されるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="c8924-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="c8924-140">一般に、ASP.NET Web Forms アプリケーションでは、`web.config` ファイル内にセキュリティを構成し、次に、必要な場合に、`.aspx` ページとその関連の `.aspx.cs` 分離コード ファイルにさらにチェックを追加し ます。</span><span class="sxs-lookup"><span data-stu-id="c8924-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` code-behind files.</span></span> <span data-ttu-id="c8924-141">ほとんどのアプリケーションでは、多くの場合に追加のロール プロバイダーと共に、ユニバーサル メンバーシップ プロバイダーが利用されています。</span><span class="sxs-lookup"><span data-stu-id="c8924-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="c8924-142">ASP.NET Core ID</span><span class="sxs-lookup"><span data-stu-id="c8924-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="c8924-143">やはり認証と認可の任務を負っていますが、ASP.NET Core Identity では、ユニバーサル プロバイダーと比べて異なる抽象化と前提条件のセットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8924-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="c8924-144">たとえば、新しい Identity モデルでは、サードパーティ認証がサポートされているため、ユーザーはソーシャル メディア アカウントまたは他の信頼された認証プロバイダーを使用して認証することができます。</span><span class="sxs-lookup"><span data-stu-id="c8924-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="c8924-145">ASP.NET Core Identity では、ログイン、ログアウト、登録など、一般的に必要なページの UI がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c8924-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="c8924-146">そのデータ アクセスには EF Core が利用され、EF Core の移行を使用して、そのデータ モデルをサポートするために必要なスキーマが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c8924-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to support its data model.</span></span> <span data-ttu-id="c8924-147">この [ASP.NET Core の ID の概要](/aspnet/core/security/authentication/identity)では、ASP.NET Core Identity に何が含まれるかと、その使用を開始する方法の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="c8924-147">This [introduction to Identity on ASP.NET Core](/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="c8924-148">アプリケーションとそのデータベースに ASP.NET Core Identity をまだセットアップしていない場合、作業の開始に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c8924-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="c8924-149">ロール、クレーム、ポリシー</span><span class="sxs-lookup"><span data-stu-id="c8924-149">Roles, claims, and policies</span></span>

<span data-ttu-id="c8924-150">ユニバーサル プロバイダーと ASP.NET Core Identity のどちらも、ロールの概念がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c8924-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="c8924-151">ユーザーのロールを作成し、ユーザーをロールに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="c8924-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="c8924-152">ユーザーは任意の数のロールに属することができ、認可実装の一部として、ロール メンバーシップを検証できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="c8924-153">ロールに加えて、ASP.NET Core Identity では、クレームとポリシーの概念がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c8924-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="c8924-154">ロールは、そのロールのユーザーがアクセスできる必要がある一連のリソースに具体的に対応していなければなりませんが、クレームはユーザーの ID の一部にすぎません。</span><span class="sxs-lookup"><span data-stu-id="c8924-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="c8924-155">クレームは、サブジェクトが何であるかを表す名前と値のペアであり、サブジェクトで何が実行できるかではありません。</span><span class="sxs-lookup"><span data-stu-id="c8924-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="c8924-156">ユーザーのクレームを直接検査し、これらの値に基づいて、ユーザーにリソースへのアクセス権を付与するべきかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-156">It is possible to directly inspect a user's claims and determine based on these values whether a user should be given access to a resource.</span></span> <span data-ttu-id="c8924-157">ただし、このようなチェックは多くの場合に繰り返され、システム全体に分散されます。</span><span class="sxs-lookup"><span data-stu-id="c8924-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="c8924-158">より優れたアプローチは、*ポリシー* を定義することです。</span><span class="sxs-lookup"><span data-stu-id="c8924-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="c8924-159">認可ポリシーは、1 つまたは複数の要件で構成されます。</span><span class="sxs-lookup"><span data-stu-id="c8924-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="c8924-160">ポリシーは、`Startup.cs` の `ConfigureServices` メソッドで認可サービス構成の一部として登録します。</span><span class="sxs-lookup"><span data-stu-id="c8924-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="c8924-161">たとえば、次のコード スニペットでは、"CanadiansOnly" というポリシーを構成しており、これには、ユーザーに "Canada" の値の Country クレームがあるという要件があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-161">For example, the following code snippet configures a policy called "CanadiansOnly", which has the requirement that the user has the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="c8924-162">[カスタム ポリシーの作成方法の詳細については、ドキュメントを参照](/aspnet/core/security/authorization/policies)してください。</span><span class="sxs-lookup"><span data-stu-id="c8924-162">You can [learn more about how to create custom policies in the documentation](/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="c8924-163">ポリシーやロールを使用しているかどうかに関係なく、Blazor アプリケーションの特定のページには、`@attribute` ディレクティブで適用された `[Authorize]` 属性を持つロールまたはポリシーが必要であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application requires that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="c8924-164">ロールが必要:</span><span class="sxs-lookup"><span data-stu-id="c8924-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="c8924-165">ポリシーが満たされていることが必要:</span><span class="sxs-lookup"><span data-stu-id="c8924-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="c8924-166">コードで、ユーザーの認証状態、ロール、またはクレームへのアクセスが必要な場合、この機能を実現するために主に 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this functionality.</span></span> <span data-ttu-id="c8924-167">1 つ目は、認証状態をカスケード パラメーターとして受け取ることです。</span><span class="sxs-lookup"><span data-stu-id="c8924-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="c8924-168">2 つ目は、挿入された `AuthenticationStateProvider` を使用して状態にアクセスすることです。</span><span class="sxs-lookup"><span data-stu-id="c8924-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="c8924-169">これらの各アプローチの詳細については、[Blazor のセキュリティに関するドキュメント](/aspnet/core/blazor/security/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8924-169">The details of each of these approaches are described in the [Blazor Security documentation](/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="c8924-170">次のコードは、`AuthenticationState` をカスケード パラメーターとして受け取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8924-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="c8924-171">このパラメーターを設定すると、次のコードを使用してユーザーを取得できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="c8924-172">次のコードは、`AuthenticationStateProvider` を挿入する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8924-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="c8924-173">プロバイダーを設定すると、次のコードを使用してユーザーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c8924-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="c8924-174">**注:** この章の後半で説明する `AuthorizeView` コンポーネントには、ユーザーがページまたはコンポーネントについて見られる内容を、宣言によって制御する方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c8924-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="c8924-175">(Blazor サーバー アプリケーションで) ユーザーとクレームを操作するには、ユーザーのクレームを列挙および変更するために使用できる `UserManager<T>` を挿入することが必要になる場合もあります (既定では `IdentityUser` を使用します)。</span><span class="sxs-lookup"><span data-stu-id="c8924-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="c8924-176">最初に型を挿入し、それをプロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c8924-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="c8924-177">次に、それを使用してユーザーのクレームを処理します。</span><span class="sxs-lookup"><span data-stu-id="c8924-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="c8924-178">次のサンプルは、ユーザーにクレームを追加して保持する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8924-178">The following sample shows how to add and persist a claim on a user:</span></span>

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

<span data-ttu-id="c8924-179">ロールを使用する必要がある場合は、同じアプローチに従います。</span><span class="sxs-lookup"><span data-stu-id="c8924-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="c8924-180">ロール自体の一覧表示と管理のために、`RoleManager<T>` (既定の型には `IdentityRole` を使用) を挿入する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="c8924-181">**注:** Blazor Webassembly プロジェクトでは、これらの操作を実行するためにサーバー API を指定する必要があります (`UserManager<T>` または `RoleManager<T>` を直接使用するのではなく)。</span><span class="sxs-lookup"><span data-stu-id="c8924-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="c8924-182">Blazor Webassembly クライアント アプリケーションでは、この目的のために公開されている API エンドポイントを安全に呼び出すことによって、クレームやロールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="c8924-183">移行ガイド</span><span class="sxs-lookup"><span data-stu-id="c8924-183">Migration guide</span></span>

<span data-ttu-id="c8924-184">ASP.NET Web Forms とユニバーサル プロバイダーから ASP.NET Core Identity に移行するには、いくつかの手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="c8924-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="c8924-185">移行先データベースに ASP.NET Core Identity データベース スキーマを作成する</span><span class="sxs-lookup"><span data-stu-id="c8924-185">Create ASP.NET Core Identity database schema in the destination database</span></span>
2. <span data-ttu-id="c8924-186">ユニバーサル プロバイダー スキーマから ASP.NET Core Identity スキーマにデータを移行する</span><span class="sxs-lookup"><span data-stu-id="c8924-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="c8924-187">`web.config` からミドルウェアおよびサービスに、構成を移行します (通常 `Startup.cs` 内)</span><span class="sxs-lookup"><span data-stu-id="c8924-187">Migrate configuration from the `web.config` to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="c8924-188">タグ ヘルパーと新しい ID API を使用するように、コントロールと条件を使用して、個々のページを更新します。</span><span class="sxs-lookup"><span data-stu-id="c8924-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="c8924-189">以下のセクションでは、これらの各手順について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="c8924-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="c8924-190">ASP.NET Core Identity スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="c8924-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="c8924-191">ASP.NET Core Identity で使用される必要なテーブル構造を作成するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="c8924-192">最も簡単なのは、新しい ASP.NET Core Web アプリケーションを作成することです。</span><span class="sxs-lookup"><span data-stu-id="c8924-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="c8924-193">[Web アプリケーション] を選択し、[認証] を [個人のユーザー アカウント] を使用するように変更します。</span><span class="sxs-lookup"><span data-stu-id="c8924-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![個別のユーザー アカウントによる新しいプロジェクト](./media/security/individual-user-accounts.png)

<span data-ttu-id="c8924-195">コマンド ラインから、`dotnet new webapp -au Individual` を実行して、同じことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c8924-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="c8924-196">アプリが作成されたら、それを実行し、サイトに登録します。</span><span class="sxs-lookup"><span data-stu-id="c8924-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="c8924-197">次に示すようなページをトリガーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-197">You should trigger a page like the one shown below:</span></span>

![移行の適用ページ](./media/security/apply-migrations-page.png)

<span data-ttu-id="c8924-199">[移行の適用] ボタンをクリックすると、必要なデータベース テーブルが自動的に作成されるはずです。</span><span class="sxs-lookup"><span data-stu-id="c8924-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="c8924-200">また、次のように、移行ファイルがプロジェクトに表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="c8924-200">In addition, the migration files should appear in your project, as shown:</span></span>

![移行ファイル](./media/security/migration-files.png)

<span data-ttu-id="c8924-202">Web アプリケーションを実行しなくても、次のコマンドライン ツールを使用して、自分で移行を実行できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-202">You can run the migration yourself, without running the web application, using this command-line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="c8924-203">または新しいスキーマを既存のデータベースに適用するスクリプトを実行する場合は、コマンドラインからこれらの移行をスクリプト化できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command-line.</span></span> <span data-ttu-id="c8924-204">次のコマンドを実行して、スクリプトを生成します。</span><span class="sxs-lookup"><span data-stu-id="c8924-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="c8924-205">上のコマンドによって、出力ファイル `auth.sql` に SQL スクリプトが生成されるので、それを任意のデータベースに対して実行できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-205">The above command will produce a SQL script in the output file `auth.sql`, which can then be run against whatever database you like.</span></span> <span data-ttu-id="c8924-206">`dotnet ef` コマンドの実行で問題が発生した場合は、[EF Core ツールがシステムにインストールされていることを確認](/ef/core/miscellaneous/cli/dotnet)してください。</span><span class="sxs-lookup"><span data-stu-id="c8924-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="c8924-207">ソース テーブルに追加の列がある場合は、新しいスキーマでこれらの列の最適な場所を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="c8924-208">一般に、`aspnet_Membership` テーブルにある列は、`AspNetUsers` テーブルにマッピングされる必要があり ます。</span><span class="sxs-lookup"><span data-stu-id="c8924-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="c8924-209">`aspnet_Roles` の列は、`AspNetRoles` にマッピングされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="c8924-210">`aspnet_UsersInRoles` テーブルの追加の列は、`AspNetUserRoles` テーブルに追加できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="c8924-211">または、個別のテーブルに追加の列を配置することも検討する価値があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-211">It's also worth considering putting any additional columns on separate tables.</span></span> <span data-ttu-id="c8924-212">そうすると、今後の移行で、既定の ID スキーマのカスタマイズを考慮する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="c8924-212">So that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="c8924-213">ユニバーサル プロバイダーから ASP.NET Core Identity へのデータの移行</span><span class="sxs-lookup"><span data-stu-id="c8924-213">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="c8924-214">移行先テーブル スキーマを設定したら、次の手順は、ユーザーとロールのレコードを新しいスキーマに移行することです。</span><span class="sxs-lookup"><span data-stu-id="c8924-214">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="c8924-215">スキーマの違い (どの列がどの新しい列にマッピングされるかなど) の完全な一覧については、[こちら](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8924-215">A complete list of the schema differences, including which columns map to which new columns, can be found [here](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="c8924-216">ユーザーをメンバーシップから新しい ID テーブルに移行するには、[ドキュメントに記載されている手順に従う](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-216">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="c8924-217">これらの手順と提供されているスクリプトに従った後に、ユーザーは次回ログインするときにパスワードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-217">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="c8924-218">ユーザーのパスワードを移行することはできますが、プロセスがはるかに複雑になります。</span><span class="sxs-lookup"><span data-stu-id="c8924-218">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="c8924-219">移行プロセスの一環としてユーザーにパスワードの更新を要求し、新しい一意のパスワードを使用するように勧めることは、アプリケーションの全体的なセキュリティを高める可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-219">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="c8924-220">web.config から Startup.cs へのセキュリティ設定の移行</span><span class="sxs-lookup"><span data-stu-id="c8924-220">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="c8924-221">上記のように、ASP.NET のメンバーシップとロール プロバイダーは、アプリケーションの `web.config` ファイルで構成します。</span><span class="sxs-lookup"><span data-stu-id="c8924-221">As noted above, ASP.NET membership and role providers are configured in the application's `web.config` file.</span></span> <span data-ttu-id="c8924-222">ASP.NET Core アプリは IIS に関連付けられず、構成に個別のシステムが使用されるため、これらの設定を他の場所に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-222">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="c8924-223">ほとんどの場合、ASP.NET Core Identity は `Startup.cs` ファイルで構成します。</span><span class="sxs-lookup"><span data-stu-id="c8924-223">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="c8924-224">(ID テーブル スキーマを作成するために) 前に作成した Web プロジェクトを開き、その `Startup.cs` ファイルを確認します。</span><span class="sxs-lookup"><span data-stu-id="c8924-224">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="c8924-225">既定の ConfigureServices メソッドによって、EF Core と ID のサポートが追加されます。</span><span class="sxs-lookup"><span data-stu-id="c8924-225">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

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

<span data-ttu-id="c8924-226">`AddDefaultIdentity` 拡張メソッドは、既定の `ApplicationDbContext` とフレームワークの `IdentityUser` 型を使用するように ID を構成するために使用します。</span><span class="sxs-lookup"><span data-stu-id="c8924-226">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="c8924-227">カスタム `IdentityUser` を使用している場合は、ここでその型を指定してください。</span><span class="sxs-lookup"><span data-stu-id="c8924-227">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="c8924-228">これらの拡張メソッドがアプリケーションで動作していない場合は、適切な using ステートメントがあることと、必要な NuGet パッケージ参照があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c8924-228">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="c8924-229">たとえば、プロジェクトには、`Microsoft.AspNetCore.Identity.EntityFrameworkCore` の何らかのバージョンと `Microsoft.AspNetCore.Identity.UI` パッケージが参照されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-229">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="c8924-230">また、`Startup.cs` に、サイトに必要なミドルウェアが構成されていることが確認されるはずです。</span><span class="sxs-lookup"><span data-stu-id="c8924-230">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="c8924-231">具体的に、`UseAuthentication` と `UseAuthorization` が設定され、適切な場所にあるはずです。</span><span class="sxs-lookup"><span data-stu-id="c8924-231">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

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

<span data-ttu-id="c8924-232">ASP.NET Identity では、`Startup.cs` から場所への匿名またはロールベースのアクセスを構成しません。</span><span class="sxs-lookup"><span data-stu-id="c8924-232">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="c8924-233">場所固有の認可構成データは ASP.NET Core のフィルターに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-233">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="c8924-234">このような更新が必要になるフォルダーとページをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="c8924-234">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="c8924-235">次のセクションでこれらの変更を行います。</span><span class="sxs-lookup"><span data-stu-id="c8924-235">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="c8924-236">ASP.NET Core Identity の抽象化を使用するように個々のページを更新する</span><span class="sxs-lookup"><span data-stu-id="c8924-236">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="c8924-237">ASP.NET Web Forms アプリケーションで、匿名ユーザーに特定のページまたはフォルダーへのアクセスを拒否する `web.config` 設定があった場合、そのようなページに `[Authorize]` 属性を追加することによって、これらの変更を移行できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-237">In your ASP.NET Web Forms application, if you had `web.config` settings to deny access to certain pages or folders to anonymous users, you would migrate these changes by adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="c8924-238">特定のロールに属しているユーザーを除くアクセスを拒否していた場合は、ロールを指定する属性を追加して、この動作を移行することもできます。</span><span class="sxs-lookup"><span data-stu-id="c8924-238">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this behavior by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="c8924-239">`[Authorize]` 属性は、Blazor ルーター経由で到達される `@page` コンポーネントに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="c8924-239">The `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="c8924-240">この属性は子コンポーネントでは動作せず、代わりに `AuthorizeView` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-240">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="c8924-241">ページ マークアップ内に、特定のユーザーに一部のコードを表示するかどうかを判断するためのロジックがある場合は、これを `AuthorizeView` コンポーネントで置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="c8924-241">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="c8924-242">[AuthorizeView コンポーネント](/aspnet/core/blazor/security#authorizeview-component)では、ユーザーがそれを表示することを認可されているかどうかに応じて、UI を選択的に表示します。</span><span class="sxs-lookup"><span data-stu-id="c8924-242">The [AuthorizeView component](/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="c8924-243">また、ユーザー情報へのアクセスに使用できる `context` 変数も公開されています。</span><span class="sxs-lookup"><span data-stu-id="c8924-243">It also exposes a `context` variable that can be used to access user information.</span></span>

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

<span data-ttu-id="c8924-244">手続き型ロジック内の認証状態にアクセスするには、`[CascadingParameter]` 属性で構成された `Task<AuthenticationState` からユーザーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="c8924-244">You can access the authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="c8924-245">この構成により、ユーザーにアクセスできるようになり、ユーザーが認証されているかどうか、および特定のロールに属しているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="c8924-245">This configuration will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="c8924-246">ポリシーを手続き上評価する必要がある場合は、`IAuthorizationService` のインスタンスを挿入し、それに対して `AuthorizeAsync` メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c8924-246">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="c8924-247">次のサンプル コードは、ユーザー情報を取得し、認可されたユーザーに、`content-editor` ポリシーによって制限されたタスクの実行を許可する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8924-247">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

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

<span data-ttu-id="c8924-248">`AuthenticationState` は、このようなカスケード型パラメーターにバインドする前に、まずカスケード値として設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8924-248">The `AuthenticationState` first need to be set up as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="c8924-249">それは一般に、`CascadingAuthenticationState` コンポーネントを使用して行います。</span><span class="sxs-lookup"><span data-stu-id="c8924-249">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="c8924-250">この構成は、一般に `App.razor` で行います。</span><span class="sxs-lookup"><span data-stu-id="c8924-250">This configuration is typically done in `App.razor`:</span></span>

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

## <a name="summary"></a><span data-ttu-id="c8924-251">まとめ</span><span class="sxs-lookup"><span data-stu-id="c8924-251">Summary</span></span>

<span data-ttu-id="c8924-252">Blazor では、ASP.NET Core Identity である ASP.NET Core と同じセキュリティ モデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8924-252">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="c8924-253">元のデータ スキーマに過剰なカスタマイズが適用されていないことを前提として、ユニバーサル プロバイダーから ASP.NET Core Identity への移行は比較的簡単です。</span><span class="sxs-lookup"><span data-stu-id="c8924-253">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="c8924-254">データが移行されたら、Blazor アプリでの認証と認可の操作については、ドキュメントに詳しく説明されています。構成可能であるほか、ほとんどのセキュリティ要件に対して、プログラムでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c8924-254">Once the data has been migrated, working with authentication and authorization in Blazor apps is well documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="c8924-255">References</span><span class="sxs-lookup"><span data-stu-id="c8924-255">References</span></span>

- [<span data-ttu-id="c8924-256">ASP.NET Core の ID の概要</span><span class="sxs-lookup"><span data-stu-id="c8924-256">Introduction to Identity on ASP.NET Core</span></span>](/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="c8924-257">ASP.NET メンバーシップ認証から ASP.NET Core 2.0 Identity への移行</span><span class="sxs-lookup"><span data-stu-id="c8924-257">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="c8924-258">ASP.NET Core への認証と ID の移行</span><span class="sxs-lookup"><span data-stu-id="c8924-258">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/core/migration/identity)
- [<span data-ttu-id="c8924-259">ASP.NET Core Blazor の認証と認可</span><span class="sxs-lookup"><span data-stu-id="c8924-259">ASP.NET Core Blazor authentication and authorization</span></span>](/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="c8924-260">[前へ](config.md)
>[次へ](migration.md)</span><span class="sxs-lookup"><span data-stu-id="c8924-260">[Previous](config.md)
[Next](migration.md)</span></span>
