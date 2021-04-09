---
title: '破壊的変更: セキュリティ: Cookie 名のエンコードを削除'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: セキュリティ: Cookie 名のエンコードを削除'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: a50ef0ee34b7148d13b01f96e754d1cb47d40819
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497892"
---
# <a name="security-cookie-name-encoding-removed"></a>セキュリティ:Cookie 名のエンコードを削除

[HTTP Cookie 標準](https://tools.ietf.org/html/rfc6265#section-4.1.1)では、Cookie の名前と値で特定の文字のみが許可されます。 許可されていない文字をサポートするため、ASP.NET Core は次のように動作します。

* 応答 Cookie の作成時にエンコードします。
* 要求 Cookie の読み取り時にデコードします。

ASP.NET Core 5.0 では、あるセキュリティ問題に対処するため、このエンコード動作が変更されました。

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 8

## <a name="old-behavior"></a>以前の動作

応答 Cookie 名がエンコードされます。 要求 Cookie 名がデコードされます。

## <a name="new-behavior"></a>新しい動作

Cookie 名のエンコードとデコードがなくなりました。 以前に[サポートされていたバージョン](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)の ASP.NET Core の場合、チームはその場でデコード問題を軽減することを計画します。 また、無効な Cookie 名で <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> を呼び出すと、型 <xref:System.ArgumentException> の例外がスローされます。 Cookie 値のエンコードとデコードは変更されていません。

## <a name="reason-for-change"></a>変更理由

[複数の Web フレームワーク](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)で問題が検出されました。 このエンコードとデコードでは、攻撃者は `__%48ost-` のようなエンコード値で `__Host-` のような予約済みプレフィックスになりすますことで [Cookie プレフィックス](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00)と呼ばれているセキュリティ機能を迂回できます。 この攻撃では、Web サイトで、クロスサイト スクリプティング (XSS) の脆弱性など、なりすまし Cookie を挿入するため、第二のエクスプロイトが必要になります。 こうしたプレフィックスは既定で、ASP.NET Core や `Microsoft.Owin` のライブラリまたはテンプレートでは使用されません。

## <a name="recommended-action"></a>推奨アクション

ASP.NET Core 5.0 以降にプロジェクトを移動する場合、Cookie 名が[トークン仕様要件](https://tools.ietf.org/html/rfc2616#section-2.2): コントロールと区切りを除く ASCII 文字 `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` に準拠するようにします。 Cookie 名やその他の HTTP ヘッダーで ASCII 以外の文字を使用すると、サーバーから例外を引き起こしたり、クライアントによって不適切にラウンドトリップしたりします。

## <a name="affected-apis"></a>影響を受ける API

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- `Microsoft.Owin.IOwinRequest.Cookies`
- `Microsoft.Owin.IOwinResponse.Cookies`

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
