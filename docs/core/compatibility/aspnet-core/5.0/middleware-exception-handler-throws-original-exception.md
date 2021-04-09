---
title: 破壊的変更:ミドルウェア:ハンドラーが見つからない場合、例外ハンドラー ミドルウェアから元の例外がスローされる
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: ミドルウェア:ハンドラーが見つからない場合、例外ハンドラー ミドルウェアから元の例外がスローされる'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c28e09e544ac01c04a23fb7d2e73f3fdc242e9cd
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497945"
---
# <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a>ミドルウェア:ハンドラーが見つからない場合、例外ハンドラー ミドルウェアから元の例外がスローされる

ASP.NET Core 5.0 より前では、例外が発生したときに、[Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) によって構成済みの例外ハンドラーが実行されます。 <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> で構成された例外ハンドラーが見つからない場合は、HTTP 404 応答が生成されます。 この応答は、次のような誤解を招きます。

* ユーザー エラーのように見える。
* サーバーで例外が発生したという事実がわからなくなる。

ASP.NET Core 5.0 のこの誤解を招くエラーに対処するために、例外ハンドラーが見つからない場合、`ExceptionHandlerMiddleware` からは元の例外がスローされます。 その結果、サーバーによって HTTP 500 応答が生成されます。 この応答であれば、発生したエラーをデバッグするときにサーバー ログで簡単に調べることができます。

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 RC 1

## <a name="old-behavior"></a>以前の動作

構成された例外ハンドラーが見つからない場合は、Exception Handler Middleware によって HTTP 404 応答が生成されます。

## <a name="new-behavior"></a>新しい動作

構成された例外ハンドラーが見つからない場合は、Exception Handler Middleware からは元の例外がスローされます。

## <a name="reason-for-change"></a>変更理由

HTTP 404 エラーを受け取っても、サーバーで例外が発生したことが明らかにはなりません。 この変更により、HTTP 500 エラーが生成され、次のことが明らかになります。

* 問題の原因はユーザー エラーではない。
* サーバー上で例外が発生した。

## <a name="recommended-action"></a>推奨アクション

API の変更はありません。 既存のすべてのアプリは引き続きコンパイルされ、実行されます。 スローされた例外は、サーバーによって処理されます。 たとえば、例外は [Kestrel](/aspnet/core/fundamentals/servers/kestrel) または [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys) によって HTTP 500 エラー応答に変換されます。

## <a name="affected-apis"></a>影響を受ける API

なし

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
