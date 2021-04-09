---
title: 破壊的変更:ミドルウェア:非推奨とマークされたデータベース エラー ページ
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: ミドルウェア:非推奨とマークされたデータベース エラー ページ'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 8bc8852d7fb54b0d558342ee3c69085117512a1a
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497620"
---
# <a name="middleware-database-error-page-marked-as-obsolete"></a>ミドルウェア:非推奨とマークされたデータベース エラー ページ

[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) とそれに関連付けられている拡張メソッドは ASP.NET Core 5.0 で非推奨としてマークされました。 このミドルウェアと拡張メソッドは ASP.NET Core 6.0 で削除されます。 この機能は代わりに `DatabaseDeveloperPageExceptionFilter` とその拡張メソッドによって提供されます。

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 RC 1

## <a name="old-behavior"></a>以前の動作

`DatabaseErrorPageMiddleware` とそれに関連付けられている拡張メソッドは非推奨ではありませんでした。

## <a name="new-behavior"></a>新しい動作

`DatabaseErrorPageMiddleware` とそれに関連付けられている拡張メソッドは非推奨です。

## <a name="reason-for-change"></a>変更理由

`DatabaseErrorPageMiddleware` は、[開発者例外ページ](/aspnet/core/fundamentals/error-handling#developer-exception-page)の拡張可能 API に移行されました。 拡張可能 API の詳細については、GitHub イシュー [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536) を参照してください。

## <a name="recommended-action"></a>推奨アクション

次の手順のようにします。

1. プロジェクトでの `DatabaseErrorPageMiddleware` の使用を停止してください。 たとえば、`Startup.Configure` から `UseDatabaseErrorPage` メソッド呼び出しを削除します。

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. 開発者例外ページをプロジェクトに追加します。 たとえば、`Startup.Configure` で <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> メソッドを呼び出します。

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. プロジェクト ファイルに [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet パッケージを追加します。

1. データベース開発者ページ例外フィルターをサービス コレクションに追加します。 たとえば、`Startup.ConfigureServices` で `AddDatabaseDeveloperPageExceptionFilter` メソッドを呼び出します。

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a>影響を受ける API

- [Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
