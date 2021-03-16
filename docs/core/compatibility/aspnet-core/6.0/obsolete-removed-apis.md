---
title: '破壊的変更: 古いおよび削除された API'
description: "\"古いおよび削除された API\" というタイトルが付けられた、ASP.NET Core 6.0 における破壊的変更について説明します"
author: scottaddie
ms.author: scaddie
ms.date: 02/16/2021
ms.openlocfilehash: 4a4819247b7e6bb957f643b457e651cca5b4e703
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108404"
---
# <a name="obsoleted-and-removed-apis"></a>古い API と削除された API

ASP.NET Core 6.0 Preview 1 では、一部の API が削除されたか、古くなったため非推奨とされました。

## <a name="version-introduced"></a>導入されたバージョン

6.0 Preview 1

## <a name="old-behavior"></a>以前の動作

ASP.NET Core 5.0 では、API が削除されておらず、非推奨 (古い) ともされていません。

## <a name="new-behavior"></a>新しい動作

ASP.NET Core 6.0 では、API が削除されており、非推奨とされています。

## <a name="reason-for-change"></a>変更理由

API は使用されていないか、機能しなくなっています。

## <a name="recommended-action"></a>推奨アクション

推奨される代替 API を使用します。

## <a name="affected-apis"></a>影響を受ける API

* [Microsoft.AspNetCore.Http.Connections.ParseResponse](/dotnet/api/microsoft.aspnetcore.http.connections.negotiateprotocol.parseresponse?view=aspnetcore-3.1&preserve-view=true#Microsoft_AspNetCore_Http_Connections_NegotiateProtocol_ParseResponse_System_IO_Stream_) が削除されました。 代わりに <xref:Microsoft.AspNetCore.Http.Connections.NegotiateProtocol.ParseResponse(System.ReadOnlySpan{System.Byte})?displayProperty=nameWithType> を使用してください
* [Microsoft.AspNetCore.SignalR.HubInvocationContext](/dotnet/api/microsoft.aspnetcore.signalr.hubinvocationcontext.-ctor?view=aspnetcore-5.0&preserve-view=true#Microsoft_AspNetCore_SignalR_HubInvocationContext__ctor_Microsoft_AspNetCore_SignalR_HubCallerContext_System_String_System_Object___) が削除されました。 代わりに <xref:Microsoft.AspNetCore.SignalR.HubInvocationContext.%23ctor(Microsoft.AspNetCore.SignalR.HubCallerContext,System.IServiceProvider,Microsoft.AspNetCore.SignalR.Hub,System.Reflection.MethodInfo,System.Collections.Generic.IReadOnlyList{System.Object})?displayProperty=nameWithType> を使用してください
* [Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature](/dotnet/api/microsoft.aspnetcore.http.features.ihttpbufferingfeature?view=aspnetcore-3.1&preserve-view=true) が削除されました。 代わりに <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseBodyFeature?displayProperty=nameWithType> を使用してください
* [Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature](/dotnet/api/microsoft.aspnetcore.http.features.ihttpsendfilefeature?view=aspnetcore-3.1&preserve-view=true) が削除されました。 代わりに <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseBodyFeature?displayProperty=nameWithType> を使用してください
* [Microsoft.AspNetCore.StaticFiles.StaticFileResponseContext](/dotnet/api/microsoft.aspnetcore.staticfiles.staticfileresponsecontext.-ctor?view=aspnetcore-3.1&preserve-view=true#Microsoft_AspNetCore_StaticFiles_StaticFileResponseContext__ctor) の引数なしコンストラクターが削除されました。 代わりに <xref:Microsoft.AspNetCore.StaticFiles.StaticFileResponseContext.%23ctor(Microsoft.AspNetCore.Http.HttpContext,Microsoft.Extensions.FileProviders.IFileInfo)?displayProperty=nameWithType> を使用してください
* コンストラクター [Microsoft.AspNetCore.Mvc.Infrastructure.ObjectResultExecutor](/dotnet/api/microsoft.aspnetcore.mvc.infrastructure.objectresultexecutor.-ctor?view=aspnetcore-3.1&preserve-view=true#Microsoft_AspNetCore_Mvc_Infrastructure_ObjectResultExecutor__ctor_Microsoft_AspNetCore_Mvc_Infrastructure_OutputFormatterSelector_Microsoft_AspNetCore_Mvc_Infrastructure_IHttpResponseStreamWriterFactory_Microsoft_Extensions_Logging_ILoggerFactory_) が削除されました。 代わりに <xref:Microsoft.AspNetCore.Mvc.Infrastructure.ObjectResultExecutor.%23ctor(Microsoft.AspNetCore.Mvc.Infrastructure.OutputFormatterSelector,Microsoft.AspNetCore.Mvc.Infrastructure.IHttpResponseStreamWriterFactory,Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})?displayProperty=nameWithType> を使用してください
* [Microsoft.AspNetCore.Mvc.ModelBinding.ValidationAllowShortCircuitingValidationWhenNoValidatorsArePresent](/dotnet/api/microsoft.aspnetcore.mvc.modelbinding.validation.validationvisitor.allowshortcircuitingvalidationwhennovalidatorsarepresent?view=aspnetcore-3.1&preserve-view=true#Microsoft_AspNetCore_Mvc_ModelBinding_Validation_ValidationVisitor_AllowShortCircuitingValidationWhenNoValidatorsArePresent) が削除されました。
* [Microsoft.AspNetCore.Mvc.ViewFeatures.ViewComponentResultExecutor](/dotnet/api/microsoft.aspnetcore.mvc.viewfeatures.viewcomponentresultexecutor.-ctor?view=aspnetcore-3.1&preserve-view=true#Microsoft_AspNetCore_Mvc_ViewFeatures_ViewComponentResultExecutor__ctor_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Mvc_MvcViewOptions__Microsoft_Extensions_Logging_ILoggerFactory_System_Text_Encodings_Web_HtmlEncoder_Microsoft_AspNetCore_Mvc_ModelBinding_IModelMetadataProvider_Microsoft_AspNetCore_Mvc_ViewFeatures_ITempDataDictionaryFactory_) が削除されました。 代わりに <xref:Microsoft.AspNetCore.Mvc.ViewFeatures.ViewComponentResultExecutor.%23ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcViewOptions},Microsoft.Extensions.Logging.ILoggerFactory,System.Text.Encodings.Web.HtmlEncoder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.ViewFeatures.ITempDataDictionaryFactory,Microsoft.AspNetCore.Mvc.Infrastructure.IHttpResponseStreamWriterFactory)?displayProperty=nameWithType> を使用してください
* [CompatibilityVersion](/dotnet/api/microsoft.aspnetcore.mvc.compatibilityversion?view=aspnetcore-3.1&preserve-view=true) が非推奨になりました。

<!--

## Category

ASP.NET Core

## Affected APIs

- `M:Microsoft.AspNetCore.Http.Connections.NegotiateProtocol.ParseResponse(System.IO.Stream)`
- `M:Microsoft.AspNetCore.SignalR.HubInvocationContext.#ctor(Microsoft.AspNetCore.SignalR.HubCallerContext,System.String,System.Object[])`
- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`
- `M:Microsoft.AspNetCore.StaticFiles.StaticFileResponseContext.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Infrastructure.ObjectResultExecutor.#ctor(Microsoft.AspNetCore.Mvc.Infrastructure.OutputFormatterSelector,Microsoft.AspNetCore.Mvc.Infrastructure.IHttpResponseStreamWriterFactory,Microsoft.Extensions.Logging.ILoggerFactory)`
- `Overload:Microsoft.AspNetCore.Mvc.ModelBinding.Validation.ValidationVisitor.AllowShortCircuitingValidationWhenNoValidatorsArePresent`
- `M:Microsoft.AspNetCore.Mvc.ViewFeatures.ViewComponentResultExecutor.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcViewOptions},Microsoft.Extensions.Logging.ILoggerFactory,System.Text.Encodings.Web.HtmlEncoder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.ViewFeatures.ITempDataDictionaryFactory)`
- `T:Microsoft.AspNetCore.Mvc.CompatibilityVersion`

-->
