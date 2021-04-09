---
title: '破壊的変更: 静的ファイル: CSV コンテンツ タイプが標準準拠に変更されました'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: 静的ファイル: CSV コンテンツ タイプが標準準拠に変更されました'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3a7a1b2fc94f5cc956d85fc93ae72362e2e89b0e
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497087"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>静的ファイル: CSV コンテンツ タイプが標準準拠に変更されました

ASP.NET Core 5.0 では、[静的ファイル ミドルウェア](/aspnet/core/fundamentals/static-files) によって *.csv* ファイルに使用される既定の `Content-Type` 応答ヘッダー値が、標準に準拠した値 `text/csv` に変更されました。

この問題に関するディスカッションについては、[dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 1

## <a name="old-behavior"></a>以前の動作

`Content-Type` ヘッダー値 `application/octet-stream` が使用されていました。

## <a name="new-behavior"></a>新しい動作

`Content-Type` ヘッダー値 `text/csv` が使用されます。

## <a name="reason-for-change"></a>変更理由

[RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) 標準に準拠しています。

## <a name="recommended-action"></a>推奨アクション

この変更によってアプリが影響を受ける場合は、ファイル拡張子と MIME の種類のマッピングをカスタマイズできます。 MIME の種類 `application/octet-stream` に戻すには、`Startup.Configure` でメソッド呼び出し <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> を変更します。 次に例を示します。

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

マッピングのカスタマイズの詳細については、「[FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider)」を参照してください。

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
