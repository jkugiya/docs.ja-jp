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
# <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="f2276-103">ミドルウェア:ハンドラーが見つからない場合、例外ハンドラー ミドルウェアから元の例外がスローされる</span><span class="sxs-lookup"><span data-stu-id="f2276-103">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="f2276-104">ASP.NET Core 5.0 より前では、例外が発生したときに、[Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) によって構成済みの例外ハンドラーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="f2276-104">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="f2276-105"><xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> で構成された例外ハンドラーが見つからない場合は、HTTP 404 応答が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f2276-105">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="f2276-106">この応答は、次のような誤解を招きます。</span><span class="sxs-lookup"><span data-stu-id="f2276-106">The response is misleading in that it:</span></span>

* <span data-ttu-id="f2276-107">ユーザー エラーのように見える。</span><span class="sxs-lookup"><span data-stu-id="f2276-107">Seems to be a user error.</span></span>
* <span data-ttu-id="f2276-108">サーバーで例外が発生したという事実がわからなくなる。</span><span class="sxs-lookup"><span data-stu-id="f2276-108">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="f2276-109">ASP.NET Core 5.0 のこの誤解を招くエラーに対処するために、例外ハンドラーが見つからない場合、`ExceptionHandlerMiddleware` からは元の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f2276-109">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="f2276-110">その結果、サーバーによって HTTP 500 応答が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f2276-110">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="f2276-111">この応答であれば、発生したエラーをデバッグするときにサーバー ログで簡単に調べることができます。</span><span class="sxs-lookup"><span data-stu-id="f2276-111">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="f2276-112">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2276-112">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f2276-113">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f2276-113">Version introduced</span></span>

<span data-ttu-id="f2276-114">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="f2276-114">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="f2276-115">以前の動作</span><span class="sxs-lookup"><span data-stu-id="f2276-115">Old behavior</span></span>

<span data-ttu-id="f2276-116">構成された例外ハンドラーが見つからない場合は、Exception Handler Middleware によって HTTP 404 応答が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f2276-116">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="f2276-117">新しい動作</span><span class="sxs-lookup"><span data-stu-id="f2276-117">New behavior</span></span>

<span data-ttu-id="f2276-118">構成された例外ハンドラーが見つからない場合は、Exception Handler Middleware からは元の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f2276-118">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f2276-119">変更理由</span><span class="sxs-lookup"><span data-stu-id="f2276-119">Reason for change</span></span>

<span data-ttu-id="f2276-120">HTTP 404 エラーを受け取っても、サーバーで例外が発生したことが明らかにはなりません。</span><span class="sxs-lookup"><span data-stu-id="f2276-120">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="f2276-121">この変更により、HTTP 500 エラーが生成され、次のことが明らかになります。</span><span class="sxs-lookup"><span data-stu-id="f2276-121">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="f2276-122">問題の原因はユーザー エラーではない。</span><span class="sxs-lookup"><span data-stu-id="f2276-122">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="f2276-123">サーバー上で例外が発生した。</span><span class="sxs-lookup"><span data-stu-id="f2276-123">An exception was encountered on the server.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f2276-124">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f2276-124">Recommended action</span></span>

<span data-ttu-id="f2276-125">API の変更はありません。</span><span class="sxs-lookup"><span data-stu-id="f2276-125">There are no API changes.</span></span> <span data-ttu-id="f2276-126">既存のすべてのアプリは引き続きコンパイルされ、実行されます。</span><span class="sxs-lookup"><span data-stu-id="f2276-126">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="f2276-127">スローされた例外は、サーバーによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="f2276-127">The exception thrown is handled by the server.</span></span> <span data-ttu-id="f2276-128">たとえば、例外は [Kestrel](/aspnet/core/fundamentals/servers/kestrel) または [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys) によって HTTP 500 エラー応答に変換されます。</span><span class="sxs-lookup"><span data-stu-id="f2276-128">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f2276-129">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f2276-129">Affected APIs</span></span>

<span data-ttu-id="f2276-130">なし</span><span class="sxs-lookup"><span data-stu-id="f2276-130">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
