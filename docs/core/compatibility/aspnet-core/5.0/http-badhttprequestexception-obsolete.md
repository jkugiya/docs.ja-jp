---
title: 破壊的変更:HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5837018def634b732b4f273f1a794267f4d17972
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498140"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP:Kestrel 型と IIS BadHttpRequestException 型が非推奨となり、置換されました

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は非推奨となっており、`Microsoft.AspNetCore.Http.BadHttpRequestException` から誘導するように変更されています。 Kestrel サーバーと IIS サーバーでは、下位互換性のために、今後も以前の例外型がスローされます。 非推奨になった型は、将来のリリースで削除される予定です。

ディスカッションについては、[dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 4

## <a name="old-behavior"></a>以前の動作

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と`Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は <xref:System.IO.IOException?displayProperty=nameWithType> から派生しています。

## <a name="new-behavior"></a>新しい動作

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` は非推奨になっています。 型は、`System.IO.IOException` の派生型である `Microsoft.AspNetCore.Http.BadHttpRequestException` からも派生します。

## <a name="reason-for-change"></a>変更理由

次の変更が行われました。

* 重複する型を統合します。
* 異なるサーバー実装間で動作を統一します。

Kestrel または IIS の使用時、アプリで基本例外 `Microsoft.AspNetCore.Http.BadHttpRequestException` をキャッチできるようになりました。

## <a name="recommended-action"></a>推奨アクション

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` と `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` の使用状況を `Microsoft.AspNetCore.Http.BadHttpRequestException` に置換します。

## <a name="affected-apis"></a>影響を受ける API

- [Microsoft.AspNetCore.Server.IIS.BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
