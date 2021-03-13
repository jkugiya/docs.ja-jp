---
title: '破壊的変更: セキュリティ: Cookie 名のエンコードを削除'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: セキュリティ: Cookie 名のエンコードを削除'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 00764493fb2d8d300612f2bd9dc6e512b10be25f
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190061"
---
# <a name="security-cookie-name-encoding-removed"></a><span data-ttu-id="0da92-103">セキュリティ:Cookie 名のエンコードを削除</span><span class="sxs-lookup"><span data-stu-id="0da92-103">Security: Cookie name encoding removed</span></span>

<span data-ttu-id="0da92-104">[HTTP Cookie 標準](https://tools.ietf.org/html/rfc6265#section-4.1.1)では、Cookie の名前と値で特定の文字のみが許可されます。</span><span class="sxs-lookup"><span data-stu-id="0da92-104">The [HTTP cookie standard](https://tools.ietf.org/html/rfc6265#section-4.1.1) allows only specific characters in cookie names and values.</span></span> <span data-ttu-id="0da92-105">許可されていない文字をサポートするため、ASP.NET Core は次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="0da92-105">To support disallowed characters, ASP.NET Core:</span></span>

* <span data-ttu-id="0da92-106">応答 Cookie の作成時にエンコードします。</span><span class="sxs-lookup"><span data-stu-id="0da92-106">Encodes when creating a response cookie.</span></span>
* <span data-ttu-id="0da92-107">要求 Cookie の読み取り時にデコードします。</span><span class="sxs-lookup"><span data-stu-id="0da92-107">Decodes when reading a request cookie.</span></span>

<span data-ttu-id="0da92-108">ASP.NET Core 5.0 では、あるセキュリティ問題に対処するため、このエンコード動作が変更されました。</span><span class="sxs-lookup"><span data-stu-id="0da92-108">In ASP.NET Core 5.0, this encoding behavior changed in response to a security concern.</span></span>

<span data-ttu-id="0da92-109">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0da92-109">For discussion, see GitHub issue [dotnet/aspnetcore#23578](https://github.com/dotnet/aspnetcore/issues/23578).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0da92-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="0da92-110">Version introduced</span></span>

<span data-ttu-id="0da92-111">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0da92-111">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="0da92-112">以前の動作</span><span class="sxs-lookup"><span data-stu-id="0da92-112">Old behavior</span></span>

<span data-ttu-id="0da92-113">応答 Cookie 名がエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="0da92-113">Response cookie names are encoded.</span></span> <span data-ttu-id="0da92-114">要求 Cookie 名がデコードされます。</span><span class="sxs-lookup"><span data-stu-id="0da92-114">Request cookie names are decoded.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="0da92-115">新しい動作</span><span class="sxs-lookup"><span data-stu-id="0da92-115">New behavior</span></span>

<span data-ttu-id="0da92-116">Cookie 名のエンコードとデコードがなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0da92-116">Encoding and decoding of cookie names was removed.</span></span> <span data-ttu-id="0da92-117">以前に[サポートされていたバージョン](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)の ASP.NET Core の場合、チームはその場でデコード問題を軽減することを計画します。</span><span class="sxs-lookup"><span data-stu-id="0da92-117">For prior [supported versions](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) of ASP.NET Core, the team plans to mitigate the decoding issue in-place.</span></span> <span data-ttu-id="0da92-118">また、無効な Cookie 名で <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> を呼び出すと、型 <xref:System.ArgumentException> の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0da92-118">Additionally, calling <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> with an invalid cookie name throws an exception of type <xref:System.ArgumentException>.</span></span> <span data-ttu-id="0da92-119">Cookie 値のエンコードとデコードは変更されていません。</span><span class="sxs-lookup"><span data-stu-id="0da92-119">Encoding and decoding of cookie values remains unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0da92-120">変更理由</span><span class="sxs-lookup"><span data-stu-id="0da92-120">Reason for change</span></span>

<span data-ttu-id="0da92-121">[複数の Web フレームワーク](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)で問題が検出されました。</span><span class="sxs-lookup"><span data-stu-id="0da92-121">An issue was discovered in [multiple web frameworks](https://github.com/advisories/GHSA-j6w9-fv6q-3q52).</span></span> <span data-ttu-id="0da92-122">このエンコードとデコードでは、攻撃者は `__%48ost-` のようなエンコード値で `__Host-` のような予約済みプレフィックスになりすますことで [Cookie プレフィックス](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00)と呼ばれているセキュリティ機能を迂回できます。</span><span class="sxs-lookup"><span data-stu-id="0da92-122">The encoding and decoding could allow an attacker to bypass a security feature called [cookie prefixes](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) by spoofing reserved prefixes like `__Host-` with encoded values like `__%48ost-`.</span></span> <span data-ttu-id="0da92-123">この攻撃では、Web サイトで、クロスサイト スクリプティング (XSS) の脆弱性など、なりすまし Cookie を挿入するため、第二のエクスプロイトが必要になります。</span><span class="sxs-lookup"><span data-stu-id="0da92-123">The attack requires a secondary exploit to inject the spoofed cookies, such as a cross-site scripting (XSS) vulnerability, in the website.</span></span> <span data-ttu-id="0da92-124">こうしたプレフィックスは既定で、ASP.NET Core や `Microsoft.Owin` のライブラリまたはテンプレートでは使用されません。</span><span class="sxs-lookup"><span data-stu-id="0da92-124">These prefixes aren't used by default in ASP.NET Core or `Microsoft.Owin` libraries or templates.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0da92-125">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="0da92-125">Recommended action</span></span>

<span data-ttu-id="0da92-126">ASP.NET Core 5.0 以降にプロジェクトを移動する場合、Cookie 名が[トークン仕様要件](https://tools.ietf.org/html/rfc2616#section-2.2): コントロールと区切りを除く ASCII 文字 `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` に準拠するようにします。</span><span class="sxs-lookup"><span data-stu-id="0da92-126">If you're moving projects to ASP.NET Core 5.0 or later, ensure that their cookie names conform to the [token specification requirements](https://tools.ietf.org/html/rfc2616#section-2.2): ASCII characters excluding controls and separators `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT`.</span></span> <span data-ttu-id="0da92-127">Cookie 名やその他の HTTP ヘッダーで ASCII 以外の文字を使用すると、サーバーから例外を引き起こしたり、クライアントによって不適切にラウンドトリップしたりします。</span><span class="sxs-lookup"><span data-stu-id="0da92-127">The use of non-ASCII characters in cookie names or other HTTP headers may cause an exception from the server or be improperly round-tripped by the client.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0da92-128">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="0da92-128">Affected APIs</span></span>

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
