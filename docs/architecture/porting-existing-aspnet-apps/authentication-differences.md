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
# <a name="compare-authentication-and-authorization-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC と ASP.NET Core 間の認証と承認を比較する

ASP.NET MVC 5 では、認証は、 *App_Start* フォルダーの *Startup.Auth.cs* で構成されます。 ASP.NET Core MVC では、この構成はで行わ `Startup.cs` れます。 認証と承認は、の要求パイプラインに追加されたミドルウェアを使用して実行され `ConfigureServices` ます。

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

ミドルウェアパイプラインの適切な順序で auth ミドルウェアを追加することが重要です。 ミドルウェアに対する要求のみが、その影響を受けます。 たとえば、の呼び出しが `UseStaticFiles()` ここに示したコードの上に配置されている場合、認証と承認によって保護されません。

ASP.NET MVC と Web API では、多くの場合、アプリケーションはプロパティを使用して現在のユーザーを参照し `ClaimsPrincipal.Current` ます。 このプロパティは ASP.NET Core では設定されません [。](/aspnet/core/migration/claimsprincipal-current) また、このプロパティに依存するアプリ内のすべての動作は、のプロパティを使用する `User` `ControllerBase` か、現在のにアクセスし、 `HttpContext` そのプロパティを参照する `User` ことによって、ClaimsPrincipal から移行する必要があります。 これらのソリューションのいずれもオプションでない場合、サービスはユーザーに引数として要求できます。この場合は、アプリ内の他の場所から指定する必要があります。または、を `IHttpContextAccessor` 要求し、を取得するために使用でき `HttpContext` ます。

## <a name="authorization"></a>承認

承認は、アプリ内で特定のユーザーが実行できる操作を定義します。 これは認証とは別のものであり、ユーザーの身元を特定するだけです。 ASP.NET Core には、単純な宣言型ロールと、承認のための高度なポリシーベースモデルが用意されています。 リソースが承認を必要とするように指定することは、多くの場合、 `[Authorize]` アクションまたはコントローラーに属性を追加するのと同じくらい簡単です。 MVC ビューから Razor Pages に移行する場合は、 [起動時に Razor Pages を構成するときに、承認規則を指定](/aspnet/core/security/authorization/razor-pages-authorization)する必要があります。

ASP.NET Core での承認は、認証されたユーザーを許可すると同時に匿名ユーザーを禁止するのと同じように簡単です。 または、ロールベース、クレームベース、またはポリシーベースの承認方法をサポートするようにスケールアップできます。 これらの方法の詳細については、 [ASP.NET Core の承認](/aspnet/core/security/authorization/introduction)に関するドキュメントを参照してください。 そのうちの1つは、現在の承認方法と密接に一致していることが考えられます。

## <a name="references"></a>関連項目

- [ASP.NET MVC を使用したセキュリティ、認証、および承認](/aspnet/mvc/overview/security/)
- [認証と Id を ASP.NET Core に移行する](/aspnet/mvc/overview/security/)
- [ClaimsPrincipal からの移行](/aspnet/core/migration/claimsprincipal-current)
- [ASP.NET Core での承認の概要](/aspnet/core/security/authorization/introduction)

>[!div class="step-by-step"]
>[前へ](webapi-differences.md)
>[次へ](identity-differences.md)
