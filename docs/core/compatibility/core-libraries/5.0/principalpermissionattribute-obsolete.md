---
title: 破壊的変更:PrincipalPermissionAttribute は現在使用されていないエラーです
description: Core .NET ライブラリにおける .NET 5 の破壊的変更について学習します。PrincipalPermissionAttribute コンストラクターは非推奨であり、コンパイル時のエラーを発生させます。
ms.date: 11/01/2020
ms.openlocfilehash: 7568883935633e98b884b553efccf50504448b77
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257233"
---
# <a name="principalpermissionattribute-is-obsolete-as-error"></a>PrincipalPermissionAttribute は現在使用されていないエラーです

<xref:System.Security.Permissions.PrincipalPermissionAttribute> コンストラクターは非推奨であり、コンパイル時のエラーを発生させます。 この属性をインスタンス化したり、メソッドに適用したりすることはできません。

## <a name="change-description"></a>変更の説明

.NET Framework と .NET Core では、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性を使用してメソッドに注釈を付けることができます。 次に例を示します。

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

.NET 5 以降では、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 属性をメソッドに適用できません。 この属性のコンストラクターは非推奨であり、コンパイル時のエラーを発生させます。 他の非推奨警告とは異なり、エラーを非表示にすることはできません。

## <a name="reason-for-change"></a>変更理由

<xref:System.Security.Permissions.SecurityAttribute> をサブクラス化する他の型と同様に、<xref:System.Security.Permissions.PrincipalPermissionAttribute> 型は .NET のコード アクセス セキュリティ (CAS) インフラストラクチャに含まれます。 .NET Framework 2.x から 4.x では、完全信頼のシナリオの下でアプリケーションが実行されている場合でも、ランタイムによってメソッド エントリで <xref:System.Security.Permissions.PrincipalPermissionAttribute> 注釈が強制されます。 .NET Core と .NET 5 以降では CAS 属性がサポートされず、ランタイムで無視されます。

.NET Framework の動作と .NET Core と .NET 5 の動作がこのように違うことで、アクセスをブロックすべきなのに許可される "フェール オープン" シナリオが発生します。 "フェール オープン" シナリオを回避するため、.NET 5 以降を対象とするコードではこの属性を適用できません。

## <a name="version-introduced"></a>導入されたバージョン

5.0

## <a name=""></a><a id="permission-action">推奨される操作</a>

非推奨エラーが発生する場合、措置をとる必要があります。

- **ASP.NET MVC アクション メソッドにこの属性を適用する場合:**

  ASP.NET に組み込まれている承認インフラストラクチャを使用することを検討してください。 次のコードからは、<xref:System.Web.Mvc.AuthorizeAttribute> 属性を使用してコントローラーに注釈を付ける方法がわかります。 ASP.NET ランタイムによって、アクションの実行前に、ユーザーが承認されます。

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  詳細については、「[ASP.NET Core でのロールベースの承認](/aspnet/core/security/authorization/roles)」と「[ASP.NET Core での承認の概要](/aspnet/core/security/authorization/introduction)」を参照してください。

- **Web アプリのコンテキスト外でライブラリ コードにこの属性を適用する場合:**

  メソッドの先頭で手動確認します。 これは <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> メソッドを使用すると実行できます。

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

## <a name="affected-apis"></a>影響を受ける API

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
