---
title: 破壊的変更:ミドルウェア:HTTPS リダイレクト ミドルウェアがあいまいな HTTPS ポートで例外をスローする
description: 'ASP.NET Core 6.0 での破壊的変更について説明します。タイトル: ミドルウェア:HTTPS リダイレクト ミドルウェアがあいまいな HTTPS ポートで例外をスローする'
ms.author: scaddie
ms.date: 02/04/2021
ms.openlocfilehash: 5c41251fac29f7c2dc2bdc3eb5610bb571f438c9
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497022"
---
# <a name="middleware-https-redirection-middleware-throws-exception-on-ambiguous-https-ports"></a>ミドルウェア:HTTPS リダイレクト ミドルウェアがあいまいな HTTPS ポートで例外をスローする

ASP.NET Core 6.0 で [HTTPS リダイレクト ミドルウェア](xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A)によって、サーバー構成で複数の HTTPS ポートが検出されると、<xref:System.InvalidOperationException> 型の例外がスローされます。 この例外メッセージには、"値が複数見つかり、IServerAddressesFeature から https ポートを判別できません。 希望のポートを HttpsRedirectionOptions.HttpsPort に明示的に設定してください。" というテキストが含まれます。

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#29222](https://github.com/dotnet/aspnetcore/issues/29222) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

6.0

## <a name="old-behavior"></a>以前の動作

HTTPS リダイレクト ミドルウェアにポートが明示的に構成されていない場合、最初の要求時に <xref:Microsoft.AspNetCore.Hosting.Server.Features.IServerAddressesFeature> が検索され、リダイレクト先の HTTPS ポートが決定されます。

HTTPS ポートがない場合、または個別のポートが複数ある場合は、どのポートを使用すべきか判別できません。 ミドルウェアが警告をログし、自身を無効にします。 HTTP 要求は正常に処理されます。

## <a name="new-behavior"></a>新しい動作

HTTPS リダイレクト ミドルウェアにポートが明示的に構成されていない場合、最初の要求時に `IServerAddressesFeature` が検索され、リダイレクト先の HTTPS ポートが決定されます。

HTTPS ポートがない場合は、ミドルウェアが警告をログ記録し、自身を無効にします。 HTTP 要求は正常に処理されます。 この動作では、次がサポートされます。

* HTTPS を使用しない開発シナリオ。
* サーバーに到達する前に TLS が終了するホストされるシナリオ。

個別のポートが複数ある場合は、どのポートを使用すべきか判別できません。 ミドルウェアが例外をスローし、HTTP 要求は失敗します。

## <a name="reason-for-change"></a>変更理由

この変更により、HTTPS が使用できることがわかっているときに、機密である可能性があるデータが、暗号化されていない HTTP 接続を介して送信されなくなります。

## <a name="recommended-action"></a>推奨される操作

サーバーに個別の HTTPS ポートが複数ある場合に HTTPS リダイレクトを有効にするには、構成でポートを 1 つ指定する必要があります。 詳細については、「[ポート構成](/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&preserve-view=true#port-configuration)」を参照してください。

お使いのアプリで HTTPS リダイレクト ミドルウェアが不要な場合は、*Startup.cs* から `UseHttpsRedirection` を削除します。

正しい HTTPS ポートを動的に選択する必要がある場合は、GitHub のイシュー [dotnet/aspnetcore#21291](https://github.com/dotnet/aspnetcore/issues/21291) にフィードバックを提供してください。

## <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A?displayProperty=nameWithType>

<!--

## Category

ASP.NET Core

## Affected APIs

`Overload:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection`

-->
