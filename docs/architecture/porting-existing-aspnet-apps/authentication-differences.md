---
title: ASP.NET MVC と ASP.NET Core 間の認証と承認を比較する
description: ASP.NET MVC と ASP.NET Core の間の認証と承認の違いについて概要を説明します。
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: c8f3314186b7408e40d3a79cbc922a29eb75c5d2
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102401415"
---
# <a name="compare-authentication-and-authorization-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="f3ea8-103">ASP.NET MVC と ASP.NET Core 間の認証と承認を比較する</span><span class="sxs-lookup"><span data-stu-id="f3ea8-103">Compare authentication and authorization between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="f3ea8-104">ASP.NET MVC 5 では、認証は、 *App_Start* フォルダーの *Startup.Auth.cs* で構成されます。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-104">In ASP.NET MVC 5, authentication is configured in *Startup.Auth.cs* in the *App_Start* folder.</span></span> <span data-ttu-id="f3ea8-105">ASP.NET Core MVC では、この構成はで行わ `Startup.cs` れます。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-105">In ASP.NET Core MVC, this configuration occurs in `Startup.cs`.</span></span> <span data-ttu-id="f3ea8-106">認証と承認は、の要求パイプラインに追加されたミドルウェアを使用して実行され `ConfigureServices` ます。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-106">Authentication and authorization are performed using middleware added to the request pipeline in `ConfigureServices`:</span></span>

```csharp
// inside Startup.ConfigureServices

app.UseRouting();

app.UseAuthentication();
app.UseAuthorization();

app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(
        name: "default",
        pattern: "{controller=Home}/{action=Index}/{id?}");
    endpoints.MapRazorPages();
});
```

<span data-ttu-id="f3ea8-107">ミドルウェアパイプラインの適切な順序で auth ミドルウェアを追加することが重要です。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-107">It's important to add the auth middleware in the appropriate order in the middleware pipeline.</span></span> <span data-ttu-id="f3ea8-108">ミドルウェアに対する要求のみが、その影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-108">Only requests that make it to the middleware will be impacted by it.</span></span> <span data-ttu-id="f3ea8-109">たとえば、の呼び出しが `UseStaticFiles()` ここに示したコードの上に配置されている場合、認証と承認によって保護されません。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-109">For instance, if a call to `UseStaticFiles()` was placed above the code shown here, it wouldn't be protected by authentication and authorization.</span></span>

<span data-ttu-id="f3ea8-110">ASP.NET MVC と Web API では、多くの場合、アプリケーションはプロパティを使用して現在のユーザーを参照し `ClaimsPrincipal.Current` ます。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-110">In ASP.NET MVC and Web API, apps often refer to the current user using the `ClaimsPrincipal.Current` property.</span></span> <span data-ttu-id="f3ea8-111">このプロパティは ASP.NET Core では設定されません [。](/aspnet/core/migration/claimsprincipal-current) また、このプロパティに依存するアプリ内のすべての動作は、のプロパティを使用する `User` `ControllerBase` か、現在のにアクセスし、 `HttpContext` そのプロパティを参照する `User` ことによって、ClaimsPrincipal から移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-111">This property isn't set in ASP.NET Core, and any behavior in your app that depends on it will need to [migrate from ClaimsPrincipal.Current](/aspnet/core/migration/claimsprincipal-current) by using the `User` property on `ControllerBase` or getting access to the current `HttpContext` and referencing its `User` property.</span></span> <span data-ttu-id="f3ea8-112">これらのソリューションのいずれもオプションでない場合、サービスはユーザーに引数として要求できます。この場合は、アプリ内の他の場所から指定する必要があります。または、を `IHttpContextAccessor` 要求し、を取得するために使用でき `HttpContext` ます。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-112">If neither of these solutions is an option, services can request the User as an argument, in which case it must be supplied from elsewhere in the app, or the `IHttpContextAccessor` can be requested and used to get the `HttpContext`.</span></span>

## <a name="authorization"></a><span data-ttu-id="f3ea8-113">承認</span><span class="sxs-lookup"><span data-stu-id="f3ea8-113">Authorization</span></span>

<span data-ttu-id="f3ea8-114">承認は、アプリ内で特定のユーザーが実行できる操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-114">Authorization defines what a given user can do within the app.</span></span> <span data-ttu-id="f3ea8-115">これは認証とは別のものであり、ユーザーの身元を特定するだけです。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-115">It's separate from authentication, which is concerned merely with identifying who the user is.</span></span> <span data-ttu-id="f3ea8-116">ASP.NET Core には、単純な宣言型ロールと、承認のための高度なポリシーベースモデルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-116">ASP.NET Core provides a simple, declarative role and a rich, policy-based model for authorization.</span></span> <span data-ttu-id="f3ea8-117">リソースが承認を必要とするように指定することは、多くの場合、 `[Authorize]` アクションまたはコントローラーに属性を追加するのと同じくらい簡単です。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-117">Specifying that a resource requires authorization is often as simple as adding the `[Authorize]` attribute to the action or controller.</span></span> <span data-ttu-id="f3ea8-118">MVC ビューから Razor Pages に移行する場合は、 [起動時に Razor Pages を構成するときに、承認規則を指定](/aspnet/core/security/authorization/razor-pages-authorization)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-118">If you're migrating to Razor Pages from MVC views, you should [specify conventions for authorization when you configure Razor Pages in Startup](/aspnet/core/security/authorization/razor-pages-authorization).</span></span>

<span data-ttu-id="f3ea8-119">ASP.NET Core での承認は、認証されたユーザーを許可すると同時に匿名ユーザーを禁止するのと同じように簡単です。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-119">Authorization in ASP.NET Core may be as simple as prohibiting anonymous users while allowing authenticated users.</span></span> <span data-ttu-id="f3ea8-120">または、ロールベース、クレームベース、またはポリシーベースの承認方法をサポートするようにスケールアップできます。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-120">Or it can scale up to support role-based, claims-based, or policy-based authorization approaches.</span></span> <span data-ttu-id="f3ea8-121">これらの方法の詳細については、 [ASP.NET Core の承認](/aspnet/core/security/authorization/introduction)に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-121">For more information on these approaches, see the documentation on [authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span> <span data-ttu-id="f3ea8-122">そのうちの1つは、現在の承認方法と密接に一致していることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="f3ea8-122">You'll likely find that one of them is closely aligned with your current authorization approach.</span></span>

## <a name="references"></a><span data-ttu-id="f3ea8-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3ea8-123">References</span></span>

- [<span data-ttu-id="f3ea8-124">ASP.NET MVC を使用したセキュリティ、認証、および承認</span><span class="sxs-lookup"><span data-stu-id="f3ea8-124">Security, Authentication, and Authorization with ASP.NET MVC</span></span>](/aspnet/mvc/overview/security/)
- [<span data-ttu-id="f3ea8-125">認証と Id を ASP.NET Core に移行する</span><span class="sxs-lookup"><span data-stu-id="f3ea8-125">Migrate Authentication and Identity to ASP.NET Core</span></span>](/aspnet/mvc/overview/security/)
- [<span data-ttu-id="f3ea8-126">ClaimsPrincipal からの移行</span><span class="sxs-lookup"><span data-stu-id="f3ea8-126">Migrate from ClaimsPrincipal.Current</span></span>](/aspnet/core/migration/claimsprincipal-current)
- [<span data-ttu-id="f3ea8-127">ASP.NET Core での承認の概要</span><span class="sxs-lookup"><span data-stu-id="f3ea8-127">Introduction to Authorization in ASP.NET Core</span></span>](/aspnet/core/security/authorization/introduction)

>[!div class="step-by-step"]
><span data-ttu-id="f3ea8-128">[前へ](webapi-differences.md)
>[次へ](identity-differences.md)</span><span class="sxs-lookup"><span data-stu-id="f3ea8-128">[Previous](webapi-differences.md)
[Next](identity-differences.md)</span></span>
