---
title: 破壊的変更:ローカリゼーション:ローカライズ ミドルウェア要求で古いコンストラクターを削除
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: ローカリゼーション:ローカライズ ミドルウェア要求で古いコンストラクターを削除'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 8c04e1735c5a35d1539b6fcb2506dbe37183ff79
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497984"
---
# <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>ローカリゼーション:ローカライズ ミドルウェア要求で古いコンストラクターを削除

<xref:Microsoft.Extensions.Logging.ILoggerFactory> パラメーターのない <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> コンストラクターは[このコミットで](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)非推奨になりました。 ASP.NET Core 5.0 では、非推奨コンストラクターが削除されました。 ディスカッションについては、[dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785) を参照してください。

## <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 8

## <a name="old-behavior"></a>以前の動作

非推奨 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` コンストラクターが存在します。

## <a name="new-behavior"></a>新しい動作

非推奨 `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` コンストラクターが存在しません。

## <a name="reason-for-change"></a>変更理由

この変更により、ローカライズ ミドルウェア要求で常にロガーにアクセスできます。

## <a name="recommended-action"></a>推奨アクション

`RequestLocalizationMiddleware` のインスタンスを手動で構築するとき、コンストラクターで `ILoggerFactory` インスタンスを渡します。 そのコンテキストで有効な `ILoggerFactory` インスタンスが利用できない場合、ミドルウェア コンストラクターに <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> インスタンスを渡すことを検討してください。

## <a name="affected-apis"></a>影響を受ける API

[RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

### Category

ASP.NET Core

### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
