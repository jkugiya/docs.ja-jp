---
title: '破壊的変更: Razor: 古いとしてマークされた RazorEngine API'
description: 'ASP.NET Core 6.0 での破壊的変更に関する詳細。タイトル: Razor: 古いとしてマークされた RazorEngine API'
no-loc:
- Razor
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 75ccc8e2640dda29749de40946e90c2b897a7245
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292250"
---
# <a name="razor-razorengine-apis-marked-obsolete"></a>Razor: 古いとしてマークされた RazorEngine API

Blazor の <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> 型に関連する型は、古いとしてマークされています。

## <a name="version-introduced"></a>導入されたバージョン

ASP.NET Core 6.0 Preview 1

## <a name="old-behavior"></a>以前の動作

`RazorEngine` API は古くありません。

## <a name="new-behavior"></a>新しい動作

`RazorEngine` API は非推奨になっています。

## <a name="reason-for-change"></a>変更理由

`RazorEngine` 型は、<xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> 型を優先して非推奨になっています。

## <a name="recommended-action"></a>推奨される操作

`RazorEngine` 型から `RazorProjectEngine` 型にソース コードを移行します。

## <a name="affected-apis"></a>影響を受ける API

- `Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- [Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

<!--

## Category

ASP.NET Core

## Affected APIs

- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register`
- `T:Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder`

-->
