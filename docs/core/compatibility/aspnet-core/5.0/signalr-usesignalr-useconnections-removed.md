---
title: 破壊的変更:SignalR:UseSignalR メソッドと UseConnections メソッドが削除された
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: SignalR:UseSignalR メソッドと UseConnections メソッドが削除された'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 3b6e301ee8414a503f7b3697d3b1a01174a1cefb
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497100"
---
# <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="5740b-103">SignalR:UseSignalR メソッドと UseConnections メソッドが削除された</span><span class="sxs-lookup"><span data-stu-id="5740b-103">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="5740b-104">ASP.NET Core 3.0 の SignalR では、エンドポイント ルーティングが採用されました。</span><span class="sxs-lookup"><span data-stu-id="5740b-104">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="5740b-105">その変更の一環として、<xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>、<xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>、およびいくつかの関連するメソッドが古い機能としてマークされました。</span><span class="sxs-lookup"><span data-stu-id="5740b-105">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="5740b-106">ASP.NET Core 5.0 では、これらの古いメソッドが削除されました。</span><span class="sxs-lookup"><span data-stu-id="5740b-106">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="5740b-107">メソッドの完全な一覧については、「[影響を受ける API](#affected-apis)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5740b-107">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="5740b-108">この問題に関するディスカッションについては、[dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5740b-108">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="5740b-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="5740b-109">Version introduced</span></span>

<span data-ttu-id="5740b-110">5.0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="5740b-110">5.0 Preview 3</span></span>

## <a name="old-behavior"></a><span data-ttu-id="5740b-111">以前の動作</span><span class="sxs-lookup"><span data-stu-id="5740b-111">Old behavior</span></span>

<span data-ttu-id="5740b-112">SignalR のハブと接続ハンドラーは、`UseSignalR` または `UseConnections` メソッドを使用して、ミドルウェア パイプラインで登録できました。</span><span class="sxs-lookup"><span data-stu-id="5740b-112">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="5740b-113">新しい動作</span><span class="sxs-lookup"><span data-stu-id="5740b-113">New behavior</span></span>

<span data-ttu-id="5740b-114">SignalR のハブと接続ハンドラーは、<xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> の <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> および <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> 拡張メソッドを使用して、<xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> 内で登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5740b-114">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="5740b-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="5740b-115">Reason for change</span></span>

<span data-ttu-id="5740b-116">以前のメソッドには、ASP.NET Core の他のルーティング コンポーネントとやり取りしないカスタム ルーティング ロジックがありました。</span><span class="sxs-lookup"><span data-stu-id="5740b-116">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="5740b-117">ASP.NET Core 3.0 では、エンドポイント ルーティングと呼ばれる新しい汎用ルーティング システムが導入されました。</span><span class="sxs-lookup"><span data-stu-id="5740b-117">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="5740b-118">エンドポイント ルーティングにより、SignalR は他のルーティング コンポーネントとやり取りできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="5740b-118">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="5740b-119">このモデルに切り替えることで、ユーザーはエンドポイント ルーティングの利点を最大限に活用できます。</span><span class="sxs-lookup"><span data-stu-id="5740b-119">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="5740b-120">そのため、古いメソッドは削除されています。</span><span class="sxs-lookup"><span data-stu-id="5740b-120">Consequently, the old methods have been removed.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="5740b-121">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="5740b-121">Recommended action</span></span>

<span data-ttu-id="5740b-122">プロジェクトの `Startup.Configure` メソッドから、`UseSignalR` または `UseConnections` を呼び出すコードを削除します。</span><span class="sxs-lookup"><span data-stu-id="5740b-122">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="5740b-123">それを、`UseEndpoints` の呼び出しの本体内で、それぞれ `MapHub` または `MapConnectionHandler` の呼び出しに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5740b-123">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="5740b-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5740b-124">For example:</span></span>

<span data-ttu-id="5740b-125">**古いコード:**</span><span class="sxs-lookup"><span data-stu-id="5740b-125">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="5740b-126">**新しいコード:**</span><span class="sxs-lookup"><span data-stu-id="5740b-126">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="5740b-127">一般に、以前の `MapHub` および `MapConnectionHandler` の呼び出しは、ほとんどまたはまったく変更を行わずに、`UseSignalR` および `UseConnections` の本体から `UseEndpoints` に直接移すことができます。</span><span class="sxs-lookup"><span data-stu-id="5740b-127">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="5740b-128">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="5740b-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->
